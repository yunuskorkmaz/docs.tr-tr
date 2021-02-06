---
description: 'Hakkında daha fazla bilgi edinin: <callbackDebug>'
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 911d738764baa800831c19f4e5d181118d1d3e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639217"
---
# \<callbackDebug>

<span data-ttu-id="c4c67-102">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4c67-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="c4c67-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4c67-103">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="c4c67-104">Tür</span><span class="sxs-lookup"><span data-stu-id="c4c67-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4c67-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c67-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c4c67-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4c67-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4c67-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4c67-107">Attributes</span></span>  
  
|<span data-ttu-id="c4c67-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4c67-108">Attribute</span></span>|<span data-ttu-id="c4c67-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c67-109">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="c4c67-110">İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c4c67-110">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="c4c67-111">Bu özniteliği programlı olarak ayarlarsanız `true` , hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4c67-111">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="c4c67-112">**Dikkat:**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c4c67-112">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="c4c67-113">Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c4c67-113">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4c67-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c67-114">Child Elements</span></span>  

 <span data-ttu-id="c4c67-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4c67-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4c67-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c67-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c4c67-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4c67-117">Element</span></span>|<span data-ttu-id="c4c67-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c67-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c4c67-119">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4c67-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4c67-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c67-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
