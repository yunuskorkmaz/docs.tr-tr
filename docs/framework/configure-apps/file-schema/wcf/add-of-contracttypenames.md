---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 69a0bbbc8774251dbdc062875bb06453f355c882
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149146"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="e262a-102">\<add> / \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="e262a-102">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="e262a-103">Aranmakta olan hizmetlerin sözleşme adını ve genellikle bir hizmet ararken kullanılan kriterleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e262a-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="e262a-104">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="e262a-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="e262a-105">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e262a-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e262a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e262a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e262a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e262a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="e262a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e262a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e262a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e262a-109">Attributes</span></span>  
  
|<span data-ttu-id="e262a-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e262a-110">Attribute</span></span>|<span data-ttu-id="e262a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e262a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e262a-112">name</span><span class="sxs-lookup"><span data-stu-id="e262a-112">name</span></span>|<span data-ttu-id="e262a-113">Anlaşma türünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e262a-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="e262a-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="e262a-114">namespace</span></span>|<span data-ttu-id="e262a-115">Anlaşma türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e262a-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e262a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e262a-116">Child Elements</span></span>  

 <span data-ttu-id="e262a-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e262a-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e262a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e262a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e262a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e262a-119">Element</span></span>|<span data-ttu-id="e262a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e262a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="e262a-121">Bir anlaşma türü adı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e262a-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e262a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e262a-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
