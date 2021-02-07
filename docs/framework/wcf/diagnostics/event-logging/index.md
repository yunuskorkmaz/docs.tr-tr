---
description: Daha fazla bilgi için bkz. WCF 'de olay günlüğü
title: WCF'de Etkinlikleri Günlüğe Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 741e6efce9f5fffec607d511f04a400e1292b682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744220"
---
# <a name="event-logging-in-wcf"></a>WCF'de Etkinlikleri Günlüğe Kaydetme

Windows Communication Foundation (WCF), Windows olay günlüğündeki iç olayları izler.  
  
## <a name="viewing-event-logs"></a>Olay günlüklerini görüntüleme  

 Olay günlüğü otomatik olarak varsayılan olarak etkindir ve devre dışı bırakmak için bir mekanizma yoktur. WCF tarafından günlüğe kaydedilen olaylar Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu aracı başlatmak için **Başlat**' a tıklayın, **Denetim Masası**' na tıklayın, **Yönetimsel Araçlar**' a çift tıklayın ve ardından **Olay Görüntüleyicisi**' ye çift tıklayın.  
  
### <a name="application-event-log"></a>Uygulama Olay Günlüğü  

 **Uygulama olay günlüğü** , WCF tarafından oluşturulan olayların çoğunu içerir. Girişlerin çoğu, belirli bir özelliğin bir uygulama için başlayamayacağı anlamına gelebilir. Örnekler arasında şunlar yer almaktadır:  
  
- İleti günlüğe kaydetme/izleme: WCF, izleme ve ileti günlüğe kaydetme başarısız olduğunda olay günlüğüne bir olay yazar. Ancak, her izleme hatası bir olayı tetiklemiyor. Olay günlüğünün izleme hatalarıyla tamamen doldurulmasını engellemek için, WCF bu tür bir olay için 10 dakikalık bir kararma süresi uygular. Bu, WCF 'nin olay günlüğüne bir izleme hatası yazıyorsa, en az 10 dakika boyunca bunu yapamayacağı anlamına gelir.  
  
- Paylaşılan dinleyici: WCF TCP bağlantı noktası paylaşım hizmeti, başlayamıyorsa bir olay günlüğe kaydeder.  
  
- CardSpace: hizmet başlayamıyorsa olayları günlüğe kaydeder.  
  
- Başlatma hataları veya kilitlenmeler gibi kritik ve hata olayları  
  
- İleti günlüğe kaydetme açıldı: ileti günlüğe kaydetme açık olduğunda olayları günlüğe kaydeder. Bu, yöneticiye gizli ve uygulamaya özgü bilgilerin ileti üstbilgilerinde ve gövdelerinde günlüğe kaydedileceğini bildirmek için kullanılır.  
  
- `enableLoggingKnownPII`Dosyanın öğesindeki özniteliği ayarlandığında bir olay günlüğe kaydedilir `machineSettings` `machine.config` . Bu öznitelik, makinede çalışan herhangi bir uygulamanın bilinen kişisel olarak tanımlanabilen bilgileri (PII) günlüğe kaydetme izni olup olmadığını belirtir.  
  
- `logKnownPii`Ya da dosyasındaki özniteliği, `app.config` `web.config` `true` PII günlüğünü açmak için belirli bir uygulama için olarak ayarlandıysa, ancak `enableLoggingKnownPII` `machineSettings` dosyanın öğesindeki özniteliği `machine.config` olarak ayarlandığında `false` bir olay günlüğe kaydedilir. Ayrıca, `logKnownPii` ve olarak `enableLoggingKnownPII` ayarlanmışsa `true` ve olay günlüğe kaydedilir. Bu yapılandırma ayarları hakkında daha fazla bilgi için, [Ileti günlüğünü yapılandırma](../configuring-message-logging.md) konusunun Güvenlik bölümüne bakın.  
  
### <a name="security-event-log"></a>Güvenlik olay günlüğü  

 **Güvenlik olay günlüğü** , WCF tarafından günlüğe kaydedilen güvenlik denetim olaylarını içerir.  
  
### <a name="system-event-log"></a>Sistem Olay Günlüğü  

 WCF, **sistem olay günlüğündeki** herhangi bir şeyi günlüğe eklemez.  
  
### <a name="event-log-entries"></a>Olay günlüğü girdileri  

 Bir olayın **kaynağı** , günlük girişini üreten derlemenin adıdır.  
  
 Olay günlüğü girişinin türü, bir olayın önem derecesini belirtmek için kullanılır. Her olay, uygulamanın olayı raporladığında gösterdiği tek bir türde olmalıdır. Olay Görüntüleyicisi, günlüğün liste görünümünde hangi simgenin görüntüleneceğini anlamak için bu türü kullanır. Olay günlüğü girişinin farklı olay türü için bkz <xref:System.Diagnostics.EventLogEntryType> ..  
  
 Olay Görüntüleyicisi bir olayı görüntülerken "daha fazla bilgi" ye tıkladığınızda, Olay Görüntüleyicisi Internet üzerinden bilgi gönderebilir. Daha fazla bilgi için Olay Görüntüleyicisi yardımına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve tanılama](../index.md)
- [Etkinlik Genel Başvurusu](events-general-reference.md)
