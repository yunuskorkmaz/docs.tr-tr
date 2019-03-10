---
title: Windows Workflow mimarisi
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 5d6e1ead9184bfb61eb466389671ca2e74264ae3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723757"
---
# <a name="windows-workflow-architecture"></a>Windows Workflow mimarisi
Windows Workflow Foundation (WF) etkileşimli uzun süre çalışan uygulamalar geliştirmek için Özet düzeyine başlatır. İş birimleri etkinlikleri kapsüllenir. Etkinlikleri olanakları sağlayan akış denetimi, özel durum işleme, hata yayma, durumu verilerini, yüklenmesi ve kaldırılması bellek, izleme ve işlem akışı devam eden iş akışı kalıcılığı için bir ortamda çalıştırın.  
  
## <a name="activity-architecture"></a>Etkinlik mimarisi  
 Etkinlik öğesinden türetilen türler CLR olarak geliştirilen <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.NativeActivity>, veya bir değer döndürmesi türevlerini <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, veya <xref:System.Activities.NativeActivity%601>. Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.Activity> hızlı bir şekilde yürütülen iş akışı ortamında iş birimleri oluşturmak için önceden var olan etkinlikleri birleştirin izin verir. <xref:System.Activities.CodeActivity>, diğer taraftan, yönetilen kod kullanarak yazılması gereken yürütme mantığı sağlayan <xref:System.Activities.CodeActivityContext> etkinlik bağımsız değişkenlere erişmek için öncelikle. <xref:System.Activities.AsyncCodeActivity> benzer <xref:System.Activities.CodeActivity> dışında zaman uyumsuz görevler uygulamak için kullanılabilir. Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.NativeActivity> çalışma zamanı aracılığıyla erişmesine olanak tanır <xref:System.Activities.NativeActivityContext> zaman uyumsuz işler, kayıt işlemleri ve diğer öğeleri için yer işaretleri, oluşturma, zamanlama gibi işlevler için çağırma.  
  
 Öğesinden türetilen etkinlikleri yazma <xref:System.Activities.Activity> bildirime dayalı olduğu ve bu etkinlikler XAML içinde yazılabilir. Aşağıdaki örnekte, bir etkinlik olarak adlandırılan `Prompt` yürütme gövdesi için diğer etkinlikleri kullanarak oluşturulur.  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>Etkinlik bağlamı  
 <xref:System.Activities.ActivityContext> Etkinlik yazarın arabirimi iş akışı çalışma zamanı ve çalışma zamanının zengin özelliklerini erişim sağlar. Aşağıdaki örnekte, Etkinlik yürütme bağlamı bir yer işareti (bir devamlılık noktası etkinliğini veri geçirme bir ana bilgisayar tarafından devam ettirilebilir yürütülmesinin kaydetmek bir etkinliği sağlar mekanizması) oluşturmak için kullandığı tanımlanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Etkinlik yaşam döngüsü  
 İçinde bir etkinlik örneği başlar <xref:System.Activities.ActivityInstanceState.Executing> durumu. Özel durumlar karşılaşılan sürece tüm alt etkinlik yürütme ve diğer bekleyen iş tamamlanana kadar bu durumda kalır (<xref:System.Activities.Bookmark> nesneleri, örneğin) tamamlandığında, hangi geçişleri noktası konumunda <xref:System.Activities.ActivityInstanceState.Closed> durumu. Bir etkinlik örneğinin üst alt iptal etmek isteyebilir; alt iptal edilmesi durumunda tamamlanırsa <xref:System.Activities.ActivityInstanceState.Canceled> durumu. Yürütme sırasında bir özel durum oluşturulursa, çalışma zamanı etkinliğini koyar <xref:System.Activities.ActivityInstanceState.Faulted> belirtin ve etkinliklerin üst zincir oluşturan bir özel durum yayar. Bir etkinliğin üç tamamlanma durumu aşağıda verilmiştir:  
  
-   **Kapalı:** Etkinlik, iş tamamlandı ve çıkıldı.  
  
-   **İptal edildi:** Etkinlik düzgün bir şekilde çalışmasını terk ve çıkıldı. Bu durum geri girildiğinde, iş açıkça döndürülmez.  
  
-   **Hatalı:** Etkinlik, bir hatayla karşılaştı ve çalışmasını tamamlamadan çıkıldı.  
  
 Etkinlikleri kalabilir <xref:System.Activities.ActivityInstanceState.Executing> kalıcı veya kaldırıldı durumu.
