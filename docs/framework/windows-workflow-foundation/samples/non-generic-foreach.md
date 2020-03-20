---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142712"
---
# <a name="non-generic-foreach"></a>Genel Olmayan ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]alet çantasında, koleksiyonlar aracılığıyla <xref:System.Activities.Statements.ForEach%601> <xref:System.Collections.Generic.IEnumerable%601> yineleme sağlayan, dahil olmak üzere bir dizi Kontrol Akışı aktivitesi gemi.  
  
 <xref:System.Activities.Statements.ForEach%601>özelliğinin <xref:System.Activities.Statements.ForEach%601.Values%2A> türünün <xref:System.Collections.Generic.IEnumerable%601>olmasını gerektirir. Bu, kullanıcıların arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601> veri yapıları üzerinde yinelemelerini <xref:System.Collections.ArrayList>(örneğin,) engellemez. Genel olmayan sürümü, <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamak için daha fazla çalışma süresi karmaşıklığı pahasına bu gereksinimin üstesinden gelir.  
  
 Bu örnek, genel <xref:System.Activities.Statements.ForEach%601> olmayan bir etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir. Bu etkinlik, <xref:System.Collections.ArrayList>'' ile yinelemek için kullanılabilir.  
  
## <a name="foreach-activity"></a>Foreach Etkinliği  
 C#/Visual Basic `foreach` deyimi, koleksiyonun her öğesi için katışılmış bir deyim çalıştırarak koleksiyonun öğelerini numaralandırır. Eşdeğer [!INCLUDE[wf1](../../../../includes/wf1-md.md)] faaliyetleri `foreach` ve <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>. Etkinlik, <xref:System.Activities.Statements.ForEach%601> değerlerin ve gövdenin bir listesini içerir. Çalışma zamanında, liste yinelenir ve gövde listedeki her değer için yürütülür.  
  
 Çoğu durumda, kullanılacağı senaryoların çoğunu kapsadığından ve derleme zamanında tür denetimi sağladığından, etkinliğin genel sürümü tercih edilen çözüm olmalıdır. Genel olmayan sürüm, genel <xref:System.Collections.IEnumerable> olmayan arabirimi uygulayan türleri yineleştirmek için kullanılabilir.  
  
## <a name="class-definition"></a>Sınıf Tanımı  
 Aşağıdaki kod örneği, genel `ForEach` olmayan bir etkinliğin tanımını gösterir.  
  
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
 <xref:System.Activities.ActivityAction> Koleksiyondaki <xref:System.Object>her öğe için yürütülen tür. Her bir element kendi `Argument` özelliği aracılığıyla Vücuda geçirilir.  
  
 Değerler (isteğe bağlı)  
 Üzerinde yinelenir öğelerin koleksiyonu. Koleksiyonun tüm öğelerinin uyumlu türlerde olmasını sağlamak çalışma zamanında yapılır.  
  
## <a name="example-of-using-foreach"></a>ForEach Kullanma Örneği  
 Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını gösterir.  
  
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
  
|Koşul|İleti|Severity|Özel Durum Türü|  
|---------------|-------------|--------------|--------------------|  
|Değerler,`null`|Gerekli bir etkinlik bağımsız değişkeni 'Değerler' için değer sağlanmadı.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Foreach Tasarımcısı  
 Örnek için etkinlik tasarımcısı, yerleşik <xref:System.Activities.Statements.ForEach%601> etkinlik için sağlanan tasarımcıya görünüm olarak benzerdir. Tasarımcı, **Örnekler**, **Genel Olmayan Etkinlikler** kategorisinde ki araç kutusunda görünür. Etkinlik, düzgün yapılandırılmış bir aktivite oluşturur araç kutusunda bir <xref:System.Activities.Presentation.IActivityTemplateFactory> ortaya çıkarır, çünkü tasarımcı, araç kutusunda **ForEachWithBodyFactory** <xref:System.Activities.ActivityAction>adlandırılır.  
  
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
  
1. Seçtiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın:  
  
    1. **CodeTestClient,** kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.  
  
    2. **DesignerTestClient,** tasarımcı içindeki etkinliğin nasıl kullanılacağını gösterir.  
  
2. Projeyi oluşturun ve çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
