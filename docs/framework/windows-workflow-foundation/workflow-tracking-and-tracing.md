---
title: İzleme ve izleme iş akışı
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 8490299e995a469860f660a50a69915d5ddc4940
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731621"
---
# <a name="workflow-tracking-and-tracing"></a>İzleme ve izleme iş akışı
Windows iş akışı izleme bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özelliği iş akışının yürütülmesini görünürlük sağlayacak şekilde tasarlanmıştır. Bu, bir iş akışı örneği yürütülmesini izlemek için izleme altyapısı sağlar. İzleme WF altyapısının şeffaf bir şekilde yürütme sırasında anahtar olayları yansıtan kayıtları yaymak için bir iş akışı Instruments. Bu işlev varsayılan olarak tüm kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. Herhangi bir değişiklik için yapılması gereken bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] gerçekleşmesi izleme iş akışını. Bu, almak istediğiniz izleme veri miktarını karar adımlarından oluşur. Bir iş akışı örneği başlatıldığında veya izleme işleme tamamlandıktan kayıtları yayılan. İzleme, iş akışı değişkenleri ile ilişkili iş ilgili verileri de ayıklayabilirsiniz. İş akışı sistem işleme bir sırayı temsil ediyorsa, örneğin, sipariş kimliği ile birlikte ayıklanabileceği <xref:System.Activities.Tracking.TrackingRecord> nesne. Genel olarak, izleme WF etkinleştirme Tanılama veya İş analizi verilerini bir iş akışı yürütülmesini erişilecek kolaylaştırır.  
  
 Bu bileşenleri izleme izleme hizmetinde eşdeğer [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]programlama modeli WF izleme özelliği için Basitleştirilmiş ve performansı İyileştirildi. İzleme çalışma zamanı iş akışı yaşam döngüsü, iş akışı etkinlikleri ve özel olaylar ile ilgili olayları yaymak için bir iş akışı örneği kullanır.  
  
 Windows Server App Fabric iş akışını ve WCF hizmetleri yürütülmesini izleme olanağı da sağlar. Daha fazla bilgi için [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273) ve [Windows Server AppFabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 İş akışı çalışma zamanı sorunlarını gidermek için tanılama iş akışı izlemeyi etkinleştirebilirsiniz. Daha fazla bilgi için [iş akışı izleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md).  
  
 İzleme altyapısının birincil bileşenlerini programlama modelini anlamak için bu konuda ele alınmıştır:  
  
-   <xref:System.Activities.Tracking.TrackingRecord> İş akışı çalışma zamanını şuradan yayılan nesneleri. Daha fazla bilgi için [izleme kayıtları](../../../docs/framework/windows-workflow-foundation/tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant> nesneleri abone <xref:System.Activities.Tracking.TrackingRecord> nesneleri. İzleme katılımcıları yükü işlemek için mantığı içeren <xref:System.Activities.Tracking.TrackingRecord> nesneleri (örneğin, bunlar bir dosyaya yazmak seçebilir). Daha fazla bilgi için [izleme katılımcıları](../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile> nesneleri bir iş akışı örneğinden yayılan filtre izleme kayıtları. Daha fazla bilgi için [izleme profilleri](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>İş akışı izleme altyapısı  
 İş akışı izleme altyapısı bir Yayımla ve abone ol paradigma izler. İş akışı örneğinin uzantıları iş akışına olarak kayıtlı aboneleri kayıtları izleme kayıtları izleme listesinin yayımcısıdır. Abone bu uzantılar <xref:System.Activities.Tracking.TrackingRecord> nesneleri izleme katılımcıları çağrılır. İzleme katılımcıları erişim genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.TrackingRecord> nesneleri ve bunları hangi şekilde Bunu yapmak için yazılır, işlem. Bir kayıt alt kümesi için abone olmak için bir katılımcı izin vermek için giden izleme kayıtları bir filtre uygulamayı izleme altyapısı sağlar. Bu filtreleme mekanizması aracılığıyla bir izleme gerçekleştirilir profili dosyası.  
  
 İzleme altyapısının yüksek düzeyde bir görünümü aşağıdaki çizimde gösterilmektedir.  
  
 ![İş akışı izleme altyapısı](../../../docs/framework/windows-workflow-foundation/media/wv.gif "WV")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzleme Kayıtları](../../../docs/framework/windows-workflow-foundation/tracking-records.md)  
 İş akışı çalışma zamanı yayan izleme kayıtları açıklar.  
  
 [İzleme Profilleri](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
 İzleme profilleri nasıl kullanıldığı açıklanır.  
  
 [İzleme Katılımcıları](../../../docs/framework/windows-workflow-foundation/tracking-participants.md)  
 Sistem tarafından sağlanan izleme katılımcı kullanma veya özel izleme katılımcıları oluşturulacağını açıklar.  
  
 [İş Akışı için İzlemeyi Yapılandırma](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
 Bir iş akışı için izlemeyi yapılandırma açıklar.  
  
 [İş Akışı İzleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 Bir iş akışı hata ayıklama izlemeyi etkinleştirmek için iki şekilde açıklar.  
  
 [İzleme Kullanarak İş Akışı Yürütme Süresini Belirleme](../../../docs/framework/windows-workflow-foundation/determining-workflow-execution-duration-using-tracing.md)  
 İş akışı yürütme süresini belirlemek için izleme iletileri kullanmayı açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL İzleme](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)
