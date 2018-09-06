---
title: Çözümleme İzleme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 9918f07d9c26c1779a1eedfbc423c31e61659334
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788019"
---
# <a name="analytic-tracing-overview"></a>Çözümleme İzleme Genel Bakış
Analitik izleme [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] yüksek performanslı ve düşük ayrıntı izleme özelliği için olay izleme Windows (ETW üstünde) ayarlayın. ETW çekirdek izleme işlemlerinin ek yükü büyük ölçüde azaltmak için düzeyinde çalışır. Verimli bir şekilde kullanıcı ve çekirdek modu olaylarını arabelleğe alır ve dinamik günlük kaydını etkinleştirme hizmetin yeniden başlatılması gerekmeden sağlar. Sonraki günlükleri yayılan ve alınan olay izleme verileri mevcut değil.  
  
 ETW hakkında daha fazla bilgi için bkz: [artırmak hata ayıklama ve performans ayarlama ETW ile](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Uygulama, analiz etmek için Windows Sistem, güvenlik ve uygulama olay günlüklerini kullanmanın yanı sıra [!INCLUDE[wv](../../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] ek günlükler uygulama ve hizmet günlükleri en üst düzey düğümü altında sunulan. Bu yeni günlükler amacı, belirli bir uygulama veya sistem genelinde etkisi (örneğin, güvenlik olay günlüğüne kaydedebilir olayların türünü) genel olaylar yerine belirli bir bileşen için olayları depolamaktır. [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] birleştirir ve WCF ileti günlüklerini WCF izleme olaylarını günlüğe kaydetmeyi ilişkilendirir ve [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] kayıtları uygulamalar ve hizmet günlükleri izleme.  
  
## <a name="concepts-and-capabilities"></a>Kavramları ve özellikleri  
 Aşağıdaki kavramları ve özellikleri WCF analiz izleme uygulayın.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>WCF tanılama ayarlarını etkinleştirme  
 WCF tanılama içinde etkin \<system.serviceModel >\<Tanılama > yapılandırma bölümü.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 IIS Web barındırılan bir sanal uygulama için tanılama ayarları WCF etkinleştirilmişse, ' Web.config dosyası. Başka bir seçenek, uygulama içinde bir alt dizindeki bir Web.config oluşturmaktır.  Bu seçenek, tüm alt dizini içindeki Hizmetler ayarlarını uygular.  Tanılama ayarları uygulamadaki tüm hizmetler için tutarlı bir şekilde başlatıldığını emin olmak için ayarları Web.config uygulama dizini ve uygulama içinde bireysel alt dizinlerden biri içinde olmalıdır.  
  
### <a name="channels"></a>Kanallar  
 ETW kanalları kullanarak doğrudan izleme olayları belirli bir hedef kitle için yazılım bileşenlerini sağlar. Örneğin, bir kanala sistem yöneticileri için olayları ve olayları, uygulama geliştiricilerin dikkatli hakkında başka bir kanala gönderebilirsiniz. Kanal adlı ve Windows ile Olay Görüntüleyicisi'ni kullanarak bir kanalın olay tüketicileri görüntüleyebilmesi için kayıtlı.  
  
 WCF'de çözümleme izleme özelliği [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] Microsoft-Windows-uygulaması-Server-uygulamalar kanala yazar. Bu kanal, üretimde WCF hizmetlerinin sistem durumunu izlemek istediğiniz kullanıcılar için özel olarak tasarlanmıştır. Bu, olayların birçok sistem durumu izleme kullanılabilir ayarlayabilir ve sorun giderme senaryoları küçük tanımlar.  
  
 Olay izleme için Windows bildirim iletileri olay günlüğüne düzgün bir şekilde çözülür biçimde etkinleştirmek için komut satırında ServiceModelReg aracı şu şekilde kullanın:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dinamik yapılandırma  
 ETW altyapı izleme olmasını sağlar etkin ve standart Windows araçlarını kullanarak dinamik olarak yapılandırılır. Daha fazla bilgi için [dinamik olarak etkinleştirme analitik izleme](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>İleti akışı izlemeyi  
 İleti akışı izlemeyi etkinleştirme hakkında daha fazla bilgi için bkz. [ileti akışı izlemeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Anahtar Sözcükler  
 İzleme İletileri Filtrele ve hangi bileşeninin tanımlamak için kullanılan anahtar sözcükler [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] olay yayılır. Daha fazla bilgi için [dinamik olarak etkinleştirme analitik izleme](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
