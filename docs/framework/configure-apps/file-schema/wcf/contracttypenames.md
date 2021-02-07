---
description: 'Hakkında daha fazla bilgi edinin: <contractTypeNames>'
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 7521b16c097a8df75819654525c0663124a1ebd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754452"
---
# \<contractTypeNames>

<span data-ttu-id="a0e3f-102">Aranan hizmetlerin sözleşme adları ve genellikle bir hizmet ararken kullanılan ölçütler olan anlaşma türü adlarının listesini belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="a0e3f-103">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="a0e3f-104">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="a0e3f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0e3f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0e3f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e3f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a0e3f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0e3f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0e3f-108">Attributes</span></span>  

 <span data-ttu-id="a0e3f-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0e3f-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e3f-110">Child Elements</span></span>  
  
|<span data-ttu-id="a0e3f-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0e3f-111">Element</span></span>|<span data-ttu-id="a0e3f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e3f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="a0e3f-113">Anlaşma türü adı, genellikle bir hizmeti ararken kullanılan ölçüt kümesini ifade eden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-113">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0e3f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e3f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a0e3f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0e3f-115">Element</span></span>|<span data-ttu-id="a0e3f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e3f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="a0e3f-117">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a0e3f-118">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0e3f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
