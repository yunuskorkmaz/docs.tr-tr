---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769752"
---
# <a name="websocketsettings"></a><span data-ttu-id="02c79-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="02c79-101">\<webSocketSettings></span></span>
<span data-ttu-id="02c79-102">Web yuvası ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="02c79-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="02c79-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02c79-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="02c79-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="02c79-104">\<bindings></span></span>  
<span data-ttu-id="02c79-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="02c79-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c79-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02c79-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02c79-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02c79-107">Attributes and Elements</span></span>  
 <span data-ttu-id="02c79-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02c79-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02c79-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02c79-109">Attributes</span></span>  
  
|<span data-ttu-id="02c79-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="02c79-110">Attribute</span></span>|<span data-ttu-id="02c79-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02c79-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02c79-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="02c79-112">createNotificationOnConnection</span></span>|<span data-ttu-id="02c79-113">Bağlantı kurulduğunda bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="02c79-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="02c79-114">disablePayloadMasking</span></span>|<span data-ttu-id="02c79-115">Web yuvası maskeleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="02c79-116">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="02c79-116">keepAliveInterval</span></span>|<span data-ttu-id="02c79-117">Canlı tutma aralığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="02c79-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="02c79-118">maxPendingConnections</span></span>|<span data-ttu-id="02c79-119">Gönderme hizmeti bekleyen bağlantılar maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="02c79-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="02c79-120">receiveBufferSize</span></span>|<span data-ttu-id="02c79-121">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="02c79-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="02c79-122">sendBufferSize</span></span>|<span data-ttu-id="02c79-123">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="02c79-124">geçersizdir</span><span class="sxs-lookup"><span data-stu-id="02c79-124">subProtocol</span></span>|<span data-ttu-id="02c79-125">Web yuvası subprotocol'üne belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="02c79-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="02c79-126">transportUsage</span></span>|<span data-ttu-id="02c79-127">Web yuvaları kullanma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c79-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="02c79-128">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="02c79-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="02c79-129">Değer</span><span class="sxs-lookup"><span data-stu-id="02c79-129">Value</span></span>|<span data-ttu-id="02c79-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02c79-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02c79-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="02c79-131">WhenDuplex</span></span>|<span data-ttu-id="02c79-132">Web yuvası Protokolü anlaşması çift yönlü olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="02c79-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="02c79-133">Her zaman</span><span class="sxs-lookup"><span data-stu-id="02c79-133">Always</span></span>|<span data-ttu-id="02c79-134">Web yuvası Protokolü anlaşması bağımsız olarak her zaman kullanın.</span><span class="sxs-lookup"><span data-stu-id="02c79-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="02c79-135">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="02c79-135">Never</span></span>|<span data-ttu-id="02c79-136">Hiçbir zaman Web yuvası protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="02c79-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02c79-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02c79-137">Child Elements</span></span>  
 <span data-ttu-id="02c79-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="02c79-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02c79-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02c79-139">Parent Elements</span></span>  
  
|<span data-ttu-id="02c79-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="02c79-140">Element</span></span>|<span data-ttu-id="02c79-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02c79-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02c79-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="02c79-142">\<netHttpBinding></span></span>|<span data-ttu-id="02c79-143">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="02c79-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="02c79-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="02c79-144">Example</span></span>  
 <span data-ttu-id="02c79-145">Aşağıdaki örnek nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="02c79-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02c79-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02c79-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="02c79-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="02c79-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="02c79-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02c79-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="02c79-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="02c79-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="02c79-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="02c79-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
