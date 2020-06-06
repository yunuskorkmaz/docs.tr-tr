---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400565"
---
# \<callbackDebug>
<span data-ttu-id="f67d1-101">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f67d1-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="f67d1-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f67d1-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="f67d1-103">Tür</span><span class="sxs-lookup"><span data-stu-id="f67d1-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f67d1-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f67d1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f67d1-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f67d1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f67d1-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f67d1-106">Attributes</span></span>  
  
|<span data-ttu-id="f67d1-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f67d1-107">Attribute</span></span>|<span data-ttu-id="f67d1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f67d1-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="f67d1-109">İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f67d1-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="f67d1-110">Bu özniteliği programlı olarak ayarlarsanız `true` , hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f67d1-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="f67d1-111">**Dikkat:**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f67d1-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="f67d1-112">Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f67d1-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f67d1-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f67d1-113">Child Elements</span></span>  
 <span data-ttu-id="f67d1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f67d1-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f67d1-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f67d1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f67d1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f67d1-116">Element</span></span>|<span data-ttu-id="f67d1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f67d1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f67d1-118">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f67d1-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f67d1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f67d1-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
