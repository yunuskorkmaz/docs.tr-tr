---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271700"
---
# <a name="mexendpoint"></a><span data-ttu-id="67ac2-101">\<mexEndpoint ></span><span class="sxs-lookup"><span data-stu-id="67ac2-101">\<mexEndpoint></span></span>
<span data-ttu-id="67ac2-102">Bu yapılandırma öğesi, bir sabit IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="67ac2-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="67ac2-103">Tüm meta veri değişimi uç noktalarını IMetadataExchange sözleşmelerine belirtin. bu yana kendiniz bir tane tanımlayacaksınız yerine bu standart noktası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67ac2-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="67ac2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67ac2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="67ac2-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="67ac2-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ac2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67ac2-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67ac2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67ac2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="67ac2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67ac2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67ac2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67ac2-109">Attributes</span></span>  
  
|<span data-ttu-id="67ac2-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67ac2-110">Attribute</span></span>|<span data-ttu-id="67ac2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67ac2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67ac2-112">name</span><span class="sxs-lookup"><span data-stu-id="67ac2-112">name</span></span>|<span data-ttu-id="67ac2-113">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="67ac2-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="67ac2-114">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="67ac2-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67ac2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67ac2-115">Child Elements</span></span>  
 <span data-ttu-id="67ac2-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="67ac2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67ac2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67ac2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="67ac2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="67ac2-118">Element</span></span>|<span data-ttu-id="67ac2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67ac2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67ac2-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="67ac2-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="67ac2-121">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="67ac2-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
