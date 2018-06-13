---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 2103c32112b6c5554d7b510f486d4cbb1349f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747962"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="55051-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="55051-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="55051-103">Hizmet için bir Windows Communication Foundation (WCF) geri çağırma nesnesi hata ayıklama belirtir.</span><span class="sxs-lookup"><span data-stu-id="55051-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="55051-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="55051-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="55051-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="55051-105">\<behaviors></span></span>  
<span data-ttu-id="55051-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="55051-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="55051-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="55051-107">\<behavior></span></span>  
<span data-ttu-id="55051-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="55051-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55051-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55051-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="55051-110">Tür</span><span class="sxs-lookup"><span data-stu-id="55051-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55051-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55051-111">Attributes and Elements</span></span>  
 <span data-ttu-id="55051-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55051-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55051-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55051-113">Attributes</span></span>  
  
|<span data-ttu-id="55051-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55051-114">Attribute</span></span>|<span data-ttu-id="55051-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55051-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="55051-116">İstemci geri araması nesneleri yönetilen özel durum bilgilerini SOAP hataları hizmete geri döndürme olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="55051-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="55051-117">Bu öznitelik ayarlanırsa, `true` tekrar hata ayıklama amacıyla hizmet için bir istemci geri çağırma nesnesindeki yönetilen özel durum bilgi akışını programlı olarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55051-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="55051-118">**Dikkat:** döndürme istemcilere yönetilen özel durum bilgileri, bir güvenlik riski olabilir.</span><span class="sxs-lookup"><span data-stu-id="55051-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="55051-119">Özel durum ayrıntıları yetkisiz istemcileri tarafından kullanılan iç hizmet uygulaması hakkında bilgi kullanıma olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="55051-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55051-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55051-120">Child Elements</span></span>  
 <span data-ttu-id="55051-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="55051-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55051-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55051-122">Parent Elements</span></span>  
  
|<span data-ttu-id="55051-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="55051-123">Element</span></span>|<span data-ttu-id="55051-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55051-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55051-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="55051-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="55051-126">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55051-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55051-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55051-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
