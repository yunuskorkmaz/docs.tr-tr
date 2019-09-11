---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850535"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="2796c-102">\<\<ContractTypeNames > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="2796c-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="2796c-103">Aranmakta olan hizmetlerin sözleşme adını ve genellikle bir hizmet ararken kullanılan kriterleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2796c-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="2796c-104">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="2796c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="2796c-105">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2796c-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="2796c-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2796c-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2796c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="2796c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="2796c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="2796c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="2796c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="2796c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<findCriteria >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="2796c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<contractTypeNames >** ](contracttypenames.md)</span><span class="sxs-lookup"><span data-stu-id="2796c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)</span></span>\
<span data-ttu-id="2796c-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="2796c-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2796c-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2796c-115">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2796c-116">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2796c-116">Attributes and Elements</span></span>  
 <span data-ttu-id="2796c-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2796c-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2796c-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2796c-118">Attributes</span></span>  
  
|<span data-ttu-id="2796c-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2796c-119">Attribute</span></span>|<span data-ttu-id="2796c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2796c-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2796c-121">name</span><span class="sxs-lookup"><span data-stu-id="2796c-121">name</span></span>|<span data-ttu-id="2796c-122">Anlaşma türünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2796c-122">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="2796c-123">ad alanı</span><span class="sxs-lookup"><span data-stu-id="2796c-123">namespace</span></span>|<span data-ttu-id="2796c-124">Anlaşma türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2796c-124">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2796c-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2796c-125">Child Elements</span></span>  
 <span data-ttu-id="2796c-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="2796c-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2796c-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2796c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="2796c-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="2796c-128">Element</span></span>|<span data-ttu-id="2796c-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2796c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2796c-130">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="2796c-130">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="2796c-131">Bir anlaşma türü adı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2796c-131">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2796c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2796c-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
