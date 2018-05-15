---
title: '&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7b56d12793ad35e6f951638465e77b92a66a6fd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="44821-102">&lt;serviceCredential&gt; için &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="44821-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="44821-103">Güvenli Konuşmayla hizmeti ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44821-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="44821-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44821-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44821-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="44821-105">\<behaviors></span></span>  
<span data-ttu-id="44821-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="44821-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="44821-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="44821-107">\<behavior></span></span>  
<span data-ttu-id="44821-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="44821-108">\<serviceCredentials></span></span>  
<span data-ttu-id="44821-109">\<Servicecredential ></span><span class="sxs-lookup"><span data-stu-id="44821-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44821-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44821-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44821-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44821-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44821-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44821-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44821-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44821-113">Attributes</span></span>  
  
|<span data-ttu-id="44821-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44821-114">Attribute</span></span>|<span data-ttu-id="44821-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44821-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="44821-116">Türünü belirten bir dize <xref:System.ServiceModel.Security.SecurityStateEncoder> kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="44821-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44821-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44821-117">Child Elements</span></span>  
 <span data-ttu-id="44821-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="44821-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44821-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44821-119">Parent Elements</span></span>  
  
|<span data-ttu-id="44821-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="44821-120">Element</span></span>|<span data-ttu-id="44821-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44821-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44821-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="44821-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="44821-123">Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44821-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44821-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44821-124">Remarks</span></span>  
 <span data-ttu-id="44821-125">Bu yapılandırma öğesi kodlamak ve tanımlama bilgilerinin güvenliğini sağlamak için bir kodlayıcı yanı sıra güvenlik bağlamı belirteci (SCT) tanımlama bilgilerini serileştirme için bilinen talep türlerinin bir listesini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="44821-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="44821-126">SCT hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="44821-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44821-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44821-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
