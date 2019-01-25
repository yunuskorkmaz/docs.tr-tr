---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 933d49092c392fa293468d546e521bf7ed858376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539850"
---
# <a name="datacontractserializer"></a><span data-ttu-id="9b57e-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="9b57e-102">dataContractSerializer</span></span>
<span data-ttu-id="9b57e-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9b57e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="9b57e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9b57e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9b57e-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9b57e-105">\<behaviors></span></span>  
<span data-ttu-id="9b57e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9b57e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9b57e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9b57e-107">\<behavior></span></span>  
<span data-ttu-id="9b57e-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9b57e-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b57e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b57e-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b57e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b57e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b57e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b57e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b57e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9b57e-112">Attributes</span></span>  
  
|<span data-ttu-id="9b57e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b57e-113">Element</span></span>|<span data-ttu-id="9b57e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b57e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b57e-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="9b57e-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="9b57e-116">Bunu edilirken uç noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="9b57e-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="9b57e-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="9b57e-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="9b57e-118">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9b57e-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b57e-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b57e-119">Child Elements</span></span>  
 <span data-ttu-id="9b57e-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="9b57e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b57e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b57e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9b57e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b57e-122">Element</span></span>|<span data-ttu-id="9b57e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b57e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b57e-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9b57e-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9b57e-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b57e-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b57e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b57e-126">Remarks</span></span>  
 <span data-ttu-id="9b57e-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9b57e-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="9b57e-128">`<dataContractSerializer>` Davranış öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` yapılandırma dosyasındaki davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="9b57e-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="9b57e-129">Aksi takdirde, sonuçta ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="9b57e-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b57e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b57e-130">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="9b57e-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="9b57e-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="9b57e-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9b57e-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
