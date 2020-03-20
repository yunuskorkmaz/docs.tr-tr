---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152456"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerRequirement>
<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
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
|sertifikaDoğrulamaModu|X.509 sertifikası için kullanılacak doğrulama modunu belirten bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> değer. Varsayılan değer "PeerOrChainTrust"tır.|  
|haritaToWindows|Belirteç işleyicisinin gelen UPN talebini kullanarak doğrulama belirteciyle bir Windows hesabıyla eşlemesi gerekip gerekmediğini belirtir. Varsayılan "false" olur.|  
|iptalModu|X.509 sertifikası için kullanılacak iptal modunu belirten bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değer. Varsayılan değer "Çevrimiçi"dir.|  
|güvenilirStoreLocation|X.509 sertifika deposunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer. Varsayılan değer "LocalMachine"dir.|  
|sertifikaValidator|'den <xref:System.IdentityModel.Selectors.X509CertificateValidator>türeyen özel bir tür. `certificateValidationMode` Öznitelik "Özel" ise, bu tür bir örneği veren sertifika doğrulama için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>ekleyin](add.md)|Belirteç işleyicisi koleksiyonuna belirtilen güvenlik belirteci işleyicisi ekler.|  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
