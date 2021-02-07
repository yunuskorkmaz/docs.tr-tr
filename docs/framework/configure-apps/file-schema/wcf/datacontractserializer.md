---
description: 'Daha fazla bilgi edinin: dataContractSerializer'
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 5dee59ba97a1632c142179aee79058dd3ce8c349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754413"
---
# <a name="datacontractserializer"></a><span data-ttu-id="1bb52-103">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="1bb52-103">dataContractSerializer</span></span>

<span data-ttu-id="1bb52-104">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="1bb52-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="1bb52-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1bb52-105">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bb52-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb52-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1bb52-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bb52-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bb52-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bb52-108">Attributes</span></span>  
  
|<span data-ttu-id="1bb52-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bb52-109">Element</span></span>|<span data-ttu-id="1bb52-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bb52-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bb52-111">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1bb52-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="1bb52-112">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğunda, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1bb52-112">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="1bb52-113">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1bb52-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="1bb52-114">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1bb52-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bb52-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb52-115">Child Elements</span></span>  

 <span data-ttu-id="1bb52-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="1bb52-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bb52-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb52-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1bb52-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bb52-118">Element</span></span>|<span data-ttu-id="1bb52-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bb52-119">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1bb52-120">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bb52-120">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bb52-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bb52-121">Remarks</span></span>  

 <span data-ttu-id="1bb52-122"><xref:System.Runtime.Serialization.DataContractSerializer>Bilinen türler hakkında daha fazla bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="1bb52-122">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1bb52-123">`<dataContractSerializer>`Davranış öğesi (varsa) her zaman `<enableWebScript>` yapılandırma dosyasındaki davranış öğesinden önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1bb52-123">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="1bb52-124">Aksi takdirde, ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="1bb52-124">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb52-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bb52-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="1bb52-126">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="1bb52-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="1bb52-127">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1bb52-127">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
