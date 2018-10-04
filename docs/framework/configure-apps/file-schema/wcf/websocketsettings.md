---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 94a5883c37221a8d637a188fe42aad220a332575
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582404"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="0dad3-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="0dad3-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="0dad3-103">Web yuvası ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0dad3-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="0dad3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0dad3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0dad3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0dad3-105">\<bindings></span></span>  
<span data-ttu-id="0dad3-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0dad3-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dad3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dad3-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dad3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dad3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0dad3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dad3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dad3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0dad3-110">Attributes</span></span>  
  
|<span data-ttu-id="0dad3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0dad3-111">Attribute</span></span>|<span data-ttu-id="0dad3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dad3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dad3-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="0dad3-113">createNotificationOnConnection</span></span>|<span data-ttu-id="0dad3-114">Bağlantı kurulduğunda bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="0dad3-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="0dad3-115">disablePayloadMasking</span></span>|<span data-ttu-id="0dad3-116">Web yuvası maskeleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="0dad3-117">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="0dad3-117">keepAliveInterval</span></span>|<span data-ttu-id="0dad3-118">Canlı tutma aralığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="0dad3-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="0dad3-119">maxPendingConnections</span></span>|<span data-ttu-id="0dad3-120">Gönderme hizmeti bekleyen bağlantılar maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="0dad3-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="0dad3-121">receiveBufferSize</span></span>|<span data-ttu-id="0dad3-122">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="0dad3-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="0dad3-123">sendBufferSize</span></span>|<span data-ttu-id="0dad3-124">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="0dad3-125">geçersizdir</span><span class="sxs-lookup"><span data-stu-id="0dad3-125">subProtocol</span></span>|<span data-ttu-id="0dad3-126">Web yuvası subprotocol'üne belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="0dad3-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="0dad3-127">transportUsage</span></span>|<span data-ttu-id="0dad3-128">Web yuvaları kullanma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dad3-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="0dad3-129">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="0dad3-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="0dad3-130">Değer</span><span class="sxs-lookup"><span data-stu-id="0dad3-130">Value</span></span>|<span data-ttu-id="0dad3-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dad3-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dad3-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="0dad3-132">WhenDuplex</span></span>|<span data-ttu-id="0dad3-133">Web yuvası Protokolü anlaşması çift yönlü olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="0dad3-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="0dad3-134">Her zaman</span><span class="sxs-lookup"><span data-stu-id="0dad3-134">Always</span></span>|<span data-ttu-id="0dad3-135">Web yuvası Protokolü anlaşması bağımsız olarak her zaman kullanın.</span><span class="sxs-lookup"><span data-stu-id="0dad3-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="0dad3-136">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="0dad3-136">Never</span></span>|<span data-ttu-id="0dad3-137">Hiçbir zaman Web yuvası protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="0dad3-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dad3-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dad3-138">Child Elements</span></span>  
 <span data-ttu-id="0dad3-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="0dad3-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dad3-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dad3-140">Parent Elements</span></span>  
  
|<span data-ttu-id="0dad3-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="0dad3-141">Element</span></span>|<span data-ttu-id="0dad3-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dad3-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0dad3-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0dad3-143">\<netHttpBinding></span></span>|<span data-ttu-id="0dad3-144">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="0dad3-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0dad3-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dad3-145">Example</span></span>  
 <span data-ttu-id="0dad3-146">Aşağıdaki örnek nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="0dad3-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0dad3-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0dad3-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="0dad3-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0dad3-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0dad3-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0dad3-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0dad3-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0dad3-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="0dad3-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0dad3-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
