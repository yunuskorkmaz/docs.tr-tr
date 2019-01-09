---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 5bd2356c3bb798e948341cb3c4ba504ac886ed44
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145087"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="4fcbb-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="4fcbb-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="4fcbb-103">Bir Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="4fcbb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4fcbb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4fcbb-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4fcbb-105">\<behaviors></span></span>  
<span data-ttu-id="4fcbb-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4fcbb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4fcbb-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4fcbb-107">\<behavior></span></span>  
<span data-ttu-id="4fcbb-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="4fcbb-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcbb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fcbb-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="4fcbb-110">Tür</span><span class="sxs-lookup"><span data-stu-id="4fcbb-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fcbb-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fcbb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4fcbb-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fcbb-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fcbb-113">Attributes</span></span>  
  
|<span data-ttu-id="4fcbb-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4fcbb-114">Attribute</span></span>|<span data-ttu-id="4fcbb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fcbb-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="4fcbb-116">İstemci geri çağırma nesnelerinin SOAP hataları içerisinde yönetilen özel durum bilgilerini hizmete döndürüp belirtir bir değeri.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="4fcbb-117">Bu öznitelik ayarlanırsa verilen `true` programlı olarak hata ayıklama amacıyla yeniden hizmetine istemci geri çağırma nesnesinde yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="4fcbb-118">**Dikkat:**  İstemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="4fcbb-119">Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fcbb-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fcbb-120">Child Elements</span></span>  
 <span data-ttu-id="4fcbb-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fcbb-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fcbb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4fcbb-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fcbb-123">Element</span></span>|<span data-ttu-id="4fcbb-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fcbb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fcbb-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4fcbb-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4fcbb-126">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fcbb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fcbb-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
