---
title: <clear><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400523"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="238ab-102">\<clear>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="238ab-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="238ab-103">Tüm talep türlerinin federal kimlik bilgilerinde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="238ab-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="238ab-104">Bu, koleksiyonun boş başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="238ab-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="238ab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="238ab-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="238ab-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="238ab-106">Attributes and Elements</span></span>  
 <span data-ttu-id="238ab-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="238ab-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="238ab-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="238ab-108">Attributes</span></span>  
 <span data-ttu-id="238ab-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="238ab-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="238ab-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="238ab-110">Child Elements</span></span>  
 <span data-ttu-id="238ab-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="238ab-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="238ab-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="238ab-112">Parent Elements</span></span>  
  
|<span data-ttu-id="238ab-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="238ab-113">Element</span></span>|<span data-ttu-id="238ab-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="238ab-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="238ab-115">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="238ab-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="238ab-116">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="238ab-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="238ab-117">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="238ab-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="238ab-118">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="238ab-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="238ab-119">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="238ab-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="238ab-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="238ab-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
