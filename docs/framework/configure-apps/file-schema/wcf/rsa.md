---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855052"
---
# <a name="rsa"></a><span data-ttu-id="c185d-101">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="c185d-101">\<rsa></span></span>
<span data-ttu-id="c185d-102">Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="c185d-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
<span data-ttu-id="c185d-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c185d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c185d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c185d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c185d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="c185d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="c185d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="c185d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="c185d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="c185d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="c185d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<RSA >**</span><span class="sxs-lookup"><span data-stu-id="c185d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c185d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c185d-109">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c185d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c185d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c185d-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c185d-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c185d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c185d-112">Attributes</span></span>  
  
|<span data-ttu-id="c185d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c185d-113">Attribute</span></span>|<span data-ttu-id="c185d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c185d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c185d-115">value</span><span class="sxs-lookup"><span data-stu-id="c185d-115">value</span></span>|<span data-ttu-id="c185d-116">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="c185d-116">Optional String.</span></span> <span data-ttu-id="c185d-117">İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="c185d-117">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c185d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c185d-118">Child Elements</span></span>  
 <span data-ttu-id="c185d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="c185d-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c185d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c185d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c185d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c185d-121">Element</span></span>|<span data-ttu-id="c185d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c185d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c185d-123">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c185d-123">\<identity></span></span>](identity.md)|<span data-ttu-id="c185d-124">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c185d-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c185d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c185d-125">Remarks</span></span>  
 <span data-ttu-id="c185d-126">Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c185d-126">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="c185d-127">Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c185d-127">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="c185d-128">Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c185d-128">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c185d-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="c185d-129">Example</span></span>  
 <span data-ttu-id="c185d-130">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c185d-130">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c185d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c185d-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="c185d-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c185d-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c185d-133">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="c185d-133">\<identity></span></span>](identity.md)
