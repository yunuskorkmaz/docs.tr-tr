---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271956"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerRequirement >
İsteğe bağlı yapılandırma için sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<Ekle >  
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
|Certificatevalidationmode'u|Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer. "PeerOrChainTrust" varsayılan değerdir.|  
|mapToWindows|Belirteci işleyicisi doğrulama belirteci için bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir. Varsayılan değer "false" dir.|  
|revocationMode|Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer. Varsayılan değer "Çevrimiçi" olur.|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer. "LocalMachine" varsayılan değerdir.|  
|certificateValidator|Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Varsa `certificateValidationMode` özniteliktir "Özel", bu türden veren sertifika doğrulaması için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.|  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
