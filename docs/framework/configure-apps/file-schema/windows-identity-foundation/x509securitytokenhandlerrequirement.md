---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8af4a718fc9f4ba7f674d98e13424bb443693c6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755948"
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a>&lt;x509SecurityTokenHandlerRequirement&gt;
İçin isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıf veya türetilmiş sınıflar.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<ekleme >  
\<x509SecurityTokenHandlerRequirement >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|certificateValidationMode değerini|Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer. Varsayılan değer "PeerOrChainTrust" dir.|  
|mapToWindows|Belirteci işleyicisi Doğrulama belirtecini bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir. Varsayılan değer "false" dir.|  
|revocationMode|Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer. Varsayılan değer "Çevrimiçi" olur.|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer. Varsayılan değer "LocalMachine" dir.|  
|certificateValidator|Türetilen bir özel tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Varsa `certificateValidationMode` özniteliği "Özel", bu türünün bir örneği veren sertifika doğrulaması için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.|  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
