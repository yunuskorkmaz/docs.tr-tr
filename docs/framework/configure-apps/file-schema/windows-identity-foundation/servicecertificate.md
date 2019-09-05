---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251866"
---
# <a name="servicecertificate"></a><span data-ttu-id="f5905-101">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f5905-101">\<serviceCertificate></span></span>
<span data-ttu-id="f5905-102">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f5905-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="f5905-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f5905-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f5905-104">&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="f5905-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="f5905-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f5905-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="f5905-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="f5905-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5905-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5905-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5905-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5905-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f5905-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5905-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5905-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5905-110">Attributes</span></span>  
 <span data-ttu-id="f5905-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5905-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5905-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5905-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5905-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5905-113">Element</span></span>|<span data-ttu-id="f5905-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5905-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5905-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="f5905-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="f5905-116">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5905-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5905-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5905-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f5905-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5905-118">Element</span></span>|<span data-ttu-id="f5905-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5905-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5905-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f5905-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="f5905-121"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f5905-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5905-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5905-122">Example</span></span>  
 <span data-ttu-id="f5905-123">Aşağıdaki XML, \<ServiceCertificate > öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5905-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="f5905-124">XML `CustomToken` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="f5905-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
