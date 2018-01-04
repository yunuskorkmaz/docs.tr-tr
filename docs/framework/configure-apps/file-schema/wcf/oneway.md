---
title: "&lt;tek yönlü&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a>&lt;tek yönlü&gt;
Paket Yönlendirme ve özel bağlama için tek yönlü yöntemlerinin kullanımını etkinleştirir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<oneWay >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`packetRoutable`|Paket yönlendirme etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`MaxAcceptedChannels`|Kabul edilebilir kanal maksimum sayısını belirten bir tamsayı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal kanal havuzunun özelliklerini içeren nesne.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paket yönlendirmeyi etkinleştirmek için bir tek yönlü dönüştürme katman gereklidir, bu öğe sağlar. Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için bir oturum algılayan veya istek-yanıt aktarma üzerinden Katmanlar özel bir bağlama oluşturabilirsiniz. Bu öğe, ayrıca tek yönlü yöntemleri daha yerel bir şekilde kullanıma sunmak istiyorsanız kullanışlıdır. Daha fazla dönüştürmeleri bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
