---
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: ea7f57b8812dca3dfcb4908730dd788182d50c5c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347613"
---
# <a name="non-generic-parallelforeach"></a>Genel olmayan ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], <xref:System.Collections.Generic.IEnumerable%601> koleksiyonları arasında yineleme sağlayan <xref:System.Activities.Statements.ParallelForEach%601>de dahil olmak üzere bir denetim akışı etkinliği kümesi araç kutusuna gönderilir.

<xref:System.Activities.Statements.ParallelForEach%601>, <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> özelliğinin <xref:System.Collections.Generic.IEnumerable%601>türünde olmasını gerektirir. Bu, kullanıcıların <xref:System.Collections.Generic.IEnumerable%601> arabirimi (örneğin, <xref:System.Collections.ArrayList>) uygulayan veri yapıları üzerinde yinelenmesine neden olacak. <xref:System.Activities.Statements.ParallelForEach%601> genel olmayan sürümü bu gereksinimi, koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına göre daha fazla gelir.

Bu örnek, genel olmayan <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik <xref:System.Collections.ArrayList>üzerinden yinelemek için kullanılabilir.

## <a name="parallelforeach-activity"></a>ParallelForEach etkinliği

C#/Visual Basic `foreach` ifade, bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] denk etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> etkinliği bir değer ve gövde listesi içerir. Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.

<xref:System.Activities.Statements.ParallelForEach%601>, <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> değerlendirmesi `true`döndürürse <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin erken tamamlanabilmesi için bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>vardır. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> her yineleme tamamlandıktan sonra değerlendirilir.

Çoğu durumda, etkinliğin genel sürümü tercih edilen çözüm olmalıdır, çünkü kullanıldığı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar. Genel olmayan sürüm, genel olmayan <xref:System.Collections.IEnumerable> arabirimini uygulayan türler arasında yineleme yapmak için kullanılabilir.

## <a name="class-definition"></a>Sınıf tanımı

Aşağıdaki kod örneği, genel olmayan `ParallelForEach` etkinliğinin tanımını gösterir.

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
Koleksiyondaki her öğe için yürütülen <xref:System.Object>türü <xref:System.Activities.ActivityAction>. Bağımsız değişken özelliği aracılığıyla her bir öğe gövdeye iletilir.

Değerler (isteğe bağlı) \
Tekrarlandırılmış öğelerin koleksiyonu. Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.

CompletionCondition (isteğe bağlı) \
<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> özelliği herhangi bir yineleme tamamlandıktan sonra değerlendirilir. `true`değerlendirilirse, zamanlanan bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, dallar koleksiyonundaki tüm etkinlikler tamamlanana kadar yürütülür.

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

Örnek için etkinlik Tasarımcısı, yerleşik <xref:System.Activities.Statements.ParallelForEach%601> etkinliği için sunulan tasarımcı görünümünde benzerdir. Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür. Tasarımcı araç kutusunda **ParallelForEachWithBodyFactory** olarak adlandırılır, çünkü etkinlik, uygun şekilde yapılandırılmış bir <xref:System.Activities.ActivityAction>etkinlik oluşturan araç kutusunda bir <xref:System.Activities.Presentation.IActivityTemplateFactory> kullanıma sunar.

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

2. Derleme ve projeyi çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
