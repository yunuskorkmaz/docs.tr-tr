---
description: 'Hakkında daha fazla bilgi edinin: <mexEndpoint>'
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 1872b6104aaaaa2787ca3f359026552499bade9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684418"
---
# \<mexEndpoint>

<span data-ttu-id="a3d6d-102">Bu yapılandırma öğesi, sabit bir IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="a3d6d-103">Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a3d6d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3d6d-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3d6d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3d6d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a3d6d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3d6d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3d6d-107">Attributes</span></span>  
  
|<span data-ttu-id="a3d6d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3d6d-108">Attribute</span></span>|<span data-ttu-id="a3d6d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d6d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3d6d-110">name</span><span class="sxs-lookup"><span data-stu-id="a3d6d-110">name</span></span>|<span data-ttu-id="a3d6d-111">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-111">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a3d6d-112">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-112">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3d6d-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3d6d-113">Child Elements</span></span>  

 <span data-ttu-id="a3d6d-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3d6d-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3d6d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a3d6d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3d6d-116">Element</span></span>|<span data-ttu-id="a3d6d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d6d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a3d6d-118">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a3d6d-118">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
