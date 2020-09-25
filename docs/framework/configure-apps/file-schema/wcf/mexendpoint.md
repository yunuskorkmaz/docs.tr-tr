---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: e8f0e0fa2ea1606bf980fd6fa1fcd47f12c3b540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204755"
---
# \<mexEndpoint>

<span data-ttu-id="67877-101">Bu yapılandırma öğesi, sabit bir IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="67877-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="67877-102">Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67877-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="67877-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="67877-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67877-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67877-104">Attributes and Elements</span></span>  

 <span data-ttu-id="67877-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67877-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67877-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67877-106">Attributes</span></span>  
  
|<span data-ttu-id="67877-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67877-107">Attribute</span></span>|<span data-ttu-id="67877-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67877-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67877-109">name</span><span class="sxs-lookup"><span data-stu-id="67877-109">name</span></span>|<span data-ttu-id="67877-110">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="67877-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="67877-111">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67877-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67877-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67877-112">Child Elements</span></span>  

 <span data-ttu-id="67877-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="67877-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67877-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67877-114">Parent Elements</span></span>  
  
|<span data-ttu-id="67877-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="67877-115">Element</span></span>|<span data-ttu-id="67877-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67877-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="67877-117">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="67877-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
