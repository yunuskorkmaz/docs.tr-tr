---
description: 'Hakkında daha fazla bilgi edinin: <x509SecurityTokenHandlerRequirement>'
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 21a05cfeee6365bd677a6f35e984cb64fa4dd078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748979"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="5c318-102">Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="5c318-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="5c318-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c318-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c318-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c318-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5c318-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c318-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c318-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c318-106">Attributes</span></span>  
  
|<span data-ttu-id="5c318-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c318-107">Attribute</span></span>|<span data-ttu-id="5c318-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c318-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c318-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="5c318-109">certificateValidationMode</span></span>|<span data-ttu-id="5c318-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5c318-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5c318-111">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="5c318-111">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="5c318-112">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="5c318-112">mapToWindows</span></span>|<span data-ttu-id="5c318-113">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c318-113">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="5c318-114">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="5c318-114">The default is "false".</span></span>|  
|<span data-ttu-id="5c318-115">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="5c318-115">revocationMode</span></span>|<span data-ttu-id="5c318-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5c318-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5c318-117">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="5c318-117">The default value is "Online".</span></span>|  
|<span data-ttu-id="5c318-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="5c318-118">trustedStoreLocation</span></span>|<span data-ttu-id="5c318-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5c318-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="5c318-120">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="5c318-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="5c318-121">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="5c318-121">certificateValidator</span></span>|<span data-ttu-id="5c318-122">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="5c318-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="5c318-123">`certificateValidationMode`Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c318-123">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c318-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c318-124">Child Elements</span></span>  

 <span data-ttu-id="5c318-125">Yok</span><span class="sxs-lookup"><span data-stu-id="5c318-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c318-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c318-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5c318-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c318-127">Element</span></span>|<span data-ttu-id="5c318-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c318-128">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="5c318-129">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="5c318-129">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5c318-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c318-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
