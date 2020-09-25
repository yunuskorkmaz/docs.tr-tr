---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: a6a8185297e1345de9fa20c7d4d0dffbdcd8620f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185398"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="a097c-101">Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="a097c-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="a097c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a097c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a097c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a097c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a097c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a097c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a097c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a097c-105">Attributes</span></span>  
  
|<span data-ttu-id="a097c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a097c-106">Attribute</span></span>|<span data-ttu-id="a097c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a097c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a097c-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a097c-108">certificateValidationMode</span></span>|<span data-ttu-id="a097c-109"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a097c-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a097c-110">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="a097c-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="a097c-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="a097c-111">mapToWindows</span></span>|<span data-ttu-id="a097c-112">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a097c-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="a097c-113">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="a097c-113">The default is "false".</span></span>|  
|<span data-ttu-id="a097c-114">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="a097c-114">revocationMode</span></span>|<span data-ttu-id="a097c-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a097c-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a097c-116">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="a097c-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="a097c-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a097c-117">trustedStoreLocation</span></span>|<span data-ttu-id="a097c-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a097c-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="a097c-119">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="a097c-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="a097c-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="a097c-120">certificateValidator</span></span>|<span data-ttu-id="a097c-121">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="a097c-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a097c-122">`certificateValidationMode`Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a097c-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a097c-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a097c-123">Child Elements</span></span>  

 <span data-ttu-id="a097c-124">Yok</span><span class="sxs-lookup"><span data-stu-id="a097c-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a097c-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a097c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a097c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="a097c-126">Element</span></span>|<span data-ttu-id="a097c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a097c-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="a097c-128">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a097c-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a097c-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a097c-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
