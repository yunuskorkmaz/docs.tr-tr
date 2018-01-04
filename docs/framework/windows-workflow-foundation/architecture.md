---
title: "Windows iş akışı mimarisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed13d7885cb8abd760aed6bd5812cb8b7c75bc02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-architecture"></a>Windows iş akışı mimarisi
[!INCLUDE[wf](../../../includes/wf-md.md)]Etkileşimli uzun süre çalışan uygulamalar geliştirmek için özet düzeyi başlatır. İş birimleri etkinlikler olarak kapsüllenir. Olanakları sağlar akış denetimi, özel durum işleme, arıza yayma, yüklenmesi ve devam eden iş akışlarının bellek, izleme ve işlem akışı kaldırılması durumu verilerinin kalıcılığı için bir ortamda etkinlikleri çalıştırın.  
  
## <a name="activity-architecture"></a>Etkinlik mimarisi  
 Etkinliklerin herhangi birinden türetilen CLR türleri olarak geliştirilen <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.NativeActivity>, veya bir değer döndürmesi bunların türevleri <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, veya <xref:System.Activities.NativeActivity%601>. Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.Activity> hızlı bir şekilde iş akışı ortamında yürütme iş birimleri oluşturmak için önceden var olan etkinlikleri derleyecek olanak tanır. <xref:System.Activities.CodeActivity>, diğer yandan, yönetilen kod kullanarak yazılmasını yürütme mantığını etkinleştirir <xref:System.Activities.CodeActivityContext> etkinlik bağımsız değişken erişimi için öncelikle. <xref:System.Activities.AsyncCodeActivity>benzer <xref:System.Activities.CodeActivity> dışında zaman uyumsuz görevleri uygulamak için kullanılabilir. Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.NativeActivity> çalışma zamanı üzerinden erişmesine olanak tanır <xref:System.Activities.NativeActivityContext> alt yer işaretleri, oluşturma, zamanlama gibi işlevler için zaman uyumsuz iş kayıt işlemleri ve çok çağırma.  
  
 Öğesinden türetilen etkinlikleri yazma <xref:System.Activities.Activity> tanımlayıcıdır ve bu etkinlikler XAML'de yazılabilir. Aşağıdaki örnekte, bir etkinlik olarak adlandırılan `Prompt` yürütme gövdesi için diğer etkinlikleri kullanarak oluşturulur.  
  
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
 <xref:System.Activities.ActivityContext> İş akışı çalışma zamanı için etkinlik yazarın arabirimi ve özellikleri zamanının bol erişim sağlar. Aşağıdaki örnekte, bir etkinlik yürütme bağlamı yer işareti (bir devamlılık noktası verileri activity içine geçirmeden bir ana bilgisayar tarafından sürdürülebilecek yürütülmesinin kaydetmek için bir etkinlik sağlar mekanizması) oluşturmak için kullandığı tanımlanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Etkinlik yaşam döngüsü  
 Bir etkinliği örneği başlatır <xref:System.Activities.ActivityInstanceState.Executing> durumu. Özel durumlar karşılaşılan sürece tüm alt etkinlikleri çalıştırma ve diğer iş bekleyen tamamlanana kadar bu durumda kalır (<xref:System.Activities.Bookmark> nesneleri, örneğin) tamamlandığında, anda bunu geçişleri <xref:System.Activities.ActivityInstanceState.Closed> durumu. Bir etkinlik örneğinin üst iptal etmek için bir alt isteyebilir; alt iptal ederse tamamlanır <xref:System.Activities.ActivityInstanceState.Canceled> durumu. Yürütme sırasında bir özel durum, çalışma zamanı etkinliğe koyar <xref:System.Activities.ActivityInstanceState.Faulted> belirtin ve özel etkinlikleri üst zincirine yukarı yayar. Bir etkinlik üç tamamlanma durumunu şunlardır:  
  
-   **Kapalı:** etkinlik kendi iş tamamlandı ve çıkıldı.  
  
-   **İptal edilen:** etkinliği düzgün bir şekilde çalışmasını terk ve çıkıldı. Bu durum geri girildiğinde, iş açıkça döndürülmez.  
  
-   **Hatalı:** etkinliği bir hatayla karşılaştı ve çalışmasını tamamlamadan çıkıldı.  
  
 Etkinlikler kalır <xref:System.Activities.ActivityInstanceState.Executing> kalıcı veya kaldırıldı durumu.
