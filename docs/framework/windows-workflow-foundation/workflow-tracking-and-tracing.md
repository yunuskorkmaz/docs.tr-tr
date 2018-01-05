---
title: "İzleme ve izleme iş akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7383d899af741e4a6c85b40e2316a6b759aa416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-tracking-and-tracing"></a>İzleme ve izleme iş akışı
Windows iş akışı izleme bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özellik iş akışı yürütme görünürlük sağlamak üzere tasarlanmıştır. Bir iş akışı örneğini yürütmeyi izlemek için izleme altyapısı sağlar. WF izleme altyapı saydam bir iş akışı yürütme sırasında anahtar olayları yansıtma kayıtları yayma Instruments. Bu işlev varsayılan herhangi kullanılabilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. Herhangi bir değişiklik için yapılması gereken bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] gerçekleşmesi izleme iş akışını. Bu karar almak istediğiniz ne kadar izleme verilerini, yalnızca bir konudur. Bir iş akışı örneği başlatıldığında veya, izleme, işlem tamamlandıktan kayıtları gösterilen. İzleme, iş akışı değişkenleri ile ilişkili iş ilgili verileri de ayıklayabilirsiniz. İş akışı işleme sistemi sipariş temsil ediyorsa, örneğin, sipariş kimliği ile birlikte ayıklanabilir <xref:System.Activities.Tracking.TrackingRecord> nesnesi. Genel olarak, izleme WF etkinleştirme Tanılama ya da bir iş akışının yürütülmesini erişilecek İş analizi veri kolaylaştırır.  
  
 Bu bileşenler izleme izleme hizmetinde eşdeğerdir [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], performansı geliştirilmiştir ve programlama modeli WF izleme özelliği için basitleştirilmiştir. İzleme çalışma zamanı iş akışı yaşam döngüsü, iş akışı etkinlikleri ve özel olaylar ile ilgili olayları yaymak üzere bir iş akışı örneği Instruments.  
  
 Windows Server App Fabric ayrıca bir WCF ve iş akışı hizmetleri yürütülmesi izleme yeteneği sağlar. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273) ve [Windows Server AppFabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201287)  
  
 İş akışı çalışma zamanı sorun giderme için tanılama iş akışı izlemeyi etkinleştirebilirsiniz. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İş akışı izleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md).  
  
 İzleme altyapısının birincil bileşenleri programlama modeli anlamak için bu konuda ele alınmaktadır:  
  
-   <xref:System.Activities.Tracking.TrackingRecord>İş akışı çalışma zamanı gösterilen nesneleri. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kayıtları izleme](../../../docs/framework/windows-workflow-foundation/tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant>nesneleri abone <xref:System.Activities.Tracking.TrackingRecord> nesneleri. İzleme katılımcıları yükü işlemek için mantığı içeren <xref:System.Activities.Tracking.TrackingRecord> nesneleri (örneğin, bir dosyaya yazmak tercih ettikleri). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Katılımcıları izleme](../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile>nesneleri bir iş akışı örneğinden yayılan izleme kayıtları filtreleyin. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Profilleri izleme](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>İş akışı izleme altyapısı  
 İş akışı izleme altyapısı bir Yayımla ve abone ol standardı izler. İş akışı örneği izleme kayıtları aboneleri akışına uzantıları olarak kaydettirilmiş ederken kayıtları, izleme, yayımcı ' dir. Abone bu uzantıları <xref:System.Activities.Tracking.TrackingRecord> nesneleri izleme katılımcıları çağrılır. İzleme katılımcılar erişim genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.TrackingRecord> nesneleri ve bunu yapmak için yazılır bunlar herhangi bir biçimde işlem. İzleme altyapısının bir filtre uygulamasını kayıtların bir alt kümesini için abone olmak katılımcı izin vermek için giden izleme kayıtları olanak tanır. Bu filtreleme mekanizması aracılığıyla bir izleme gerçekleştirilir profil dosyası.  
  
 İzleme altyapı yüksek düzey bir görünümünü aşağıdaki çizimde gösterilmiştir.  
  
 ![İş akışı altyapı izleme](../../../docs/framework/windows-workflow-foundation/media/wv.gif "WV")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzleme Kayıtları](../../../docs/framework/windows-workflow-foundation/tracking-records.md)  
 İş akışı çalışma zamanı yayar izleme kayıtları açıklar.  
  
 [İzleme Profilleri](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
 İzleme profilleri nasıl kullanıldığı açıklanır.  
  
 [İzleme Katılımcıları](../../../docs/framework/windows-workflow-foundation/tracking-participants.md)  
 Sistem tarafından sağlanan izleme katılımcı kullanma veya özel izleme katılımcıları oluşturulacağını açıklar.  
  
 [İş Akışı için İzlemeyi Yapılandırma](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
 Bir iş akışı için izleme yapılandırma açıklar.  
  
 [İş Akışı İzleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 Bir iş akışı için hata ayıklama izlemeyi etkinleştirmek için iki yol açıklar.  
  
 [İzleme Kullanarak İş Akışı Yürütme Süresini Belirleme](../../../docs/framework/windows-workflow-foundation/determining-workflow-execution-duration-using-tracing.md)  
 İzleme iletileri iş akışı yürütme süresini belirlemek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL İzleme](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)
