---
title: Windows Workflow Mimarisi
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: e2effc0f53153057b8a9034e4dc80cb19bbe7685
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834861"
---
# <a name="windows-workflow-architecture"></a>Windows Workflow Mimarisi
Windows Workflow Foundation (WF), etkileşimli uzun süre çalışan uygulamalar geliştirmeye yönelik özet düzeyi oluşturur. İş birimleri etkinlik olarak kapsüllenir. Etkinlikler, akış denetimi, özel durum işleme, hata yayma, durum verilerinin kalıcılığı, bellek, izleme ve işlem akışından devam eden iş akışlarını yükleme ve kaldırma olanakları sağlayan bir ortamda çalışır.  
  
## <a name="activity-architecture"></a>Etkinlik mimarisi  
 Etkinlikler, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> veya <xref:System.Activities.NativeActivity> ' ten veya <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> veya <xref:System.Activities.NativeActivity%601> değeri döndüren türevlerini türettirilen CLR türleri olarak geliştirilmiştir. @No__t-0 ' dan türetilen etkinliklerin geliştirilmesi, kullanıcının iş akışı ortamında yürütülen iş birimlerini hızlı bir şekilde oluşturmak için önceden var olan etkinlikleri dermesini sağlar. <xref:System.Activities.CodeActivity>, diğer yandan, etkinlik bağımsız değişkenlerine erişmek için öncelikle <xref:System.Activities.CodeActivityContext> kullanılarak yönetilen kodda yürütme mantığının yazılmasını sağlar. <xref:System.Activities.AsyncCodeActivity>, zaman uyumsuz görevleri uygulamak için kullanılabilmesi dışında <xref:System.Activities.CodeActivity> ile benzerdir. @No__t-0 ' dan türetilen etkinliklerin geliştirilmesi, kullanıcıların çalışma zamanına, alt öğeleri zamanlama, yer işaretleri oluşturma, zaman uyumsuz çalışma çağırma, işlemleri kaydetme ve daha birçok işlev için <xref:System.Activities.NativeActivityContext> aracılığıyla çalışma zamanına erişmelerini sağlar.  
  
 @No__t-0 ' dan türetilen yazma etkinlikleri bildirime göre yapılır ve bu etkinlikler XAML 'de yazılabilir. Aşağıdaki örnekte, yürütme gövdesi için diğer etkinlikler kullanılarak `Prompt` adlı bir etkinlik oluşturulur.  
  
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
 @No__t-0, iş akışı çalışma zamanı için etkinlik yazarının arabirimidir ve çalışma zamanının geniş özelliklerine erişim sağlar. Aşağıdaki örnekte, bir yer işareti oluşturmak için yürütme bağlamını kullanan bir etkinlik tanımlanmıştır (bir etkinliğin yürütmeye, verileri etkinliğe geçen bir konak tarafından sürdürülebilecek bir devamlılık noktası kaydetmesini sağlayan mekanizma).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Etkinlik yaşam döngüsü  
 Etkinliğin bir örneği <xref:System.Activities.ActivityInstanceState.Executing> durumunda başlatılır. Özel durumlarla karşılaşılmadığı sürece, tüm alt etkinliklerin yürütülmesi tamamlanana kadar bu durumda kalır ve diğer bir bekleyen iş (örneğin, <xref:System.Activities.Bookmark> nesneleri) tamamlanır ve bu noktada <xref:System.Activities.ActivityInstanceState.Closed> durumuna geçiş yapar. Etkinlik örneğinin üst öğesi iptal etmek için bir alt öğe isteyebilir; alt öğe iptal edilirse <xref:System.Activities.ActivityInstanceState.Canceled> durumunda tamamlanır. Yürütme sırasında bir özel durum oluşturulursa, çalışma zamanı etkinliği <xref:System.Activities.ActivityInstanceState.Faulted> durumuna geçirir ve özel durumu, etkinlik zincirinin üst zincirini yayar. Etkinliğin üç tamamlanma durumu aşağıda verilmiştir:
  
- **Kapalı:** Etkinlik, işini tamamladı ve çıkıldı.  
  
- **Iptal edildi:** Etkinlik, işini düzgün bir şekilde terk etti ve çıkıldı. Bu durum girildiğinde iş açık bir şekilde geri alınmaz.  
  
- **Hatalı:** Etkinlik bir hatayla karşılaştı ve işi tamamlanmadan çıkıldı.  
  
 Etkinlikler kalıcı veya kaldırılmış olduğunda <xref:System.Activities.ActivityInstanceState.Executing> durumunda kalır.
