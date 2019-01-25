---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 1aa292a3fe06af9cf1dbc53ebf5bbdf9841be8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687381"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="08a71-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="08a71-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="08a71-103">Bir Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08a71-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="08a71-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="08a71-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="08a71-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="08a71-105">\<behaviors></span></span>  
<span data-ttu-id="08a71-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="08a71-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="08a71-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="08a71-107">\<behavior></span></span>  
<span data-ttu-id="08a71-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="08a71-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a71-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08a71-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="08a71-110">Tür</span><span class="sxs-lookup"><span data-stu-id="08a71-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08a71-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08a71-111">Attributes and Elements</span></span>  
 <span data-ttu-id="08a71-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08a71-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08a71-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08a71-113">Attributes</span></span>  
  
|<span data-ttu-id="08a71-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08a71-114">Attribute</span></span>|<span data-ttu-id="08a71-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08a71-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="08a71-116">İstemci geri çağırma nesnelerinin SOAP hataları içerisinde yönetilen özel durum bilgilerini hizmete döndürüp belirtir bir değeri.</span><span class="sxs-lookup"><span data-stu-id="08a71-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="08a71-117">Bu öznitelik ayarlanırsa verilen `true` programlı olarak hata ayıklama amacıyla yeniden hizmetine istemci geri çağırma nesnesinde yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08a71-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="08a71-118">**Dikkat:**  İstemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir.</span><span class="sxs-lookup"><span data-stu-id="08a71-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="08a71-119">Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="08a71-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08a71-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08a71-120">Child Elements</span></span>  
 <span data-ttu-id="08a71-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="08a71-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08a71-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08a71-122">Parent Elements</span></span>  
  
|<span data-ttu-id="08a71-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="08a71-123">Element</span></span>|<span data-ttu-id="08a71-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08a71-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08a71-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="08a71-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="08a71-126">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="08a71-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08a71-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a71-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
