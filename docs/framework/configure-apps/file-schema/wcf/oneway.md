---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 35631cc4b120169e0cadb80c6beba26ab9eafd7a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283276"
---
# <a name="oneway"></a>\<oneWay>
Paket Yönlendirme ve özel bir bağlama için tek yönlü yöntemlerin kullanımını etkinleştirir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<oneWay>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`packetRoutable`|Paket yönlendirmenin etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`MaxAcceptedChannels`|Kabul edilebilir kanal sayısını belirten bir tamsayı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal için kanal havuzu özelliklerini içeren nesne.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paket yönlendirme etkinleştirmek için tek yönlü dönüştürme katman gereklidir, bu öğe sağlar. Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için oturum durumunu algılayan veya istek-yanıt aktarım Katmanlar özel bir bağlama oluşturabilirsiniz. Bu öğe, daha doğal bir biçimde one-way metotları kullanıma sunmak istediğiniz durumlarda da kullanışlıdır. Daha fazla dönüştürme bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
