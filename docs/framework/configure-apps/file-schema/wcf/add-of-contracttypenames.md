---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701196"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="47ffd-102">\<Ekle >, \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="47ffd-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="47ffd-103">Sözleşme adı Aranan Hizmetleri ve genellikle bir hizmet için ararken kullanılan ölçütü belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="47ffd-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="47ffd-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="47ffd-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="47ffd-105">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47ffd-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="47ffd-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="47ffd-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="47ffd-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="47ffd-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ffd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47ffd-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47ffd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47ffd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47ffd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47ffd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47ffd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47ffd-111">Attributes</span></span>  
  
|<span data-ttu-id="47ffd-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47ffd-112">Attribute</span></span>|<span data-ttu-id="47ffd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47ffd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47ffd-114">name</span><span class="sxs-lookup"><span data-stu-id="47ffd-114">name</span></span>|<span data-ttu-id="47ffd-115">Sözleşme türü adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="47ffd-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="47ffd-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="47ffd-116">namespace</span></span>|<span data-ttu-id="47ffd-117">Sözleşme türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="47ffd-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47ffd-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47ffd-118">Child Elements</span></span>  
 <span data-ttu-id="47ffd-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="47ffd-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47ffd-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47ffd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="47ffd-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="47ffd-121">Element</span></span>|<span data-ttu-id="47ffd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47ffd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47ffd-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="47ffd-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="47ffd-124">Sözleşme türü adları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="47ffd-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47ffd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47ffd-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
