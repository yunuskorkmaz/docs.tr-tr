---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790513"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache>
Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<önbelleğe alan >  
\<tokenReplayCache>  
  
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
|türü|Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı. Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç yeniden yürütme önbelleğini yeniden yürütülmüş belirteçleri algılamak için kullanılır. Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) öğesi, ayrıca belirteçleri maksimum sona erme süresini belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
