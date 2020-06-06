---
title: <add> / <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850535"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="78cdf-102">\<add> / \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="78cdf-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="78cdf-103">Aranmakta olan hizmetlerin sözleşme adını ve genellikle bir hizmet ararken kullanılan kriterleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="78cdf-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="78cdf-104">Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmelerle eşleşen hizmet uç noktaları yanıtlanacak.</span><span class="sxs-lookup"><span data-stu-id="78cdf-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="78cdf-105">Windows Communication Foundation (WCF) ' de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="78cdf-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="78cdf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78cdf-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78cdf-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78cdf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="78cdf-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78cdf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78cdf-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78cdf-109">Attributes</span></span>  
  
|<span data-ttu-id="78cdf-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78cdf-110">Attribute</span></span>|<span data-ttu-id="78cdf-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78cdf-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78cdf-112">name</span><span class="sxs-lookup"><span data-stu-id="78cdf-112">name</span></span>|<span data-ttu-id="78cdf-113">Anlaşma türünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="78cdf-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="78cdf-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="78cdf-114">namespace</span></span>|<span data-ttu-id="78cdf-115">Anlaşma türünün ad alanını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="78cdf-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78cdf-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78cdf-116">Child Elements</span></span>  
 <span data-ttu-id="78cdf-117">Yok</span><span class="sxs-lookup"><span data-stu-id="78cdf-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78cdf-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78cdf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="78cdf-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="78cdf-119">Element</span></span>|<span data-ttu-id="78cdf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78cdf-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="78cdf-121">Bir anlaşma türü adı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="78cdf-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78cdf-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78cdf-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
