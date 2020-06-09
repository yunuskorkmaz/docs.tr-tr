---
title: 'Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 6f2064c696e3186c3208a7e57dc51655056d23ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595355"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma
Hizmeti barındırmadan hizmet uygulamalarında ve yapılandırmalarda hataları algılamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.  
  
### <a name="to-validate-a-service"></a>Bir hizmeti doğrulamak için  
  
1. Hizmetinizi bir yürütülebilir dosya ve bir veya daha fazla bağımlı derlemeye derleyin.  
  
2. SDK komut istemi açın  
  
3. Komut isteminde, aşağıdaki biçimi kullanarak Svcutil. exe aracını başlatın. Çeşitli parametreler hakkında daha fazla bilgi için, [ServiceModel Metadata Utility aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) konusunun Service validationsection bölümüne bakın.  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     `/serviceName`Doğrulamak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir.  
  
     `assemblyPath`Bağımsız değişkeni, hizmet için yürütülebilir dosyanın yolunu ve doğrulanacak hizmet türlerini içeren bir veya daha fazla derlemeyi belirtir. Yürütülebilir derlemenin hizmet yapılandırmasını sağlaması için ilişkili bir yapılandırma dosyası olması gerekir. Birden çok derleme sağlamak için standart komut satırı joker karakterlerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut myServiceName. exe yürütülebilir dosyasında uygulanan myServiceName hizmetidir.  Hizmetin yapılandırma dosyası (myServiceHost. exe. config) otomatik olarak yüklenir.  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
