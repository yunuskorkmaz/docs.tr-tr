---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: ce8be6eea5469b099a368a0b62e791faa7e3cbfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156998"
---
# \<serviceCertificate>

<span data-ttu-id="3e88c-101">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3e88c-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="3e88c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e88c-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e88c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e88c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3e88c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e88c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e88c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e88c-105">Attributes</span></span>  

 <span data-ttu-id="3e88c-106">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3e88c-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e88c-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e88c-107">Child Elements</span></span>  
  
|<span data-ttu-id="3e88c-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e88c-108">Element</span></span>|<span data-ttu-id="3e88c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e88c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="3e88c-110">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e88c-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e88c-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e88c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3e88c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e88c-112">Element</span></span>|<span data-ttu-id="3e88c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e88c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="3e88c-114"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3e88c-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e88c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e88c-115">Example</span></span>  

 <span data-ttu-id="3e88c-116">Aşağıdaki XML, öğesinin kullanımını gösterir \<serviceCertificate> .</span><span class="sxs-lookup"><span data-stu-id="3e88c-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="3e88c-117">XML `CustomToken` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="3e88c-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
