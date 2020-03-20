---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152638"
---
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenRequirement>
Bu sınıflardan <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> herhangi <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> birinin sınıf, sınıf veya türetilmiş sınıfı için yapılandırma sağlar. <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> Sınıf tarafından temsil edilir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|haritaToWindows|Belirteç işleyicisinin gelen UPN talebini kullanarak doğrulama belirteciyle bir Windows hesabıyla eşlemesi gerekip gerekmediğini belirtir. Varsayılan "false" olur.|  
|verenSertifikaRevocationMode|X.509 sertifikası için kullanılacak iptal modunu belirten bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değer. Varsayılan değer "Çevrimiçi"dir.|  
|verenSertifikaDoğrulamaModu|X.509 sertifikası için kullanılacak doğrulama modunu belirten bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> değer. Varsayılan değer "PeerOrChainTrust"tır.|  
|verenSertifikaTrustedStoreLocation|X.509 sertifika deposunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer. Varsayılan değer "LocalMachine"dir.|  
|verenSertifikaValidator|'den <xref:System.IdentityModel.Selectors.X509CertificateValidator>türeyen özel bir tür. `issuerCertificateValidationMode` Öznitelik "Özel" ise, bu tür bir örneği veren sertifika doğrulama için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.|  
|[\<roleClaimType>](roleclaimtype.md)|Belirteç işleyicisi <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> yöntemiyle döndürülen nesnelerin koleksiyonunda rol türü taleplerini tanımlayan talep türünü belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>ekleyin](add.md)|Belirteç işleyicisi koleksiyonuna belirtilen güvenlik belirteci işleyicisi ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe `<samlSecurityTokenRequirement>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> modelinde sınıf tarafından temsil edilir ve bir veya `SamlSecurityTokenRequirement` bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>özelliği yapılandırmak için kullanılır .  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
