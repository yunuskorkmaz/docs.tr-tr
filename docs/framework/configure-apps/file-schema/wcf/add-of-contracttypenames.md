---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 24f1478b99aef909ae93f87a70be257e9ba10d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926743"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="8b164-102">\<\<ContractTypeNames > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="8b164-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="8b164-103">Aranmakta olan hizmetlerin sözleşme adını ve genellikle bir hizmet ararken kullanılan kriterleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="8b164-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="8b164-104">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="8b164-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="8b164-105">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b164-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="8b164-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8b164-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="8b164-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="8b164-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b164-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b164-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b164-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b164-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8b164-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b164-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b164-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b164-111">Attributes</span></span>  
  
|<span data-ttu-id="8b164-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b164-112">Attribute</span></span>|<span data-ttu-id="8b164-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b164-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b164-114">name</span><span class="sxs-lookup"><span data-stu-id="8b164-114">name</span></span>|<span data-ttu-id="8b164-115">Anlaşma türünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b164-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="8b164-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="8b164-116">namespace</span></span>|<span data-ttu-id="8b164-117">Anlaşma türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b164-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b164-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b164-118">Child Elements</span></span>  
 <span data-ttu-id="8b164-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="8b164-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b164-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b164-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8b164-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b164-121">Element</span></span>|<span data-ttu-id="8b164-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b164-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b164-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="8b164-123">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="8b164-124">Bir anlaşma türü adı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8b164-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b164-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b164-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
