---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452233"
---
# <a name="dns"></a><span data-ttu-id="c4b98-101">DNS > \<</span><span class="sxs-lookup"><span data-stu-id="c4b98-101">\<dns></span></span>
<span data-ttu-id="c4b98-102">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="c4b98-103">Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="c4b98-104">SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="c4b98-105">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c4b98-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="c4b98-106">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4b98-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4b98-107">[**System. serviceModel >\<** ](system-servicemodel.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="c4b98-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c4b98-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<istemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="c4b98-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="c4b98-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="c4b98-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="c4b98-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="c4b98-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="c4b98-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dns >**</span><span class="sxs-lookup"><span data-stu-id="c4b98-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b98-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4b98-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4b98-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4b98-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c4b98-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4b98-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4b98-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4b98-115">Attributes</span></span>  
  
|<span data-ttu-id="c4b98-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4b98-116">Attribute</span></span>|<span data-ttu-id="c4b98-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4b98-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4b98-118">value</span><span class="sxs-lookup"><span data-stu-id="c4b98-118">value</span></span>|<span data-ttu-id="c4b98-119">Sertifikanın DNS 'i.</span><span class="sxs-lookup"><span data-stu-id="c4b98-119">The DNS of the certificate.</span></span> <span data-ttu-id="c4b98-120">DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="c4b98-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="c4b98-121">Kullanıcılar, `https://go.microsoft.com/fwlink/?prd=10929` veya `https://go.microsoft.com/fwlink/?LinkID=96165`gibi görünen adları, 207.46.131.137 gibi sayı tabanlı adreslerden daha kolay anımsayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-121">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4b98-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4b98-122">Child Elements</span></span>  
 <span data-ttu-id="c4b98-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4b98-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4b98-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4b98-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c4b98-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4b98-125">Element</span></span>|<span data-ttu-id="c4b98-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4b98-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4b98-127">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c4b98-127">\<identity></span></span>](identity.md)|<span data-ttu-id="c4b98-128">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4b98-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4b98-129">Example</span></span>  
 <span data-ttu-id="c4b98-130">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4b98-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c4b98-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4b98-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="c4b98-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c4b98-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c4b98-133">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c4b98-133">\<identity></span></span>](identity.md)
