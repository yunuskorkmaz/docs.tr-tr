---
description: 'Hakkında daha fazla bilgi edinin: <comContracts>'
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 263210b4499274fe009a6b1b1e46c1f09dd007ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638658"
---
# \<comContracts>

`comContracts`Yapılandırma bölümü, BIR COM+ tümleştirme hizmeti sözleşmesinin çeşitli özelliklerini belirtmenizi sağlayan öğeleri içerir.  
  
## <a name="specifying-namespace-and-contract"></a>Ad alanı ve sözleşme belirtme  

 COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı DESTEKLEYICI com arabiriminden türetilir. Ancak, `comContracts` yapılandırma dosyasının bölümünü kullanarak alternatifler belirtebilirsiniz.  
  
 Örneğin, hizmet sözleşmesinin ad alanını ve sözleşme adını ve oturum açma bağlamalarında kullanımı zorlama seçeneğini belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.  
  
 Bu bölüm boş olduğunda, hizmet başlatma, destekleyici COM arabirim KIMLIĞINDEN alınan bir varsayılan ad alanı ve sözleşme adı uygular.  
  
 Ayrıca, [\<exposedMethod>](exposedmethod.md) BIR COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya ÇıKARıLAN com+ yöntemlerini belirtmek için öğesini kullanabilirsiniz. Ayrıca, [\<persistableTypes>](persistabletypes.md) tümleştirmede kullanılan kalıcı tablo türlerini belirtmek için de kullanabilirsiniz. Son olarak, [\<userDefinedType>](userdefinedtype.md) öğesini hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (udt) dahil etmek için kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [COM+ uygulamalarıyla tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
