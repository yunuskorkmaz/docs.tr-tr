---
title: .NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: fb9536d5ee7a31039d77deffc3c0b0c7a6263b66
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802576"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>.NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
<xref:System.Activities.Statements.Interop> etkinliği, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bir iş akışı içinde .NET Framework 3,5 (WF 3,5) etkinliğini sarmalayan bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4,5) etkinliğidir. WF 3 etkinliği tek bir yaprak etkinlik veya bir etkinlik ağacının tamamına ait olabilir. Yürütme (iptal ve özel durum işleme dahil) ve .NET Framework 3,5 etkinliğinin kalıcılığı, yürüten [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı örneği bağlamında oluşur.  
  
> [!NOTE]
> İş akışının projesi **hedef Framework** ayarı **.NET Framework 4,5**olarak ayarlanmadığı takdirde, <xref:System.Activities.Statements.Interop> etkinliği iş akışı Tasarımcısı araç kutusunda görünmez.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğiyle WF 3 etkinliğinin kullanımı için ölçütler  
 Bir WF 3 etkinliğinin <xref:System.Activities.Statements.Interop> etkinliği içinde başarıyla yürütülmesi için aşağıdaki ölçütlerin karşılanması gerekir:  
  
- WF 3 etkinliğinin <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>türetmeniz gerekir.  
  
- WF 3 etkinliğinin `public` olarak bildirilmelidir ve `abstract`olamaz.  
  
- WF 3 etkinliğinin ortak parametresiz bir oluşturucusu olmalıdır.  
  
- <xref:System.Activities.Statements.Interop> etkinliğinin destekleyebileceği arabirim türlerindeki sınırlamalar nedeniyle, <xref:System.Workflow.Activities.HandleExternalEventActivity> ve <xref:System.Workflow.Activities.CallExternalMethodActivity> doğrudan kullanılamaz, ancak Iş akışı Iletişimi etkinlik aracı (WCA. exe) kullanılarak oluşturulan türev etkinlikler kullanılabilir. Ayrıntılar için bkz. [Windows Workflow Foundation araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms734408(v=vs.90)) .  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğini yapılandırma  
 Bir WF 3 etkinliğinin içine ve dışına veri yapılandırmak ve bu etkinliği kapatmak için, WF 3 etkinliğinin özellikleri ve meta verileri özellikleri <xref:System.Activities.Statements.Interop> etkinliği tarafından gösterilir. WF 3 etkinliğinin meta veri özellikleri (örneğin, <xref:System.Workflow.ComponentModel.Activity.Name%2A>) <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> koleksiyonu aracılığıyla gösterilir. Bu, WF 3 etkinliğinin meta veri özelliklerine ilişkin değerleri tanımlamak için kullanılan ad-değer çiftleri koleksiyonudur. Meta veri özelliği, <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> bayrağının ayarlandığı Dependency özelliği tarafından desteklenen bir özelliktir.  
  
 WF 3 etkinliğinin özellikleri <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu aracılığıyla sunulur. Bu, her değerin bir <xref:System.Activities.Argument> nesnesi olduğu, WF 3 etkinliğinin özelliklerinin bağımsız değişkenlerini tanımlamak için kullanılan bir ad-değer çiftleri kümesidir. Bir WF 3 etkinlik özelliğinin yönü çıkarsanamıyor, her özellik <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument> çifti olarak ortaya çıkmış olur. Etkinliğin özelliğinin kullanımına bağlı olarak, bir <xref:System.Activities.InArgument> girişi, <xref:System.Activities.OutArgument> girişi veya her ikisini de sağlamak isteyebilirsiniz. Koleksiyonda <xref:System.Activities.InArgument> girdinin beklenen adı, WF 3 etkinliğinde tanımlanan özelliğin adıdır. Koleksiyonda <xref:System.Activities.OutArgument> girdinin beklenen adı, özelliğin adının ve "Out" dizesinin bir bitiştirilmesi.  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğinin kullanım sınırlamaları  
 WF 3 sistem tarafından belirtilen etkinlikler bir <xref:System.Activities.Statements.Interop> etkinliğine doğrudan sarmalanamaz. <xref:System.Workflow.Activities.DelayActivity>gibi bazı WF 3 etkinlikleri için, bunun nedeni, benzer bir WF 4,5 etkinliğidir. Bunun nedeni, etkinliğin işlevselliğinin desteklenmediği içindir. Birçok WF 3 sistem tarafından sunulan etkinlik, <xref:System.Activities.Statements.Interop> etkinliği tarafından Sarmalanan iş akışları içinde aşağıdaki kısıtlamalara tabi olarak kullanılabilir:  
  
1. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> <xref:System.Activities.Statements.Interop> etkinliğinde kullanılamaz.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>ve <xref:System.Workflow.Activities.WebServiceFaultActivity> <xref:System.Activities.Statements.Interop> etkinliği içinde kullanılamaz.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> bir <xref:System.Activities.Statements.Interop> etkinliği içinde kullanılamaz.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> bir <xref:System.Activities.Statements.Interop> etkinliği içinde kullanılamaz.  
  
5. Tazminat ilgili etkinlikler bir <xref:System.Activities.Statements.Interop> etkinliği içinde kullanılamaz.  
  
 <xref:System.Activities.Statements.Interop> etkinliğinde WF 3 etkinliklerinin kullanımıyla ilgili bilgi edinmek için de bazı davranış özellikleri vardır:  
  
1. <xref:System.Activities.Statements.Interop> etkinliğin içinde yer alan WF 3 etkinlikleri, <xref:System.Activities.Statements.Interop> etkinliği yürütüldüğünde başlatılır. WF 4,5 ' de yürütmeden önce bir iş akışı örneği için başlatma aşaması yoktur.  
  
2. WF 4,5 çalışma zamanı, işlemin başladığı (<xref:System.Activities.Statements.Interop> etkinliğinin içinde veya dışında) bağımsız olarak bir işlem başladığında iş akışı örneği durumunu kontrol etmez.  
  
3. WF 3 <xref:System.Activities.Statements.Interop> etkinliği içindeki etkinliklerin izleme kayıtları, WF 4,5 izleme katılımcılarına <xref:System.Activities.Tracking.InteropTrackingRecord> nesneleri olarak sunulmaktadır. <xref:System.Activities.Tracking.InteropTrackingRecord>, <xref:System.Activities.Tracking.CustomTrackingRecord>bir türevi.  
  
4. WF 3 özel etkinliği, birlikte çalışabilirlik ortamında iş akışı kuyruklarını, WF 3 iş akışı çalışma zamanı ile tamamen aynı şekilde kullanarak verilere erişebilir. Özel etkinlik kodu değişikliği gerekli değildir. Konakta, veriler bir <xref:System.Activities.Bookmark>sürdürülerek WF 3 iş akışı kuyruğuna sıraya konur. Yer işaretinin adı, <xref:System.IComparable> iş akışı sırasının adının dize biçimidir.
