---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919131"
---
# <a name="dns"></a><span data-ttu-id="c39bb-101">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="c39bb-101">\<dns></span></span>
<span data-ttu-id="c39bb-102">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="c39bb-103">Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="c39bb-104">SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="c39bb-105">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c39bb-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c39bb-106">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c39bb-106">\<identity></span></span>  
<span data-ttu-id="c39bb-107">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="c39bb-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39bb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c39bb-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c39bb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c39bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c39bb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c39bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c39bb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c39bb-111">Attributes</span></span>  
  
|<span data-ttu-id="c39bb-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c39bb-112">Attribute</span></span>|<span data-ttu-id="c39bb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c39bb-114">value</span><span class="sxs-lookup"><span data-stu-id="c39bb-114">value</span></span>|<span data-ttu-id="c39bb-115">Sertifikanın DNS 'i.</span><span class="sxs-lookup"><span data-stu-id="c39bb-115">The DNS of the certificate.</span></span> <span data-ttu-id="c39bb-116">DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="c39bb-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="c39bb-117">Kullanıcılar, 207.46.131.137 gibi sayı tabanlı adreslerden daha <https://go.microsoft.com/fwlink/?prd=10929> kolay [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)görünen adları anımsayabilir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c39bb-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c39bb-118">Child Elements</span></span>  
 <span data-ttu-id="c39bb-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="c39bb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c39bb-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c39bb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c39bb-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c39bb-121">Element</span></span>|<span data-ttu-id="c39bb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39bb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c39bb-123">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c39bb-123">\<identity></span></span>](identity.md)|<span data-ttu-id="c39bb-124">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c39bb-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c39bb-125">Example</span></span>  
 <span data-ttu-id="c39bb-126">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c39bb-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c39bb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39bb-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="c39bb-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39bb-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c39bb-129">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c39bb-129">\<identity></span></span>](identity.md)
