---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091323"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="248af-102">\<Ekle >, \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="248af-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="248af-103">Sözleşme adı Aranan Hizmetleri ve genellikle bir hizmet için ararken kullanılan ölçütü belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="248af-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="248af-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="248af-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="248af-105">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="248af-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="248af-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="248af-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="248af-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="248af-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248af-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="248af-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="248af-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="248af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="248af-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="248af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="248af-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="248af-111">Attributes</span></span>  
  
|<span data-ttu-id="248af-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="248af-112">Attribute</span></span>|<span data-ttu-id="248af-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="248af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="248af-114">name</span><span class="sxs-lookup"><span data-stu-id="248af-114">name</span></span>|<span data-ttu-id="248af-115">Sözleşme türü adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="248af-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="248af-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="248af-116">namespace</span></span>|<span data-ttu-id="248af-117">Sözleşme türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="248af-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="248af-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="248af-118">Child Elements</span></span>  
 <span data-ttu-id="248af-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="248af-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="248af-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="248af-120">Parent Elements</span></span>  
  
|<span data-ttu-id="248af-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="248af-121">Element</span></span>|<span data-ttu-id="248af-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="248af-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="248af-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="248af-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="248af-124">Sözleşme türü adları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="248af-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="248af-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="248af-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
