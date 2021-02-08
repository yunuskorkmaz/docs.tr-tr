---
description: 'Hakkında daha fazla bilgi <add> edinin: <contractTypeNames>'
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 0708aa277b4250cb4134a98ddf7af661840981a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804003"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="331a4-103">\<add> / \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="331a4-103">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="331a4-104">Aranmakta olan hizmetlerin sözleşme adını ve genellikle bir hizmet ararken kullanılan kriterleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="331a4-104">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="331a4-105">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="331a4-105">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="331a4-106">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="331a4-106">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="331a4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="331a4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="331a4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="331a4-108">Attributes and Elements</span></span>  

 <span data-ttu-id="331a4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="331a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="331a4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="331a4-110">Attributes</span></span>  
  
|<span data-ttu-id="331a4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="331a4-111">Attribute</span></span>|<span data-ttu-id="331a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="331a4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="331a4-113">name</span><span class="sxs-lookup"><span data-stu-id="331a4-113">name</span></span>|<span data-ttu-id="331a4-114">Anlaşma türünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="331a4-114">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="331a4-115">ad alanı</span><span class="sxs-lookup"><span data-stu-id="331a4-115">namespace</span></span>|<span data-ttu-id="331a4-116">Anlaşma türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="331a4-116">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="331a4-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="331a4-117">Child Elements</span></span>  

 <span data-ttu-id="331a4-118">Yok</span><span class="sxs-lookup"><span data-stu-id="331a4-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="331a4-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="331a4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="331a4-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="331a4-120">Element</span></span>|<span data-ttu-id="331a4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="331a4-121">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="331a4-122">Bir anlaşma türü adı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="331a4-122">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="331a4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="331a4-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
