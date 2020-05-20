---
title: Windows Workflow Mimarisi
description: Windows Workflow Foundation, akış denetimi, özel durum işleme ve diğer özelliklerle bir ortamda çalıştırılan iş birimlerini etkinlik olarak kapsüller.
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 22ebeb7d95342ad6843e0721da8b213ed4a4d9b6
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420142"
---
# <a name="windows-workflow-architecture"></a>Windows Workflow Mimarisi
Windows Workflow Foundation (WF), etkileşimli uzun süre çalışan uygulamalar geliştirmeye yönelik özet düzeyi oluşturur. İş birimleri etkinlik olarak kapsüllenir. Etkinlikler, akış denetimi, özel durum işleme, hata yayma, durum verilerinin kalıcılığı, bellek, izleme ve işlem akışından devam eden iş akışlarını yükleme ve kaldırma olanakları sağlayan bir ortamda çalışır.  
  
## <a name="activity-architecture"></a>Etkinlik mimarisi  
 Etkinlikler,,, veya <xref:System.Activities.Activity> bir değer döndüren,,, <xref:System.Activities.CodeActivity> ya <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> da türevlerinden türetilen <xref:System.Activities.Activity%601> <xref:System.Activities.CodeActivity%601> <xref:System.Activities.AsyncCodeActivity%601> clr türleri olarak geliştirilir <xref:System.Activities.NativeActivity%601> . Öğesinden türetilen etkinliklerin geliştirilmesi <xref:System.Activities.Activity> , kullanıcının iş akışı ortamında yürütülen iş birimlerini hızlı bir şekilde oluşturmak için önceden mevcut etkinlikleri oluşturmalarına olanak tanır. <xref:System.Activities.CodeActivity>, diğer yandan, <xref:System.Activities.CodeActivityContext> etkinlik bağımsız değişkenlerine erişmek için öncelikli olarak yönetilen kodda yürütme mantığının yazılmasını sağlar. <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.CodeActivity> zaman uyumsuz görevleri uygulamak için kullanılabilmesi hariç, öğesine benzerdir. Öğesinden türetilen etkinliklerin geliştirilmesi <xref:System.Activities.NativeActivity> , kullanıcıların çalışma zamanına, <xref:System.Activities.NativeActivityContext> alt öğeleri zamanlama, yer işaretleri oluşturma, zaman uyumsuz çalışma çağırma, işlemleri kaydetme ve daha fazlası gibi işlevler için çalışma zamanına erişmelerini sağlar.  
  
 Öğesinden türetilen yazma etkinlikleri <xref:System.Activities.Activity> bildirime göre yapılır ve bu ETKINLIKLER xaml 'de yazılabilir. Aşağıdaki örnekte, adlı bir etkinlik `Prompt` yürütme gövdesi için diğer etkinlikler kullanılarak oluşturulur.  
  
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
 , <xref:System.Activities.ActivityContext> İş akışı çalışma zamanı için etkinlik yazarının arabirimidir ve çalışma zamanının bol özelliklerine erişim sağlar. Aşağıdaki örnekte, bir yer işareti oluşturmak için yürütme bağlamını kullanan bir etkinlik tanımlanmıştır (bir etkinliğin yürütmeye, verileri etkinliğe geçen bir konak tarafından sürdürülebilecek bir devamlılık noktası kaydetmesini sağlayan mekanizma).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Etkinlik yaşam döngüsü  
 Etkinliğin bir örneği <xref:System.Activities.ActivityInstanceState.Executing> durumunda başlatılır. Özel durumlarla karşılaşılmadığı sürece, tüm alt etkinliklerin yürütülmesi bitene ve diğer bekleyen işler (örneğin, nesneler) tamamlanana kadar bu durumda kalır ve bu <xref:System.Activities.Bookmark> noktada duruma geçiş yapar <xref:System.Activities.ActivityInstanceState.Closed> . Etkinlik örneğinin üst öğesi iptal etmek için bir alt öğe isteyebilir; alt öğe iptal edilirse, <xref:System.Activities.ActivityInstanceState.Canceled> durumunda tamamlanır. Yürütme sırasında bir özel durum oluşturulursa, çalışma zamanı etkinliği <xref:System.Activities.ActivityInstanceState.Faulted> duruma geçirir ve özel durumu etkinlik zincirinin üst zincirini yayar. Etkinliğin üç tamamlanma durumu aşağıda verilmiştir:
  
- **Kapalı:** Etkinlik, işini tamamladı ve çıkıldı.  
  
- **Iptal edildi:** Etkinlik, işini düzgün bir şekilde terk etti ve çıkıldı. Bu durum girildiğinde iş açık bir şekilde geri alınmaz.  
  
- **Hatalı:** Etkinlik bir hatayla karşılaştı ve işi tamamlanmadan çıkıldı.  
  
 Etkinlikler <xref:System.Activities.ActivityInstanceState.Executing> kalıcı veya kaldırılmış olduklarında durumunda kalır.
