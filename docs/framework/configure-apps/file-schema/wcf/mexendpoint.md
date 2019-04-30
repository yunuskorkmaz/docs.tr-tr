---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772482"
---
# <a name="mexendpoint"></a><span data-ttu-id="0a054-101">\<mexEndpoint ></span><span class="sxs-lookup"><span data-stu-id="0a054-101">\<mexEndpoint></span></span>
<span data-ttu-id="0a054-102">Bu yapılandırma öğesi, bir sabit IMetadataExchange sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a054-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="0a054-103">Tüm meta veri değişimi uç noktalarını IMetadataExchange sözleşmelerine belirtin. bu yana kendiniz bir tane tanımlayacaksınız yerine bu standart noktası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a054-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="0a054-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0a054-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a054-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0a054-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a054-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a054-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a054-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a054-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0a054-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a054-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a054-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a054-109">Attributes</span></span>  
  
|<span data-ttu-id="0a054-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a054-110">Attribute</span></span>|<span data-ttu-id="0a054-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a054-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a054-112">name</span><span class="sxs-lookup"><span data-stu-id="0a054-112">name</span></span>|<span data-ttu-id="0a054-113">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0a054-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0a054-114">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="0a054-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a054-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a054-115">Child Elements</span></span>  
 <span data-ttu-id="0a054-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="0a054-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a054-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a054-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0a054-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a054-118">Element</span></span>|<span data-ttu-id="0a054-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a054-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a054-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0a054-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0a054-121">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="0a054-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
