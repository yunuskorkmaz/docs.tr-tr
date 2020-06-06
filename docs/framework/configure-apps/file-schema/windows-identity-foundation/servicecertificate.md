---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251866"
---
# \<serviceCertificate>
<span data-ttu-id="046e3-101">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="046e3-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="046e3-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="046e3-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="046e3-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="046e3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="046e3-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="046e3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="046e3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="046e3-105">Attributes</span></span>  
 <span data-ttu-id="046e3-106">Yok</span><span class="sxs-lookup"><span data-stu-id="046e3-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="046e3-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="046e3-107">Child Elements</span></span>  
  
|<span data-ttu-id="046e3-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="046e3-108">Element</span></span>|<span data-ttu-id="046e3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="046e3-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="046e3-110">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="046e3-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="046e3-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="046e3-111">Parent Elements</span></span>  
  
|<span data-ttu-id="046e3-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="046e3-112">Element</span></span>|<span data-ttu-id="046e3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="046e3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="046e3-114"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="046e3-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="046e3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="046e3-115">Example</span></span>  
 <span data-ttu-id="046e3-116">Aşağıdaki XML, öğesinin kullanımını gösterir \<serviceCertificate> .</span><span class="sxs-lookup"><span data-stu-id="046e3-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="046e3-117">XML `CustomToken` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="046e3-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
