---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 47a7d862cf85254f88373d582169ff421be2b5b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115836"
---
# <a name="comcontracts"></a>\<comContracts >
`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesinin çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.  
  
## <a name="specifying-namespace-and-contract"></a>Namespace ve sözleşme belirtme  
 COM + tümleştirme Hizmet sözleşmeleri için kısıtlı `http://tempuri.org` ad alanını ve sözleşme adı destekleyici bir COM arabiriminden elde edilmiştir. Ancak, alternatif kullanarak belirtebilirsiniz `comContracts` yapılandırma dosyasının bir bölümünde.  
  
 Örneğin, isteğe bağlı oturumdaki bağlamalarda kulanılıp kullanımı zorlamak için yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için şu yapılandırmayı kullanın.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Hizmet başlatıldığında sözleşmesi adları ve belirtilen ad alanları için oluşturulan hizmet açıklamaları uygulanır.  
  
 Bu bölümde boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınan bir varsayılan ad alanı ve sözleşme adı geçerlidir.  
  
 Ayrıca, kullanabileceğiniz [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + yöntemlerini belirtmek için öğesi. Ayrıca [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirmesi kullanılan kalıcı türlerini belirtmek için. Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türleri (hizmet sözleşmesi içerisinde dahil edilecek olan UDT) içerecek şekilde öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)
- [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)
- [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)
- [\<comContract >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)
- [COM Uygulamaları ile Tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
