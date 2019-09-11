---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855444"
---
# <a name="contracttypenames"></a><span data-ttu-id="0274e-101">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="0274e-101">\<contractTypeNames></span></span>
<span data-ttu-id="0274e-102">Aranan hizmetlerin sözleşme adları ve genellikle bir hizmet ararken kullanılan ölçütler olan anlaşma türü adlarının listesini belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="0274e-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="0274e-103">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="0274e-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="0274e-104">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0274e-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="0274e-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0274e-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0274e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="0274e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="0274e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="0274e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="0274e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="0274e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<findCriteria >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="0274e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="0274e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<contractTypeNames >**</span><span class="sxs-lookup"><span data-stu-id="0274e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0274e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0274e-113">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0274e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0274e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="0274e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0274e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0274e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0274e-116">Attributes</span></span>  
 <span data-ttu-id="0274e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="0274e-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0274e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0274e-118">Child Elements</span></span>  
  
|<span data-ttu-id="0274e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0274e-119">Element</span></span>|<span data-ttu-id="0274e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0274e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0274e-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="0274e-121">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="0274e-122">Anlaşma türü adı, genellikle bir hizmeti ararken kullanılan ölçüt kümesini ifade eden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0274e-122">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0274e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0274e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0274e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0274e-124">Element</span></span>|<span data-ttu-id="0274e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0274e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0274e-126">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="0274e-126">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="0274e-127">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0274e-127">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="0274e-128">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0274e-128">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0274e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0274e-129">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
