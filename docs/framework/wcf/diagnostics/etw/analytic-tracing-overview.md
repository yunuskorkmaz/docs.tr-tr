---
title: Çözümleme İzleme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: f6ffed3d9f0bf5e3dc5698d51276eb1db276993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837499"
---
# <a name="analytic-tracing-overview"></a>Çözümleme İzleme Genel Bakış
[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] çözümleme izlemesi, Windows için olay Izleme 'nin (ETW) üzerinde yüksek performanslı ve düşük bir ayrıntı izleme özelliği kümesidir. ETW, izleme işlemlerinin yükünü büyük ölçüde azaltmak için çekirdek düzeyinde çalışır. Kullanıcı ve çekirdek modu olaylarını etkin bir şekilde arabelleğe alır ve hizmetin yeniden başlatılmasına gerek kalmadan günlük kaydının dinamik olarak etkinleştirilmesini sağlar. İzleme verileri, oluşturulduktan ve alındıktan sonra olay günlüklerinde kullanılabilir.  
  
 ETW hakkında daha fazla bilgi için bkz. [ETW Ile hata ayıklamayı ve performans ayarlamayı geliştirme](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Windows Vista ve [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] uygulamayı çözümlemek için Windows sistem, güvenlik ve uygulama olay günlüklerini kullanmanın yanı sıra, uygulama ve hizmet günlükleri üst düzey düğümü altında ek Günlükler sunmuştur. Bu yeni günlüklerin amacı, belirli bir uygulama için olayları veya sistem genelinde etkileri olan (güvenlik olay günlüğünün kaydedebileceği olayların türü gibi) genel olaylar yerine belirli bir bileşeni depolar. [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], WCF Izleme olaylarının, WCF Ileti günlüklerinin ve [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Izleme kayıtlarının uygulama ve hizmet günlüklerine kaydedilmesini sağlar ve birleştirir.  
  
## <a name="concepts-and-capabilities"></a>Kavramlar ve yetenekler  
 Aşağıdaki kavramlar ve yetenekler WCF analitik Izleme için geçerlidir.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>WCF tanılama ayarlarını etkinleştirme  
 WCF tanılama \<System. serviceModel >\<Tanılama > yapılandırma bölümünde etkinleştirilmiştir.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Web 'de barındırılan bir IIS sanal uygulaması için WCF Tanılama ayarları, ' Web. config dosyasında etkindir. Diğer bir seçenek de uygulama içindeki bir alt dizinde Web. config oluşturmaktır.  Bu seçenek, ayarları bir alt dizin içindeki tüm hizmetlere uygular.  Tanılama ayarlarının uygulamadaki tüm hizmetler için tutarlı bir şekilde başlatıldığından emin olmak için, ayarların uygulama dizinindeki Web. config içinde olması ve uygulamadaki ayrı alt dizinlerden birinde olmaması gerekir.  
  
### <a name="channels"></a>Kanallar  
 ETW, yazılım bileşenlerinin kanalları kullanarak belirli bir hedef kitleye olayları doğrudan izlemesini sağlar. Örneğin, sistem yöneticileri için olayları tek bir kanala ve uygulama geliştiricilerinin başka bir kanala karşı ilgilenme olaylarını gönderebilirsiniz. Kanallar, tüketicilerin Olay Görüntüleyicisi kullanarak bir kanalın olaylarını görüntüleyebilmeleri için Windows ile adlandırılır ve kaydedilir.  
  
 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] içindeki WCF için analitik izleme özelliği, Microsoft-Windows-Application-Server-Applications kanalına yazar. Bu kanal, üretimde WCF hizmetlerinin sistem durumunu izlemek isteyen kullanıcılar için özel olarak tasarlanmıştır. Birçok sistem durumu izleme ve sorun giderme senaryosunda kullanılabilecek küçük, olay kümesini tanımlar.  
  
 İletilerin olay günlüğünde doğru şekilde kodu çözülecek şekilde Windows bildirimi için olay Izlemeyi etkinleştirmek üzere komut satırındaki ServiceModelReg aracını aşağıdaki gibi kullanın:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dinamik yapılandırma  
 ETW altyapısı, izlemenin etkin ve standart Windows araçları kullanılarak dinamik olarak yapılandırılmasını sağlar. Daha fazla bilgi için bkz. [analitik Izlemeyi dinamik olarak etkinleştirme](dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>İleti akışı Izleme  
 İleti akışı izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [Ileti akışı Izlemeyi yapılandırma](configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Anahtar Sözcükler  
 Anahtar sözcükler, izleme iletilerini filtrelemek için kullanılır ve hangi .NET Framework bileşeni olayı yayındığını tanımlar. Daha fazla bilgi için bkz. [analitik Izlemeyi dinamik olarak etkinleştirme](dynamically-enabling-analytic-tracing.md).
