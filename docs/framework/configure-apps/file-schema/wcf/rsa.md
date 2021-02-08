---
description: 'Hakkında daha fazla bilgi edinin: <rsa>'
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 5e558e608ec1196081166d01415e12fb2c3083b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786882"
---
# \<rsa>

<span data-ttu-id="61820-102">Bu kimlikle bir uç noktaya bağlanan güvenli bir WCF istemcisi, sunucu tarafından sunulan taleplerin, bu kimliği oluşturmak için kullanılan RSA ortak anahtarını içeren bir talep içerdiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="61820-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="61820-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="61820-103">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61820-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61820-104">Attributes and Elements</span></span>  

 <span data-ttu-id="61820-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="61820-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61820-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61820-106">Attributes</span></span>  
  
|<span data-ttu-id="61820-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="61820-107">Attribute</span></span>|<span data-ttu-id="61820-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61820-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61820-109">değer</span><span class="sxs-lookup"><span data-stu-id="61820-109">value</span></span>|<span data-ttu-id="61820-110">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="61820-110">Optional String.</span></span> <span data-ttu-id="61820-111">İstemci üzerindeki ile Karşılaştırılacak RSA ortak anahtar değeri.</span><span class="sxs-lookup"><span data-stu-id="61820-111">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61820-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61820-112">Child Elements</span></span>  

 <span data-ttu-id="61820-113">Yok</span><span class="sxs-lookup"><span data-stu-id="61820-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61820-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61820-114">Parent Elements</span></span>  
  
|<span data-ttu-id="61820-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="61820-115">Element</span></span>|<span data-ttu-id="61820-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61820-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="61820-117">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61820-117">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61820-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61820-118">Remarks</span></span>  

 <span data-ttu-id="61820-119">Bir RSA denetimi, kimlik doğrulamasını RSA anahtarına göre veya kendi RSA anahtar değerini oluşturan tek bir sertifika ile kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="61820-119">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="61820-120">Bu, RSA anahtar değeri değiştirilirse hizmetin masrafına daha sıkı bir RSA anahtarının daha sıkı şekilde doğrulanmasını, ancak mevcut istemcilerle çalışmamayı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="61820-120">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="61820-121">Bir istemciye hizmet doğrulamak üzere kimlik kullanma hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="61820-121">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61820-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="61820-122">Example</span></span>  

 <span data-ttu-id="61820-123">Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının ortak anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61820-123">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="61820-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61820-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="61820-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="61820-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
