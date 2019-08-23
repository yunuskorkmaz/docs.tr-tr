---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 12f9d4eca02ae3b306646826667c4eafef51a95c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919373"
---
# <a name="contracttypenames"></a><span data-ttu-id="64cbf-101">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="64cbf-101">\<contractTypeNames></span></span>
<span data-ttu-id="64cbf-102">Aranan hizmetlerin sözleşme adları ve genellikle bir hizmet ararken kullanılan ölçütler olan anlaşma türü adlarının listesini belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="64cbf-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="64cbf-103">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="64cbf-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="64cbf-104">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64cbf-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="64cbf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="64cbf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="64cbf-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="64cbf-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64cbf-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64cbf-107">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64cbf-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64cbf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64cbf-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64cbf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64cbf-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64cbf-110">Attributes</span></span>  
 <span data-ttu-id="64cbf-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="64cbf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64cbf-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64cbf-112">Child Elements</span></span>  
  
|<span data-ttu-id="64cbf-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="64cbf-113">Element</span></span>|<span data-ttu-id="64cbf-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64cbf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64cbf-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="64cbf-115">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="64cbf-116">Anlaşma türü adı, genellikle bir hizmeti ararken kullanılan ölçüt kümesini ifade eden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="64cbf-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64cbf-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64cbf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="64cbf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="64cbf-118">Element</span></span>|<span data-ttu-id="64cbf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64cbf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64cbf-120">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="64cbf-120">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="64cbf-121">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="64cbf-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="64cbf-122">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64cbf-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64cbf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64cbf-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
