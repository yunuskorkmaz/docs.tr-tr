---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919484"
---
# <a name="comcontracts"></a>\<comContracts >
Yapılandırma `comContracts` bölümü, bir com+ tümleştirme hizmeti sözleşmesinin çeşitli özelliklerini belirtmenizi sağlayan öğeleri içerir.  
  
## <a name="specifying-namespace-and-contract"></a>Ad alanı ve sözleşme belirtme  
 COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı destekleyici com arabiriminden türetilir. Ancak, yapılandırma dosyasının `comContracts` bölümünü kullanarak alternatifler belirtebilirsiniz.  
  
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
  
 Ayrıca, bir com+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda sunulan com+ yöntemlerini belirtmek için [ \<ExposedMethod >](exposedmethod.md) öğesini kullanabilirsiniz. Ayrıca, [ \<](persistabletypes.md) tümleştirmede kullanılan kalıcı tablo türlerini belirtmek için > PersistableTypes da kullanabilirsiniz. Son olarak, [ \<UserDefinedType >](userdefinedtype.md) öğesini hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (udt) dahil etmek için kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod >](exposedmethod.md)
- [\<persistableTypes >](persistabletypes.md)
- [\<userDefinedType >](userdefinedtype.md)
- [\<comContract >](comcontract.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
