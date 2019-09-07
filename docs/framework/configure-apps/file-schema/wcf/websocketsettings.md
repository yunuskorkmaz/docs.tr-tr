---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399142"
---
# <a name="websocketsettings"></a><span data-ttu-id="6a7a1-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="6a7a1-101">\<webSocketSettings></span></span>
<span data-ttu-id="6a7a1-102">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="6a7a1-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6a7a1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6a7a1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6a7a1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6a7a1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6a7a1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6a7a1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6a7a1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="6a7a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="6a7a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6a7a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="6a7a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7a1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a7a1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a7a1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a7a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6a7a1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a7a1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a7a1-112">Attributes</span></span>  
  
|<span data-ttu-id="6a7a1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a7a1-113">Attribute</span></span>|<span data-ttu-id="6a7a1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a7a1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a7a1-115">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="6a7a1-115">createNotificationOnConnection</span></span>|<span data-ttu-id="6a7a1-116">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="6a7a1-117">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="6a7a1-117">disablePayloadMasking</span></span>|<span data-ttu-id="6a7a1-118">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="6a7a1-119">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="6a7a1-119">keepAliveInterval</span></span>|<span data-ttu-id="6a7a1-120">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="6a7a1-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="6a7a1-121">maxPendingConnections</span></span>|<span data-ttu-id="6a7a1-122">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="6a7a1-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6a7a1-123">receiveBufferSize</span></span>|<span data-ttu-id="6a7a1-124">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="6a7a1-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="6a7a1-125">sendBufferSize</span></span>|<span data-ttu-id="6a7a1-126">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="6a7a1-127">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="6a7a1-127">subProtocol</span></span>|<span data-ttu-id="6a7a1-128">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="6a7a1-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="6a7a1-129">transportUsage</span></span>|<span data-ttu-id="6a7a1-130">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="6a7a1-131">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="6a7a1-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="6a7a1-132">Değer</span><span class="sxs-lookup"><span data-stu-id="6a7a1-132">Value</span></span>|<span data-ttu-id="6a7a1-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a7a1-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a7a1-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="6a7a1-134">WhenDuplex</span></span>|<span data-ttu-id="6a7a1-135">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="6a7a1-136">Her zaman</span><span class="sxs-lookup"><span data-stu-id="6a7a1-136">Always</span></span>|<span data-ttu-id="6a7a1-137">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="6a7a1-138">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="6a7a1-138">Never</span></span>|<span data-ttu-id="6a7a1-139">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a7a1-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a7a1-140">Child Elements</span></span>  
 <span data-ttu-id="6a7a1-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a7a1-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a7a1-142">Parent Elements</span></span>  
  
|<span data-ttu-id="6a7a1-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a7a1-143">Element</span></span>|<span data-ttu-id="6a7a1-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a7a1-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a7a1-145">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6a7a1-145">\<netHttpBinding></span></span>|<span data-ttu-id="6a7a1-146">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="6a7a1-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a7a1-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a7a1-147">Example</span></span>  
 <span data-ttu-id="6a7a1-148">Aşağıdaki örnek, \<WebSocketSettings > öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a7a1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a7a1-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6a7a1-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6a7a1-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a7a1-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6a7a1-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6a7a1-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6a7a1-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6a7a1-153">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6a7a1-153">\<binding></span></span>](../../../misc/binding.md)
