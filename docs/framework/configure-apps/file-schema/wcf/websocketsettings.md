---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: e5f34dca83c8d3d08d27fb72bee5af2a89ac6b9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416434"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="b6eed-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="b6eed-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="b6eed-103">Web yuvası ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="b6eed-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="b6eed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6eed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6eed-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b6eed-105">\<bindings></span></span>  
<span data-ttu-id="b6eed-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b6eed-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6eed-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6eed-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6eed-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6eed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b6eed-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6eed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6eed-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6eed-110">Attributes</span></span>  
  
|<span data-ttu-id="b6eed-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b6eed-111">Attribute</span></span>|<span data-ttu-id="b6eed-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6eed-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6eed-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="b6eed-113">createNotificationOnConnection</span></span>|<span data-ttu-id="b6eed-114">Bağlantı kurulduğunda bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="b6eed-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="b6eed-115">disablePayloadMasking</span></span>|<span data-ttu-id="b6eed-116">Web yuvası maskeleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="b6eed-117">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="b6eed-117">keepAliveInterval</span></span>|<span data-ttu-id="b6eed-118">Canlı tutma aralığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="b6eed-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="b6eed-119">maxPendingConnections</span></span>|<span data-ttu-id="b6eed-120">Gönderme hizmeti bekleyen bağlantılar maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="b6eed-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="b6eed-121">receiveBufferSize</span></span>|<span data-ttu-id="b6eed-122">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="b6eed-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="b6eed-123">sendBufferSize</span></span>|<span data-ttu-id="b6eed-124">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="b6eed-125">geçersizdir</span><span class="sxs-lookup"><span data-stu-id="b6eed-125">subProtocol</span></span>|<span data-ttu-id="b6eed-126">Web yuvası subprotocol'üne belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="b6eed-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="b6eed-127">transportUsage</span></span>|<span data-ttu-id="b6eed-128">Web yuvaları kullanma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6eed-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="b6eed-129">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="b6eed-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="b6eed-130">Değer</span><span class="sxs-lookup"><span data-stu-id="b6eed-130">Value</span></span>|<span data-ttu-id="b6eed-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6eed-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6eed-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="b6eed-132">WhenDuplex</span></span>|<span data-ttu-id="b6eed-133">Web yuvası Protokolü anlaşması çift yönlü olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6eed-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="b6eed-134">Her zaman</span><span class="sxs-lookup"><span data-stu-id="b6eed-134">Always</span></span>|<span data-ttu-id="b6eed-135">Web yuvası Protokolü anlaşması bağımsız olarak her zaman kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6eed-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="b6eed-136">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="b6eed-136">Never</span></span>|<span data-ttu-id="b6eed-137">Hiçbir zaman Web yuvası protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6eed-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6eed-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6eed-138">Child Elements</span></span>  
 <span data-ttu-id="b6eed-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6eed-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6eed-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6eed-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b6eed-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6eed-141">Element</span></span>|<span data-ttu-id="b6eed-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6eed-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6eed-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b6eed-143">\<netHttpBinding></span></span>|<span data-ttu-id="b6eed-144">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="b6eed-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6eed-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6eed-145">Example</span></span>  
 <span data-ttu-id="b6eed-146">Aşağıdaki örnek nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="b6eed-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6eed-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6eed-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="b6eed-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b6eed-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b6eed-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b6eed-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b6eed-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="b6eed-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b6eed-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b6eed-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
