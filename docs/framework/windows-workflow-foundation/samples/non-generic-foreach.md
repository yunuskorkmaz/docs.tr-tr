---
title: Genel olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: c67f6e3c3afb893f7bb5713d64ce2f119eebc157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519486"
---
# <a name="non-generic-foreach"></a>Genel olmayan ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] kendi araç kutusunda etkinlikleri, akış denetimi dahil olmak üzere bir dizi gelir <xref:System.Activities.Statements.ForEach%601>, böylece üzerinden yineleme <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.  
  
 <xref:System.Activities.Statements.ForEach%601> gerektirir, <xref:System.Activities.Statements.ForEach%601.Values%2A> türünde olması özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Bu uygulama veri yapıları yineleme kullanıcılar önleyen <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>). Genel olmayan sürümü <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değerlerin türleri uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklık ödün verme pahasına bu gereksinimi ortadan kaldırır.  
  
 Bu örnek, genel olmayan uygulamak gösterilmiştir <xref:System.Activities.Statements.ForEach%601> etkinliği ve onun Tasarımcısı. Bu etkinlik yinelemek için kullanılabilecek <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>ForEach etkinliği  
 C# /VB `foreach` deyimi koleksiyonunun her öğe için katıştırılmış bir deyimi yürütme bir koleksiyonun öğelerini numaralandırır. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinliklerini `foreach` olan <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir. Çalışma zamanında listesi yinelendiğinde ve listedeki her bir değer için gövdesi yürütülür.  
  
 Kullanılacak ve tür derleme zamanında denetlemesini sağlar senaryoları çoğunu kapsar çünkü çoğu durumda, tercih edilen bir çözüm etkinlik genel sürümü olmalıdır. Genel olmayan uygulama türleri aracılığıyla yineleme için genel olmayan sürüm kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneğinde genel olmayan tanımını gösterir `ForEach` etkinlik.  
  
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
 <xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için yürütüldü. Her öğesi gövdesine geçirilen kendi `Argument` özelliği.  
  
 Değerleri (isteğe bağlı)  
 Üzerinden yinelendiğinde öğeleri koleksiyonu. Tüm koleksiyon öğelerini uyumlu türleri emin olma çalışma zamanında yapılır.  
  
## <a name="example-of-using-foreach"></a>ForEach kullanma örneği  
 Aşağıdaki kod bir uygulamada ForEach etkinlik kullanımı gösterilmiştir.  
  
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
  
|Koşul|İleti|Önem Derecesi|Özel durum türü|  
|---------------|-------------|--------------|--------------------|  
|Değerler `null`|Gerekli etkinlik bağımsız değişkeni 'Değerleri' için değer girilmedi.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Tasarımcısı  
 Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcısı görünümüne benzer <xref:System.Activities.Statements.ForEach%601> etkinlik. Araç kutusunda Tasarımcı görünür **örnekleri**, **olmayan genel etkinlikleri** kategorisi. Tasarımcı adlı **ForEachWithBodyFactory** araç kutusunda etkinlik sunan çünkü bir <xref:System.Activities.Presentation.IActivityTemplateFactory> araç kutusunda oluşturan etkinliğin bir düzgün yapılandırılmış <xref:System.Activities.ActivityAction>.  
  
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
  
1.  Projenin tercih ettiğiniz çözüm başlangıç projesi olarak ayarla:  
  
    1.  **CodeTestClient** kodu kullanarak etkinliğini kullanmayı gösterir.  
  
    2.  **DesignerTestClient** etkinlik Tasarımcısı'nda kullanmayı gösterir.  
  
2.  Oluşturun ve projeyi çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
