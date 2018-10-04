---
title: '&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
ms.openlocfilehash: 3adcf7ba9814bcf494d345cf0e3f47c57df2152c
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266110"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="2fd36-102">&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="2fd36-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="2fd36-103">Güvenli konuşma hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd36-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="2fd36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fd36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fd36-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2fd36-105">\<behaviors></span></span>  
<span data-ttu-id="2fd36-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2fd36-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2fd36-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2fd36-107">\<behavior></span></span>  
<span data-ttu-id="2fd36-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2fd36-108">\<serviceCredentials></span></span>  
<span data-ttu-id="2fd36-109">\<Servicecredential ></span><span class="sxs-lookup"><span data-stu-id="2fd36-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd36-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fd36-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fd36-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2fd36-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2fd36-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fd36-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2fd36-113">Attributes</span></span>  
  
|<span data-ttu-id="2fd36-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2fd36-114">Attribute</span></span>|<span data-ttu-id="2fd36-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd36-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="2fd36-116">Türünü belirten bir dize <xref:System.ServiceModel.Security.SecurityStateEncoder> kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2fd36-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fd36-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd36-117">Child Elements</span></span>  
 <span data-ttu-id="2fd36-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="2fd36-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fd36-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fd36-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2fd36-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="2fd36-120">Element</span></span>|<span data-ttu-id="2fd36-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fd36-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fd36-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2fd36-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="2fd36-123">Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd36-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fd36-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fd36-124">Remarks</span></span>  
 <span data-ttu-id="2fd36-125">Bu yapılandırma öğesi için güvenlik bağlamı belirteci (SCT) tanımlama bilgilerini serileştirme yanı sıra, kodlamak ve tanımlama bilgilerinin güvenliğini sağlamak için bir kodlayıcı bilinen talep türlerinin bir listesini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fd36-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="2fd36-126">SCT hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="2fd36-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd36-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fd36-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
