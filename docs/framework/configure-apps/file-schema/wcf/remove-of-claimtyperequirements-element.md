---
title: <remove><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399993"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="2d0cc-102">\<remove>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="2d0cc-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="2d0cc-103">Federal kimlik bilgilerinde kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="2d0cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d0cc-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d0cc-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d0cc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2d0cc-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d0cc-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d0cc-107">Attributes</span></span>  
  
|<span data-ttu-id="2d0cc-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d0cc-108">Attribute</span></span>|<span data-ttu-id="2d0cc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d0cc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d0cc-110">claimType</span><span class="sxs-lookup"><span data-stu-id="2d0cc-110">claimType</span></span>|<span data-ttu-id="2d0cc-111">Kaldırılacak talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d0cc-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d0cc-112">Child Elements</span></span>  
 <span data-ttu-id="2d0cc-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d0cc-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d0cc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2d0cc-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d0cc-115">Element</span></span>|<span data-ttu-id="2d0cc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d0cc-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="2d0cc-117">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2d0cc-118">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="2d0cc-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2d0cc-119">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2d0cc-120">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2d0cc-121">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d0cc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d0cc-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
