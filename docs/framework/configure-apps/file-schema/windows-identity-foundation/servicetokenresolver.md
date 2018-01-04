---
title: '&lt;serviceTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd981c8e48f003060c74787fdd2f29557c07901d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder. Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirteci çözmek için kullanılır.  
  
 \<System.IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Hizmet belirteç Çözümleyicisi türünü belirtir. Her iki <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür veya türeyen bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı. Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirtecini çözümlemek için kullanılabilir. Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtar almak için kullanılır. Belirtmeniz gerekir `type` özniteliği. Belirtilen tür ya da olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ya türetilen özel bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.  
  
 Bazı belirteci işleyicileri yapılandırmada hizmet belirteç Çözümleyicisi ayarları belirtmenizi sağlar. Tek tek belirteç işleyicileri ayarları güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.  
  
> [!NOTE]
>  Belirtme `<serviceTokenResolver>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir. Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.  
  
## <a name="example"></a>Örnek  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
