---
title: <secureConversationAuthentication> / <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935832"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="e03bd-102">\<\<SecureConversationAuthentication > securekonuşma kimlik doğrulaması ></span><span class="sxs-lookup"><span data-stu-id="e03bd-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="e03bd-103">Güvenli konuşma hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e03bd-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="e03bd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e03bd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e03bd-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e03bd-105">\<behaviors></span></span>  
<span data-ttu-id="e03bd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e03bd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e03bd-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="e03bd-107">\<behavior></span></span>  
<span data-ttu-id="e03bd-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e03bd-108">\<serviceCredentials></span></span>  
<span data-ttu-id="e03bd-109">\<Securekonuşma kimlik doğrulaması ></span><span class="sxs-lookup"><span data-stu-id="e03bd-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e03bd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e03bd-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e03bd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03bd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e03bd-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e03bd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e03bd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e03bd-113">Attributes</span></span>  
  
|<span data-ttu-id="e03bd-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e03bd-114">Attribute</span></span>|<span data-ttu-id="e03bd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e03bd-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="e03bd-116">Kullanılacak türünü <xref:System.ServiceModel.Security.SecurityStateEncoder> belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e03bd-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e03bd-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03bd-117">Child Elements</span></span>  
 <span data-ttu-id="e03bd-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e03bd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e03bd-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03bd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e03bd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e03bd-120">Element</span></span>|<span data-ttu-id="e03bd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e03bd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e03bd-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e03bd-122">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="e03bd-123">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e03bd-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e03bd-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e03bd-124">Remarks</span></span>  
 <span data-ttu-id="e03bd-125">Bu yapılandırma öğesini, güvenlik bağlamı belirteci (SCT) tanımlama bilgileri serileştirmesi için bilinen talep türlerinin bir listesini belirtmek ve tanımlama bilgilerini kodlamak ve güvenli hale getirmek için bir kodlayıcı kullanmak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="e03bd-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="e03bd-126">SCT hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="e03bd-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03bd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e03bd-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
