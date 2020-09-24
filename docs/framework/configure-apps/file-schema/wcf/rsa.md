---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 1698ce421b4dcefc6ab94206443d2d7bca47aca8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162289"
---
# \<rsa>

<span data-ttu-id="1b9cf-101">Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="1b9cf-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b9cf-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b9cf-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9cf-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1b9cf-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="1b9cf-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b9cf-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b9cf-105">Attributes</span></span>  
  
|<span data-ttu-id="1b9cf-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b9cf-106">Attribute</span></span>|<span data-ttu-id="1b9cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b9cf-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b9cf-108">değer</span><span class="sxs-lookup"><span data-stu-id="1b9cf-108">value</span></span>|<span data-ttu-id="1b9cf-109">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-109">Optional String.</span></span> <span data-ttu-id="1b9cf-110">İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b9cf-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9cf-111">Child Elements</span></span>  

 <span data-ttu-id="1b9cf-112">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="1b9cf-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b9cf-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9cf-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1b9cf-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b9cf-114">Element</span></span>|<span data-ttu-id="1b9cf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b9cf-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="1b9cf-116">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b9cf-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b9cf-117">Remarks</span></span>  

 <span data-ttu-id="1b9cf-118">Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="1b9cf-119">Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="1b9cf-120">Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1b9cf-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9cf-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b9cf-121">Example</span></span>  

 <span data-ttu-id="1b9cf-122">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="1b9cf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="1b9cf-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="1b9cf-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
