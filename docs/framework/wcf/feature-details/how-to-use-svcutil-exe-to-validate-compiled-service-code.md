---
title: "Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b60356bd66a49c9599a8e0a9138d3b92dbe0b23c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma
Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) barındırma hizmeti olmadan hatalarını hizmet uygulamaları ve yapılandırmaları algılamak için.  
  
### <a name="to-validate-a-service"></a>Bir hizmeti doğrulamak için  
  
1.  Hizmetinizi yürütülebilir bir dosya halinde ve bir veya daha fazla bağımlı derlemeleri derleyin.  
  
2.  Bir SDK komut istemi açın  
  
3.  Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe Aracı'nı başlatın. Hizmet Validationsection, çeşitli parametreleri hakkında daha fazla bilgi için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) konu.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneği.  
  
     `assemblyPath` Bağımsız değişkeni hizmeti ve doğrulanacak hizmet türlerini içeren bir veya daha fazla derlemeler için yürütülebilir dosya yolunu belirtir. Yürütülebilir derleme hizmet yapılandırmasını sağlamak için ilişkili bir yapılandırma dosyası olmalıdır. Birden çok derleme sağlamak için standart komut satırı joker karakterleri kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu hizmet myServiceName myServiceHost.exe yürütülebilir dosya olarak uygulanır.  Yapılandırma dosyası (myServiceHost.exe.config) hizmeti için otomatik olarak yüklenir.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
