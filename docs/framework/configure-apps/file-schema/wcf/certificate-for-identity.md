---
title: <certificate> için <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850019"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="a4f5b-102">\<kimlik > için \<sertifika ></span><span class="sxs-lookup"><span data-stu-id="a4f5b-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="a4f5b-103">Bir sunucuyu bir istemciye doğrulamak için kullanılan X. 509.440 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="a4f5b-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a4f5b-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="a4f5b-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4f5b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4f5b-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a4f5b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a4f5b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="a4f5b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="a4f5b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="a4f5b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="a4f5b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="a4f5b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="a4f5b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Sertifika >**</span><span class="sxs-lookup"><span data-stu-id="a4f5b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f5b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4f5b-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4f5b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4f5b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a4f5b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4f5b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4f5b-114">Attributes</span></span>  
  
|<span data-ttu-id="a4f5b-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4f5b-115">Attribute</span></span>|<span data-ttu-id="a4f5b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4f5b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4f5b-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="a4f5b-117">encodedValue</span></span>|<span data-ttu-id="a4f5b-118">Sertifikanın Base64 kodlaması.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4f5b-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4f5b-119">Child Elements</span></span>  
 <span data-ttu-id="a4f5b-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4f5b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4f5b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a4f5b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4f5b-122">Element</span></span>|<span data-ttu-id="a4f5b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4f5b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4f5b-124">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="a4f5b-124">\<identity></span></span>](identity.md)|<span data-ttu-id="a4f5b-125">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4f5b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4f5b-126">Example</span></span>  
 <span data-ttu-id="a4f5b-127">Aşağıdaki kod, bir sunucunun bir istemciye doğrulanması için kullanılan sertifikanın kodlanmış gösterimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="a4f5b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f5b-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="a4f5b-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a4f5b-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a4f5b-130">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="a4f5b-130">\<identity></span></span>](identity.md)
