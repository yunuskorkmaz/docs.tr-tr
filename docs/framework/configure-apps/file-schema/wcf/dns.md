---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452233"
---
# \<dns>
<span data-ttu-id="10227-101">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10227-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="10227-102">Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10227-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="10227-103">SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10227-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="10227-104">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="10227-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="10227-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10227-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10227-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10227-106">Attributes and Elements</span></span>  
 <span data-ttu-id="10227-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10227-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10227-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10227-108">Attributes</span></span>  
  
|<span data-ttu-id="10227-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10227-109">Attribute</span></span>|<span data-ttu-id="10227-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10227-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10227-111">value</span><span class="sxs-lookup"><span data-stu-id="10227-111">value</span></span>|<span data-ttu-id="10227-112">Sertifikanın DNS 'i.</span><span class="sxs-lookup"><span data-stu-id="10227-112">The DNS of the certificate.</span></span> <span data-ttu-id="10227-113">DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="10227-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="10227-114">Kullanıcılar, `https://go.microsoft.com/fwlink/?prd=10929` `https://go.microsoft.com/fwlink/?LinkID=96165` 207.46.131.137 gibi sayı tabanlı adreslerden daha kolay görünen adları anımsayabilir.</span><span class="sxs-lookup"><span data-stu-id="10227-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10227-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10227-115">Child Elements</span></span>  
 <span data-ttu-id="10227-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="10227-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10227-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10227-117">Parent Elements</span></span>  
  
|<span data-ttu-id="10227-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="10227-118">Element</span></span>|<span data-ttu-id="10227-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10227-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="10227-120">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10227-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10227-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="10227-121">Example</span></span>  
 <span data-ttu-id="10227-122">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10227-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="10227-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10227-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="10227-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="10227-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
