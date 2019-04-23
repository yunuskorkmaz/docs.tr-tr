---
title: <certificate> için <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 76bdcb40d5016d7fcbff6c0d9769819f710065fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205842"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="c08dd-102">\<Sertifika > için \<kimliği ></span><span class="sxs-lookup"><span data-stu-id="c08dd-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="c08dd-103">Bir istemci sunucuya doğrulamak için kullanılan bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c08dd-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="c08dd-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c08dd-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c08dd-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c08dd-105">\<identity></span></span>  
<span data-ttu-id="c08dd-106">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="c08dd-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08dd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c08dd-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c08dd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c08dd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c08dd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c08dd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c08dd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c08dd-110">Attributes</span></span>  
  
|<span data-ttu-id="c08dd-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c08dd-111">Attribute</span></span>|<span data-ttu-id="c08dd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c08dd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c08dd-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="c08dd-113">encodedValue</span></span>|<span data-ttu-id="c08dd-114">Bir Base64 sertifikasını kodlaması.</span><span class="sxs-lookup"><span data-stu-id="c08dd-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c08dd-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c08dd-115">Child Elements</span></span>  
 <span data-ttu-id="c08dd-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c08dd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c08dd-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c08dd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c08dd-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c08dd-118">Element</span></span>|<span data-ttu-id="c08dd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c08dd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c08dd-120">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c08dd-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c08dd-121">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c08dd-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c08dd-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c08dd-122">Example</span></span>  
 <span data-ttu-id="c08dd-123">Aşağıdaki kod, bir istemci sunucuya doğrulamak için kullanılan bir sertifika kodlamalı gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c08dd-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c08dd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c08dd-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="c08dd-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c08dd-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c08dd-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c08dd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
