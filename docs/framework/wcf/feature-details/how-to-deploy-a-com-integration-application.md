---
title: 'Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-deploy-a-com-integration-application"></a>Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma
Bir kez bir COM + tümleştirme uygulaması, başka bir makinede dağıtmak isteyebilirsiniz yazmıştır. Bu konuda, bir COM + tümleştirme uygulaması bir makineden diğerine taşımak açıklar.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Taşıma COM + tümleştirme uygulaması barındırılan  
  
1.  WCF hem makinelerde yüklü olduğundan emin olun.  
  
2.  Uygulama makine A'dan dışarı aktarma  
  
3.  B. makinedeki uygulama alma  
  
4.  Uygulama kök dizini ayarlayın. Kurala göre %PROGRAMFILES%/ComPlus uygulamaları budur / {UygulamaGUID'i}.  
  
5.  Uygulama kök dizini makine a Application.config ve Application.manifest dosyalarını B. makinedeki uygulama kök dizini kopyalayın  
  
6.  Hizmet uç noktası adresleri uygun makine tanımlamak için B makinede Application.config dosyasında düzenleyin. Örneğin, değiştirme http://machineA/MyService için http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Bir Web barındırılan tümleştirme uygulaması taşıma  
  
1.  WCF hem makinelerde yüklü olduğundan emin olun.  
  
2.  Uygulama makine A'dan dışarı aktarma  
  
3.  B. makinedeki uygulama alma  
  
4.  B. makinesinde IIS vroot oluşturma  
  
5.  .Svc dosyasını (componentName.svc) ve Web.config dosyasını vroot makine a b makinedeki yeni oluşturulan vroot kopyalayın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM+ Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
