---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755129"
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyonu ile bir simge tekrar yürütme önbelleğine kaydeder.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<önbelleğe alan >  
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
|türü|Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı. Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvuruları] bakın.
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<önbelleğe alan >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Simge tekrar yürütme önbelleğine yeniden yürütülmüş belirteçleri algılamak için kullanılır. Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) ayrıca belirteçleri için en fazla süre sonu zamanı belirtir öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
