---
title: 'Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778332"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma
Bir kez, başka bir makineye dağıtmak istediğiniz bir COM + tümleştirme uygulaması, yazdınız. Bu konu, bir COM + tümleştirme uygulaması bir makineden diğerine taşıyabilirsiniz açıklar.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Taşıma bir COM + tümleştirme uygulaması barındırılan  
  
1. WCF'ın her iki makinelerde yüklü olduğundan emin olun.  
  
2. Makine A'dan uygulamayı dışarı aktarma  
  
3. B. makinedeki uygulamanın içeri aktarma  
  
4. Uygulama kök dizinini ayarlayın. Kural olarak, bu %PROGRAMFILES%/ComPlus uygulamaları, / {appGUID}.  
  
5. Makine a uygulaması kök dizini Application.config ve Application.manifest dosyaları b makinede uygulamanın kök dizinine kopyalayın  
  
6. Hizmet uç noktası adreslerini makineye uygun makineyi tanımlamak için B Application.config dosyasındaki düzenleyin. Örneğin, değiştirme `http://machineA/MyService` için `http://machineB/MyService`.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Bir Web barındırılan bir tümleştirme uygulaması taşıma  
  
1. WCF'ın her iki makinelerde yüklü olduğundan emin olun.  
  
2. Makine A'dan uygulamayı dışarı aktarma  
  
3. B. makinedeki uygulamanın içeri aktarma  
  
4. B. makinede IIS vroot oluşturma  
  
5. .Svc dosyasını (componentName.svc) ve Web.config dosyasını vroot makine a b makinede yeni oluşturulan vroot kopyalayın  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
