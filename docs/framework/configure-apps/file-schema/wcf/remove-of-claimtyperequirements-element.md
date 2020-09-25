---
title: <remove><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 773f37156969f64f02711e6a60764aeb7e50a840
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181329"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="a7f4f-102">\<remove>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="a7f4f-102">\<remove> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="a7f4f-103">Federal kimlik bilgilerinde kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a7f4f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7f4f-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f4f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f4f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a7f4f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f4f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7f4f-107">Attributes</span></span>  
  
|<span data-ttu-id="a7f4f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7f4f-108">Attribute</span></span>|<span data-ttu-id="a7f4f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f4f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7f4f-110">claimType</span><span class="sxs-lookup"><span data-stu-id="a7f4f-110">claimType</span></span>|<span data-ttu-id="a7f4f-111">Kaldırılacak talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f4f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f4f-112">Child Elements</span></span>  

 <span data-ttu-id="a7f4f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f4f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f4f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f4f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7f4f-115">Element</span></span>|<span data-ttu-id="a7f4f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f4f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="a7f4f-117">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a7f4f-118">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="a7f4f-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a7f4f-119">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a7f4f-120">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a7f4f-121">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7f4f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f4f-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
