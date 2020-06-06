---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152456"
---
# \<x509SecurityTokenHandlerRequirement>
<span data-ttu-id="b0271-101">Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="b0271-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="b0271-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0271-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0271-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0271-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b0271-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0271-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0271-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0271-105">Attributes</span></span>  
  
|<span data-ttu-id="b0271-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0271-106">Attribute</span></span>|<span data-ttu-id="b0271-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0271-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0271-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b0271-108">certificateValidationMode</span></span>|<span data-ttu-id="b0271-109"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b0271-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b0271-110">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="b0271-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="b0271-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="b0271-111">mapToWindows</span></span>|<span data-ttu-id="b0271-112">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0271-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="b0271-113">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="b0271-113">The default is "false".</span></span>|  
|<span data-ttu-id="b0271-114">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="b0271-114">revocationMode</span></span>|<span data-ttu-id="b0271-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b0271-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b0271-116">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="b0271-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="b0271-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b0271-117">trustedStoreLocation</span></span>|<span data-ttu-id="b0271-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b0271-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b0271-119">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="b0271-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="b0271-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="b0271-120">certificateValidator</span></span>|<span data-ttu-id="b0271-121">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="b0271-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="b0271-122">`certificateValidationMode`Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0271-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0271-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0271-123">Child Elements</span></span>  
 <span data-ttu-id="b0271-124">Yok</span><span class="sxs-lookup"><span data-stu-id="b0271-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0271-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0271-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b0271-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0271-126">Element</span></span>|<span data-ttu-id="b0271-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0271-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="b0271-128">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="b0271-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b0271-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0271-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
