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
ms.openlocfilehash: 6eefecb696c88d160e56c7f12a1b03ea67e531b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="51175-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="51175-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="51175-103">Bu yapılandırma öğesi, standart bir uç nokta sabit bir IMetadataExchange sözleşme ile tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51175-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="51175-104">Tüm meta veri exchange uç noktalar kendi sözleşme IMetadataExchange belirtin olduğundan, kendiniz için bir tane tanımlama yerine bu standart noktasını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="51175-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="51175-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="51175-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="51175-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="51175-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51175-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51175-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51175-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="51175-108">Attributes and Elements</span></span>  
 <span data-ttu-id="51175-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51175-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51175-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="51175-110">Attributes</span></span>  
  
|<span data-ttu-id="51175-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="51175-111">Attribute</span></span>|<span data-ttu-id="51175-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51175-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51175-113">name</span><span class="sxs-lookup"><span data-stu-id="51175-113">name</span></span>|<span data-ttu-id="51175-114">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="51175-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="51175-115">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="51175-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51175-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="51175-116">Child Elements</span></span>  
 <span data-ttu-id="51175-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="51175-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51175-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="51175-118">Parent Elements</span></span>  
  
|<span data-ttu-id="51175-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="51175-119">Element</span></span>|<span data-ttu-id="51175-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51175-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51175-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="51175-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="51175-122">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="51175-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
