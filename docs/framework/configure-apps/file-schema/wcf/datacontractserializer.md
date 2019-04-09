---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8ba16d9cc30b07d3e6b0924e6013ec01443867d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139054"
---
# <a name="datacontractserializer"></a><span data-ttu-id="8e5e0-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="8e5e0-102">dataContractSerializer</span></span>
<span data-ttu-id="8e5e0-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="8e5e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e5e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e5e0-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8e5e0-105">\<behaviors></span></span>  
<span data-ttu-id="8e5e0-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e5e0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8e5e0-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8e5e0-107">\<behavior></span></span>  
<span data-ttu-id="8e5e0-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="8e5e0-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5e0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e5e0-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e5e0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e5e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8e5e0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e5e0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e5e0-112">Attributes</span></span>  
  
|<span data-ttu-id="8e5e0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e5e0-113">Element</span></span>|<span data-ttu-id="8e5e0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e5e0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e5e0-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="8e5e0-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="8e5e0-116">Bunu edilirken uç noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="8e5e0-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="8e5e0-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="8e5e0-118">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e5e0-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e5e0-119">Child Elements</span></span>  
 <span data-ttu-id="8e5e0-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e5e0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e5e0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8e5e0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e5e0-122">Element</span></span>|<span data-ttu-id="8e5e0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e5e0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e5e0-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8e5e0-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e5e0-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e5e0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e5e0-126">Remarks</span></span>  
 <span data-ttu-id="8e5e0-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8e5e0-128">`<dataContractSerializer>` Davranış öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` yapılandırma dosyasındaki davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="8e5e0-129">Aksi takdirde, sonuçta ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5e0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5e0-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="8e5e0-131">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="8e5e0-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="8e5e0-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8e5e0-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
