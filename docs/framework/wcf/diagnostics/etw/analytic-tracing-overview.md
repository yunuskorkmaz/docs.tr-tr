---
title: Çözümleme İzleme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 7718c8f2a82178bedc080eda0cd0fdf728213a27
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900633"
---
# <a name="analytic-tracing-overview"></a>Analitik izlemeye genel bakış

[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] çözümleme izlemesi, Windows için olay Izleme 'nin (ETW) üzerinde yüksek performanslı ve düşük bir ayrıntı izleme özelliği kümesidir. ETW, izleme işlemlerinin yükünü büyük ölçüde azaltmak için çekirdek düzeyinde çalışır. Kullanıcı ve çekirdek modu olaylarını etkin bir şekilde arabelleğe alır ve hizmetin yeniden başlatılmasına gerek kalmadan günlük kaydının dinamik olarak etkinleştirilmesini sağlar. İzleme verileri, oluşturulduktan ve alındıktan sonra olay günlüklerinde kullanılabilir.

ETW hakkında daha fazla bilgi için bkz. [ETW Ile hata ayıklamayı ve performans ayarlamayı geliştirme](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).

 Windows Vista ve Windows Server 2008, uygulamayı çözümlemek için Windows sistem, güvenlik ve uygulama olay günlüklerini kullanmanın yanı sıra, uygulamalar ve hizmetler günlükleri üst düzey düğümü altında ek Günlükler sunmuştur. Bu yeni günlüklerin amacı, belirli bir uygulama için olayları veya sistem genelinde etkileri olan (güvenlik olay günlüğünün kaydedebileceği olayların türü gibi) genel olaylar yerine belirli bir bileşeni depolar. [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], WCF Izleme olaylarının, WCF Ileti günlüklerinin ve [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Izleme kayıtlarının uygulama ve hizmet günlüklerine kaydedilmesini sağlar ve birleştirir.

Aşağıdaki bölümlerde, WCF analitik izleme için uygulanan kavramlar ve yetenekler ele alınmaktadır.

## <a name="enable-wcf-diagnostics-settings"></a>WCF tanılama ayarlarını etkinleştir

WCF tanılama `<system.serviceModel><diagnostics>` yapılandırma bölümünde etkinleştirilir.

```xml
<system.serviceModel>
  <diagnostics>
```

Web 'de barındırılan IIS sanal uygulamasının WCF Tanılama ayarları *Web. config* dosyasında etkinleştirilmiştir. Diğer bir seçenek de uygulama içindeki bir alt dizinde *Web. config* dosyası oluşturmaktır. Bu seçim, bir alt dizin içindeki tüm hizmetlere ayarları uygular. Tanılama ayarlarının uygulamadaki tüm hizmetler için düzenli olarak başlatıldığından emin olmak için, ayarlar uygulama içindeki *Web. config* dosyasında olmalıdır ve uygulamanın içindeki her bir alt dizinden birine değil.

## <a name="channels"></a>Kanallar

ETW, yazılım bileşenlerinin kanalları kullanarak belirli bir hedef kitleye olayları doğrudan izlemesini sağlar. Örneğin, sistem yöneticileri için olayları, uygulama geliştiricilerinin başka bir kanala karşı ilgilenmediği bir kanala ve olaylara gönderebilirsiniz. Kanallar, tüketicilerin Olay Görüntüleyicisi kullanarak bir kanalın olaylarını görüntüleyebilmeleri için Windows ile adlandırılır ve kaydedilir.

 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] içindeki WCF için analitik izleme özelliği, Microsoft-Windows-Application-Server-Applications kanalına yazar. Bu kanal, üretimde WCF hizmetlerinin sistem durumunu izlemek isteyen kullanıcılar için tasarlanmıştır. Birçok sistem durumu izleme ve sorun giderme senaryosunda kullanılabilecek küçük bir olay kümesini tanımlar.

 İletilerin olay günlüğünde doğru şekilde kodu çözülecek şekilde Windows bildirimi için olay Izlemeyi etkinleştirmek üzere komut satırındaki ServiceModelReg aracını aşağıdaki gibi kullanın:

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a>Dinamik yapılandırma

ETW altyapısı, izlemenin etkin ve standart Windows araçları kullanılarak dinamik olarak yapılandırılmasını sağlar. Daha fazla bilgi için bkz. [analitik Izlemeyi dinamik olarak etkinleştirme](dynamically-enabling-analytic-tracing.md).

## <a name="message-flow-tracing"></a>İleti akışı Izleme

İleti akışı izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [Ileti akışı Izlemeyi yapılandırma](configuring-message-flow-tracing.md).

## <a name="keywords"></a>Anahtar Sözcükler

Anahtar sözcükler, izleme iletilerini filtrelemek için kullanılır ve hangi .NET Framework bileşeni olayı yayındığını tanımlar. Daha fazla bilgi için bkz. [analitik Izlemeyi dinamik olarak etkinleştirme](dynamically-enabling-analytic-tracing.md).
