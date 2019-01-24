---
title: WCF'de Etkinlikleri Günlüğe Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
  - 'event logging [WCF]'
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
---
# <a name="event-logging-in-wcf"></a>WCF'de Etkinlikleri Günlüğe Kaydetme
Windows Communication Foundation (WCF) Windows olay günlüğünden ilgili iç olayları izler.  
  
## <a name="viewing-event-logs"></a>Olay günlüklerini görüntüleme  
 Olay günlüğü varsayılan olarak otomatik olarak etkinleştirilir ve devre dışı bırakmak için bir mekanizma yoktur. WCF tarafından günlüğe kaydedilen olayları, Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu aracını başlatmak için tıklayın **Başlat**, tıklayın **Denetim Masası**, çift **Yönetimsel Araçlar**ve çift tıklatarak **Olay Görüntüleyicisi'ni**.  
  
### <a name="application-event-log"></a>Uygulama olay günlüğü  
 **Uygulama olay günlüğüne** WCF tarafından oluşturulan olaylar çoğunu içerir. Girişlerin çoğu belirli bir özellik için uygulama başlatma başarısız olduğunu gösterir. Örnekler:  
  
-   İleti günlüğe kaydetme/izleme: İzleme ve iletileri günlüğe kaydetme başarısız olduğunda WCF olay günlüğüne bir olay yazar. Ancak, her izleme başarısız bir olayı tetikler. Olay günlüğü izlemeleri hatalarla tamamen doldurulmuş önlemek için bu tür bir olay için 10 dakikalık bir Kararma süre WCF uygular. Başka bir deyişle, WCF izleme hatası olay günlüğüne yazar, bu nedenle yeniden en az 10 dakika için yapacağınız değil.  
  
-   Paylaşılan dinleyici: WCF TCP bağlantı noktası paylaşım hizmetini başlatmak başarısız olduğunda bir olayı günlüğe kaydeder.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Hizmeti başlatmak başarısız olduğunda olayları kaydeder.  
  
-   Başlatma hataları veya kilitlenmeleri gibi kritik ve hata olayları  
  
-   Günlüğe ileti kaydetme açık: Günlüğe ileti kaydetme açık olduğunda olayları kaydeder. Hassas ve uygulamaya özgü bilgileri ileti üstbilgileri ve gövdeleri kaydedilebilir yöneticiyi bilgilendirmek üzere budur.  
  
-   Bir olay kaydedilir, `enableLoggingKnownPII` özniteliğini `machineSettings` öğesinin `machine.config` dosya ayarlanır. Bu öznitelik makine üzerinde çalışan herhangi bir uygulama bilinen kişisel olarak tanımlanabilen bilgileri (PII) için izinli olup olmadığını belirtir.  
  
-   Varsa `logKnownPii` ya da özniteliğinde `app.config` veya `web.config` dosya kümesine `true` PII günlük özelliğini açmak belirli bir uygulama için ancak `enableLoggingKnownPII` özniteliğini `machineSettings` öğesinin `machine.config` dosya ayarlanmış için `false`, bir olay kaydedilir. Ayrıca, her iki `logKnownPii` ve `enableLoggingKnownPII` ayarlandığından `true`, ve olay günlüğe kaydedilir. Bu yapılandırma ayarları hakkında daha fazla bilgi için bkz: güvenlik bölümünü [iletileri günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.  
  
### <a name="security-event-log"></a>Güvenlik olay günlüğü  
 **Güvenlik olay günlüğü** WCF tarafından günlüğe kaydedilen güvenlik denetim olaylarını içerir.  
  
### <a name="system-event-log"></a>Sistem olay günlüğü  
 WCF değil oturum herhangi bir şey **sistem olay günlüğünü**.  
  
### <a name="event-log-entries"></a>Olay günlüğü girişleri  
 **Kaynak** olay günlük girişi oluşturur derlemenin adıdır.  
  
 Bir olay günlüğü girişi türü, bir olayın önem derecesini belirtmek için kullanılır. Her olay, olay rapor zaman uygulama gösteren tek bir türü içeren olması gerekir. Olay Görüntüleyicisi'ni bu tür günlük liste görünümünde hangi simgenin görüntüleneceğini belirlemek için kullanır. Bir olay günlüğü girişi farklı olay türü için bkz: <xref:System.Diagnostics.EventLogEntryType>.  
  
 "Daha fazla bilgi" tıkladığınızda bir olay Olay Görüntüleyicisi'nde görüntülendiğinde, Olay Görüntüleyicisi'ni Internet üzerinden bilgi gönderebilir. Daha fazla bilgi için Olay Görüntüleyicisi'ni Yardım'a bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Etkinlik Genel Başvurusu](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
