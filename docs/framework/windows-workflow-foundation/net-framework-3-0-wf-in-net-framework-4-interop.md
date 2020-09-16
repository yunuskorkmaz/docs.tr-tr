---
title: .NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 02f7a4d9cdda0a6c4f23574c5a20ac78eb783ef2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556082"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>.NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
Etkinlik, bir <xref:System.Activities.Statements.Interop> [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı içinde .NET Framework 3,5 (WF 3,5) etkinliğini sarmalayan bir (WF 4,5) etkinliğidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] . WF 3 etkinliği tek bir yaprak etkinlik veya bir etkinlik ağacının tamamına ait olabilir. Yürütme (iptal ve özel durum işleme dahil) ve .NET Framework 3,5 etkinliğinin kalıcılığı, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yürütülmekte olan iş akışı örneği bağlamında oluşur.  
  
> [!NOTE]
> <xref:System.Activities.Statements.Interop>İş akışı projesinin **hedef Framework** ayarı **.NET Framework 4,5**olarak ayarlanmadığı takdirde etkinlik iş akışı Tasarımcısı araç kutusunda görünmez.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğiyle WF 3 etkinliğinin kullanımı için ölçütler  
 Bir etkinlik içinde başarılı bir şekilde yürütülecek bir WF 3 etkinliğinin <xref:System.Activities.Statements.Interop> sağlanması için aşağıdaki ölçütlerin karşılanması gerekir:  
  
- WF 3 etkinliğinin türevi olması gerekir <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType> .  
  
- WF 3 etkinliğinin olarak tanımlanmış olması gerekir `public` `abstract` .  
  
- WF 3 etkinliğinin ortak parametresiz bir oluşturucusu olmalıdır.  
  
- Etkinliğin destekleyebileceği arabirim türlerindeki sınırlamalar nedeniyle <xref:System.Activities.Statements.Interop> <xref:System.Workflow.Activities.HandleExternalEventActivity> <xref:System.Workflow.Activities.CallExternalMethodActivity> doğrudan kullanılamaz, ancak Iş akışı iletişim etkinlik aracı (WCA.exe) kullanılarak oluşturulan türev etkinlikler kullanılabilir. Ayrıntılar için bkz. [Windows Workflow Foundation araçları](/previous-versions/dotnet/netframework-3.5/ms734408(v=vs.90)) .  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğini yapılandırma  
 Bir WF 3 etkinliğinin içine ve dışına verileri yapılandırmak ve kapatmak için, birlikte çalışma sınırı boyunca, WF 3 etkinliğinin özellikleri ve meta verileri özellikleri etkinlik tarafından gösterilir <xref:System.Activities.Statements.Interop> . WF 3 etkinliğinin meta veri özellikleri (gibi), <xref:System.Workflow.ComponentModel.Activity.Name%2A> koleksiyon aracılığıyla sunulur <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> . Bu, WF 3 etkinliğinin meta veri özelliklerine ilişkin değerleri tanımlamak için kullanılan ad-değer çiftleri koleksiyonudur. Meta veri özelliği, bayrağın ayarlandığı bağımlılık özelliği tarafından desteklenen bir özelliktir <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> .  
  
 WF 3 etkinliğinin özellikleri koleksiyon aracılığıyla sunulur <xref:System.Activities.Statements.Interop.ActivityProperties%2A> . Bu, her değerin bir nesne olduğu, <xref:System.Activities.Argument> WF 3 etkinliğinin özelliklerinin bağımsız değişkenlerini tanımlamak için kullanılan bir ad-değer çiftleri kümesidir. Bir WF 3 etkinlik özelliğinin yönü çıkarsanamıyor, her özellik bir çift olarak ortaya çıkmış olur <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> . Etkinliğin özelliğinin kullanımına bağlı olarak, bir <xref:System.Activities.InArgument> giriş, <xref:System.Activities.OutArgument> giriş veya her ikisini de sağlamak isteyebilirsiniz. Koleksiyondaki girdinin beklenen adı, <xref:System.Activities.InArgument> WF 3 etkinliğinde tanımlanan özelliğin adıdır. Koleksiyondaki girdinin beklenen adı, <xref:System.Activities.OutArgument> özelliğin adının ve "Out" dizesinin bir bitiştirilmesi olur.  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğinin kullanım sınırlamaları  
 WF 3 sistem tarafından belirtilen etkinlikler bir etkinlikte doğrudan sarmalanamaz <xref:System.Activities.Statements.Interop> . Gibi bazı WF 3 etkinlikleri için, bunun nedeni, <xref:System.Workflow.Activities.DelayActivity> benzer BIR wf 4,5 etkinliğidir. Bunun nedeni, etkinliğin işlevselliğinin desteklenmediği içindir. Birçok WF 3 sistem tarafından sunulan etkinlik, etkinlik tarafından Sarmalanan iş akışları dahilinde <xref:System.Activities.Statements.Interop> aşağıdaki kısıtlamalara tabi olarak kullanılabilir:  
  
1. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> bir <xref:System.Activities.Statements.Interop> etkinlikte kullanılamaz.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity> , ve <xref:System.Workflow.Activities.WebServiceFaultActivity> bir etkinlik içinde kullanılamaz <xref:System.Activities.Statements.Interop> .  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> etkinlik içinde kullanılamaz <xref:System.Activities.Statements.Interop> .  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> etkinlik içinde kullanılamaz <xref:System.Activities.Statements.Interop> .  
  
5. Tazminat ilgili etkinlikler bir etkinlik içinde kullanılamaz <xref:System.Activities.Statements.Interop> .  
  
 Etkinliğin içinde WF 3 etkinliklerinin kullanımıyla ilgili bilgi almak için bazı davranış özellikleri de mevcuttur <xref:System.Activities.Statements.Interop> :  
  
1. Etkinlik yürütüldüğünde bir etkinliğin içinde yer alan WF 3 etkinlikleri <xref:System.Activities.Statements.Interop> başlatılır <xref:System.Activities.Statements.Interop> . WF 4,5 ' de yürütmeden önce bir iş akışı örneği için başlatma aşaması yoktur.  
  
2. WF 4,5 çalışma zamanı, işlemin başladığı yere (bir etkinliğin içinde veya dışında) bakılmaksızın bir işlem başladığında iş akışı örneği durumunu kontrol etmez <xref:System.Activities.Statements.Interop> .  
  
3. WF 3 bir etkinlik içindeki etkinliklerin izleme kayıtları <xref:System.Activities.Statements.Interop> , wf 4,5 izleme katılımcılarına nesne olarak sunulmaktadır <xref:System.Activities.Tracking.InteropTrackingRecord> . <xref:System.Activities.Tracking.InteropTrackingRecord> , ' ın bir türevi <xref:System.Activities.Tracking.CustomTrackingRecord> .  
  
4. WF 3 özel etkinliği, birlikte çalışabilirlik ortamında iş akışı kuyruklarını, WF 3 iş akışı çalışma zamanı ile tamamen aynı şekilde kullanarak verilere erişebilir. Özel etkinlik kodu değişikliği gerekli değildir. Konakta veriler bir WF 3 iş akışı kuyruğuna sıraya alınır <xref:System.Activities.Bookmark> . Yer işaretinin adı, <xref:System.IComparable> iş akışı sırasının adının dize biçimidir.
