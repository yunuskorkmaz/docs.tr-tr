---
description: 'Hakkında daha fazla bilgi <secureConversationAuthentication> edinin: <serviceCredential>'
title: <secureConversationAuthentication> / <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 8f95b4009111996d2a5c1133c9ef762375b4e3e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683326"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="93aff-103">\<secureConversationAuthentication> / \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="93aff-103">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="93aff-104">Güvenli konuşma hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="93aff-104">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="93aff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="93aff-105">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93aff-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="93aff-106">Attributes and Elements</span></span>  

 <span data-ttu-id="93aff-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93aff-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93aff-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="93aff-108">Attributes</span></span>  
  
|<span data-ttu-id="93aff-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="93aff-109">Attribute</span></span>|<span data-ttu-id="93aff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93aff-110">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="93aff-111">Kullanılacak türünü belirten bir dize <xref:System.ServiceModel.Security.SecurityStateEncoder> .</span><span class="sxs-lookup"><span data-stu-id="93aff-111">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93aff-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="93aff-112">Child Elements</span></span>  

 <span data-ttu-id="93aff-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="93aff-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93aff-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="93aff-114">Parent Elements</span></span>  
  
|<span data-ttu-id="93aff-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="93aff-115">Element</span></span>|<span data-ttu-id="93aff-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93aff-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="93aff-117">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="93aff-117">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93aff-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93aff-118">Remarks</span></span>  

 <span data-ttu-id="93aff-119">Bu yapılandırma öğesini, güvenlik bağlamı belirteci (SCT) tanımlama bilgileri serileştirmesi için bilinen talep türlerinin bir listesini belirtmek ve tanımlama bilgilerini kodlamak ve güvenli hale getirmek için bir kodlayıcı kullanmak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="93aff-119">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="93aff-120">SCT hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Security.SecureConversationServiceCredential> ..</span><span class="sxs-lookup"><span data-stu-id="93aff-120">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93aff-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93aff-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
