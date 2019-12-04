---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: a4bbc594ec0bf2d387e700508c7d92685216accc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715649"
---
# <a name="non-generic-foreach"></a>Genel Olmayan ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], <xref:System.Collections.Generic.IEnumerable%601> koleksiyonları arasında yineleme sağlayan <xref:System.Activities.Statements.ForEach%601>de dahil olmak üzere bir denetim akışı etkinliği kümesi araç kutusuna gönderilir.  
  
 <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.ForEach%601.Values%2A> özelliğinin <xref:System.Collections.Generic.IEnumerable%601>türünde olmasını gerektirir. Bu, kullanıcıların <xref:System.Collections.Generic.IEnumerable%601> arabirimi (örneğin, <xref:System.Collections.ArrayList>) uygulayan veri yapıları üzerinde yinelenmesine neden olacak. <xref:System.Activities.Statements.ForEach%601> genel olmayan sürümü bu gereksinimi, koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına göre daha fazla gelir.  
  
 Bu örnek, genel olmayan <xref:System.Activities.Statements.ForEach%601> etkinliğinin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik <xref:System.Collections.ArrayList>üzerinden yinelemek için kullanılabilir.  
  
## <a name="foreach-activity"></a>ForEach etkinliği  
 C#/Vb `foreach` ifade, bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur. `foreach` [!INCLUDE[wf1](../../../../includes/wf1-md.md)] denk etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> etkinliği bir değer ve gövde listesi içerir. Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.  
  
 Çoğu durumda, etkinliğin genel sürümünün tercih edilen çözüm olması gerekir, çünkü bu, kullanılacağı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar. Genel olmayan sürüm, genel olmayan <xref:System.Collections.IEnumerable> arabirimini uygulayan türler arasında yineleme yapmak için kullanılabilir.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneği, genel olmayan `ForEach` etkinliğinin tanımını gösterir.  
  
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
 Koleksiyondaki her öğe için yürütülen <xref:System.Object>türü <xref:System.Activities.ActivityAction>. Her bireysel öğe, `Argument` özelliği aracılığıyla gövdeye geçirilir.  
  
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
  
|Koşul|İleti|Önem Derecesi|Özel durum türü|  
|---------------|-------------|--------------|--------------------|  
|Değerler `null`|Gerekli etkinlik bağımsız değişkeni ' Values ' değeri sağlanmadı.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Tasarımcısı  
 Örnek için etkinlik Tasarımcısı, yerleşik <xref:System.Activities.Statements.ForEach%601> etkinliği için sunulan tasarımcı görünümünde benzerdir. Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür. Tasarımcı araç kutusunda **ForEachWithBodyFactory** olarak adlandırılır çünkü <xref:System.Activities.Presentation.IActivityTemplateFactory> etkinlik, düzgün şekilde yapılandırılmış bir <xref:System.Activities.ActivityAction>sahip etkinliği oluşturur.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
