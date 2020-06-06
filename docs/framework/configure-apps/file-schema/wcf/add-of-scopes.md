---
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398300"
---
# <a name="add-of-scopes"></a><span data-ttu-id="fd387-102">\<add> / \<scopes></span><span class="sxs-lookup"><span data-stu-id="fd387-102">\<add> of \<scopes></span></span>
<span data-ttu-id="fd387-103">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek bir özel kapsam URI 'Si ekler.</span><span class="sxs-lookup"><span data-stu-id="fd387-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fd387-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd387-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd387-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd387-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd387-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd387-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd387-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd387-107">Attributes</span></span>  
  
|<span data-ttu-id="fd387-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd387-108">Attribute</span></span>|<span data-ttu-id="fd387-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd387-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd387-110">scope</span><span class="sxs-lookup"><span data-stu-id="fd387-110">scope</span></span>|<span data-ttu-id="fd387-111">Uç nokta için hizmet bulmaya yönelik eşleştirme ölçütlerinde kullanılabilecek kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="fd387-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd387-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd387-112">Child Elements</span></span>  
 <span data-ttu-id="fd387-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd387-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd387-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd387-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fd387-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd387-115">Element</span></span>|<span data-ttu-id="fd387-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd387-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="fd387-117">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="fd387-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd387-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd387-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
