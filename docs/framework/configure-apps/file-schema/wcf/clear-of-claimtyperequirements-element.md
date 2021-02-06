---
description: 'Hakkında daha fazla bilgi edinin: <clear> <claimTypeRequirements> öğe'
title: <clear><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: d25dad5afcec352f040ea4f8c08e5ffa2bc16d19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638892"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="0ba89-103">\<clear>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="0ba89-103">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="0ba89-104">Tüm talep türlerinin federal kimlik bilgilerinde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ba89-104">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="0ba89-105">Bu, koleksiyonun boş başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba89-105">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="0ba89-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ba89-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ba89-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba89-107">Attributes and Elements</span></span>  

 <span data-ttu-id="0ba89-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ba89-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ba89-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ba89-109">Attributes</span></span>  

 <span data-ttu-id="0ba89-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ba89-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ba89-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba89-111">Child Elements</span></span>  

 <span data-ttu-id="0ba89-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ba89-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ba89-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba89-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0ba89-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ba89-114">Element</span></span>|<span data-ttu-id="0ba89-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ba89-115">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="0ba89-116">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ba89-116">Specifies a collection of required claim types.</span></span> <span data-ttu-id="0ba89-117">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="0ba89-117">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="0ba89-118">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0ba89-118">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0ba89-119">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ba89-119">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0ba89-120">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ba89-120">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ba89-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba89-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
