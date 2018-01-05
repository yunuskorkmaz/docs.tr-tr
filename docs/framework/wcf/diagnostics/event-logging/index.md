---
title: "WCF'de Etkinlikleri Günlüğe Kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4028772caef8e5c0301ab3a6a0bde2f180d821ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-in-wcf"></a>WCF'de Etkinlikleri Günlüğe Kaydetme
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Windows Olay Günlüğü'nde iç olayları izler.  
  
## <a name="viewing-event-logs"></a>Olay günlüklerini görüntüleme  
 Olay günlüğü varsayılan olarak otomatik olarak etkinleştirilir ve devre dışı bırakmak için bir mekanizma yoktur. Tarafından kaydedilen olayları [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Olay Görüntüleyicisi'ni kullanarak görüntülenebilir. Bu aracı başlatmak için tıklatın **Başlat**, tıklatın **Denetim Masası**, çift **Yönetimsel Araçlar**, çift tıklayın ve ardından **Olay Görüntüleyicisi'ni**.  
  
### <a name="application-event-log"></a>Uygulama olay günlüğü  
 **Uygulama olay günlüğü** tarafından oluşturulan olayları çoğunu içeren [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Çoğu girişleri, belirli bir özellik için uygulama başlatma başarısız olduğunu gösterir. Örnekler:  
  
-   İleti günlüğe kaydetme/izleme: [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] izleme ve iletileri günlüğe kaydetme başarısız olduğunda olay günlüğüne bir olay yazar. Bununla birlikte, her izleme hatası bir olay tetikler. Olay günlüğü izlemeleri hatalarıyla tamamen doldurulmuş önlemek için [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] böyle bir olay için bir 10 dakikalık Kararma süresi uygular. Bu olması durumunda gelir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] izleme hatası değil bunu şekilde yeniden en az 10 dakika için olay günlüğüne yazar.  
  
-   Dinleyici paylaşılan: WCF TCP bağlantı noktası Paylaşımı hizmeti başlatmak başarısız olduğunda bir olayı günlüğe kaydeder.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Başlatmak hizmet başarısız olduğunda olayları günlüğe kaydeder.  
  
-   Başlatma hataları veya kilitlenme gibi kritik ve hata olayları  
  
-   İleti günlüğe kaydetme açık: ileti günlüğe kaydetme açık olduğunda olayları günlüğe kaydeder. Bu ileti üstbilgilerini ve gövdeleri hassas, uygulamaya özgü bilgileri kaydedilebilir yöneticiyi bilgilendirmek için yapılır.  
  
-   Bir olay kaydedilir zaman `enableLoggingKnownPII` özniteliğini `machineSettings` öğesinin `machine.config` dosya ayarlanır. Bu öznitelik, makinede çalışan herhangi bir uygulama bilinen kişisel bilgileri (PII) oturum açmasına izin varsa belirtir.  
  
-   Varsa `logKnownPii` ya da özniteliğinde `app.config` veya `web.config` dosya ayarlanmış `true` PII günlük özelliğini açmak belirli bir uygulama için ancak `enableLoggingKnownPII` özniteliğini `machineSettings` öğesinin `machine.config` dosya ayarlanır için `false`, bir olay kaydedilir. Ayrıca, her iki `logKnownPii` ve `enableLoggingKnownPII` ayarlanır `true`, ve olay günlüğe kaydedilir. Bu yapılandırma ayarları hakkında daha fazla bilgi için güvenlik bölümüne bakın [yapılandırma ileti günlüğe kaydetme](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.  
  
### <a name="security-event-log"></a>Güvenlik olay günlüğü  
 **Güvenlik olay günlüğü** WCF tarafından günlüğe kaydedilen güvenlik denetim olaylarını içerir.  
  
### <a name="system-event-log"></a>Sistem olay günlüğü  
 WCF değil oturum herhangi bir şey **sistem olay günlüğünü**.  
  
### <a name="event-log-entries"></a>Olay günlüğü girişleri  
 **Kaynak** olay günlüğü girişi oluşturur derleme adıdır.  
  
 Bir olay günlüğü girişi türü, bir olayın önem belirtmek için kullanılır. Her olay olduğunda olay raporları uygulama gösteren tek türde olması gerekir. Olay Görüntüleyicisi'ni bu tür günlük liste görünümünde görüntülemek için hangi simgesine belirlemek için kullanır. Bir olay günlüğü girişi farklı olay türü için bkz: <xref:System.Diagnostics.EventLogEntryType>.  
  
 "Daha fazla bilgi" tıkladığınızda, Olay Görüntüleyicisi'nde bir olayı görüntülerken, Olay Görüntüleyicisi'ni Internet üzerinden bilgi gönderebilir. Daha fazla bilgi için Olay Görüntüleyicisi'ni yardımına bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Etkinlik Genel Başvurusu](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
