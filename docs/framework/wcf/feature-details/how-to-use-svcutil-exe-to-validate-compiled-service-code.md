---
title: 'Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 1e90d71d5831ccf262315ebf9c1deb99b386e224
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196417"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma
Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) barındırma hizmeti olmadan hizmet uygulamaları ve yapılandırmalarında hataları algılamak için.  
  
### <a name="to-validate-a-service"></a>Bir hizmeti doğrulamak için  
  
1.  Hizmetiniz bir yürütülebilir dosyasına ve bir veya daha fazla bağımlı derlemeleri derleyin.  
  
2.  Bir SDK komut istemi açın  
  
3.  Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın. Çeşitli parametreler hakkında daha fazla bilgi için bkz, hizmet Validationsection [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) konu.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmeti yapılandırma adını belirtmek için seçeneği.  
  
     `assemblyPath` Bağımsız değişkeni hizmeti ve doğrulanması için hizmet türlerini içeren bir veya daha fazla derlemeler için yürütülebilir dosyanın yolunu belirtir. Yürütülebilir derleme hizmeti yapılandırması sağlamak için ilişkili bir yapılandırma dosyası olmalıdır. Birden çok derleme sağlamak için standart bir komut satırı joker karakterler kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu, hizmet myServiceName myServiceHost.exe yürütülebilir dosya olarak uygulanır.  Yapılandırma dosyası (myServiceHost.exe.config) hizmeti için otomatik olarak yüklenir.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
