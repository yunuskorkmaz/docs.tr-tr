---
title: Genel olmayan ParallelForEach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eb019aed7fce267506ddb495609df5a80a8f8d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="non-generic-parallelforeach"></a>Genel olmayan ParallelForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]kendi araç kutusunda etkinlikleri, akış denetimi dahil olmak üzere bir dizi gelir <xref:System.Activities.Statements.ParallelForEach%601>, böylece üzerinden yineleme <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>gerektirir, <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> türünde olması özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Bu uygulama veri yapıları yineleme kullanıcılar önleyen <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>). Genel olmayan sürümü <xref:System.Activities.Statements.ParallelForEach%601> koleksiyondaki değerlerin türleri uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklık ödün verme pahasına bu gereksinimi ortadan kaldırır.  
  
 Bu örnek, genel olmayan uygulamak gösterilmiştir <xref:System.Activities.Statements.ParallelForEach%601> etkinliği ve onun Tasarımcısı. Bu etkinlik yinelemek için kullanılabilecek <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>ParallelForEach etkinliği  
 C# /VB `foreach` deyimi koleksiyonunun her öğe için katıştırılmış bir deyimi yürütme bir koleksiyonun öğelerini numaralandırır. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir. Çalışma zamanında listesi yinelendiğinde ve listedeki her bir değer için gövdesi yürütülür.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>sahip bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, böylece <xref:System.Activities.Statements.ParallelForEach%601> etkinliği tamamlamak erken varsa değerlendirmesi <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> döndürür `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Her bir yineleme tamamlandıktan sonra değerlendirilir.  
  
 Kullanılır ve tür derleme zamanında denetlemesini sağlar senaryoları çoğunu kapsar çünkü çoğu durumda, tercih edilen bir çözüm etkinlik genel sürümü olmalıdır. Genel olmayan uygulama türleri aracılığıyla yineleme için genel olmayan sürüm kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneğinde genel olmayan tanımını gösterir `ParallelForEach` etkinliktir.  
  
```  
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
  
 Gövde (isteğe bağlı)  
 <xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için yürütüldü. Her öğesi gövde kendi bağımsız değişkeni özelliği üzerinden geçirilir.  
  
 Değerleri (isteğe bağlı)  
 Üzerinden yinelendiğinde öğeleri koleksiyonu. Tüm koleksiyon öğelerini uyumlu türleri emin olma çalışma zamanında yapılır.  
  
 CompletionCondition (isteğe bağlı)  
 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Özelliği, tüm yineleme tamamlandıktan sonra değerlendirildiği. Değerlendirilirse `true`, ardından zamanlanan yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, dalları koleksiyonundaki tüm etkinlikleri tamamlanana kadar yürütün.  
  
## <a name="example-of-using-parallelforeach"></a>ParallelForEach kullanma örneği  
 Aşağıdaki kod bir uygulamada ParallelForEach etkinlik kullanımı gösterilmiştir.  
  
```  
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
 Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcısı görünümüne benzer <xref:System.Activities.Statements.ParallelForEach%601> etkinlik. Araç kutusunda Tasarımcı görünür **örnekleri**, **olmayan genel etkinlikleri** kategorisi. Tasarımcı adlı **ParallelForEachWithBodyFactory** araç kutusunda etkinlik sunan çünkü bir <xref:System.Activities.Presentation.IActivityTemplateFactory> etkinlik bir düzgün yapılandırılmış oluşturur araç çubuğundaki <xref:System.Activities.ActivityAction>.  
  
```  
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
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Projenin tercih ettiğiniz çözüm başlangıç projesi olarak ayarla.  
  
    1.  **CodeTestClient** kodu kullanarak etkinliğini kullanmayı gösterir.  
  
    2.  **DesignerTestClient** etkinlik Tasarımcısı'nda kullanmayı gösterir.  
  
2.  Oluşturun ve projeyi çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
