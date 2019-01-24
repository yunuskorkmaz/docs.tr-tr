---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e00cc6f3214dc9a040a9b6170271b1f4188d1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601629"
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
İstemcinin hizmetin istemciye geri göndermek bir uç noktası kullanıma sunması gerektiğinde kullanılan bağlama öğesi tanımlar.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<compositeDuplex >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientBaseAddress|Çift yönlü modda geri kanal adresini ayarlar bir URI. Hizmet bu adrese başvurun ve istemci ile bağlantı kurmak için kullanır.<br /><br /> Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur. Varsayılan, `null` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır. TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.  
  
 İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir. Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği. Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir açıkça kullanıcı tarafından ayarlanmamışsa ürettiği unutmayın.  
  
## <a name="example"></a>Örnek  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
