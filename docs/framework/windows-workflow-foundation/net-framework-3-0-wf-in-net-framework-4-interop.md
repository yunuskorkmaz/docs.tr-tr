---
title: .NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 00636824277b57c46d760c419138dc9e001af17e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649365"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>.NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
<xref:System.Activities.Statements.Interop> Etkinliği bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sarmalar (WF 4.5) etkinliği bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) etkinlik içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. 3 WF etkinliği, bir tek yaprak etkinliği veya etkinlikleri ağacının tümünü olabilir. (İptal ve özel durum işleme dahil) yürütme ve sürekliliği [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik bağlamında oluşan [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yürütülmekte olan iş akışı örneği.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> İş akışının proje sahip olmadığı sürece etkinlik iş akışı Tasarımcısı araç kutusunda görünmüyor, **hedef Framework'ü** ayarının **.NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Bir WF 3 kullanarak ölçütleri etkinliği ile bir birlikte çalışma etkinliği  
 İçinde başarılı bir şekilde yürütmek 3 WF etkinliği için bir <xref:System.Activities.Statements.Interop> etkinlik, aşağıdaki ölçütleri karşılanması gerekir:  
  
- WF 3 etkinlik öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- 3 WF etkinliği olarak bildirilmelidir `public` ve olamaz `abstract`.  
  
- 3 WF etkinliği, ortak varsayılan oluşturucuya sahip olmalıdır.  
  
- Arabiriminde sınırlamaları nedeniyle, türleri <xref:System.Activities.Statements.Interop> etkinlik destekleyebilir <xref:System.Workflow.Activities.HandleExternalEventActivity> ve <xref:System.Workflow.Activities.CallExternalMethodActivity> oluşturulan iş akışı iletişim etkinlik aracını (WCA.exe) kullanarak kullanılabilir doğrudan kullanılır, ancak türetilmiş etkinlikleri olamaz. Bkz: [Windows Workflow Foundation Araçları](https://go.microsoft.com/fwlink/?LinkId=178889) Ayrıntılar için.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Yapılandırma 3 bir WF etkinliğinin bir birlikte çalışma etkinliği içinde  
 Yapılandırma ve birlikte çalışabilirlik sınırında içine ve dışına bir 3 WF etkinliği veri iletmek için 3 WF etkinlik özelliklerini ve meta veri özelliklerini tarafından kullanıma sunulan <xref:System.Activities.Statements.Interop> etkinlik. WF 3 etkinliğin meta veri özelliklerini (gibi <xref:System.Workflow.ComponentModel.Activity.Name%2A>) aracılığıyla kullanıma <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> koleksiyonu. WF 3 etkinliğin meta veri özelliklerini değerlerini tanımlamak için kullanılan ad-değer çiftleri koleksiyonu budur. Meta veri özelliği tarafından bağımlılık özelliği için desteklenen bir özelliktir <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> bayrağı ayarlanır.  
  
 WF 3 etkinliğin özellikleri aracılığıyla sunulan <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu. Her değerin olduğu bir dizi ad-değer çiftleri budur bir <xref:System.Activities.Argument> 3 WF etkinlik özelliklerini bağımsız değişkenleri tanımlamak için kullanılan nesne. WF 3 etkinlik özelliği yönünü çıkarsanamadığından, her bir özellik olarak kullanıma sunulur bir <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> çifti. Özellik etkinliğin kullanımınıza bağlı olarak sağlamak isteyebilirsiniz bir <xref:System.Activities.InArgument> girişi bir <xref:System.Activities.OutArgument> girişi veya her ikisi de. Beklenen adı <xref:System.Activities.InArgument> koleksiyondaki girdidir özelliğin adı 3 WF etkinliği tanımlandığı gibi. Beklenen adı <xref:System.Activities.OutArgument> girdidir koleksiyondaki bir özelliğin adını ve "Out" dizesi birleşimi.  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Bir WF 3 kullanma sınırlamaları bir birlikte çalışma etkinliği içinde etkinlik  
 Sistem tarafından sağlanan 3 WF etkinlikleri doğrudan içinde sarmalamak edilemez bir <xref:System.Activities.Statements.Interop> etkinlik. Bazı 3 WF etkinlikleri gibi <xref:System.Workflow.Activities.DelayActivity>, benzer bir 4.5 WF etkinliği olduğundan budur. Etkinlik işlevlerini desteklenmediğinden başkaları için budur. Sistem tarafından sağlanan birçok 3 WF etkinlikleri tarafından Sarmalanan iş akışı içinde kullanılabilir <xref:System.Activities.Statements.Interop> etkinlik, aşağıdaki kısıtlamalara tabidir:  
  
1. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, ve <xref:System.Workflow.Activities.WebServiceFaultActivity> içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> içinde kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
5. İçinde maaş ilgili etkinlikleri kullanılamaz bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
 İçindeki 3 WF etkinlikleri kullanımına ilişkin anlamak için bazı davranış özellikleri de vardır <xref:System.Activities.Statements.Interop> etkinlik:  
  
1. 3 WF etkinlikleri içinde yer alan bir <xref:System.Activities.Statements.Interop> etkinliği olan ne zaman başlatılır <xref:System.Activities.Statements.Interop> etkinlik yürütüldüğünde. WF 4.5 hiçbir başlatma aşaması yürütme önce bir iş akışı örneği için yoktur.  
  
2. Bu işlem bağımsız olarak başladığı bir işlem başladığında değil denetim noktası iş akışı örneği durumu WF 4.5 çalışma zamanı yapar (içinde veya dışında bir <xref:System.Activities.Statements.Interop> etkinliği).  
  
3. İçindeki etkinlikler için WF 3 izleme kayıtları bir <xref:System.Activities.Statements.Interop> Etkinlik izleme katılımcıları WF 4.5 için sağlanan <xref:System.Activities.Tracking.InteropTrackingRecord> nesneleri. <xref:System.Activities.Tracking.InteropTrackingRecord> bir türevi olan <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. WF 3 özel aktivite 3 WF iş akışı çalışma zamanı gibi içinde tam olarak aynı şekilde birlikte çalışabilirlik ortamında iş akışı kuyrukları kullanarak verilere erişebilir. Özel Etkinlik kod değişikliği yapmadan gereklidir. Konakta veri sürdürme tarafından sıraya alınan 3 WF iş akışını kuyruğa olduğu bir <xref:System.Activities.Bookmark>. Yer işaretinin adı dize biçimindedir <xref:System.IComparable> iş akışı kuyruk adı.
