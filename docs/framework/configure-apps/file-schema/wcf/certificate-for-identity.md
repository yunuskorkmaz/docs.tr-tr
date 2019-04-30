---
title: <certificate> için <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 76bdcb40d5016d7fcbff6c0d9769819f710065fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673366"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="3f227-102">\<Sertifika > için \<kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f227-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="3f227-103">Bir istemci sunucuya doğrulamak için kullanılan bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f227-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="3f227-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3f227-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="3f227-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f227-105">\<identity></span></span>  
<span data-ttu-id="3f227-106">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="3f227-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f227-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f227-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f227-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f227-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3f227-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f227-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f227-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f227-110">Attributes</span></span>  
  
|<span data-ttu-id="3f227-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f227-111">Attribute</span></span>|<span data-ttu-id="3f227-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f227-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f227-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="3f227-113">encodedValue</span></span>|<span data-ttu-id="3f227-114">Bir Base64 sertifikasını kodlaması.</span><span class="sxs-lookup"><span data-stu-id="3f227-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f227-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f227-115">Child Elements</span></span>  
 <span data-ttu-id="3f227-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f227-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f227-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f227-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3f227-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f227-118">Element</span></span>|<span data-ttu-id="3f227-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f227-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f227-120">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f227-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3f227-121">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f227-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f227-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f227-122">Example</span></span>  
 <span data-ttu-id="3f227-123">Aşağıdaki kod, bir istemci sunucuya doğrulamak için kullanılan bir sertifika kodlamalı gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f227-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="3f227-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f227-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="3f227-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="3f227-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3f227-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3f227-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
