---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 99547967b65e5d7663ec11be98247e2018aaa34c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="bd11a-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="bd11a-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="bd11a-103">Aranan hizmetleri sözleşmesi adlardır, sözleşme tür adları ve genellikle ararken bir hizmet için kullanılan ölçüt listesini belirtir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="bd11a-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="bd11a-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmeleri eşleşen yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="bd11a-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="bd11a-105">Windows Communication Foundation (WCF) bir uç nokta yalnızca bir sözleşme destekleyebileceği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd11a-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="bd11a-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd11a-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd11a-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="bd11a-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd11a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd11a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd11a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd11a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd11a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd11a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd11a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd11a-111">Attributes</span></span>  
 <span data-ttu-id="bd11a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd11a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd11a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd11a-113">Child Elements</span></span>  
  
|<span data-ttu-id="bd11a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd11a-114">Element</span></span>|<span data-ttu-id="bd11a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd11a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd11a-116">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="bd11a-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="bd11a-117">Bir sözleşme türü adı genellikle ararken bir hizmet için kullanılan ölçüt kümesine başvuruda bulunan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="bd11a-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd11a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd11a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bd11a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd11a-119">Element</span></span>|<span data-ttu-id="bd11a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd11a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd11a-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="bd11a-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="bd11a-122">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd11a-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="bd11a-123">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="bd11a-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd11a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd11a-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
