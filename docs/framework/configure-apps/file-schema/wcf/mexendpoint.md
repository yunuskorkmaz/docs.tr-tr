---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 4e2fb4946ee68b3cbd5bd6bfbafe6bb5e9c9106f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149156"
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="5b8d1-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5b8d1-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="5b8d1-103">Bu yapılandırma öğesi, bir sabit IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="5b8d1-104">Tüm meta veri değişimi uç noktalarını IMetadataExchange sözleşmelerine belirtin. bu yana kendiniz bir tane tanımlayacaksınız yerine bu standart noktası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="5b8d1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5b8d1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b8d1-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5b8d1-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8d1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b8d1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b8d1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b8d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b8d1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b8d1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b8d1-110">Attributes</span></span>  
  
|<span data-ttu-id="5b8d1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b8d1-111">Attribute</span></span>|<span data-ttu-id="5b8d1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b8d1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b8d1-113">name</span><span class="sxs-lookup"><span data-stu-id="5b8d1-113">name</span></span>|<span data-ttu-id="5b8d1-114">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5b8d1-115">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b8d1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b8d1-116">Child Elements</span></span>  
 <span data-ttu-id="5b8d1-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b8d1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b8d1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5b8d1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b8d1-119">Element</span></span>|<span data-ttu-id="5b8d1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b8d1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b8d1-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5b8d1-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5b8d1-122">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="5b8d1-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
