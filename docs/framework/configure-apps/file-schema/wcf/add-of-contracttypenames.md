---
title: '&lt;contractTypeNames&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d7cfcb8217bbf157af4ba2893773b180f0a9f28
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="ad063-102">&lt;contractTypeNames&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="ad063-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="ad063-103">Aranan Hizmetleri ve genellikle ararken bir hizmet için kullanılan ölçüt sözleşme adını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ad063-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="ad063-104">Birden fazla sözleşme adı belirtilmezse, yalnızca hizmet uç noktaları tüm sözleşmeleri eşleşen yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="ad063-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="ad063-105">İçinde unutmayın [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], bir uç nokta yalnızca bir sözleşme destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ad063-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="ad063-106">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ad063-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad063-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ad063-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad063-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad063-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad063-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad063-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ad063-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad063-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad063-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad063-111">Attributes</span></span>  
  
|<span data-ttu-id="ad063-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ad063-112">Attribute</span></span>|<span data-ttu-id="ad063-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad063-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad063-114">name</span><span class="sxs-lookup"><span data-stu-id="ad063-114">name</span></span>|<span data-ttu-id="ad063-115">Sözleşme türünün adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ad063-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="ad063-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="ad063-116">namespace</span></span>|<span data-ttu-id="ad063-117">Sözleşme türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ad063-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad063-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad063-118">Child Elements</span></span>  
 <span data-ttu-id="ad063-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad063-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad063-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad063-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ad063-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad063-121">Element</span></span>|<span data-ttu-id="ad063-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad063-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad063-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ad063-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ad063-124">Sözleşme tür adları topluluğu.</span><span class="sxs-lookup"><span data-stu-id="ad063-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad063-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad063-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
