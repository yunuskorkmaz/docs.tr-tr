---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855052"
---
# \<rsa>
<span data-ttu-id="878bb-101">Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="878bb-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="878bb-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="878bb-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="878bb-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="878bb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="878bb-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="878bb-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="878bb-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="878bb-105">Attributes</span></span>  
  
|<span data-ttu-id="878bb-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="878bb-106">Attribute</span></span>|<span data-ttu-id="878bb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="878bb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="878bb-108">value</span><span class="sxs-lookup"><span data-stu-id="878bb-108">value</span></span>|<span data-ttu-id="878bb-109">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="878bb-109">Optional String.</span></span> <span data-ttu-id="878bb-110">İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="878bb-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="878bb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="878bb-111">Child Elements</span></span>  
 <span data-ttu-id="878bb-112">Yok</span><span class="sxs-lookup"><span data-stu-id="878bb-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="878bb-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="878bb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="878bb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="878bb-114">Element</span></span>|<span data-ttu-id="878bb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="878bb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="878bb-116">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="878bb-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="878bb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="878bb-117">Remarks</span></span>  
 <span data-ttu-id="878bb-118">Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="878bb-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="878bb-119">Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="878bb-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="878bb-120">Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="878bb-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="878bb-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="878bb-121">Example</span></span>  
 <span data-ttu-id="878bb-122">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="878bb-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="878bb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="878bb-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="878bb-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="878bb-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
