---
description: 'Hakkında daha fazla bilgi edinin: <remove> <claimTypeRequirements> öğe'
title: <remove><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 2ec917d27966954382e5b091fd538168b48b5ffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786908"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="d5d18-103">\<remove>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="d5d18-103">\<remove> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="d5d18-104">Federal kimlik bilgilerinde kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5d18-104">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="d5d18-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5d18-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5d18-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5d18-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d5d18-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d5d18-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5d18-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5d18-108">Attributes</span></span>  
  
|<span data-ttu-id="d5d18-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5d18-109">Attribute</span></span>|<span data-ttu-id="d5d18-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5d18-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5d18-111">claimType</span><span class="sxs-lookup"><span data-stu-id="d5d18-111">claimType</span></span>|<span data-ttu-id="d5d18-112">Kaldırılacak talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="d5d18-112">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5d18-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5d18-113">Child Elements</span></span>  

 <span data-ttu-id="d5d18-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5d18-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5d18-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5d18-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d5d18-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5d18-116">Element</span></span>|<span data-ttu-id="d5d18-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5d18-117">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="d5d18-118">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5d18-118">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d5d18-119">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="d5d18-119">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d5d18-120">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d5d18-120">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d5d18-121">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5d18-121">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d5d18-122">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5d18-122">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5d18-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d18-123">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
