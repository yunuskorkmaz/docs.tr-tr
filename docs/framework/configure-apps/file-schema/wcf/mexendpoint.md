---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855117"
---
# <a name="mexendpoint"></a><span data-ttu-id="1caff-101">\<mexEndpoint ></span><span class="sxs-lookup"><span data-stu-id="1caff-101">\<mexEndpoint></span></span>
<span data-ttu-id="1caff-102">Bu yapılandırma öğesi, sabit bir IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1caff-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="1caff-103">Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1caff-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="1caff-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1caff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1caff-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1caff-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1caff-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="1caff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="1caff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="1caff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1caff-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1caff-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1caff-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1caff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1caff-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1caff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1caff-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1caff-111">Attributes</span></span>  
  
|<span data-ttu-id="1caff-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1caff-112">Attribute</span></span>|<span data-ttu-id="1caff-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1caff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1caff-114">name</span><span class="sxs-lookup"><span data-stu-id="1caff-114">name</span></span>|<span data-ttu-id="1caff-115">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1caff-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1caff-116">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1caff-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1caff-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1caff-117">Child Elements</span></span>  
 <span data-ttu-id="1caff-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="1caff-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1caff-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1caff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1caff-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1caff-120">Element</span></span>|<span data-ttu-id="1caff-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1caff-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1caff-122">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1caff-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1caff-123">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1caff-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
