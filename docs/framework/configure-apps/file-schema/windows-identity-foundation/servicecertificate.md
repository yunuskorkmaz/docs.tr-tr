---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400419"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="c6fa6-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="c6fa6-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="c6fa6-103">Şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="c6fa6-104">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="c6fa6-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="c6fa6-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="c6fa6-105">\<federationConfiguration></span></span>  
<span data-ttu-id="c6fa6-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c6fa6-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6fa6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6fa6-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6fa6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6fa6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c6fa6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6fa6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6fa6-110">Attributes</span></span>  
 <span data-ttu-id="c6fa6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6fa6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6fa6-112">Child Elements</span></span>  
  
|<span data-ttu-id="c6fa6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6fa6-113">Element</span></span>|<span data-ttu-id="c6fa6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6fa6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6fa6-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="c6fa6-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="c6fa6-116">Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6fa6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6fa6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c6fa6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6fa6-118">Element</span></span>|<span data-ttu-id="c6fa6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6fa6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6fa6-120">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="c6fa6-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="c6fa6-121">Yapılandırma ayarları içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="c6fa6-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c6fa6-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6fa6-122">Example</span></span>  
 <span data-ttu-id="c6fa6-123">Aşağıdaki XML kullanımını gösterir \<serviceCertificate > öğesi.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="c6fa6-124">XML alınır `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="c6fa6-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
