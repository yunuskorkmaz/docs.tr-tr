---
description: 'Hakkında daha fazla bilgi edinin: <dns>'
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: a5c0601a027c72b4d6307261793bd5725979db92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803899"
---
# \<dns>

<span data-ttu-id="06152-102">Sunucunun beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06152-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="06152-103">Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="06152-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="06152-104">SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="06152-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="06152-105">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="06152-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="06152-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="06152-106">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06152-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06152-107">Attributes and Elements</span></span>  

 <span data-ttu-id="06152-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06152-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06152-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06152-109">Attributes</span></span>  
  
|<span data-ttu-id="06152-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="06152-110">Attribute</span></span>|<span data-ttu-id="06152-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06152-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06152-112">değer</span><span class="sxs-lookup"><span data-stu-id="06152-112">value</span></span>|<span data-ttu-id="06152-113">Sertifikanın DNS 'i.</span><span class="sxs-lookup"><span data-stu-id="06152-113">The DNS of the certificate.</span></span> <span data-ttu-id="06152-114">DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="06152-114">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="06152-115">Kullanıcılar, `https://go.microsoft.com/fwlink/?prd=10929` `https://go.microsoft.com/fwlink/?LinkID=96165` 207.46.131.137 gibi sayı tabanlı adreslerden daha kolay görünen adları anımsayabilir.</span><span class="sxs-lookup"><span data-stu-id="06152-115">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06152-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06152-116">Child Elements</span></span>  

 <span data-ttu-id="06152-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="06152-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06152-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06152-118">Parent Elements</span></span>  
  
|<span data-ttu-id="06152-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="06152-119">Element</span></span>|<span data-ttu-id="06152-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06152-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="06152-121">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06152-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06152-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="06152-122">Example</span></span>  

 <span data-ttu-id="06152-123">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06152-123">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="06152-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06152-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="06152-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="06152-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
