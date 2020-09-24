---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0e4cbc50c25d4fa1f67f283f2b52d4b174428cd3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153930"
---
# <a name="datacontractserializer"></a><span data-ttu-id="69e71-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="69e71-102">dataContractSerializer</span></span>

<span data-ttu-id="69e71-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="69e71-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="69e71-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="69e71-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e71-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69e71-105">Attributes and Elements</span></span>  

 <span data-ttu-id="69e71-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69e71-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e71-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69e71-107">Attributes</span></span>  
  
|<span data-ttu-id="69e71-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="69e71-108">Element</span></span>|<span data-ttu-id="69e71-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69e71-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69e71-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="69e71-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="69e71-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğunda, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="69e71-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="69e71-112">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="69e71-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="69e71-113">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="69e71-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69e71-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69e71-114">Child Elements</span></span>  

 <span data-ttu-id="69e71-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="69e71-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69e71-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69e71-116">Parent Elements</span></span>  
  
|<span data-ttu-id="69e71-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="69e71-117">Element</span></span>|<span data-ttu-id="69e71-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69e71-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="69e71-119">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="69e71-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69e71-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69e71-120">Remarks</span></span>  

 <span data-ttu-id="69e71-121"><xref:System.Runtime.Serialization.DataContractSerializer>Bilinen türler hakkında daha fazla bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="69e71-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="69e71-122">`<dataContractSerializer>`Davranış öğesi (varsa) her zaman `<enableWebScript>` yapılandırma dosyasındaki davranış öğesinden önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="69e71-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="69e71-123">Aksi takdirde, ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="69e71-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e71-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69e71-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="69e71-125">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="69e71-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="69e71-126">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="69e71-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
