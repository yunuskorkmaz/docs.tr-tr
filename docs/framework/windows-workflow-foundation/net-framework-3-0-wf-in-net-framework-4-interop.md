---
title: .NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: baca65da29fd0b18bd61f9b79ce82429faaed432
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364141"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>.NET Framework 4’te Birlikte Çalışma Etkinliği ile .NET Framework 3.0 WF Etkinlikleri Kullanma
Etkinlik, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bir iş[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] akışı içinde (WF 3,5) etkinliğini sarmalayan bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4,5) etkinliğidir. <xref:System.Activities.Statements.Interop> WF 3 etkinliği tek bir yaprak etkinlik veya bir etkinlik ağacının tamamına ait olabilir. Yürütme (iptal ve özel durum işleme dahil) ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinliğin kalıcılığı, yürütülmekte olan [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı örneği bağlamı içinde gerçekleşir.  
  
> [!NOTE]
>  İş akışı projesinin **hedef Framework** ayarı **.NET Framework 4,5**olarak ayarlanmadığı takdirde etkinlikişakışıTasarımcısıaraçkutusundagörünmez.<xref:System.Activities.Statements.Interop>  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğiyle WF 3 etkinliğinin kullanımı için ölçütler  
 Bir <xref:System.Activities.Statements.Interop> etkinlik içinde başarılı bir şekilde yürütülecek bir WF 3 etkinliğinin sağlanması için aşağıdaki ölçütlerin karşılanması gerekir:  
  
- WF 3 etkinliğinin türevi <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>olması gerekir.  
  
- WF 3 etkinliğinin olarak `public` `abstract`tanımlanmış olması gerekir.  
  
- WF 3 etkinliğinin ortak parametresiz bir oluşturucusu olmalıdır.  
  
- <xref:System.Activities.Statements.Interop> Etkinliğin destekleyebileceği<xref:System.Workflow.Activities.CallExternalMethodActivity> arabirim türlerindeki sınırlamalar nedeniyle doğrudan kullanılamaz, ancak iş akışı iletişimi etkinlik aracı (WCA. exe) kullanılarak oluşturulan türev etkinlikler kullanılabilir. <xref:System.Workflow.Activities.HandleExternalEventActivity> Ayrıntılar için bkz. [Windows Workflow Foundation araçları](https://go.microsoft.com/fwlink/?LinkId=178889) .  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğini yapılandırma  
 Bir WF 3 etkinliğinin içine ve dışına verileri yapılandırmak ve kapatmak için, birlikte çalışma sınırı boyunca, WF 3 etkinliğinin özellikleri ve meta verileri özellikleri <xref:System.Activities.Statements.Interop> etkinlik tarafından gösterilir. WF 3 etkinliğinin meta veri özellikleri (gibi <xref:System.Workflow.ComponentModel.Activity.Name%2A>), <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> koleksiyon aracılığıyla sunulur. Bu, WF 3 etkinliğinin meta veri özelliklerine ilişkin değerleri tanımlamak için kullanılan ad-değer çiftleri koleksiyonudur. Meta veri özelliği, <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> bayrağın ayarlandığı bağımlılık özelliği tarafından desteklenen bir özelliktir.  
  
 WF 3 etkinliğinin özellikleri <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyon aracılığıyla sunulur. Bu, her değerin bir <xref:System.Activities.Argument> nesne olduğu, WF 3 etkinliğinin özelliklerinin bağımsız değişkenlerini tanımlamak için kullanılan bir ad-değer çiftleri kümesidir. Bir WF 3 etkinlik özelliğinin yönü çıkarsanamıyor, her özellik bir <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> çift olarak ortaya çıkmış olur. Etkinliğin özelliğinin kullanımına bağlı olarak, bir <xref:System.Activities.InArgument> giriş <xref:System.Activities.OutArgument> , giriş veya her ikisini de sağlamak isteyebilirsiniz. Koleksiyondaki <xref:System.Activities.InArgument> girdinin beklenen adı, WF 3 etkinliğinde tanımlanan özelliğin adıdır. Koleksiyondaki <xref:System.Activities.OutArgument> girdinin beklenen adı, özelliğin adının ve "Out" dizesinin bir bitiştirilmesi olur.  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Birlikte çalışabilirlik etkinliğinde WF 3 etkinliğinin kullanım sınırlamaları  
 WF 3 sistem tarafından belirtilen etkinlikler bir <xref:System.Activities.Statements.Interop> etkinlikte doğrudan sarmalanamaz. Gibi bazı WF 3 etkinlikleri <xref:System.Workflow.Activities.DelayActivity>için, bunun nedeni, benzer bir WF 4,5 etkinliğidir. Bunun nedeni, etkinliğin işlevselliğinin desteklenmediği içindir. Birçok WF 3 sistem tarafından sunulan etkinlik, <xref:System.Activities.Statements.Interop> etkinlik tarafından Sarmalanan iş akışları dahilinde aşağıdaki kısıtlamalara tabi olarak kullanılabilir:  
  
1. <xref:System.ServiceModel.Activities.Send>ve <xref:System.ServiceModel.Activities.Receive> bir<xref:System.Activities.Statements.Interop> etkinlikte kullanılamaz.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, ve <xref:System.Workflow.Activities.WebServiceFaultActivity> bir <xref:System.Activities.Statements.Interop> etkinlik içinde kullanılamaz.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity><xref:System.Activities.Statements.Interop> etkinlik içinde kullanılamaz.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity><xref:System.Activities.Statements.Interop> etkinlik içinde kullanılamaz.  
  
5. Tazminat ilgili etkinlikler bir <xref:System.Activities.Statements.Interop> etkinlik içinde kullanılamaz.  
  
 <xref:System.Activities.Statements.Interop> Etkinliğin içinde WF 3 etkinliklerinin kullanımıyla ilgili bilgi almak için bazı davranış özellikleri de mevcuttur:  
  
1. Etkinlik yürütüldüğünde bir <xref:System.Activities.Statements.Interop> etkinliğin içinde yer alan WF 3 etkinlikleri başlatılır <xref:System.Activities.Statements.Interop> . WF 4,5 ' de yürütmeden önce bir iş akışı örneği için başlatma aşaması yoktur.  
  
2. WF 4,5 çalışma zamanı, işlemin başladığı yere (bir <xref:System.Activities.Statements.Interop> etkinliğin içinde veya dışında) bakılmaksızın bir işlem başladığında iş akışı örneği durumunu kontrol etmez.  
  
3. WF 3 bir <xref:System.Activities.Statements.Interop> etkinlik içindeki etkinliklerin izleme kayıtları, WF 4,5 izleme katılımcılarına nesne olarak <xref:System.Activities.Tracking.InteropTrackingRecord> sunulmaktadır. <xref:System.Activities.Tracking.InteropTrackingRecord>, ' ın <xref:System.Activities.Tracking.CustomTrackingRecord>bir türevi.  
  
4. WF 3 özel etkinliği, birlikte çalışabilirlik ortamında iş akışı kuyruklarını, WF 3 iş akışı çalışma zamanı ile tamamen aynı şekilde kullanarak verilere erişebilir. Özel etkinlik kodu değişikliği gerekli değildir. Konakta veriler bir <xref:System.Activities.Bookmark>WF 3 iş akışı kuyruğuna sıraya alınır. Yer işaretinin adı, <xref:System.IComparable> iş akışı sırasının adının dize biçimidir.
