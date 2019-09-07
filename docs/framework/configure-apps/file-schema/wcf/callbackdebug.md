---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400565"
---
# <a name="callbackdebug"></a><span data-ttu-id="58277-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="58277-101">\<callbackDebug></span></span>
<span data-ttu-id="58277-102">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="58277-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
<span data-ttu-id="58277-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58277-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58277-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="58277-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="58277-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58277-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="58277-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58277-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="58277-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58277-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="58277-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackDebug >**</span><span class="sxs-lookup"><span data-stu-id="58277-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58277-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58277-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="58277-110">Tür</span><span class="sxs-lookup"><span data-stu-id="58277-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58277-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="58277-111">Attributes and Elements</span></span>  
 <span data-ttu-id="58277-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58277-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58277-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="58277-113">Attributes</span></span>  
  
|<span data-ttu-id="58277-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="58277-114">Attribute</span></span>|<span data-ttu-id="58277-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58277-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="58277-116">İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="58277-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="58277-117">Bu özniteliği `true` programlı olarak ayarlarsanız, hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58277-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="58277-118">**Dikkatli**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="58277-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="58277-119">Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="58277-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58277-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="58277-120">Child Elements</span></span>  
 <span data-ttu-id="58277-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="58277-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58277-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="58277-122">Parent Elements</span></span>  
  
|<span data-ttu-id="58277-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="58277-123">Element</span></span>|<span data-ttu-id="58277-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58277-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58277-125">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="58277-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="58277-126">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="58277-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58277-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58277-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
