---
title: <secureConversationAuthentication> / <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399936"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="230f4-102">\<\<SecureConversationAuthentication > securekonuşma kimlik doğrulaması ></span><span class="sxs-lookup"><span data-stu-id="230f4-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="230f4-103">Güvenli konuşma hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="230f4-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="230f4-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="230f4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="230f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="230f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="230f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="230f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="230f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="230f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Securekonuşma kimlik doğrulaması >**</span><span class="sxs-lookup"><span data-stu-id="230f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230f4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="230f4-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="230f4-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="230f4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="230f4-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="230f4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="230f4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="230f4-114">Attributes</span></span>  
  
|<span data-ttu-id="230f4-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="230f4-115">Attribute</span></span>|<span data-ttu-id="230f4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230f4-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="230f4-117">Kullanılacak türünü <xref:System.ServiceModel.Security.SecurityStateEncoder> belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="230f4-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="230f4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="230f4-118">Child Elements</span></span>  
 <span data-ttu-id="230f4-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="230f4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="230f4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="230f4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="230f4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="230f4-121">Element</span></span>|<span data-ttu-id="230f4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230f4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="230f4-123">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="230f4-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="230f4-124">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="230f4-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230f4-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230f4-125">Remarks</span></span>  
 <span data-ttu-id="230f4-126">Bu yapılandırma öğesini, güvenlik bağlamı belirteci (SCT) tanımlama bilgileri serileştirmesi için bilinen talep türlerinin bir listesini belirtmek ve tanımlama bilgilerini kodlamak ve güvenli hale getirmek için bir kodlayıcı kullanmak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="230f4-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="230f4-127">SCT hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="230f4-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230f4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="230f4-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
