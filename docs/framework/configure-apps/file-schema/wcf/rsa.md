---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934746"
---
# <a name="rsa"></a><span data-ttu-id="3df41-101">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="3df41-101">\<rsa></span></span>
<span data-ttu-id="3df41-102">Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="3df41-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="3df41-103">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="3df41-103">\<identity></span></span>  
<span data-ttu-id="3df41-104">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="3df41-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3df41-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3df41-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3df41-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3df41-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3df41-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3df41-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3df41-108">Attributes</span></span>  
  
|<span data-ttu-id="3df41-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3df41-109">Attribute</span></span>|<span data-ttu-id="3df41-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3df41-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3df41-111">value</span><span class="sxs-lookup"><span data-stu-id="3df41-111">value</span></span>|<span data-ttu-id="3df41-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="3df41-112">Optional String.</span></span> <span data-ttu-id="3df41-113">İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="3df41-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3df41-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3df41-114">Child Elements</span></span>  
 <span data-ttu-id="3df41-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3df41-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3df41-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3df41-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3df41-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3df41-117">Element</span></span>|<span data-ttu-id="3df41-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3df41-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3df41-119">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="3df41-119">\<identity></span></span>](identity.md)|<span data-ttu-id="3df41-120">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3df41-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3df41-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3df41-121">Remarks</span></span>  
 <span data-ttu-id="3df41-122">Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3df41-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="3df41-123">Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3df41-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="3df41-124">Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3df41-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3df41-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3df41-125">Example</span></span>  
 <span data-ttu-id="3df41-126">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3df41-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="3df41-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3df41-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="3df41-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="3df41-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3df41-129">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="3df41-129">\<identity></span></span>](identity.md)
