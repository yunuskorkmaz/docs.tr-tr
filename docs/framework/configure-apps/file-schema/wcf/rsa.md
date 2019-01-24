---
title: '&lt;rsa&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 74da1e2ae02f151f928afec24d6af3adf703bdcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612808"
---
# <a name="ltrsagt"></a><span data-ttu-id="8f147-102">&lt;rsa&gt;</span><span class="sxs-lookup"><span data-stu-id="8f147-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="8f147-103">Bu kimlik ile bir uç noktayı bağlayan güvenli bir WCF istemcisi, sunucu tarafından sunulan istemlerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarı içeren bir istem bulundurabileceğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8f147-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="8f147-104">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8f147-104">\<identity></span></span>  
<span data-ttu-id="8f147-105">\<rsa></span><span class="sxs-lookup"><span data-stu-id="8f147-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f147-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f147-106">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f147-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f147-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8f147-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f147-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f147-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f147-109">Attributes</span></span>  
  
|<span data-ttu-id="8f147-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f147-110">Attribute</span></span>|<span data-ttu-id="8f147-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f147-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f147-112">value</span><span class="sxs-lookup"><span data-stu-id="8f147-112">value</span></span>|<span data-ttu-id="8f147-113">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="8f147-113">Optional String.</span></span> <span data-ttu-id="8f147-114">İstemcide ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="8f147-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f147-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f147-115">Child Elements</span></span>  
 <span data-ttu-id="8f147-116">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="8f147-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f147-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f147-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8f147-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f147-118">Element</span></span>|<span data-ttu-id="8f147-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f147-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f147-120">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8f147-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8f147-121">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f147-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f147-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f147-122">Remarks</span></span>  
 <span data-ttu-id="8f147-123">RSA onay, özellikle RSA anahtarıyla dayalı tek bir sertifika kimlik doğrulaması sınırlamanıza olanak sağlar veya kendi RSA anahtar değeri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f147-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="8f147-124">Bu daha sıkı kimlik doğrulamayı etkinleştirir hizmeti çoğaltamaz belirli bir RSA anahtar artık, RSA anahtar değeri değiştirilirse mevcut istemcileriyle çalışma.</span><span class="sxs-lookup"><span data-stu-id="8f147-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="8f147-125">Kimlik doğrulamak için bir istemci bir hizmet için kullanma hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8f147-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f147-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f147-126">Example</span></span>  
 <span data-ttu-id="8f147-127">Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikasının ortak anahtar değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f147-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="8f147-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f147-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="8f147-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8f147-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8f147-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8f147-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
