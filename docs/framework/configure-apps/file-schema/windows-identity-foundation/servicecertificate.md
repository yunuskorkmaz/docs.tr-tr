---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793828"
---
# <a name="servicecertificate"></a><span data-ttu-id="268a4-101">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="268a4-101">\<serviceCertificate></span></span>
<span data-ttu-id="268a4-102">Şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="268a4-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="268a4-103">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="268a4-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="268a4-104">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="268a4-104">\<federationConfiguration></span></span>  
<span data-ttu-id="268a4-105">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="268a4-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="268a4-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="268a4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="268a4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="268a4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="268a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="268a4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="268a4-109">Attributes</span></span>  
 <span data-ttu-id="268a4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="268a4-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="268a4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="268a4-111">Child Elements</span></span>  
  
|<span data-ttu-id="268a4-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="268a4-112">Element</span></span>|<span data-ttu-id="268a4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="268a4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="268a4-114">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="268a4-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="268a4-115">Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="268a4-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="268a4-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="268a4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="268a4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="268a4-117">Element</span></span>|<span data-ttu-id="268a4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="268a4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="268a4-119">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="268a4-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="268a4-120">Yapılandırma ayarları içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="268a4-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="268a4-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="268a4-121">Example</span></span>  
 <span data-ttu-id="268a4-122">Aşağıdaki XML kullanımını gösterir \<serviceCertificate > öğesi.</span><span class="sxs-lookup"><span data-stu-id="268a4-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="268a4-123">XML alınır `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="268a4-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
