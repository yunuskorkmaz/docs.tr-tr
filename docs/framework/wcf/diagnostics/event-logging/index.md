---
title: WCF'de Etkinlikleri Günlüğe Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 0c74b93be026007a5593372c938cf73e08fafb15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797802"
---
# <a name="event-logging-in-wcf"></a>WCF'de Etkinlikleri Günlüğe Kaydetme
Windows Communication Foundation (WCF), Windows olay günlüğündeki iç olayları izler.  
  
## <a name="viewing-event-logs"></a>Olay günlüklerini görüntüleme  
 Olay günlüğü otomatik olarak varsayılan olarak etkindir ve devre dışı bırakmak için bir mekanizma yoktur. WCF tarafından günlüğe kaydedilen olaylar Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu aracı başlatmak için **Başlat**' a tıklayın, **Denetim Masası**' na tıklayın, **Yönetimsel Araçlar**' a çift tıklayın ve ardından **Olay Görüntüleyicisi**' ye çift tıklayın.  
  
### <a name="application-event-log"></a>Uygulama olay günlüğü  
 **Uygulama olay günlüğü** , WCF tarafından oluşturulan olayların çoğunu içerir. Girişlerin çoğu, belirli bir özelliğin bir uygulama için başlayamayacağı anlamına gelebilir. Örnekler:  
  
- İleti günlüğe kaydetme/izleme: WCF, izleme ve ileti günlüğe kaydetme başarısız olduğunda olay günlüğüne bir olay yazar. Ancak, her izleme hatası bir olayı tetiklemiyor. Olay günlüğünün izleme hatalarıyla tamamen doldurulmasını engellemek için, WCF bu tür bir olay için 10 dakikalık bir kararma süresi uygular. Bu, WCF 'nin olay günlüğüne bir izleme hatası yazıyorsa, en az 10 dakika boyunca bunu yapamayacağı anlamına gelir.  
  
- Paylaşılan dinleyici: WCF TCP bağlantı noktası paylaşım hizmeti, başlayamıyorsa bir olay günlüğe kaydeder.  
  
- Rağmen Hizmet başlayamıyorsa olayları günlüğe kaydeder.  
  
- Başlatma hataları veya kilitlenmeler gibi kritik ve hata olayları  
  
- İleti günlüğe kaydetme açıldı: İleti günlüğe kaydetme açık olduğunda olayları günlüğe kaydeder. Bu, yöneticiye gizli ve uygulamaya özgü bilgilerin ileti üstbilgilerinde ve gövdelerinde günlüğe kaydedileceğini bildirmek için kullanılır.  
  
- Dosyanın öğesindeki `enableLoggingKnownPII` `machineSettings` özniteliği ayarlandığında bir olay günlüğe kaydedilir. `machine.config` Bu öznitelik, makinede çalışan herhangi bir uygulamanın bilinen kişisel olarak tanımlanabilen bilgileri (PII) günlüğe kaydetme izni olup olmadığını belirtir.  
  
- `app.config` `enableLoggingKnownPII` `true` Ya dadosyasındaki`machineSettings` özniteliği, PII günlüğünü açmak için belirli bir uygulama için olarak ayarlandıysa, ancak dosyanınöğesindekiözniteliğiayarlanır`machine.config` `logKnownPii` `web.config` için `false`bir olay günlüğe kaydedilir. Ayrıca `logKnownPii` , ve `enableLoggingKnownPII` olarak ayarlanmışsa `true`ve olay günlüğe kaydedilir. Bu yapılandırma ayarları hakkında daha fazla bilgi için, [Ileti günlüğünü yapılandırma](../configuring-message-logging.md) konusunun Güvenlik bölümüne bakın.  
  
### <a name="security-event-log"></a>Güvenlik olay günlüğü  
 **Güvenlik olay günlüğü** , WCF tarafından günlüğe kaydedilen güvenlik denetim olaylarını içerir.  
  
### <a name="system-event-log"></a>Sistem olay günlüğü  
 WCF, **sistem olay günlüğündeki**herhangi bir şeyi günlüğe eklemez.  
  
### <a name="event-log-entries"></a>Olay günlüğü girdileri  
 Bir olayın **kaynağı** , günlük girişini üreten derlemenin adıdır.  
  
 Olay günlüğü girişinin türü, bir olayın önem derecesini belirtmek için kullanılır. Her olay, uygulamanın olayı raporladığında gösterdiği tek bir türde olmalıdır. Olay Görüntüleyicisi, günlüğün liste görünümünde hangi simgenin görüntüleneceğini anlamak için bu türü kullanır. Olay günlüğü girişinin farklı olay türü için bkz <xref:System.Diagnostics.EventLogEntryType>.  
  
 Olay Görüntüleyicisi bir olayı görüntülerken "daha fazla bilgi" ye tıkladığınızda, Olay Görüntüleyicisi Internet üzerinden bilgi gönderebilir. Daha fazla bilgi için Olay Görüntüleyicisi yardımına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve Tanılama](../index.md)
- [Etkinlik Genel Başvurusu](events-general-reference.md)
