---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a642a79618329a55afa98dba04e4ac5f419cae7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a>&lt;samlSecurityTokenRequirement&gt;
İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf. Tarafından temsil edilen <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıfı.  
  
 \<System.IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<ekleme >  
\<samlSecurityTokenRequirement >  
  
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
|mapToWindows|Belirteci işleyicisi Doğrulama belirtecini bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir. Varsayılan değer "false" dir.|  
|issuerCertificateRevocationMode|Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer. Varsayılan değer "Çevrimiçi" olur.|  
|issuerCertificateValidationMode|Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer. Varsayılan değer "PeerOrChainTrust" dir.|  
|issuerCertificateTrustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer. Varsayılan değer "LocalMachine" dir.|  
|issuerCertificateValidator|Türetilen bir özel tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Varsa `issuerCertificateValidationMode` özniteliği "Özel", bu türünün bir örneği veren sertifika doğrulaması için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<nameClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|Belirtir talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.|  
|[\<roleClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|Rol türü talepleri koleksiyonundaki tanımlar talep türünü belirten <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<samlSecurityTokenRequirement>` Öğesi ile temsil edilir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıf nesne modelinde ve yapılandırmak için kullanılan `SamlSecurityTokenRequirement` özelliği bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
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
