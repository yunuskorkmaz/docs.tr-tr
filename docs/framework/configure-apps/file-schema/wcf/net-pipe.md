---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397722"
---
# <a name="netpipe"></a>\<net. pipe >
Named Pipe 'ın süresini yöneten ve adlandırılmış kanallar üzerinden gelen etkinleştirme isteklerini işleyen adlandırılmış kanal etkinleştirme hizmeti için yapılandırma ayarlarını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<net. pipe >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxPendingAccepts`|Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı. Varsayılan değer 2 ' dir.|  
|`maxPendingConnections`|Dağıtım için bekilebilecek en fazla bağlantı sayısını belirten bir tamsayı. Varsayılan değer 100'dür.|  
|`receiveTimeout`|Çerçeveleme <xref:System.TimeSpan> verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir. Varsayılan değer "00:00:10" dır|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts >](allowaccounts.md)|WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
