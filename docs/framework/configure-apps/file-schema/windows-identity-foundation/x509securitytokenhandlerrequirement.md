---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945177"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerRequirement >
<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<> Ekle  
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
|certificateValidationMode|X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer. Varsayılan değer "PeerOrChainTrust" dır.|  
|mapToWindows|Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir. Varsayılan değer "false" dır.|  
|Revocationmodu|X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer. Varsayılan değer "çevrimiçi" dır.|  
|trustedStoreLocation|X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer. Varsayılan değer "LocalMachine" dır.|  
|certificateValidator|Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilen özel bir tür. `certificateValidationMode` Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add.md)|Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.|  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
