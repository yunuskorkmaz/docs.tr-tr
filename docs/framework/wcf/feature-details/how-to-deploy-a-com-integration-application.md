---
title: "Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63478620a2b604d27f2d9d154383cb0bae6b6da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma
Bir kez bir COM + tümleştirme uygulaması, başka bir makinede dağıtmak isteyebilirsiniz yazmıştır. Bu konuda, bir COM + tümleştirme uygulaması bir makineden diğerine taşımak açıklar.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Taşıma COM + tümleştirme uygulaması barındırılan  
  
1.  Emin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem makinelerde yüklü.  
  
2.  Uygulama makine A'dan dışarı aktarma  
  
3.  B. makinedeki uygulama alma  
  
4.  Uygulama kök dizini ayarlayın. Kurala göre %PROGRAMFILES%/ComPlus uygulamaları budur / {UygulamaGUID'i}.  
  
5.  Uygulama kök dizini makine a Application.config ve Application.manifest dosyalarını B. makinedeki uygulama kök dizini kopyalayın  
  
6.  Hizmet uç noktası adresleri uygun makine tanımlamak için B makinede Application.config dosyasında düzenleyin. Örneğin, http://machineA/MyService http://machineB/MyService için değiştirin.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Bir Web barındırılan tümleştirme uygulaması taşıma  
  
1.  Emin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem makinelerde yüklü.  
  
2.  Uygulama makine A'dan dışarı aktarma  
  
3.  B. makinedeki uygulama alma  
  
4.  B. makinesinde IIS vroot oluşturma  
  
5.  .Svc dosyasını (componentName.svc) ve Web.config dosyasını vroot makine a b makinedeki yeni oluşturulan vroot kopyalayın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM + uygulamaları ile tümleştirme genel bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
