---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931253"
---
# <a name="mexendpoint"></a><span data-ttu-id="505a0-101">\<mexEndpoint ></span><span class="sxs-lookup"><span data-stu-id="505a0-101">\<mexEndpoint></span></span>
<span data-ttu-id="505a0-102">Bu yapılandırma öğesi, sabit bir IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="505a0-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="505a0-103">Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="505a0-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="505a0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="505a0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="505a0-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="505a0-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505a0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="505a0-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="505a0-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="505a0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="505a0-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="505a0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="505a0-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="505a0-109">Attributes</span></span>  
  
|<span data-ttu-id="505a0-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="505a0-110">Attribute</span></span>|<span data-ttu-id="505a0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="505a0-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="505a0-112">name</span><span class="sxs-lookup"><span data-stu-id="505a0-112">name</span></span>|<span data-ttu-id="505a0-113">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="505a0-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="505a0-114">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="505a0-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="505a0-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="505a0-115">Child Elements</span></span>  
 <span data-ttu-id="505a0-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="505a0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="505a0-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="505a0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="505a0-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="505a0-118">Element</span></span>|<span data-ttu-id="505a0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="505a0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="505a0-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="505a0-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="505a0-121">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="505a0-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
