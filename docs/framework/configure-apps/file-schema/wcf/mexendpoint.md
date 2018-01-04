---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713c1c260f36d6d980903cce1ebcc9c5648116c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="62c51-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="62c51-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="62c51-103">Bu yapılandırma öğesi, standart bir uç nokta sabit bir IMetadataExchange sözleşme ile tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62c51-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="62c51-104">Tüm meta veri exchange uç noktalar kendi sözleşme IMetadataExchange belirtin olduğundan, kendiniz için bir tane tanımlama yerine bu standart noktasını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="62c51-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="62c51-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="62c51-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="62c51-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="62c51-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c51-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62c51-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62c51-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c51-108">Attributes and Elements</span></span>  
 <span data-ttu-id="62c51-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62c51-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62c51-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62c51-110">Attributes</span></span>  
  
|<span data-ttu-id="62c51-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62c51-111">Attribute</span></span>|<span data-ttu-id="62c51-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62c51-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62c51-113">name</span><span class="sxs-lookup"><span data-stu-id="62c51-113">name</span></span>|<span data-ttu-id="62c51-114">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="62c51-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="62c51-115">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="62c51-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62c51-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c51-116">Child Elements</span></span>  
 <span data-ttu-id="62c51-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="62c51-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62c51-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c51-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62c51-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="62c51-119">Element</span></span>|<span data-ttu-id="62c51-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62c51-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62c51-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="62c51-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="62c51-122">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="62c51-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
