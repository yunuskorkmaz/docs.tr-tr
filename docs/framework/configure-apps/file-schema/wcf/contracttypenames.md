---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 60647e6ec31e7228f09d084ff669a1829770ca14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144737"
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="6aa67-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="6aa67-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="6aa67-103">Aranan hizmetleri sözleşmesi adlarıdır, sözleşme türü adları ve genellikle bir hizmet için ararken kullanılan ölçütü listesi belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="6aa67-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="6aa67-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="6aa67-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="6aa67-105">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6aa67-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="6aa67-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6aa67-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="6aa67-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="6aa67-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa67-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aa67-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aa67-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aa67-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6aa67-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6aa67-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aa67-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6aa67-111">Attributes</span></span>  
 <span data-ttu-id="6aa67-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="6aa67-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6aa67-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aa67-113">Child Elements</span></span>  
  
|<span data-ttu-id="6aa67-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="6aa67-114">Element</span></span>|<span data-ttu-id="6aa67-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6aa67-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aa67-116">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="6aa67-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="6aa67-117">Sözleşme türü adı genellikle bir hizmet için ararken kullanılan ölçüt kümesine başvuran bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="6aa67-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6aa67-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aa67-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6aa67-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6aa67-119">Element</span></span>|<span data-ttu-id="6aa67-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6aa67-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aa67-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="6aa67-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="6aa67-122">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6aa67-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6aa67-123">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="6aa67-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aa67-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6aa67-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
