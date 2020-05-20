---
title: İş Akışı Takip ve İzleme
description: Windows Iş akışı izleme, bir iş akışı örneğinin yürütülmesini izlemek için izleme altyapısı sağlayan bir .NET Framework 4.6.1 özelliğidir.
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: f88ff68a361bf3882d75bc2d5fb21903fd283a4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421299"
---
# <a name="workflow-tracking-and-tracing"></a>İş Akışı Takip ve İzleme
Windows Iş akışı izleme, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] iş akışı yürütmeye görünürlük sağlamak için tasarlanmış bir özelliktir. Bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar. WF izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışını saydam olarak araçlar. Bu işlevsellik, tüm iş akışları için varsayılan olarak kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] . [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]İzleme işleminin gerçekleşmesi için bir iş akışında yapılacak değişiklik yapılması gerekmez. Bu, ne kadar izleme verisi almak istediğinize karar vermenize oldukça önemlidir. Bir iş akışı örneği başlatıldığında veya tamamlandığında, işlem izleme kayıtları yayınlanır. İzleme, iş akışı değişkenleriyle ilişkili işle ilgili verileri de ayıklayabilir. Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, düzen KIMLIĞI nesnesiyle birlikte ayıklanamaz <xref:System.Activities.Tracking.TrackingRecord> . Genel olarak, WF izlemeyi etkinleştirmek, tanılama veya iş analizi verilerine bir iş akışı yürütmeden erişilmesine olanak tanır.  
  
 Bu izleme bileşenleri, WinFX içindeki izleme hizmetiyle eşdeğerdir. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]' De, performans geliştirilmiştir ve WF izleme özelliği için Basitleştirilmiş programlama modeli. İzleme çalışma zamanı, iş akışı yaşam döngüsü, iş akışı etkinlikleri ve özel olaylarla ilgili olayları göstermek için bir iş akışı örneğini araçlar.  
  
 Windows Server App Fabric Ayrıca bir WCF ve iş akışı hizmetlerinin yürütülmesini izleme olanağı sağlar. Daha fazla bilgi için bkz. Windows Server [uygulama yapısı izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) ve [Windows Server AppFabric ile izleme uygulamaları](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))  
  
 İş akışı çalışma zamanı sorunlarını gidermek için tanılama iş akışı izlemeyi açabilirsiniz. Daha fazla bilgi için bkz. [Iş akışı izleme](workflow-tracing.md).  
  
 Programlama modelini anlamak için, izleme altyapısının birincil bileşenleri bu konuda ele alınmıştır:  
  
- <xref:System.Activities.Tracking.TrackingRecord>iş akışı çalışma zamanından yayılan nesneler. Daha fazla bilgi için bkz. [kayıtları izleme](tracking-records.md).  
  
- <xref:System.Activities.Tracking.TrackingParticipant>Nesneler nesnelere abone olur <xref:System.Activities.Tracking.TrackingRecord> . İzleme katılımcıları, nesnelerden yükü işlemek için mantığı içerir <xref:System.Activities.Tracking.TrackingRecord> (örneğin, bir dosyaya yazmayı seçebilirler). Daha fazla bilgi için bkz. [katılımcıları izleme](tracking-participants.md).  
  
- <xref:System.Activities.Tracking.TrackingProfile>nesneler, bir iş akışı örneğinden yayılan izleme kayıtlarını filtreler. Daha fazla bilgi için bkz. [Izleme profilleri](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>İş akışı Izleme altyapısı  
 İş akışı izleme altyapısı bir Yayımla ve abone ol paradigmasını izler. İş akışı örneği kayıtları izlemenin yayımcısıdır, izleme kayıtlarının aboneleri iş akışına uzantı olarak kaydedilir. Nesnelere abone olan bu uzantılar <xref:System.Activities.Tracking.TrackingRecord> katılımcıları izleme olarak adlandırılır. Katılımcıları izlemek, <xref:System.Activities.Tracking.TrackingRecord> nesnelere erişen ve bunları yazdıkları her türlü şekilde işleyen genişletilebilirlik noktalarıdır. İzleme altyapısı, bir katılımcının kayıtların bir alt kümesine abone olmasına izin vermek için giden izleme kayıtlarında bir filtrenin uygulamasına izin verir. Bu filtreleme mekanizması, bir izleme profili dosyası aracılığıyla gerçekleştirilir.  
  
 İzleme altyapısının yüksek düzey görünümü aşağıdaki çizimde gösterilmiştir:  
  
 ![İş akışı izleme altyapısını gösteren ekran görüntüsü.](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzleme Kayıtları](tracking-records.md)  
 İş akışı çalışma zamanının yaydığı izleme kayıtlarını açıklar.  
  
 [İzleme Profilleri](tracking-profiles.md)  
 İzleme profillerinin nasıl kullanıldığını açıklar.  
  
 [İzleme Katılımcıları](tracking-participants.md)  
 Sistem tarafından belirtilen izleme katılımcısının nasıl kullanılacağını veya özel izleme katılımcıları nasıl oluşturulacağını açıklar.  
  
 [İş Akışı için İzlemeyi Yapılandırma](configuring-tracking-for-a-workflow.md)  
 Bir iş akışı için izlemenin nasıl yapılandırılacağını açıklar.  
  
 [İş Akışı İzleme](workflow-tracing.md)  
 Bir iş akışı için hata ayıklama izlemeyi etkinleştirmenin iki yolunu açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL İzleme](./samples/sql-tracking.md)
