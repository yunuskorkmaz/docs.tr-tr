---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942405"
---
# <a name="servicecertificate"></a><span data-ttu-id="b6056-101">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b6056-101">\<serviceCertificate></span></span>
<span data-ttu-id="b6056-102">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b6056-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="b6056-103">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="b6056-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="b6056-104">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b6056-104">\<federationConfiguration></span></span>  
<span data-ttu-id="b6056-105">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b6056-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6056-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6056-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6056-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6056-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b6056-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6056-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6056-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6056-109">Attributes</span></span>  
 <span data-ttu-id="b6056-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6056-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6056-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6056-111">Child Elements</span></span>  
  
|<span data-ttu-id="b6056-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6056-112">Element</span></span>|<span data-ttu-id="b6056-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6056-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6056-114">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="b6056-114">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="b6056-115">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6056-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6056-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6056-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b6056-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6056-117">Element</span></span>|<span data-ttu-id="b6056-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6056-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6056-119">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b6056-119">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="b6056-120"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b6056-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6056-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6056-121">Example</span></span>  
 <span data-ttu-id="b6056-122">Aşağıdaki XML, \<ServiceCertificate > öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6056-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="b6056-123">XML `CustomToken` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="b6056-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
