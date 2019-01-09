---
title: '&lt;contractTypeNames&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 79972eaea6918b3fe923c963b6a219fd8f972516
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145620"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="0aea4-102">&lt;contractTypeNames&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="0aea4-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="0aea4-103">Sözleşme adı Aranan Hizmetleri ve genellikle bir hizmet için ararken kullanılan ölçütü belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0aea4-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="0aea4-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="0aea4-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="0aea4-105">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0aea4-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="0aea4-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0aea4-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="0aea4-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0aea4-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aea4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aea4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0aea4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0aea4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0aea4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0aea4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0aea4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0aea4-111">Attributes</span></span>  
  
|<span data-ttu-id="0aea4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0aea4-112">Attribute</span></span>|<span data-ttu-id="0aea4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0aea4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0aea4-114">name</span><span class="sxs-lookup"><span data-stu-id="0aea4-114">name</span></span>|<span data-ttu-id="0aea4-115">Sözleşme türü adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0aea4-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="0aea4-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="0aea4-116">namespace</span></span>|<span data-ttu-id="0aea4-117">Sözleşme türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0aea4-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0aea4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0aea4-118">Child Elements</span></span>  
 <span data-ttu-id="0aea4-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0aea4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0aea4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0aea4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0aea4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0aea4-121">Element</span></span>|<span data-ttu-id="0aea4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0aea4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0aea4-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="0aea4-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="0aea4-124">Sözleşme türü adları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0aea4-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0aea4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0aea4-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
