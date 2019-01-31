---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 298bf27b171772bb039b11b5e5de70e7d45b061d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258463"
---
# <a name="websocketsettings"></a><span data-ttu-id="335e2-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="335e2-101">\<webSocketSettings></span></span>
<span data-ttu-id="335e2-102">Web yuvası ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="335e2-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="335e2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="335e2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="335e2-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="335e2-104">\<bindings></span></span>  
<span data-ttu-id="335e2-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="335e2-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335e2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="335e2-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="335e2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="335e2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="335e2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="335e2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="335e2-109">Attributes</span></span>  
  
|<span data-ttu-id="335e2-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="335e2-110">Attribute</span></span>|<span data-ttu-id="335e2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335e2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="335e2-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="335e2-112">createNotificationOnConnection</span></span>|<span data-ttu-id="335e2-113">Bağlantı kurulduğunda bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="335e2-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="335e2-114">disablePayloadMasking</span></span>|<span data-ttu-id="335e2-115">Web yuvası maskeleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="335e2-116">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="335e2-116">keepAliveInterval</span></span>|<span data-ttu-id="335e2-117">Canlı tutma aralığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="335e2-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="335e2-118">maxPendingConnections</span></span>|<span data-ttu-id="335e2-119">Gönderme hizmeti bekleyen bağlantılar maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="335e2-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="335e2-120">receiveBufferSize</span></span>|<span data-ttu-id="335e2-121">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="335e2-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="335e2-122">sendBufferSize</span></span>|<span data-ttu-id="335e2-123">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="335e2-124">geçersizdir</span><span class="sxs-lookup"><span data-stu-id="335e2-124">subProtocol</span></span>|<span data-ttu-id="335e2-125">Web yuvası subprotocol'üne belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="335e2-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="335e2-126">transportUsage</span></span>|<span data-ttu-id="335e2-127">Web yuvaları kullanma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e2-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="335e2-128">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="335e2-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="335e2-129">Değer</span><span class="sxs-lookup"><span data-stu-id="335e2-129">Value</span></span>|<span data-ttu-id="335e2-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335e2-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="335e2-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="335e2-131">WhenDuplex</span></span>|<span data-ttu-id="335e2-132">Web yuvası Protokolü anlaşması çift yönlü olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="335e2-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="335e2-133">Her zaman</span><span class="sxs-lookup"><span data-stu-id="335e2-133">Always</span></span>|<span data-ttu-id="335e2-134">Web yuvası Protokolü anlaşması bağımsız olarak her zaman kullanın.</span><span class="sxs-lookup"><span data-stu-id="335e2-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="335e2-135">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="335e2-135">Never</span></span>|<span data-ttu-id="335e2-136">Hiçbir zaman Web yuvası protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="335e2-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="335e2-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e2-137">Child Elements</span></span>  
 <span data-ttu-id="335e2-138">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="335e2-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="335e2-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e2-139">Parent Elements</span></span>  
  
|<span data-ttu-id="335e2-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="335e2-140">Element</span></span>|<span data-ttu-id="335e2-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335e2-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="335e2-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="335e2-142">\<netHttpBinding></span></span>|<span data-ttu-id="335e2-143">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="335e2-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="335e2-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="335e2-144">Example</span></span>  
 <span data-ttu-id="335e2-145">Aşağıdaki örnek nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="335e2-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="335e2-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="335e2-146">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="335e2-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="335e2-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="335e2-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="335e2-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="335e2-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="335e2-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="335e2-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="335e2-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
