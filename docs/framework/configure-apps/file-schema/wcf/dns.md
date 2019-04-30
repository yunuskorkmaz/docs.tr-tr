---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 26b45b17ecd7bbd3fffb5d03553834ec22eedc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700936"
---
# <a name="dns"></a><span data-ttu-id="8b2cc-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="8b2cc-101">\<dns></span></span>
<span data-ttu-id="8b2cc-102">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="8b2cc-103">Bu kimlik için X509 geçerli sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="8b2cc-104">SPN aynı değere sahipse, ayrıca Windows kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="8b2cc-105">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8b2cc-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="8b2cc-106">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8b2cc-106">\<identity></span></span>  
<span data-ttu-id="8b2cc-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="8b2cc-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2cc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b2cc-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b2cc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2cc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8b2cc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b2cc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b2cc-111">Attributes</span></span>  
  
|<span data-ttu-id="8b2cc-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b2cc-112">Attribute</span></span>|<span data-ttu-id="8b2cc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b2cc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b2cc-114">value</span><span class="sxs-lookup"><span data-stu-id="8b2cc-114">value</span></span>|<span data-ttu-id="8b2cc-115">Sertifika DNS'i.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-115">The DNS of the certificate.</span></span> <span data-ttu-id="8b2cc-116">DNS, IP tabanlı bir ağda bilgisayarların yerini bulmak için kullanılan bir endüstri standardı protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="8b2cc-117">Kullanıcılar unutmayın görünen adları gibi <https://go.microsoft.com/fwlink/?prd=10929> veya [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b2cc-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2cc-118">Child Elements</span></span>  
 <span data-ttu-id="8b2cc-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b2cc-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b2cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8b2cc-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b2cc-121">Element</span></span>|<span data-ttu-id="8b2cc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b2cc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b2cc-123">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8b2cc-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8b2cc-124">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8b2cc-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b2cc-125">Example</span></span>  
 <span data-ttu-id="8b2cc-126">Aşağıdaki yapılandırma kodunu DNS bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="8b2cc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2cc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="8b2cc-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8b2cc-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8b2cc-129">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8b2cc-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
