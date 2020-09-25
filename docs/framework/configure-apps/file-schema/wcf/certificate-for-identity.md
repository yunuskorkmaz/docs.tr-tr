---
title: <certificate> bekleniyor <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 24c39b5efaee7f8db12088d272efeb3783efab04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198866"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="5abb1-102">\<certificate> bekleniyor \<identity></span><span class="sxs-lookup"><span data-stu-id="5abb1-102">\<certificate> for \<identity></span></span>

<span data-ttu-id="5abb1-103">Bir sunucuyu bir istemciye doğrulamak için kullanılan X. 509.440 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5abb1-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="5abb1-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5abb1-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5abb1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5abb1-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5abb1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5abb1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5abb1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5abb1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5abb1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5abb1-108">Attributes</span></span>  
  
|<span data-ttu-id="5abb1-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5abb1-109">Attribute</span></span>|<span data-ttu-id="5abb1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5abb1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5abb1-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="5abb1-111">encodedValue</span></span>|<span data-ttu-id="5abb1-112">Sertifikanın Base64 kodlaması.</span><span class="sxs-lookup"><span data-stu-id="5abb1-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5abb1-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5abb1-113">Child Elements</span></span>  

 <span data-ttu-id="5abb1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5abb1-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5abb1-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5abb1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5abb1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5abb1-116">Element</span></span>|<span data-ttu-id="5abb1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5abb1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="5abb1-118">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5abb1-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5abb1-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abb1-119">Example</span></span>  

 <span data-ttu-id="5abb1-120">Aşağıdaki kod, bir sunucunun bir istemciye doğrulanması için kullanılan sertifikanın kodlanmış gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5abb1-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="5abb1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5abb1-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="5abb1-122">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5abb1-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
