---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 9678d929375857a76d01f575e637a069b0911ae5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283581"
---
# <a name="non-generic-foreach"></a>Genel Olmayan ForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] , kendi araç kutusunda, <xref:System.Activities.Statements.ForEach%601> koleksiyonlar arasında yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir <xref:System.Collections.Generic.IEnumerable%601> .  
  
 <xref:System.Activities.Statements.ForEach%601><xref:System.Activities.Statements.ForEach%601.Values%2A>özelliğinin türünde olması gerekir <xref:System.Collections.Generic.IEnumerable%601> . Bu <xref:System.Collections.Generic.IEnumerable%601> , kullanıcıların arabirimi (örneğin,) uygulayan veri yapıları üzerinde yinelenmesine neden olacak <xref:System.Collections.ArrayList> . Genel olmayan sürüm, <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.  
  
 Bu örnek, genel olmayan bir <xref:System.Activities.Statements.ForEach%601> etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik, üzerinden yinelemek için kullanılabilir <xref:System.Collections.ArrayList> .  
  
## <a name="foreach-activity"></a>ForEach etkinliği  

 C#/Visual Basic `foreach` ifade bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur. [!INCLUDE[wf1](../../../../includes/wf1-md.md)]Eşdeğer etkinlikleri `foreach` <xref:System.Activities.Statements.ForEach%601> ve ' dir <xref:System.Activities.Statements.ParallelForEach%601> . <xref:System.Activities.Statements.ForEach%601>Etkinlik bir değer ve gövde listesi içerir. Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.  
  
 Çoğu durumda, etkinliğin genel sürümünün tercih edilen çözüm olması gerekir, çünkü bu, kullanılacağı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar. Genel olmayan sürüm, genel olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir <xref:System.Collections.IEnumerable> .  
  
## <a name="class-definition"></a>Sınıf tanımı  

 Aşağıdaki kod örneği genel olmayan bir etkinliğin tanımını gösterir `ForEach` .  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 Gövde (isteğe bağlı)  
 <xref:System.Activities.ActivityAction> <xref:System.Object> Koleksiyondaki her öğe için yürütülen türü. Her tek öğe, özelliği aracılığıyla gövdeye geçirilir `Argument` .  
  
 Değerler (isteğe bağlı)  
 Tekrarlandırılmış öğelerin koleksiyonu. Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.  
  
## <a name="example-of-using-foreach"></a>ForEach kullanma örneği  

 Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını göstermektedir.  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|Koşul|İleti|Önem derecesi|Özel durum türü|  
|---------------|-------------|--------------|--------------------|  
|Değerler `null`|Gerekli etkinlik bağımsız değişkeni ' Values ' değeri sağlanmadı.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Tasarımcısı  

 Örnek için etkinlik Tasarımcısı, yerleşik etkinlik için sunulan tasarımcı görünümünde benzerdir <xref:System.Activities.Statements.ForEach%601> . Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür. Tasarımcı araç kutusunda **ForEachWithBodyFactory** olarak adlandırılır çünkü etkinlik, düzgün bir şekilde <xref:System.Activities.Presentation.IActivityTemplateFactory> yapılandırılmış olan etkinliği oluşturur <xref:System.Activities.ActivityAction> .  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1. Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın:  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
