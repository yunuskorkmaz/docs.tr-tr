---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: adfd94365ceb0ddc3164a6baef838c16027b4bc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190147"
---
# \<dns>

<span data-ttu-id="57da2-101">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57da2-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="57da2-102">Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57da2-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="57da2-103">SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57da2-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="57da2-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="57da2-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="57da2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="57da2-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57da2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57da2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="57da2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57da2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57da2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57da2-108">Attributes</span></span>  
  
|<span data-ttu-id="57da2-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57da2-109">Attribute</span></span>|<span data-ttu-id="57da2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57da2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57da2-111">değer</span><span class="sxs-lookup"><span data-stu-id="57da2-111">value</span></span>|<span data-ttu-id="57da2-112">Sertifikanın DNS 'i.</span><span class="sxs-lookup"><span data-stu-id="57da2-112">The DNS of the certificate.</span></span> <span data-ttu-id="57da2-113">DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="57da2-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="57da2-114">Kullanıcılar, `https://go.microsoft.com/fwlink/?prd=10929` `https://go.microsoft.com/fwlink/?LinkID=96165` 207.46.131.137 gibi sayı tabanlı adreslerden daha kolay görünen adları anımsayabilir.</span><span class="sxs-lookup"><span data-stu-id="57da2-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57da2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57da2-115">Child Elements</span></span>  

 <span data-ttu-id="57da2-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="57da2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57da2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57da2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="57da2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="57da2-118">Element</span></span>|<span data-ttu-id="57da2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57da2-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="57da2-120">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57da2-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="57da2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="57da2-121">Example</span></span>  

 <span data-ttu-id="57da2-122">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57da2-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="57da2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57da2-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="57da2-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="57da2-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
