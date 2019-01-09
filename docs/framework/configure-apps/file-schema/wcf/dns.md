---
title: '&lt;DNS&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 10fe4c63b08459914a16b2c736c1a454c6914a0b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145308"
---
# <a name="ltdnsgt"></a><span data-ttu-id="b44b6-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="b44b6-102">&lt;dns&gt;</span></span>
<span data-ttu-id="b44b6-103">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b44b6-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="b44b6-104">Bu kimlik için X509 geçerli sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="b44b6-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="b44b6-105">SPN aynı değere sahipse, ayrıca Windows kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b44b6-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="b44b6-106">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b44b6-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="b44b6-107">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="b44b6-107">\<identity></span></span>  
<span data-ttu-id="b44b6-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="b44b6-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b44b6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b44b6-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b44b6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b44b6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b44b6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b44b6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b44b6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b44b6-112">Attributes</span></span>  
  
|<span data-ttu-id="b44b6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b44b6-113">Attribute</span></span>|<span data-ttu-id="b44b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b44b6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b44b6-115">value</span><span class="sxs-lookup"><span data-stu-id="b44b6-115">value</span></span>|<span data-ttu-id="b44b6-116">Sertifika DNS'i.</span><span class="sxs-lookup"><span data-stu-id="b44b6-116">The DNS of the certificate.</span></span> <span data-ttu-id="b44b6-117">DNS, IP tabanlı bir ağda bilgisayarların yerini bulmak için kullanılan bir endüstri standardı protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="b44b6-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="b44b6-118">Kullanıcılar unutmayın görünen adları gibi [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) veya [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b44b6-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b44b6-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b44b6-119">Child Elements</span></span>  
 <span data-ttu-id="b44b6-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="b44b6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b44b6-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b44b6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b44b6-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b44b6-122">Element</span></span>|<span data-ttu-id="b44b6-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b44b6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b44b6-124">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="b44b6-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b44b6-125">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b44b6-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b44b6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b44b6-126">Example</span></span>  
 <span data-ttu-id="b44b6-127">Aşağıdaki yapılandırma kodunu DNS bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="b44b6-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="b44b6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b44b6-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="b44b6-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b44b6-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b44b6-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="b44b6-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
