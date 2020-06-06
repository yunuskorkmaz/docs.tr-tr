---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400442"
---
# <a name="datacontractserializer"></a><span data-ttu-id="c1c39-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c1c39-102">dataContractSerializer</span></span>
<span data-ttu-id="c1c39-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="c1c39-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="c1c39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1c39-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1c39-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1c39-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c1c39-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1c39-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1c39-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1c39-107">Attributes</span></span>  
  
|<span data-ttu-id="c1c39-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1c39-108">Element</span></span>|<span data-ttu-id="c1c39-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c39-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1c39-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c1c39-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="c1c39-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğunda, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c1c39-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="c1c39-112">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c1c39-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="c1c39-113">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c1c39-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1c39-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1c39-114">Child Elements</span></span>  
 <span data-ttu-id="c1c39-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1c39-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1c39-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1c39-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c1c39-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1c39-117">Element</span></span>|<span data-ttu-id="c1c39-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c39-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c1c39-119">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1c39-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1c39-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1c39-120">Remarks</span></span>  
 <span data-ttu-id="c1c39-121"><xref:System.Runtime.Serialization.DataContractSerializer>Bilinen türler hakkında daha fazla bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="c1c39-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c1c39-122">`<dataContractSerializer>`Davranış öğesi (varsa) her zaman `<enableWebScript>` yapılandırma dosyasındaki davranış öğesinden önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="c1c39-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="c1c39-123">Aksi takdirde, ortaya çıkan davranış tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c1c39-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c39-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c39-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="c1c39-125">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c1c39-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="c1c39-126">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c1c39-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
