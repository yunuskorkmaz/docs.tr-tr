---
description: 'Hakkında daha fazla bilgi edinin: <serviceCertificate>'
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: d9940fd96667211b1f9fd672b824af84e0d5143a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725330"
---
# \<serviceCertificate>

<span data-ttu-id="9b9c8-102">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9b9c8-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="9b9c8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b9c8-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b9c8-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b9c8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9b9c8-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b9c8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b9c8-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9b9c8-106">Attributes</span></span>  

 <span data-ttu-id="9b9c8-107">Yok</span><span class="sxs-lookup"><span data-stu-id="9b9c8-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b9c8-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b9c8-108">Child Elements</span></span>  
  
|<span data-ttu-id="9b9c8-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b9c8-109">Element</span></span>|<span data-ttu-id="9b9c8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b9c8-110">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="9b9c8-111">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b9c8-111">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b9c8-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b9c8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9b9c8-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b9c8-113">Element</span></span>|<span data-ttu-id="9b9c8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b9c8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="9b9c8-115"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9b9c8-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9b9c8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b9c8-116">Example</span></span>  

 <span data-ttu-id="9b9c8-117">Aşağıdaki XML, öğesinin kullanımını gösterir \<serviceCertificate> .</span><span class="sxs-lookup"><span data-stu-id="9b9c8-117">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="9b9c8-118">XML `CustomToken` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="9b9c8-118">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
