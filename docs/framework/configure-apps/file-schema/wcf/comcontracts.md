---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: b44c09e7e32129ba21834f7fbb8dc4699904e46b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesini çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.  
  
## <a name="specifying-namespace-and-contract"></a>Namespace ve sözleşme belirtme  
 COM + tümleştirme Hizmet sözleşmeleri için şu anda kısıtlı "http://tempuri.org" ad alanı, ve sözleşme adı destek COM arabiriminden elde edilmiştir. Bununla birlikte, alternatifleri kullanarak belirleyebilirsiniz `comContracts` yapılandırma dosyasındaki bölüm.  
  
 Örneğin, aşağıdaki yapılandırma süre sonuyla bağlamaları kullanımı zorlamak için bir seçenek yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için kullanabilirsiniz.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 Hizmet başlatıldığında belirtilen ad alanları ve sözleşmesi adları için oluşturulan hizmet açıklamaları uygulanır.  
  
 Bu bölüm boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınır varsayılan ad alanı ve sözleşme adı geçerlidir.  
  
 Ayrıca, [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğesi bir COM bileşeni arabirimde bir Web hizmeti olarak kullanıma sunulduğunda gösterilen COM + yöntemleri belirtin. Aynı zamanda [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirme sırasında kullanılan kalıcı türlerini belirtmek için. Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türler (hizmet sözleşmesinde eklenecek olan UDT) eklenecek öğe.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [COM+ Uygulamaları ile Tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
