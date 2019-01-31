---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 62ce1bc179c7215d4988e4c6bda08025c3d3e5de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286318"
---
# <a name="callbackdebug"></a><span data-ttu-id="aa4a7-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="aa4a7-101">\<callbackDebug></span></span>
<span data-ttu-id="aa4a7-102">Bir Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="aa4a7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aa4a7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa4a7-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="aa4a7-104">\<behaviors></span></span>  
<span data-ttu-id="aa4a7-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="aa4a7-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="aa4a7-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="aa4a7-106">\<behavior></span></span>  
<span data-ttu-id="aa4a7-107">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="aa4a7-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa4a7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa4a7-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="aa4a7-109">Tür</span><span class="sxs-lookup"><span data-stu-id="aa4a7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa4a7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa4a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aa4a7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa4a7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa4a7-112">Attributes</span></span>  
  
|<span data-ttu-id="aa4a7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa4a7-113">Attribute</span></span>|<span data-ttu-id="aa4a7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa4a7-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="aa4a7-115">İstemci geri çağırma nesnelerinin SOAP hataları içerisinde yönetilen özel durum bilgilerini hizmete döndürüp belirtir bir değeri.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="aa4a7-116">Bu öznitelik ayarlanırsa verilen `true` programlı olarak hata ayıklama amacıyla yeniden hizmetine istemci geri çağırma nesnesinde yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="aa4a7-117">**Dikkat:**  İstemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="aa4a7-118">Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa4a7-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa4a7-119">Child Elements</span></span>  
 <span data-ttu-id="aa4a7-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa4a7-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa4a7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="aa4a7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa4a7-122">Element</span></span>|<span data-ttu-id="aa4a7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa4a7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa4a7-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="aa4a7-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="aa4a7-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa4a7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa4a7-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
