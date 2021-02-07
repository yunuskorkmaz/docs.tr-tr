---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: genel olmayan ParallelForEach'
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 9eaa4ed565fa00a0479f21d907fe5433317d88f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741945"
---
# <a name="non-generic-parallelforeach"></a>Genel olmayan ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] , kendi araç kutusunda, <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonlar arasında yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir <xref:System.Collections.Generic.IEnumerable%601> .

<xref:System.Activities.Statements.ParallelForEach%601><xref:System.Activities.Statements.ParallelForEach%601.Values%2A>özelliğinin türünde olması gerekir <xref:System.Collections.Generic.IEnumerable%601> . Bu <xref:System.Collections.Generic.IEnumerable%601> , kullanıcıların arabirimi (örneğin,) uygulayan veri yapıları üzerinde yinelenmesine neden olacak <xref:System.Collections.ArrayList> . Genel olmayan sürüm, <xref:System.Activities.Statements.ParallelForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.

Bu örnek, genel olmayan bir <xref:System.Activities.Statements.ParallelForEach%601> etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik, üzerinden yinelemek için kullanılabilir <xref:System.Collections.ArrayList> .

## <a name="parallelforeach-activity"></a>ParallelForEach etkinliği

C#/Visual Basic `foreach` ifade bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur. [!INCLUDE[wf1](../../../../includes/wf1-md.md)]Eşdeğer etkinlikler <xref:System.Activities.Statements.ForEach%601> ve ' dir <xref:System.Activities.Statements.ParallelForEach%601> . <xref:System.Activities.Statements.ForEach%601>Etkinlik bir değer ve gövde listesi içerir. Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.

<xref:System.Activities.Statements.ParallelForEach%601> , ' a sahip olduğundan <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> , <xref:System.Activities.Statements.ParallelForEach%601> geri dönüşler değerlendirmesi durumunda etkinliğin erken tamamlanabilmesi için <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> `true` . <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>Her yineleme tamamlandıktan sonra değerlendirilir.

Çoğu durumda, etkinliğin genel sürümü tercih edilen çözüm olmalıdır, çünkü kullanıldığı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar. Genel olmayan sürüm, genel olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir <xref:System.Collections.IEnumerable> .

## <a name="class-definition"></a>Sınıf tanımı

Aşağıdaki kod örneği, genel olmayan bir etkinliğin tanımını gösterir `ParallelForEach` .

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

Gövde (isteğe bağlı) \
<xref:System.Activities.ActivityAction> <xref:System.Object> Koleksiyondaki her öğe için yürütülen türü. Bağımsız değişken özelliği aracılığıyla her bir öğe gövdeye iletilir.

Değerler (isteğe bağlı) \
Tekrarlandırılmış öğelerin koleksiyonu. Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.

CompletionCondition (isteğe bağlı) \
<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>Özellik, herhangi bir yineleme tamamlandıktan sonra değerlendirilir. Olarak değerlendirilirse `true` , zamanlanan bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, dallar koleksiyonundaki tüm etkinlikler tamamlanana kadar yürütülür.

## <a name="example-of-using-parallelforeach"></a>ParallelForEach kullanma örneği

Aşağıdaki kod, bir uygulamada ParallelForEach etkinliğinin nasıl kullanılacağını göstermektedir.

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a>ParallelForEach Tasarımcısı

Örnek için etkinlik Tasarımcısı, yerleşik etkinlik için sunulan tasarımcı görünümünde benzerdir <xref:System.Activities.Statements.ParallelForEach%601> . Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür. Tasarımcı araç kutusunda **ParallelForEachWithBodyFactory** olarak adlandırılır, çünkü etkinlik, <xref:System.Activities.Presentation.IActivityTemplateFactory> düzgün bir şekilde yapılandırılmış olan etkinliği oluşturan araç kutusunda bir araç gösterir <xref:System.Activities.ActivityAction> .

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın.

    1. **Codetekstclient** , kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.

    2. **DesignerTestClient** , etkinliğin tasarımcı içinde nasıl kullanılacağını gösterir.

2. Projeyi derleyin ve çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
