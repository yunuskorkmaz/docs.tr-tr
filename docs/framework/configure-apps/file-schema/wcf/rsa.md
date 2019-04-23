---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091661"
---
# <a name="rsa"></a><span data-ttu-id="8d221-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="8d221-101">\<rsa></span></span>
<span data-ttu-id="8d221-102">Bu kimlik ile bir uç noktayı bağlayan güvenli bir WCF istemcisi, sunucu tarafından sunulan istemlerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarı içeren bir istem bulundurabileceğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8d221-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="8d221-103">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8d221-103">\<identity></span></span>  
<span data-ttu-id="8d221-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="8d221-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d221-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d221-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d221-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d221-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8d221-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d221-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d221-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d221-108">Attributes</span></span>  
  
|<span data-ttu-id="8d221-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8d221-109">Attribute</span></span>|<span data-ttu-id="8d221-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d221-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d221-111">value</span><span class="sxs-lookup"><span data-stu-id="8d221-111">value</span></span>|<span data-ttu-id="8d221-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="8d221-112">Optional String.</span></span> <span data-ttu-id="8d221-113">İstemcide ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="8d221-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d221-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d221-114">Child Elements</span></span>  
 <span data-ttu-id="8d221-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d221-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d221-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d221-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8d221-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d221-117">Element</span></span>|<span data-ttu-id="8d221-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d221-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d221-119">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8d221-119">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8d221-120">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d221-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d221-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d221-121">Remarks</span></span>  
 <span data-ttu-id="8d221-122">RSA onay, özellikle RSA anahtarıyla dayalı tek bir sertifika kimlik doğrulaması sınırlamanıza olanak sağlar veya kendi RSA anahtar değeri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d221-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="8d221-123">Bu daha sıkı kimlik doğrulamayı etkinleştirir hizmeti çoğaltamaz belirli bir RSA anahtar artık, RSA anahtar değeri değiştirilirse mevcut istemcileriyle çalışma.</span><span class="sxs-lookup"><span data-stu-id="8d221-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="8d221-124">Kimlik doğrulamak için bir istemci bir hizmet için kullanma hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8d221-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d221-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d221-125">Example</span></span>  
 <span data-ttu-id="8d221-126">Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikasının ortak anahtar değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d221-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="8d221-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d221-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="8d221-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8d221-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8d221-129">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8d221-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
