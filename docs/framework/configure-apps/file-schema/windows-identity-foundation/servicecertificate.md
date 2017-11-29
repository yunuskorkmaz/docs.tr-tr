---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="ff368-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="ff368-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="ff368-103">Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan X.509 sertifikasının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ff368-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="ff368-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="ff368-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="ff368-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="ff368-105">\<federationConfiguration></span></span>  
<span data-ttu-id="ff368-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="ff368-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff368-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff368-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff368-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff368-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ff368-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff368-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff368-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff368-110">Attributes</span></span>  
 <span data-ttu-id="ff368-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff368-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff368-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff368-112">Child Elements</span></span>  
  
|<span data-ttu-id="ff368-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff368-113">Element</span></span>|<span data-ttu-id="ff368-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff368-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff368-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="ff368-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="ff368-116">Bul ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff368-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff368-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff368-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ff368-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff368-118">Element</span></span>|<span data-ttu-id="ff368-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff368-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff368-120">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="ff368-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="ff368-121">Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="ff368-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff368-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff368-122">Example</span></span>  
 <span data-ttu-id="ff368-123">Aşağıdaki XML kullanımı gösterilmiştir \<serviceCertificate > öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff368-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="ff368-124">XML alınırlar `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="ff368-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
