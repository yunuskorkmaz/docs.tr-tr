---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 84aee31b6c15beb32732f89eae7c3d176f57971d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754843"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="7881b-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="7881b-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="7881b-103">Web yuvasını ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="7881b-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="7881b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7881b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7881b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7881b-105">\<bindings></span></span>  
<span data-ttu-id="7881b-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7881b-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7881b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7881b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7881b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7881b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7881b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7881b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7881b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7881b-110">Attributes</span></span>  
  
|<span data-ttu-id="7881b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7881b-111">Attribute</span></span>|<span data-ttu-id="7881b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7881b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7881b-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="7881b-113">createNotificationOnConnection</span></span>|<span data-ttu-id="7881b-114">Bağlantıda bir bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="7881b-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="7881b-115">disablePayloadMasking</span></span>|<span data-ttu-id="7881b-116">Web yuvasını maskeleme etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="7881b-117">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="7881b-117">keepAliveInterval</span></span>|<span data-ttu-id="7881b-118">Canlı tutma aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="7881b-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="7881b-119">maxPendingConnections</span></span>|<span data-ttu-id="7881b-120">Gönderme hizmeti üzerinde bekleyen bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="7881b-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="7881b-121">receiveBufferSize</span></span>|<span data-ttu-id="7881b-122">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="7881b-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="7881b-123">sendBufferSize</span></span>|<span data-ttu-id="7881b-124">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="7881b-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="7881b-125">subProtocol</span></span>|<span data-ttu-id="7881b-126">Web yuvasını subprotocol belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="7881b-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="7881b-127">transportUsage</span></span>|<span data-ttu-id="7881b-128">Ne zaman Web yuvalarını kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7881b-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="7881b-129">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="7881b-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="7881b-130">Değer</span><span class="sxs-lookup"><span data-stu-id="7881b-130">Value</span></span>|<span data-ttu-id="7881b-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7881b-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7881b-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="7881b-132">WhenDuplex</span></span>|<span data-ttu-id="7881b-133">Sözleşme çift yönlü olduğunda Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7881b-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="7881b-134">Her zaman</span><span class="sxs-lookup"><span data-stu-id="7881b-134">Always</span></span>|<span data-ttu-id="7881b-135">Her zaman sözleşme bağımsız olarak Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7881b-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="7881b-136">Hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="7881b-136">Never</span></span>|<span data-ttu-id="7881b-137">Hiçbir zaman Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7881b-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7881b-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7881b-138">Child Elements</span></span>  
 <span data-ttu-id="7881b-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="7881b-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7881b-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7881b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="7881b-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="7881b-141">Element</span></span>|<span data-ttu-id="7881b-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7881b-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7881b-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7881b-143">\<netHttpBinding></span></span>|<span data-ttu-id="7881b-144">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="7881b-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7881b-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="7881b-145">Example</span></span>  
 <span data-ttu-id="7881b-146">Aşağıdaki örnekte nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="7881b-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7881b-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7881b-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="7881b-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7881b-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7881b-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7881b-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7881b-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="7881b-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7881b-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7881b-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
