---
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514141"
---
# <a name="non-generic-parallelforeach"></a>Genel olmayan ParallelForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] kendi araç kutusunda etkinlikler, akış denetimi dahil olmak üzere bir dizi birlikte gelen <xref:System.Activities.Statements.ParallelForEach%601>, üzerinden yineleme olanak tanıyan <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> gerektirir, <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> türünde olmasını özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Bu kullanıcılar, uygulama veri yapıları üzerinde yineleme gelen ışığının <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>). Genel olmayan sürümü <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonundaki değerleri türlerinin uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı çoğaltamaz bu gereksinimi ortadan kaldırır.  
  
 Bu örnek, genel olmayan bir uygulama gösterilmektedir <xref:System.Activities.Statements.ParallelForEach%601> etkinlik ve iş Tasarımcısı. Bu etkinlik yinelemek için kullanılabilir <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>ParallelForEach etkinliği  
 C# /VB `foreach` deyimi koleksiyonundaki her öğe için bir katıştırılmış deyim yürütülürken, bir koleksiyonun öğeleri sıralar. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir. Çalışma zamanında, listenin yinelenir ve listedeki her değerin gövdesi yürütülür.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> sahip bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, böylece <xref:System.Activities.Statements.ParallelForEach%601> etkinliği tamamlamak erken varsa değerlendirmesi <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> döndürür `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Her yineleme tamamlandıktan sonra değerlendirilir.  
  
 Burada kullanılır ve derleme zamanında tür sağlar senaryoları çoğunu kapsar için çoğu durumda, tercih edilen bir çözüm etkinliğin genel sürüm olmamalıdır. Genel olmayan sürümü, genel olmayan uygulayan türler yineleme için kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.  
  
## <a name="class-definition"></a>Sınıf tanımı  
 Aşağıdaki kod örneği, genel olmayan bir tanımı gösterilmektedir `ParallelForEach` etkinliktir.  
  
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
 <xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için gerçekleştirilir. Her bağımsız öğede gövdesine, bağımsız değişken özelliği üzerinden geçirilir.  
  
 Değer (isteğe bağlı)  
 Üzerinden yinelenir öğeleri koleksiyonu. Tüm koleksiyon öğelerini uyumlu bir tür olduğundan emin olmak için çalışma zamanında gerçekleştirilir.  
  
 CompletionCondition (isteğe bağlı)  
 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Özelliği, tüm yineleme tamamlandıktan sonra değerlendirilir. Değerlendirilirse `true`, sonra zamanlanan yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, dallar koleksiyondaki tüm etkinlikleri işlem tamamlanana kadar yürütün.  
  
## <a name="example-of-using-parallelforeach"></a>ParallelForEach kullanma örneği  
 Aşağıdaki kod bir uygulamada ParallelForEach etkinlik kullanmayı gösterir.  
  
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
 Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcı görünümü benzer <xref:System.Activities.Statements.ParallelForEach%601> etkinlik. Tasarımcı araç kutusunda görünür **örnekleri**, **genel olmayan etkinlikler** kategorisi. Tasarımcı adlı **ParallelForEachWithBodyFactory** Araç Kutusu'nda, etkinlik kullanıma sunduğundan bir <xref:System.Activities.Presentation.IActivityTemplateFactory> etkinliği bir düzgün bir şekilde yapılandırılmış oluşturan araç kutusunda <xref:System.Activities.ActivityAction>.  
  
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
  
1.  Seçtiğiniz proje, çözümün başlangıç projesi olarak ayarlayın.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
