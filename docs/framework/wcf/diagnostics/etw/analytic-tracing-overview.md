---
title: Çözümleme İzleme Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c29065ebe03617e288d7ebde3dc6b42cbfcf6061
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="analytic-tracing-overview"></a>Çözümleme İzleme Genel Bakış
Çözümleme izleme içinde [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] yüksek performans ve düşük ayrıntı izleme özelliği olay izleme için Windows (ETW üstünde) ayarlayın. ETW çekirdek izleme işlemlerinin ek yükünü önemli ölçüde azaltan düzeyinde çalışır. Verimli bir şekilde kullanıcı ve çekirdek modu olaylarını arabelleğe alır ve dinamik günlüğü etkinleştirme hizmet yeniden başlatıldığında gerek kalmadan sağlar. Sonraki günlükleri yayılan ve alınan olay izleme verileri mevcut değil.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] ETW, bkz: [artırmak hata ayıklama ve performans ayarlama ETW ile](http://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Uygulama, analiz etmek için Windows Sistem, güvenlik ve uygulama olay günlüklerini kullanmanın yanı sıra [!INCLUDE[wv](../../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] ek günlükleri uygulama ve hizmet günlükleri en üst düzey düğümü altında sunulan. Belirli bir uygulama veya sistem genelinde etkileyebilir (örneğin, güvenlik olay günlüğüne kaydedebilir olayların türünü) genel olayları yerine belirli bileşeni için olayları depolamak için bu yeni günlükler amacı budur. [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] birleştirir ve günlüğe karşılık gelen [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] izleme olayları [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti günlüklerini ve [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] kayıtları uygulamalar ve hizmet günlükleri izleme.  
  
## <a name="concepts-and-capabilities"></a>Kavramları ve Özellikler  
 Aşağıdaki kavramlar ve yetenekleri uygulamak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analitik izleme.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>WCF tanılama ayarlarını etkinleştirme  
 WCF tanılama içindeki etkin \<system.serviceModel >\<Tanılama > yapılandırma bölümü.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 WCF tanılama ayarlarını IIS Web barındırılan sanal uygulama için de etkinleştirildiğinde, ' Web.config dosyası. Uygulama içinde alt dizindeki bir Web.config oluşturun başka bir seçenektir.  Bu seçenek tüm alt dizindeki Hizmetleri ayarlarını uygular.  Tanılama ayarları uygulamadaki tüm hizmetler için tutarlı bir şekilde başlatılır emin olmak için ayarları bir uygulama içinde bireysel alt dizinleri değil ve uygulama dizinindeki Web.config içinde olmalıdır.  
  
### <a name="channels"></a>Kanallar  
 ETW kanalları kullanarak belirli bir hedef kitleye doğrudan izleme olayları için yazılım bileşenleri sağlar. Örneğin, bir kanala sistem yöneticileri için olaylar ve olaylar, uygulama geliştiricilerin bakımı hakkında başka bir kanala gönderebilirsiniz. Kanallar adlı ve tüketicilerin Olay Görüntüleyicisi'ni kullanarak bir kanalın olayları görüntüleyebilmesi için Windows ile kayıtlı.  
  
 Çözümleme izleme özelliğini [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] içinde [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] Microsoft-Windows-uygulama-Server-uygulamalar kanala yazar. Bu kanal sağlığını izlemek istediğiniz kullanıcılar için özellikle tasarlanmış [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] üretimde Hizmetleri. Birçok sistem durumu izleme kullanılan olayların ayarlayın ve sorun giderme senaryoları küçük tanımlar.  
  
 Windows için olay izleme bildirim iletileri düzgün olay günlüğü'nde çözülür biçimde etkinleştirmek için komut satırında ServiceModelReg aracı şu şekilde kullanın:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dinamik yapılandırma  
 ETW altyapı olması için izlemeyi sağlar etkinleştirilmeli ve standart Windows araçlarını kullanarak dinamik olarak yapılandırılmalıdır. Daha fazla bilgi için bkz: [izlemeyi dinamik olarak etkinleştirme analitik](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>İleti akışı izlemeyi  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] ileti akışı izlemeyi etkinleştirmek için bkz: nasıl [ileti akışı izlemeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Anahtar Sözcükler  
 İzleme İletileri Filtrele ve hangi bileşeninin tanımlamak için kullanılan anahtar sözcükleri [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] olay yayılan. Daha fazla bilgi için bkz: [izlemeyi dinamik olarak etkinleştirme analitik](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
