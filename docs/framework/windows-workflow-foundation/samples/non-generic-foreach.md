---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: e467534ba2b233f1f3c279e89badf12846c6b7f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038071"
---
# <a name="non-generic-foreach"></a>Genel Olmayan ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], kendi araç kutusunda, <xref:System.Activities.Statements.ForEach%601>koleksiyonlar arasında <xref:System.Collections.Generic.IEnumerable%601> yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir.  
  
 <xref:System.Activities.Statements.ForEach%601><xref:System.Activities.Statements.ForEach%601.Values%2A> özelliğinin türünde<xref:System.Collections.Generic.IEnumerable%601>olması gerekir. Bu, kullanıcıların arabirimi (örneğin, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.ArrayList>) uygulayan veri yapıları üzerinde yinelenmesine neden olacak. Genel olmayan sürüm <xref:System.Activities.Statements.ForEach%601> , koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.  
  
 Bu örnek, genel <xref:System.Activities.Statements.ForEach%601> olmayan bir etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik, üzerinden <xref:System.Collections.ArrayList>yinelemek için kullanılabilir.  
  
## <a name="foreach-activity"></a>ForEach etkinliği  
 C#/Vb `foreach` ekstresi bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur. Eşdeğer etkinlikleri ve <xref:System.Activities.Statements.ForEach%601> ' dir<xref:System.Activities.Statements.ParallelForEach%601>. `foreach` [!INCLUDE[wf1](../../../../includes/wf1-md.md)] <xref:System.Activities.Statements.ForEach%601> Etkinlik bir değer ve gövde listesi içerir. Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.  
  
 Çoğu durumda, etkinliğin genel sürümünün tercih edilen çözüm olması gerekir, çünkü bu, kullanılacağı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar. Genel olmayan sürüm, genel <xref:System.Collections.IEnumerable> olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneği genel `ForEach` olmayan bir etkinliğin tanımını gösterir.  
  
```  
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
 Koleksiyondaki her öğe için yürütülen türü <xref:System.Object>. <xref:System.Activities.ActivityAction> Her tek öğe, `Argument` özelliği aracılığıyla gövdeye geçirilir.  
  
 Değerler (isteğe bağlı)  
 Tekrarlandırılmış öğelerin koleksiyonu. Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.  
  
## <a name="example-of-using-foreach"></a>ForEach kullanma örneği  
 Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını göstermektedir.  
  
```  
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
  
|Koşul|`Message`|Önem Derecesi|Özel Durum Türü|  
|---------------|-------------|--------------|--------------------|  
|Değerler`null`|Gerekli etkinlik bağımsız değişkeni ' Values ' değeri sağlanmadı.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Tasarımcısı  
 Örnek için etkinlik Tasarımcısı, yerleşik <xref:System.Activities.Statements.ForEach%601> etkinlik için sunulan tasarımcı görünümünde benzerdir. Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür. Tasarımcı araç kutusunda **ForEachWithBodyFactory** olarak adlandırılır çünkü etkinlik <xref:System.Activities.Presentation.IActivityTemplateFactory> , düzgün bir şekilde yapılandırılmış <xref:System.Activities.ActivityAction>olan etkinliği oluşturur.  
  
```  
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
  
2. Derleme ve projeyi çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
