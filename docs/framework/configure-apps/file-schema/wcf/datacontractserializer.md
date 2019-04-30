---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8ba16d9cc30b07d3e6b0924e6013ec01443867d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704134"
---
# <a name="datacontractserializer"></a><span data-ttu-id="6e535-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6e535-102">dataContractSerializer</span></span>
<span data-ttu-id="6e535-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6e535-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6e535-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6e535-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e535-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6e535-105">\<behaviors></span></span>  
<span data-ttu-id="6e535-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6e535-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6e535-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6e535-107">\<behavior></span></span>  
<span data-ttu-id="6e535-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6e535-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e535-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e535-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e535-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e535-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e535-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e535-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e535-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e535-112">Attributes</span></span>  
  
|<span data-ttu-id="6e535-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e535-113">Element</span></span>|<span data-ttu-id="6e535-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e535-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e535-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6e535-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6e535-116">Bunu edilirken uç noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="6e535-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="6e535-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6e535-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6e535-118">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6e535-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e535-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e535-119">Child Elements</span></span>  
 <span data-ttu-id="6e535-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e535-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e535-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e535-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6e535-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e535-122">Element</span></span>|<span data-ttu-id="6e535-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e535-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e535-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6e535-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6e535-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e535-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e535-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e535-126">Remarks</span></span>  
 <span data-ttu-id="6e535-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6e535-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6e535-128">`<dataContractSerializer>` Davranış öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` yapılandırma dosyasındaki davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e535-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="6e535-129">Aksi takdirde, sonuçta ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6e535-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e535-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e535-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="6e535-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="6e535-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="6e535-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6e535-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
