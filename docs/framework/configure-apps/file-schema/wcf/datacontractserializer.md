---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 7952e6cc4d2fe7eaa77e297a650f7ffbd7aec785
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040938"
---
# <a name="datacontractserializer"></a><span data-ttu-id="109d0-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="109d0-102">dataContractSerializer</span></span>
<span data-ttu-id="109d0-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="109d0-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="109d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="109d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="109d0-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="109d0-105">\<behaviors></span></span>  
<span data-ttu-id="109d0-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="109d0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="109d0-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="109d0-107">\<behavior></span></span>  
<span data-ttu-id="109d0-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="109d0-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109d0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="109d0-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="109d0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="109d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="109d0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="109d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="109d0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="109d0-112">Attributes</span></span>  
  
|<span data-ttu-id="109d0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="109d0-113">Element</span></span>|<span data-ttu-id="109d0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109d0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="109d0-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="109d0-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="109d0-116">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğunda, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="109d0-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="109d0-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="109d0-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="109d0-118">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="109d0-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="109d0-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="109d0-119">Child Elements</span></span>  
 <span data-ttu-id="109d0-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="109d0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="109d0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="109d0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="109d0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="109d0-122">Element</span></span>|<span data-ttu-id="109d0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="109d0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="109d0-124">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="109d0-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="109d0-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="109d0-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="109d0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="109d0-126">Remarks</span></span>  
 <span data-ttu-id="109d0-127">Bilinen türler hakkında daha fazla bilgi için belgelerebakın.<xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="109d0-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="109d0-128">Davranış öğesi (varsa) her zaman yapılandırma dosyasındaki `<enableWebScript>` davranış öğesinden önce görünmelidir. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="109d0-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="109d0-129">Aksi takdirde, ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="109d0-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="109d0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="109d0-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="109d0-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="109d0-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="109d0-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="109d0-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
