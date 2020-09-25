---
title: <clear><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: aa94a012da11bcec6fb5fe270ad9f3574f88e6d7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172911"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="1359a-102">\<clear>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="1359a-102">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="1359a-103">Tüm talep türlerinin federal kimlik bilgilerinde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1359a-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="1359a-104">Bu, koleksiyonun boş başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1359a-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="1359a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1359a-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1359a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1359a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1359a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1359a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1359a-108">Attributes</span></span>  

 <span data-ttu-id="1359a-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="1359a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1359a-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359a-110">Child Elements</span></span>  

 <span data-ttu-id="1359a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1359a-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1359a-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1359a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="1359a-113">Element</span></span>|<span data-ttu-id="1359a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1359a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="1359a-115">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1359a-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="1359a-116">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="1359a-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="1359a-117">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="1359a-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1359a-118">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1359a-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1359a-119">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1359a-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1359a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1359a-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
