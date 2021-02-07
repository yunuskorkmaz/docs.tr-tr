---
description: 'Hakkında daha fazla bilgi <add> edinin: <scopes>'
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e5582a7599c221e9ac00e03178911290e18ff536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750240"
---
# <a name="add-of-scopes"></a><span data-ttu-id="03e4a-103">\<add> / \<scopes></span><span class="sxs-lookup"><span data-stu-id="03e4a-103">\<add> of \<scopes></span></span>

<span data-ttu-id="03e4a-104">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek bir özel kapsam URI 'Si ekler.</span><span class="sxs-lookup"><span data-stu-id="03e4a-104">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="03e4a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="03e4a-105">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03e4a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="03e4a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="03e4a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03e4a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03e4a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="03e4a-108">Attributes</span></span>  
  
|<span data-ttu-id="03e4a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="03e4a-109">Attribute</span></span>|<span data-ttu-id="03e4a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03e4a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03e4a-111">scope</span><span class="sxs-lookup"><span data-stu-id="03e4a-111">scope</span></span>|<span data-ttu-id="03e4a-112">Uç nokta için hizmet bulmaya yönelik eşleştirme ölçütlerinde kullanılabilecek kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="03e4a-112">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03e4a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="03e4a-113">Child Elements</span></span>  

 <span data-ttu-id="03e4a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="03e4a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03e4a-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="03e4a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="03e4a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="03e4a-116">Element</span></span>|<span data-ttu-id="03e4a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03e4a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="03e4a-118">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="03e4a-118">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03e4a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03e4a-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
