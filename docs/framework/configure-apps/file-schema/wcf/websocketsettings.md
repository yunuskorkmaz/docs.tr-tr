---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71ed2fc6e4e5407cdf8c3e2334dcc0c16a00cf83
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="b8509-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="b8509-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="b8509-103">Web yuvasını ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8509-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="b8509-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b8509-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8509-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b8509-105">\<bindings></span></span>  
<span data-ttu-id="b8509-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b8509-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8509-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8509-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8509-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8509-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8509-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8509-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8509-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8509-110">Attributes</span></span>  
  
|<span data-ttu-id="b8509-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8509-111">Attribute</span></span>|<span data-ttu-id="b8509-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8509-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8509-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="b8509-113">createNotificationOnConnection</span></span>|<span data-ttu-id="b8509-114">Bağlantıda bir bildirim gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="b8509-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="b8509-115">disablePayloadMasking</span></span>|<span data-ttu-id="b8509-116">Web yuvasını maskeleme etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="b8509-117">KeepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="b8509-117">keepAliveInterval</span></span>|<span data-ttu-id="b8509-118">Canlı tutma aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="b8509-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="b8509-119">maxPendingConnections</span></span>|<span data-ttu-id="b8509-120">Gönderme hizmeti üzerinde bekleyen bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="b8509-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="b8509-121">receiveBufferSize</span></span>|<span data-ttu-id="b8509-122">Alış arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="b8509-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="b8509-123">sendBufferSize</span></span>|<span data-ttu-id="b8509-124">Gönderme arabellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="b8509-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="b8509-125">subProtocol</span></span>|<span data-ttu-id="b8509-126">Web yuvasını subprotocol belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="b8509-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="b8509-127">transportUsage</span></span>|<span data-ttu-id="b8509-128">Ne zaman Web yuvalarını kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8509-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="b8509-129">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="b8509-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="b8509-130">Değer</span><span class="sxs-lookup"><span data-stu-id="b8509-130">Value</span></span>|<span data-ttu-id="b8509-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8509-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8509-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="b8509-132">WhenDuplex</span></span>|<span data-ttu-id="b8509-133">Sözleşme çift yönlü olduğunda Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8509-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="b8509-134">Her zaman</span><span class="sxs-lookup"><span data-stu-id="b8509-134">Always</span></span>|<span data-ttu-id="b8509-135">Her zaman sözleşme bağımsız olarak Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8509-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="b8509-136">Hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="b8509-136">Never</span></span>|<span data-ttu-id="b8509-137">Hiçbir zaman Web yuvasını protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8509-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8509-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8509-138">Child Elements</span></span>  
 <span data-ttu-id="b8509-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8509-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8509-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8509-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b8509-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8509-141">Element</span></span>|<span data-ttu-id="b8509-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8509-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8509-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b8509-143">\<netHttpBinding></span></span>|<span data-ttu-id="b8509-144">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="b8509-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b8509-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8509-145">Example</span></span>  
 <span data-ttu-id="b8509-146">Aşağıdaki örnekte nasıl kullanılacağını gösterir \<webSocketSettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8509-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8509-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8509-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="b8509-148">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b8509-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b8509-149">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8509-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b8509-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="b8509-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b8509-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b8509-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
