---
description: 'Hakkında daha fazla bilgi <certificate> edinin: <identity>'
title: <certificate> bekleniyor <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: b1ccda7e8e84825cc0b2b2be123fe30be449189a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639113"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="c9177-103">\<certificate> bekleniyor \<identity></span><span class="sxs-lookup"><span data-stu-id="c9177-103">\<certificate> for \<identity></span></span>

<span data-ttu-id="c9177-104">Bir sunucuyu bir istemciye doğrulamak için kullanılan X. 509.440 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9177-104">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="c9177-105">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c9177-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="c9177-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9177-106">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9177-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9177-107">Attributes and Elements</span></span>  

 <span data-ttu-id="c9177-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9177-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9177-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9177-109">Attributes</span></span>  
  
|<span data-ttu-id="c9177-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9177-110">Attribute</span></span>|<span data-ttu-id="c9177-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9177-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9177-112">encodedValue</span><span class="sxs-lookup"><span data-stu-id="c9177-112">encodedValue</span></span>|<span data-ttu-id="c9177-113">Sertifikanın Base64 kodlaması.</span><span class="sxs-lookup"><span data-stu-id="c9177-113">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9177-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9177-114">Child Elements</span></span>  

 <span data-ttu-id="c9177-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9177-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9177-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9177-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c9177-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9177-117">Element</span></span>|<span data-ttu-id="c9177-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9177-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c9177-119">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9177-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9177-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9177-120">Example</span></span>  

 <span data-ttu-id="c9177-121">Aşağıdaki kod, bir sunucunun bir istemciye doğrulanması için kullanılan sertifikanın kodlanmış gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9177-121">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9177-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9177-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="c9177-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c9177-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
