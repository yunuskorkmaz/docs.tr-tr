---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855444"
---
# \<contractTypeNames>
<span data-ttu-id="1d8a4-101">Aranan hizmetlerin sözleşme adları ve genellikle bir hizmet ararken kullanılan ölçütler olan anlaşma türü adlarının listesini belirten bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-101">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="1d8a4-102">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-102">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="1d8a4-103">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-103">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="1d8a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d8a4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d8a4-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d8a4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d8a4-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d8a4-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d8a4-107">Attributes</span></span>  
 <span data-ttu-id="1d8a4-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d8a4-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d8a4-109">Child Elements</span></span>  
  
|<span data-ttu-id="1d8a4-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d8a4-110">Element</span></span>|<span data-ttu-id="1d8a4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d8a4-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="1d8a4-112">Anlaşma türü adı, genellikle bir hizmeti ararken kullanılan ölçüt kümesini ifade eden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-112">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d8a4-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d8a4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1d8a4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d8a4-114">Element</span></span>|<span data-ttu-id="1d8a4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d8a4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="1d8a4-116">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-116">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1d8a4-117">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-117">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d8a4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d8a4-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
