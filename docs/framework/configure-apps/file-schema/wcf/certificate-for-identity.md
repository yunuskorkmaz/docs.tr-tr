---
title: <certificate> için <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 52d1fa31cebd949c91809464976739ef1334af29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919611"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="59c34-102">\<kimlik > için \<sertifika ></span><span class="sxs-lookup"><span data-stu-id="59c34-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="59c34-103">Bir sunucuyu bir istemciye doğrulamak için kullanılan X. 509.440 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59c34-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="59c34-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="59c34-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="59c34-105">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="59c34-105">\<identity></span></span>  
<span data-ttu-id="59c34-106">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="59c34-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c34-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59c34-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59c34-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59c34-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59c34-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59c34-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59c34-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59c34-110">Attributes</span></span>  
  
|<span data-ttu-id="59c34-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59c34-111">Attribute</span></span>|<span data-ttu-id="59c34-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c34-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59c34-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="59c34-113">encodedValue</span></span>|<span data-ttu-id="59c34-114">Sertifikanın Base64 kodlaması.</span><span class="sxs-lookup"><span data-stu-id="59c34-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59c34-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59c34-115">Child Elements</span></span>  
 <span data-ttu-id="59c34-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="59c34-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59c34-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59c34-117">Parent Elements</span></span>  
  
|<span data-ttu-id="59c34-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="59c34-118">Element</span></span>|<span data-ttu-id="59c34-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c34-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59c34-120">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="59c34-120">\<identity></span></span>](identity.md)|<span data-ttu-id="59c34-121">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59c34-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59c34-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="59c34-122">Example</span></span>  
 <span data-ttu-id="59c34-123">Aşağıdaki kod, bir sunucunun bir istemciye doğrulanması için kullanılan sertifikanın kodlanmış gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59c34-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="59c34-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59c34-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="59c34-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="59c34-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="59c34-126">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="59c34-126">\<identity></span></span>](identity.md)
