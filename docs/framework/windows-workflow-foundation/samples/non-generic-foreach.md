---
title: Genel olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: b94ad54d248af7f6ad45c11b9860dd415db840f9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419323"
---
# <a name="non-generic-foreach"></a>Genel olmayan ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] kendi araç kutusunda etkinlikler, akış denetimi dahil olmak üzere bir dizi birlikte gelen <xref:System.Activities.Statements.ForEach%601>, üzerinden yineleme olanak tanıyan <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.  
  
 <xref:System.Activities.Statements.ForEach%601> gerektirir, <xref:System.Activities.Statements.ForEach%601.Values%2A> türünde olmasını özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Bu kullanıcılar, uygulama veri yapıları üzerinde yineleme gelen ışığının <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>). Genel olmayan sürümü <xref:System.Activities.Statements.ForEach%601> koleksiyonundaki değerleri türlerinin uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı çoğaltamaz bu gereksinimi ortadan kaldırır.  
  
 Bu örnek, genel olmayan bir uygulama gösterilmektedir <xref:System.Activities.Statements.ForEach%601> etkinlik ve iş Tasarımcısı. Bu etkinlik yinelemek için kullanılabilir <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>ForEach etkinliği  
 C# /VB `foreach` deyimi koleksiyonundaki her öğe için bir katıştırılmış deyim yürütülürken, bir koleksiyonun öğeleri sıralar. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinliklerini `foreach` olan <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir. Çalışma zamanında, listenin yinelenir ve listedeki her değerin gövdesi yürütülür.  
  
 Çoğu durumda, kullanılabilir ve derleme zamanında tür sağlar senaryoları çoğunu kapsar için etkinliğin genel sürüm tercih edilen bir çözüm olmamalıdır. Genel olmayan sürümü, genel olmayan uygulayan türler yineleme için kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneği, genel olmayan bir tanımı gösterilmektedir `ForEach` etkinlik.  
  
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
 <xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için gerçekleştirilir. Her bağımsız öğede gövdesine geçirilir, `Argument` özelliği.  
  
 Değer (isteğe bağlı)  
 Üzerinden yinelenir öğeleri koleksiyonu. Tüm koleksiyon öğelerini uyumlu bir tür olduğundan emin olmak için çalışma zamanında gerçekleştirilir.  
  
## <a name="example-of-using-foreach"></a>ForEach kullanma örneği  
 Aşağıdaki kod ForEach etkinliği bir uygulamada kullanma işlemini gösterir.  
  
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
|Değeri. `null`|Povinný argument 'Değerleri' için değer sağlanmadı.|Hata|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Tasarımcısı  
 Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcı görünümü benzer <xref:System.Activities.Statements.ForEach%601> etkinlik. Tasarımcı araç kutusunda görünür **örnekleri**, **genel olmayan etkinlikler** kategorisi. Tasarımcı adlı **ForEachWithBodyFactory** Araç Kutusu'nda, etkinlik kullanıma sunduğundan bir <xref:System.Activities.Presentation.IActivityTemplateFactory> araç kutusunda oluşturan etkinliğin bir düzgün bir şekilde yapılandırılmış <xref:System.Activities.ActivityAction>.  
  
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
  
1.  Seçtiğiniz proje, çözümün başlangıç projesi ayarlayın:  
  
    1.  **CodeTestClient** kod kullanarak etkinliğini kullanma işlemini gösterir.  
  
    2.  **DesignerTestClient** etkinlik Tasarımcısı içinde kullanmayı gösterir.  
  
2.  Derleme ve projeyi çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
