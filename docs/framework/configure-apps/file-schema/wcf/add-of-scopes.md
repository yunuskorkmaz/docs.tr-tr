---
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398300"
---
# <a name="add-of-scopes"></a><span data-ttu-id="f59ca-102">\<\<kapsamların > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="f59ca-102">\<add> of \<scopes></span></span>
<span data-ttu-id="f59ca-103">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek bir özel kapsam URI 'Si ekler.</span><span class="sxs-lookup"><span data-stu-id="f59ca-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="f59ca-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f59ca-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f59ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f59ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f59ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f59ca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="f59ca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kapsamlar >** ](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="f59ca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="f59ca-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="f59ca-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59ca-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f59ca-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f59ca-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f59ca-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f59ca-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f59ca-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f59ca-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f59ca-115">Attributes</span></span>  
  
|<span data-ttu-id="f59ca-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f59ca-116">Attribute</span></span>|<span data-ttu-id="f59ca-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f59ca-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f59ca-118">kapsam</span><span class="sxs-lookup"><span data-stu-id="f59ca-118">scope</span></span>|<span data-ttu-id="f59ca-119">Uç nokta için hizmet bulmaya yönelik eşleştirme ölçütlerinde kullanılabilecek kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="f59ca-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f59ca-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f59ca-120">Child Elements</span></span>  
 <span data-ttu-id="f59ca-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f59ca-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f59ca-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f59ca-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f59ca-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f59ca-123">Element</span></span>|<span data-ttu-id="f59ca-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f59ca-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f59ca-125">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="f59ca-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f59ca-126">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f59ca-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f59ca-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f59ca-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
