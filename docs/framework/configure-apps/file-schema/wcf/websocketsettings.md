---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940316"
---
# <a name="websocketsettings"></a><span data-ttu-id="5c8c7-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="5c8c7-101">\<webSocketSettings></span></span>
<span data-ttu-id="5c8c7-102">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="5c8c7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5c8c7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c8c7-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5c8c7-104">\<bindings></span></span>  
<span data-ttu-id="5c8c7-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5c8c7-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8c7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c8c7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c8c7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8c7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5c8c7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c8c7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c8c7-109">Attributes</span></span>  
  
|<span data-ttu-id="5c8c7-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c8c7-110">Attribute</span></span>|<span data-ttu-id="5c8c7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c8c7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c8c7-112">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="5c8c7-112">createNotificationOnConnection</span></span>|<span data-ttu-id="5c8c7-113">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="5c8c7-114">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="5c8c7-114">disablePayloadMasking</span></span>|<span data-ttu-id="5c8c7-115">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="5c8c7-116">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="5c8c7-116">keepAliveInterval</span></span>|<span data-ttu-id="5c8c7-117">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="5c8c7-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="5c8c7-118">maxPendingConnections</span></span>|<span data-ttu-id="5c8c7-119">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="5c8c7-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="5c8c7-120">receiveBufferSize</span></span>|<span data-ttu-id="5c8c7-121">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="5c8c7-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="5c8c7-122">sendBufferSize</span></span>|<span data-ttu-id="5c8c7-123">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="5c8c7-124">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="5c8c7-124">subProtocol</span></span>|<span data-ttu-id="5c8c7-125">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="5c8c7-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="5c8c7-126">transportUsage</span></span>|<span data-ttu-id="5c8c7-127">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="5c8c7-128">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="5c8c7-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="5c8c7-129">Değer</span><span class="sxs-lookup"><span data-stu-id="5c8c7-129">Value</span></span>|<span data-ttu-id="5c8c7-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c8c7-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c8c7-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="5c8c7-131">WhenDuplex</span></span>|<span data-ttu-id="5c8c7-132">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="5c8c7-133">Her zaman</span><span class="sxs-lookup"><span data-stu-id="5c8c7-133">Always</span></span>|<span data-ttu-id="5c8c7-134">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="5c8c7-135">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="5c8c7-135">Never</span></span>|<span data-ttu-id="5c8c7-136">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c8c7-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8c7-137">Child Elements</span></span>  
 <span data-ttu-id="5c8c7-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c8c7-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8c7-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5c8c7-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c8c7-140">Element</span></span>|<span data-ttu-id="5c8c7-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c8c7-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c8c7-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5c8c7-142">\<netHttpBinding></span></span>|<span data-ttu-id="5c8c7-143">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="5c8c7-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5c8c7-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c8c7-144">Example</span></span>  
 <span data-ttu-id="5c8c7-145">Aşağıdaki örnek, \<WebSocketSettings > öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c8c7-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c8c7-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="5c8c7-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5c8c7-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c8c7-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5c8c7-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c8c7-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5c8c7-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5c8c7-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5c8c7-150">\<binding></span></span>](../../../misc/binding.md)
