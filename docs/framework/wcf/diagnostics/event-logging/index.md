---
title: WCF'de Etkinlikleri Günlüğe Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: ea0e6f3dc66bf40d631077c0dce20ea46f3a6688
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="event-logging-in-wcf"></a>WCF'de Etkinlikleri Günlüğe Kaydetme
Windows Communication Foundation (WCF) Windows Olay Günlüğü'nde iç olayları izler.  
  
## <a name="viewing-event-logs"></a>Olay günlüklerini görüntüleme  
 Olay günlüğü varsayılan olarak otomatik olarak etkinleştirilir ve devre dışı bırakmak için bir mekanizma yoktur. WCF tarafından günlüğe kaydedilen olayları Olay Görüntüleyicisi'ni kullanarak görüntülenebilir. Bu aracı başlatmak için tıklatın **Başlat**, tıklatın **Denetim Masası**, çift **Yönetimsel Araçlar**, çift tıklayın ve ardından **Olay Görüntüleyicisi'ni**.  
  
### <a name="application-event-log"></a>Uygulama olay günlüğü  
 **Uygulama olay günlüğü** WCF tarafından oluşturulan olayları çoğunu içerir. Çoğu girişleri, belirli bir özellik için uygulama başlatma başarısız olduğunu gösterir. Örnekler:  
  
-   İleti günlüğe kaydetme/izleme: izleme ve iletileri günlüğe kaydetme başarısız olduğunda WCF, bir olay olay günlüğüne yazar. Bununla birlikte, her izleme hatası bir olay tetikler. Olay günlüğü izlemeleri hatalarıyla tamamen doldurulmuş önlemek için böyle bir olay için bir 10 dakikalık Kararma süresi WCF uygular. Bu WCF izleme hatası olay günlüğüne yazar, bu nedenle yeniden en az 10 dakika için yapacağınız değil anlamına gelir.  
  
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
