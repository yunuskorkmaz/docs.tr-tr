---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944072"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache >
Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<önbellekler >  
\<tokenReplayCache >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|<xref:System.IdentityModel.Tokens.TokenReplayCache> Sınıfından türeten bir tür. Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbellekler >](caches.md)|Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır. Belirteç yeniden yürütme algılaması, belirteçlerin en uzun süre sonu süresini de belirten [ \<TokenReplayDetection >](tokenreplaydetection.md) öğesi tarafından etkinleştirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection >](tokenreplaydetection.md)
