---
title: <secureConversationAuthentication> / <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: be2a9298a78de1503271f41076b9f5bb63c73f74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162250"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="909bb-102">\<secureConversationAuthentication> / \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="909bb-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="909bb-103">Güvenli konuşma hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="909bb-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="909bb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="909bb-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="909bb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="909bb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="909bb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="909bb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="909bb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="909bb-107">Attributes</span></span>  
  
|<span data-ttu-id="909bb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="909bb-108">Attribute</span></span>|<span data-ttu-id="909bb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="909bb-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="909bb-110">Kullanılacak türünü belirten bir dize <xref:System.ServiceModel.Security.SecurityStateEncoder> .</span><span class="sxs-lookup"><span data-stu-id="909bb-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="909bb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="909bb-111">Child Elements</span></span>  

 <span data-ttu-id="909bb-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="909bb-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="909bb-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="909bb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="909bb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="909bb-114">Element</span></span>|<span data-ttu-id="909bb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="909bb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="909bb-116">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="909bb-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="909bb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="909bb-117">Remarks</span></span>  

 <span data-ttu-id="909bb-118">Bu yapılandırma öğesini, güvenlik bağlamı belirteci (SCT) tanımlama bilgileri serileştirmesi için bilinen talep türlerinin bir listesini belirtmek ve tanımlama bilgilerini kodlamak ve güvenli hale getirmek için bir kodlayıcı kullanmak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="909bb-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="909bb-119">SCT hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Security.SecureConversationServiceCredential> ..</span><span class="sxs-lookup"><span data-stu-id="909bb-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909bb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="909bb-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
