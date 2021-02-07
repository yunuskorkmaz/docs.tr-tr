---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: COM+ tümleştirme uygulaması dağıtma'
title: 'Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 4bf9e72a631c97f3b791ecd01abb5cb74365772d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734392"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma

Bir COM+ tümleştirme uygulaması yazdıktan sonra, bunu başka bir makineye dağıtmak isteyebilirsiniz. Bu konu, bir COM+ tümleştirme uygulamasının bir makineden diğerine nasıl taşınacağını açıklamaktadır.  
  
### <a name="moving-a-com-hosted-integration-app"></a>COM+ barındırılan tümleştirme uygulamasını taşıma  
  
1. WCF 'nin her iki makinede de yüklü olduğundan emin olun.  
  
2. Uygulamayı A makinesinden dışarı aktarın.  
  
3. Uygulamayı B makinesinde içeri aktarın.  
  
4. Uygulama kök dizini ' ni ayarlayın. Kurala göre, bu% PROGRAMFILES%/ComPlus Applications/{appGUID}.  
  
5. Application.config ve Application. manifest dosyalarını A makinesindeki uygulama kök dizininden B makinesindeki uygulama kök dizinine kopyalayın.  
  
6. Uygun makineyi belirlemek için B makinesindeki Application.config dosyasında hizmet uç noktası adreslerini düzenleyin. Örneğin, olarak değiştirin `http://machineA/MyService` `http://machineB/MyService` .  
  
### <a name="moving-a-web-hosted-integration-application"></a>Web 'de barındırılan tümleştirme uygulamasını taşıma  
  
1. WCF 'nin her iki makinede de yüklü olduğundan emin olun.  
  
2. Uygulamayı A makinesinden dışarı aktarın.  
  
3. Uygulamayı B makinesinde içeri aktarın.  
  
4. B makinesi üzerinde bir IIS vroot oluşturun.  
  
5. . Svc dosyasını (componentName. svc) ve Web.config dosyasını A makinesindeki sanal gruptan B makinesinde yeni oluşturulan vroot öğesine kopyalayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ uygulamaları ile tümleştirme genel bakış](integrating-with-com-plus-applications-overview.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](how-to-configure-com-service-settings.md)
- [Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma](how-to-use-the-com-service-model-configuration-tool.md)
