---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926316"
---
# <a name="callbackdebug"></a><span data-ttu-id="0fdbe-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-101">\<callbackDebug></span></span>
<span data-ttu-id="0fdbe-102">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="0fdbe-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fdbe-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fdbe-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-104">\<behaviors></span></span>  
<span data-ttu-id="0fdbe-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="0fdbe-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-106">\<behavior></span></span>  
<span data-ttu-id="0fdbe-107">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fdbe-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fdbe-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="0fdbe-109">Tür</span><span class="sxs-lookup"><span data-stu-id="0fdbe-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fdbe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fdbe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fdbe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fdbe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0fdbe-112">Attributes</span></span>  
  
|<span data-ttu-id="0fdbe-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0fdbe-113">Attribute</span></span>|<span data-ttu-id="0fdbe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fdbe-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="0fdbe-115">İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="0fdbe-116">Bu özniteliği `true` programlı olarak ayarlarsanız, hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="0fdbe-117">**Dikkatli**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="0fdbe-118">Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fdbe-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fdbe-119">Child Elements</span></span>  
 <span data-ttu-id="0fdbe-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fdbe-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fdbe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0fdbe-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0fdbe-122">Element</span></span>|<span data-ttu-id="0fdbe-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fdbe-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fdbe-124">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0fdbe-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fdbe-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
