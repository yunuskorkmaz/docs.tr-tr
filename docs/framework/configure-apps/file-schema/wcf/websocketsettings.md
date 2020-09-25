---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177858"
---
# \<webSocketSettings>

<span data-ttu-id="3300d-101">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="3300d-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="3300d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="3300d-102">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3300d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3300d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3300d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3300d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3300d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3300d-105">Attributes</span></span>  
  
|<span data-ttu-id="3300d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3300d-106">Attribute</span></span>|<span data-ttu-id="3300d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3300d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3300d-108">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="3300d-108">createNotificationOnConnection</span></span>|<span data-ttu-id="3300d-109">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="3300d-110">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="3300d-110">disablePayloadMasking</span></span>|<span data-ttu-id="3300d-111">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="3300d-112">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="3300d-112">keepAliveInterval</span></span>|<span data-ttu-id="3300d-113">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="3300d-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="3300d-114">maxPendingConnections</span></span>|<span data-ttu-id="3300d-115">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="3300d-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="3300d-116">receiveBufferSize</span></span>|<span data-ttu-id="3300d-117">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="3300d-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="3300d-118">sendBufferSize</span></span>|<span data-ttu-id="3300d-119">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="3300d-120">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="3300d-120">subProtocol</span></span>|<span data-ttu-id="3300d-121">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="3300d-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="3300d-122">transportUsage</span></span>|<span data-ttu-id="3300d-123">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3300d-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="3300d-124">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="3300d-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="3300d-125">Değer</span><span class="sxs-lookup"><span data-stu-id="3300d-125">Value</span></span>|<span data-ttu-id="3300d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3300d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3300d-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="3300d-127">WhenDuplex</span></span>|<span data-ttu-id="3300d-128">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="3300d-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="3300d-129">Her zaman</span><span class="sxs-lookup"><span data-stu-id="3300d-129">Always</span></span>|<span data-ttu-id="3300d-130">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="3300d-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="3300d-131">Asla</span><span class="sxs-lookup"><span data-stu-id="3300d-131">Never</span></span>|<span data-ttu-id="3300d-132">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3300d-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3300d-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3300d-133">Child Elements</span></span>  

 <span data-ttu-id="3300d-134">Yok</span><span class="sxs-lookup"><span data-stu-id="3300d-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3300d-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3300d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3300d-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3300d-136">Element</span></span>|<span data-ttu-id="3300d-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3300d-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="3300d-138">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="3300d-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3300d-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="3300d-139">Example</span></span>  

 <span data-ttu-id="3300d-140">Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir \<webSocketSettings> .</span><span class="sxs-lookup"><span data-stu-id="3300d-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="3300d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3300d-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="3300d-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3300d-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3300d-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3300d-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3300d-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3300d-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
