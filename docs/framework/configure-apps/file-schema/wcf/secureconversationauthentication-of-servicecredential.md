---
title: '&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 2c8479c4d8a321c822d49bdc24f359ffad5500e9
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147193"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="f6994-102">&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="f6994-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="f6994-103">Güvenli konuşma hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6994-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="f6994-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6994-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6994-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f6994-105">\<behaviors></span></span>  
<span data-ttu-id="f6994-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f6994-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f6994-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f6994-107">\<behavior></span></span>  
<span data-ttu-id="f6994-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f6994-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f6994-109">\<Servicecredential ></span><span class="sxs-lookup"><span data-stu-id="f6994-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6994-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6994-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6994-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6994-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f6994-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6994-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6994-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6994-113">Attributes</span></span>  
  
|<span data-ttu-id="f6994-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6994-114">Attribute</span></span>|<span data-ttu-id="f6994-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6994-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="f6994-116">Türünü belirten bir dize <xref:System.ServiceModel.Security.SecurityStateEncoder> kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="f6994-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6994-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6994-117">Child Elements</span></span>  
 <span data-ttu-id="f6994-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="f6994-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6994-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6994-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f6994-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6994-120">Element</span></span>|<span data-ttu-id="f6994-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6994-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6994-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f6994-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f6994-123">Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6994-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6994-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6994-124">Remarks</span></span>  
 <span data-ttu-id="f6994-125">Bu yapılandırma öğesi için güvenlik bağlamı belirteci (SCT) tanımlama bilgilerini serileştirme yanı sıra, kodlamak ve tanımlama bilgilerinin güvenliğini sağlamak için bir kodlayıcı bilinen talep türlerinin bir listesini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6994-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="f6994-126">SCT hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="f6994-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6994-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6994-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
