---
title: '&lt;ServiceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af59562dbf6c13970526f1665a9ba2c57c4f32ee
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="56a8a-102">&lt;ServiceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="56a8a-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="56a8a-103">Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan X.509 sertifikasının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="56a8a-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="56a8a-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="56a8a-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="56a8a-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="56a8a-105">\<federationConfiguration></span></span>  
<span data-ttu-id="56a8a-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="56a8a-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a8a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56a8a-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56a8a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56a8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56a8a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56a8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56a8a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56a8a-110">Attributes</span></span>  
 <span data-ttu-id="56a8a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="56a8a-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56a8a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56a8a-112">Child Elements</span></span>  
  
|<span data-ttu-id="56a8a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="56a8a-113">Element</span></span>|<span data-ttu-id="56a8a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56a8a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56a8a-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="56a8a-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="56a8a-116">Bul ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="56a8a-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56a8a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56a8a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="56a8a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="56a8a-118">Element</span></span>|<span data-ttu-id="56a8a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56a8a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56a8a-120">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="56a8a-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="56a8a-121">Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="56a8a-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="56a8a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="56a8a-122">Example</span></span>  
 <span data-ttu-id="56a8a-123">Aşağıdaki XML kullanımı gösterilmiştir \<serviceCertificate > öğesi.</span><span class="sxs-lookup"><span data-stu-id="56a8a-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="56a8a-124">XML alınırlar `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="56a8a-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
