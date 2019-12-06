---
title: İş Akışı Takip ve İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 9f887babec5c070eed2fb3c7e4d8d35cdfb3f488
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837486"
---
# <a name="workflow-tracking-and-tracing"></a>İş Akışı Takip ve İzleme
Windows Iş akışı izleme, iş akışı yürütmeye görünürlük sağlamak için tasarlanan bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özelliğidir. Bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar. WF izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışını saydam olarak araçlar. Bu işlevsellik, tüm [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışları için varsayılan olarak kullanılabilir. İzleme işleminin gerçekleşmesi için [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bir iş akışında değişiklik yapılması gerekmez. Bu, ne kadar izleme verisi almak istediğinize karar vermenize oldukça önemlidir. Bir iş akışı örneği başlatıldığında veya tamamlandığında, işlem izleme kayıtları yayınlanır. İzleme, iş akışı değişkenleriyle ilişkili işle ilgili verileri de ayıklayabilir. Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, Order ID <xref:System.Activities.Tracking.TrackingRecord> nesnesiyle birlikte ayıklanabilir. Genel olarak, WF izlemeyi etkinleştirmek, tanılama veya iş analizi verilerine bir iş akışı yürütmeden erişilmesine olanak tanır.  
  
 Bu izleme bileşenleri, WinFX içindeki izleme hizmetiyle eşdeğerdir. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], performans geliştirilmiştir ve WF izleme özelliği için Basitleştirilmiş programlama modeli. İzleme çalışma zamanı, iş akışı yaşam döngüsü, iş akışı etkinlikleri ve özel olaylarla ilgili olayları göstermek için bir iş akışı örneğini araçlar.  
  
 Windows Server App Fabric Ayrıca bir WCF ve iş akışı hizmetlerinin yürütülmesini izleme olanağı sağlar. Daha fazla bilgi için bkz. Windows Server [uygulama yapısı izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) ve [Windows Server AppFabric ile izleme uygulamaları](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))  
  
 İş akışı çalışma zamanı sorunlarını gidermek için tanılama iş akışı izlemeyi açabilirsiniz. Daha fazla bilgi için bkz. [Iş akışı izleme](workflow-tracing.md).  
  
 Programlama modelini anlamak için, izleme altyapısının birincil bileşenleri bu konuda ele alınmıştır:  
  
- iş akışı çalışma zamanından yayılan nesneleri <xref:System.Activities.Tracking.TrackingRecord>. Daha fazla bilgi için bkz. [kayıtları izleme](tracking-records.md).  
  
- <xref:System.Activities.Tracking.TrackingParticipant> nesneler <xref:System.Activities.Tracking.TrackingRecord> nesnelerine abone olur. İzleme katılımcıları, <xref:System.Activities.Tracking.TrackingRecord> nesnelerden yükü işlemek için mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler). Daha fazla bilgi için bkz. [katılımcıları izleme](tracking-participants.md).  
  
- <xref:System.Activities.Tracking.TrackingProfile> nesneleri, bir iş akışı örneğinden yayılan izleme kayıtlarını filtreler. Daha fazla bilgi için bkz. [Izleme profilleri](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>İş akışı Izleme altyapısı  
 İş akışı izleme altyapısı bir Yayımla ve abone ol paradigmasını izler. İş akışı örneği kayıtları izlemenin yayımcısıdır, izleme kayıtlarının aboneleri iş akışına uzantı olarak kaydedilir. <xref:System.Activities.Tracking.TrackingRecord> nesnelerine abone olan bu uzantılar katılımcıları izleme olarak adlandırılır. Katılımcıları izlemek, nesneleri <xref:System.Activities.Tracking.TrackingRecord> erişen ve bunları yapmak için yazıldığı şekilde işleyen genişletilebilirlik noktalarıdır. İzleme altyapısı, bir katılımcının kayıtların bir alt kümesine abone olmasına izin vermek için giden izleme kayıtlarında bir filtrenin uygulamasına izin verir. Bu filtreleme mekanizması, bir izleme profili dosyası aracılığıyla gerçekleştirilir.  
  
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
