---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: a024ca89bd766681f25b992f1d2c66a92e3b31b7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150207"
---
# <a name="datacontractserializer"></a><span data-ttu-id="6fa4f-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6fa4f-102">dataContractSerializer</span></span>
<span data-ttu-id="6fa4f-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6fa4f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6fa4f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6fa4f-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6fa4f-105">\<behaviors></span></span>  
<span data-ttu-id="6fa4f-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6fa4f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6fa4f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6fa4f-107">\<behavior></span></span>  
<span data-ttu-id="6fa4f-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6fa4f-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa4f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fa4f-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fa4f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fa4f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6fa4f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fa4f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6fa4f-112">Attributes</span></span>  
  
|<span data-ttu-id="6fa4f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fa4f-113">Element</span></span>|<span data-ttu-id="6fa4f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa4f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6fa4f-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6fa4f-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6fa4f-116">Bunu edilirken uç noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="6fa4f-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6fa4f-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6fa4f-118">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fa4f-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fa4f-119">Child Elements</span></span>  
 <span data-ttu-id="6fa4f-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fa4f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6fa4f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6fa4f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fa4f-122">Element</span></span>|<span data-ttu-id="6fa4f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa4f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fa4f-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6fa4f-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6fa4f-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa4f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fa4f-126">Remarks</span></span>  
 <span data-ttu-id="6fa4f-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6fa4f-128">`<dataContractSerializer>` Davranış öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` yapılandırma dosyasındaki davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="6fa4f-129">Aksi takdirde, sonuçta ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa4f-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa4f-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="6fa4f-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="6fa4f-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="6fa4f-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6fa4f-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
