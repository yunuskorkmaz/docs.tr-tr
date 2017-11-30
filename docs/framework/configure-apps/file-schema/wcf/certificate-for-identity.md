---
title: "&lt;kimlik&gt; için &lt;sertifika&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="7bd40-102">&lt;kimlik&gt; için &lt;sertifika&gt;</span><span class="sxs-lookup"><span data-stu-id="7bd40-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="7bd40-103">Bir istemci sunucuya doğrulamak için kullanılan bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bd40-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="7bd40-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7bd40-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7bd40-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="7bd40-105">\<identity></span></span>  
<span data-ttu-id="7bd40-106">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="7bd40-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd40-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd40-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd40-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd40-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7bd40-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bd40-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd40-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bd40-110">Attributes</span></span>  
  
|<span data-ttu-id="7bd40-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bd40-111">Attribute</span></span>|<span data-ttu-id="7bd40-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd40-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bd40-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="7bd40-113">encodedValue</span></span>|<span data-ttu-id="7bd40-114">Bir Base64'ın sertifikasını kodlaması.</span><span class="sxs-lookup"><span data-stu-id="7bd40-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bd40-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd40-115">Child Elements</span></span>  
 <span data-ttu-id="7bd40-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bd40-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd40-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd40-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd40-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bd40-118">Element</span></span>|<span data-ttu-id="7bd40-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd40-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bd40-120">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="7bd40-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7bd40-121">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bd40-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7bd40-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bd40-122">Example</span></span>  
 <span data-ttu-id="7bd40-123">Aşağıdaki kod, bir istemci sunucuya doğrulamak için kullanılan bir sertifika kodlanmış gösterimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bd40-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bd40-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd40-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="7bd40-125">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7bd40-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7bd40-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="7bd40-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
