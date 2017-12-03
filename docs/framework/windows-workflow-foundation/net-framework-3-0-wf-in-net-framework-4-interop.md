---
title: "Itanium tabanlı sistemler için .NET Framework 4 ile birlikte çalışma etkinlik .NET Framework 3.0 WF etkinlikleri kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51f11beb474758f16c6de0c47444e0467cac8bec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Itanium tabanlı sistemler için .NET Framework 4 ile birlikte çalışma etkinlik .NET Framework 3.0 WF etkinlikleri kullanma
<xref:System.Activities.Statements.Interop> Etkinliği bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sarmalar (WF 4.5) etkinliği bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] içinde (WF 3.5) etkinlik bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. WF 3 etkinlik tek yaprak etkinlik veya etkinlikleri ağacının tümünü olabilir. (İptal ve özel durum işleme dahil) yürütme ve kalıcılığı [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik ortaya bağlamında [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yürütüyor iş akışı örneği.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Etkinliği iş akışı Proje olmadıkça iş akışı Tasarımcısı Araç Kutusu'nda görünmez kendi **hedef Framework** ayarını **.NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>WF 3 kullanarak ölçütlerini etkinliği ile birlikte çalışma etkinlik  
 İçinde başarıyla yürütmek WF 3 etkinliği için bir <xref:System.Activities.Statements.Interop> etkinlik, aşağıdaki kriterlerin karşılanması gerekir:  
  
-   WF 3 etkinlik öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
-   WF 3 etkinlik olarak bildirilmelidir `public` ve olamaz `abstract`.  
  
-   WF 3 etkinlik ortak varsayılan bir oluşturucu olması gerekir.  
  
-   Arabiriminde sınırlamaları nedeniyle, türleri <xref:System.Activities.Statements.Interop> etkinlik destekleyebilmesi <xref:System.Workflow.Activities.HandleExternalEventActivity> ve <xref:System.Workflow.Activities.CallExternalMethodActivity> oluşturulan iş akışı iletişimi etkinlik aracını (WCA.exe) kullanarak kullanılabilir doğrudan kullanılan ancak türetilmiş etkinlikleri olamaz. Bkz: [Windows Workflow Foundation Araçları](http://go.microsoft.com/fwlink/?LinkId=178889) Ayrıntılar için.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>WF 3 yapılandırma birlikte çalışma aktivite içinde etkinlik  
 Yapılandırma ve birlikte çalışabilirlik sınırından içine ve dışına WF 3 etkinlik veri iletmek için WF 3 etkinliğin özellikleri ve meta veri özellikleri tarafından kullanıma sunulan <xref:System.Activities.Statements.Interop> etkinlik. WF 3 etkinliğin meta veri özelliklerini (gibi <xref:System.Workflow.ComponentModel.Activity.Name%2A>) aracılığıyla sunulan <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> koleksiyonu. WF 3 etkinliğin meta veri özelliklerine ilişkin değerleri tanımlamak için kullanılan ad-değer çiftleri koleksiyonu budur. Meta veri özelliği için bağımlılık özelliği tarafından yedeklenen bir özelliktir <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> bayrağı ayarlanır.  
  
 WF 3 etkinliğin özellikleri aracılığıyla sunulan <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu. Bu, ad-değer çiftleri kümesi her değeri olduğu bir <xref:System.Activities.Argument> WF 3 etkinliğin özellikleri bağımsız değişkenleri tanımlamak için kullanılan nesne. WF 3 etkinlik özelliği yönünü çıkarsanamıyor çünkü her özellik olarak ortaya bir <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> çifti. Bağlı olarak etkinliğe ilişkin kullanım özelliğinin sağlamak isteyebilirsiniz bir <xref:System.Activities.InArgument> girişi, bir <xref:System.Activities.OutArgument> girişi ya da her ikisini de. Beklenen adını <xref:System.Activities.InArgument> koleksiyondaki giriştir özelliğinin adı WF 3 faaliyete tanımlandığı gibi. Beklenen adını <xref:System.Activities.OutArgument> giriştir koleksiyonundaki bir birleşimini özelliğin adını ve "Out" dizesi.  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>WF 3 kullanma sınırlamaları birlikte çalışma aktivite içinde etkinlik  
 WF 3 sistem tarafından sağlanan etkinlikler doğrudan içinde sarmalamak olamaz bir <xref:System.Activities.Statements.Interop> etkinlik. Bazı WF 3 etkinlikler için gibi <xref:System.Workflow.Activities.DelayActivity>, benzer bir WF 4.5 etkinlik olduğundan budur. Etkinlik işlevselliğini desteklenmediğinden diğerleri için budur. Birçok WF 3 sistem tarafından sağlanan etkinlikler tarafından Sarmalanan iş akışları kullanılabilir <xref:System.Activities.Statements.Interop> aşağıdaki kısıtlamalara tabi etkinlik:  
  
1.  <xref:System.ServiceModel.Activities.Send>ve <xref:System.ServiceModel.Activities.Receive> kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, ve <xref:System.Workflow.Activities.WebServiceFaultActivity> içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity>içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity>içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
5.  Maaş ilgili etkinlikleri, içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
 Ayrıca içindeki WF 3 etkinlikleri kullanımına ilişkin anlamak için davranış bazı özellikleri olan <xref:System.Activities.Statements.Interop> etkinlik:  
  
1.  WF 3 içindeki etkinlikler bir <xref:System.Activities.Statements.Interop> etkinliği olan zaman başlatıldı <xref:System.Activities.Statements.Interop> etkinlik gerçekleştirilir. WF 4.5 yürütülmesinin önce bir iş akışı örneği için hiçbir başlatma aşaması vardır.  
  
2.  Bu işlem başladığı bağımsız olarak bir işlem başladığında WF 4.5 çalışma zamanı değil denetim noktası iş akışı örneği durum mu (içinde veya dışında bir <xref:System.Activities.Statements.Interop> etkinlik).  
  
3.  WF 3 izleme kayıtları içindeki etkinlikler için bir <xref:System.Activities.Statements.Interop> etkinlik WF 4.5 izleme katılımcılara sağlanan <xref:System.Activities.Tracking.InteropTrackingRecord> nesneleri. <xref:System.Activities.Tracking.InteropTrackingRecord>bir türevi değil <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4.  WF 3 özel bir aktivite içinde WF 3 iş akışı çalışma zamanı gibi aynı şekilde tam olarak birlikte çalışabilirlik ortamı içindeki iş akışı kuyrukları kullanma verilere erişebilir. Özel Etkinlik kodu değişiklik gerekmez. Konak üzerinde sıraya alınan WF 3 iş akışı kuyruğuna sürdürme tarafından verilerdir bir <xref:System.Activities.Bookmark>. Yer işareti dize biçiminde adıdır <xref:System.IComparable> iş akışı sıra adı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework 3.0 veya .NET Framework 3.5 etkinliği bir .NET Framework 4.5 iş akışında kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)
