---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: b1cec9272a1de029ab72ea4d5f36c74630e5b93a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673205"
---
# <a name="contracttypenames"></a><span data-ttu-id="0f82a-101">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="0f82a-101">\<contractTypeNames></span></span>
<span data-ttu-id="0f82a-102">Aranan hizmetleri sözleşmesi adlarıdır, sözleşme türü adları ve genellikle bir hizmet için ararken kullanılan ölçütü listesi belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="0f82a-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="0f82a-103">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="0f82a-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="0f82a-104">Windows Communication Foundation (WCF), bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f82a-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="0f82a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0f82a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0f82a-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0f82a-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f82a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f82a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f82a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f82a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0f82a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f82a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f82a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f82a-110">Attributes</span></span>  
 <span data-ttu-id="0f82a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f82a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0f82a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f82a-112">Child Elements</span></span>  
  
|<span data-ttu-id="0f82a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f82a-113">Element</span></span>|<span data-ttu-id="0f82a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f82a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f82a-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="0f82a-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="0f82a-116">Sözleşme türü adı genellikle bir hizmet için ararken kullanılan ölçüt kümesine başvuran bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0f82a-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f82a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f82a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0f82a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f82a-118">Element</span></span>|<span data-ttu-id="0f82a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f82a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f82a-120">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="0f82a-120">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="0f82a-121">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0f82a-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="0f82a-122">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="0f82a-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f82a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f82a-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
