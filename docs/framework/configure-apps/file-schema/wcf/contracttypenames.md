---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 2c3f501f44d9e3c601e654041eb9d5a7de8a0a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626777"
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="5e282-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="5e282-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="5e282-103">Aranan hizmetleri sözleşmesi adlarıdır, sözleşme türü adları ve genellikle bir hizmet için ararken kullanılan ölçütü listesi belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="5e282-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="5e282-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="5e282-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="5e282-105">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e282-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="5e282-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e282-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e282-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5e282-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e282-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e282-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e282-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e282-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e282-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e282-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e282-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e282-111">Attributes</span></span>  
 <span data-ttu-id="5e282-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e282-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e282-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e282-113">Child Elements</span></span>  
  
|<span data-ttu-id="5e282-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e282-114">Element</span></span>|<span data-ttu-id="5e282-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e282-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e282-116">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5e282-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="5e282-117">Sözleşme türü adı genellikle bir hizmet için ararken kullanılan ölçüt kümesine başvuran bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="5e282-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e282-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e282-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5e282-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e282-119">Element</span></span>|<span data-ttu-id="5e282-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e282-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e282-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="5e282-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="5e282-122">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e282-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="5e282-123">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="5e282-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e282-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e282-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
