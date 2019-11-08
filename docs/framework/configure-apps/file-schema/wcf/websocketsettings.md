---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732560"
---
# <a name="websocketsettings"></a><span data-ttu-id="06971-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="06971-101">\<webSocketSettings></span></span>
<span data-ttu-id="06971-102">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="06971-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="06971-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="06971-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06971-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="06971-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06971-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="06971-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="06971-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="06971-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="06971-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="06971-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="06971-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="06971-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06971-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06971-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06971-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06971-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06971-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06971-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06971-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06971-112">Attributes</span></span>  
  
|<span data-ttu-id="06971-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="06971-113">Attribute</span></span>|<span data-ttu-id="06971-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06971-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06971-115">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="06971-115">createNotificationOnConnection</span></span>|<span data-ttu-id="06971-116">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="06971-117">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="06971-117">disablePayloadMasking</span></span>|<span data-ttu-id="06971-118">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="06971-119">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="06971-119">keepAliveInterval</span></span>|<span data-ttu-id="06971-120">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="06971-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="06971-121">maxPendingConnections</span></span>|<span data-ttu-id="06971-122">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="06971-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="06971-123">receiveBufferSize</span></span>|<span data-ttu-id="06971-124">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="06971-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="06971-125">sendBufferSize</span></span>|<span data-ttu-id="06971-126">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="06971-127">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="06971-127">subProtocol</span></span>|<span data-ttu-id="06971-128">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="06971-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="06971-129">transportUsage</span></span>|<span data-ttu-id="06971-130">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06971-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="06971-131">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="06971-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="06971-132">Değer</span><span class="sxs-lookup"><span data-stu-id="06971-132">Value</span></span>|<span data-ttu-id="06971-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06971-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06971-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="06971-134">WhenDuplex</span></span>|<span data-ttu-id="06971-135">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="06971-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="06971-136">Her</span><span class="sxs-lookup"><span data-stu-id="06971-136">Always</span></span>|<span data-ttu-id="06971-137">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="06971-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="06971-138">Amaçlan</span><span class="sxs-lookup"><span data-stu-id="06971-138">Never</span></span>|<span data-ttu-id="06971-139">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="06971-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06971-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06971-140">Child Elements</span></span>  
 <span data-ttu-id="06971-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="06971-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06971-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06971-142">Parent Elements</span></span>  
  
|<span data-ttu-id="06971-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="06971-143">Element</span></span>|<span data-ttu-id="06971-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06971-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06971-145">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="06971-145">\<netHttpBinding></span></span>|<span data-ttu-id="06971-146">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="06971-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06971-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="06971-147">Example</span></span>  
 <span data-ttu-id="06971-148">Aşağıdaki örnek, \<webSocketSettings > öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06971-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06971-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06971-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="06971-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="06971-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06971-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06971-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="06971-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="06971-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="06971-153">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="06971-153">\<binding></span></span>](bindings.md)
