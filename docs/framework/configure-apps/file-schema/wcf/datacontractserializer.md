---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400442"
---
# <a name="datacontractserializer"></a><span data-ttu-id="62340-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="62340-102">dataContractSerializer</span></span>
<span data-ttu-id="62340-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="62340-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="62340-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62340-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62340-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62340-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62340-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62340-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="62340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="62340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="62340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="62340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62340-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62340-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62340-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62340-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62340-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62340-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62340-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62340-113">Attributes</span></span>  
  
|<span data-ttu-id="62340-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="62340-114">Element</span></span>|<span data-ttu-id="62340-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62340-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62340-116">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="62340-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="62340-117">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğunda, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="62340-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="62340-118">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="62340-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="62340-119">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="62340-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62340-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62340-120">Child Elements</span></span>  
 <span data-ttu-id="62340-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="62340-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62340-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62340-122">Parent Elements</span></span>  
  
|<span data-ttu-id="62340-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="62340-123">Element</span></span>|<span data-ttu-id="62340-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62340-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62340-125">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="62340-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="62340-126">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62340-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62340-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62340-127">Remarks</span></span>  
 <span data-ttu-id="62340-128">Bilinen türler hakkında daha fazla bilgi için belgelerebakın.<xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="62340-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="62340-129">Davranış öğesi (varsa) her zaman yapılandırma dosyasındaki `<enableWebScript>` davranış öğesinden önce görünmelidir. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="62340-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="62340-130">Aksi takdirde, ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="62340-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62340-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62340-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="62340-132">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="62340-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="62340-133">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="62340-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
