---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855117"
---
# \<mexEndpoint>
<span data-ttu-id="ddc89-101">Bu yapılandırma öğesi, sabit bir IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ddc89-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="ddc89-102">Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddc89-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="ddc89-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddc89-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddc89-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddc89-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ddc89-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddc89-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddc89-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddc89-106">Attributes</span></span>  
  
|<span data-ttu-id="ddc89-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddc89-107">Attribute</span></span>|<span data-ttu-id="ddc89-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc89-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddc89-109">name</span><span class="sxs-lookup"><span data-stu-id="ddc89-109">name</span></span>|<span data-ttu-id="ddc89-110">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ddc89-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ddc89-111">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddc89-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddc89-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddc89-112">Child Elements</span></span>  
 <span data-ttu-id="ddc89-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="ddc89-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddc89-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddc89-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ddc89-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddc89-115">Element</span></span>|<span data-ttu-id="ddc89-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc89-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ddc89-117">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ddc89-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
