---
title: '&lt;DNS&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 2f5b9d5e1bc57230adbb32664e9ae15d3c71d46f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732628"
---
# <a name="ltdnsgt"></a><span data-ttu-id="38d20-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="38d20-102">&lt;dns&gt;</span></span>
<span data-ttu-id="38d20-103">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38d20-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="38d20-104">Bu kimlik için X509 geçerli sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="38d20-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="38d20-105">SPN aynı değere sahipse, ayrıca Windows kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="38d20-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="38d20-106">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="38d20-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="38d20-107">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="38d20-107">\<identity></span></span>  
<span data-ttu-id="38d20-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="38d20-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d20-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38d20-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38d20-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="38d20-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38d20-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38d20-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38d20-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38d20-112">Attributes</span></span>  
  
|<span data-ttu-id="38d20-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="38d20-113">Attribute</span></span>|<span data-ttu-id="38d20-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38d20-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38d20-115">value</span><span class="sxs-lookup"><span data-stu-id="38d20-115">value</span></span>|<span data-ttu-id="38d20-116">Sertifika DNS'i.</span><span class="sxs-lookup"><span data-stu-id="38d20-116">The DNS of the certificate.</span></span> <span data-ttu-id="38d20-117">DNS, IP tabanlı bir ağda bilgisayarların yerini bulmak için kullanılan bir endüstri standardı protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="38d20-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="38d20-118">Kullanıcılar unutmayın görünen adları gibi [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) veya [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.</span><span class="sxs-lookup"><span data-stu-id="38d20-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38d20-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="38d20-119">Child Elements</span></span>  
 <span data-ttu-id="38d20-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="38d20-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38d20-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="38d20-121">Parent Elements</span></span>  
  
|<span data-ttu-id="38d20-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="38d20-122">Element</span></span>|<span data-ttu-id="38d20-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38d20-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38d20-124">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="38d20-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="38d20-125">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38d20-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38d20-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="38d20-126">Example</span></span>  
 <span data-ttu-id="38d20-127">Aşağıdaki yapılandırma kodunu DNS bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="38d20-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38d20-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38d20-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="38d20-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="38d20-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="38d20-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="38d20-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
