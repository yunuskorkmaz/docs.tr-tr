---
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 1f5b5ea621614880286181c7584863ea024b3d04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149016"
---
# <a name="add-of-scopes"></a><span data-ttu-id="f2f54-102">\<add> / \<scopes></span><span class="sxs-lookup"><span data-stu-id="f2f54-102">\<add> of \<scopes></span></span>

<span data-ttu-id="f2f54-103">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek bir özel kapsam URI 'Si ekler.</span><span class="sxs-lookup"><span data-stu-id="f2f54-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f2f54-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2f54-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f54-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f54-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f2f54-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2f54-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f54-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2f54-107">Attributes</span></span>  
  
|<span data-ttu-id="f2f54-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2f54-108">Attribute</span></span>|<span data-ttu-id="f2f54-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f54-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2f54-110">scope</span><span class="sxs-lookup"><span data-stu-id="f2f54-110">scope</span></span>|<span data-ttu-id="f2f54-111">Uç nokta için hizmet bulmaya yönelik eşleştirme ölçütlerinde kullanılabilecek kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="f2f54-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2f54-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f54-112">Child Elements</span></span>  

 <span data-ttu-id="f2f54-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2f54-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f54-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f54-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f54-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2f54-115">Element</span></span>|<span data-ttu-id="f2f54-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f54-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="f2f54-117">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f54-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2f54-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f54-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
