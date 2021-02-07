---
description: 'Hakkında daha fazla bilgi edinin: <webSocketSettings>'
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: a0b67a0088491c73ed0214191283ae5292a654b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682494"
---
# \<webSocketSettings>

<span data-ttu-id="6222c-102">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6222c-102">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="6222c-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6222c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6222c-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6222c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6222c-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6222c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6222c-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6222c-106">Attributes</span></span>  
  
|<span data-ttu-id="6222c-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6222c-107">Attribute</span></span>|<span data-ttu-id="6222c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6222c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6222c-109">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="6222c-109">createNotificationOnConnection</span></span>|<span data-ttu-id="6222c-110">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-110">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="6222c-111">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="6222c-111">disablePayloadMasking</span></span>|<span data-ttu-id="6222c-112">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-112">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="6222c-113">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="6222c-113">keepAliveInterval</span></span>|<span data-ttu-id="6222c-114">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-114">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="6222c-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="6222c-115">maxPendingConnections</span></span>|<span data-ttu-id="6222c-116">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-116">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="6222c-117">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6222c-117">receiveBufferSize</span></span>|<span data-ttu-id="6222c-118">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-118">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="6222c-119">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="6222c-119">sendBufferSize</span></span>|<span data-ttu-id="6222c-120">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-120">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="6222c-121">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="6222c-121">subProtocol</span></span>|<span data-ttu-id="6222c-122">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-122">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="6222c-123">transportUsage</span><span class="sxs-lookup"><span data-stu-id="6222c-123">transportUsage</span></span>|<span data-ttu-id="6222c-124">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6222c-124">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="6222c-125">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="6222c-125">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="6222c-126">Değer</span><span class="sxs-lookup"><span data-stu-id="6222c-126">Value</span></span>|<span data-ttu-id="6222c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6222c-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6222c-128">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="6222c-128">WhenDuplex</span></span>|<span data-ttu-id="6222c-129">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6222c-129">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="6222c-130">Her zaman</span><span class="sxs-lookup"><span data-stu-id="6222c-130">Always</span></span>|<span data-ttu-id="6222c-131">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6222c-131">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="6222c-132">Asla</span><span class="sxs-lookup"><span data-stu-id="6222c-132">Never</span></span>|<span data-ttu-id="6222c-133">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6222c-133">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6222c-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6222c-134">Child Elements</span></span>  

 <span data-ttu-id="6222c-135">Yok</span><span class="sxs-lookup"><span data-stu-id="6222c-135">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6222c-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6222c-136">Parent Elements</span></span>  
  
|<span data-ttu-id="6222c-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="6222c-137">Element</span></span>|<span data-ttu-id="6222c-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6222c-138">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="6222c-139">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="6222c-139">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6222c-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="6222c-140">Example</span></span>  

 <span data-ttu-id="6222c-141">Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir \<webSocketSettings> .</span><span class="sxs-lookup"><span data-stu-id="6222c-141">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6222c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6222c-142">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6222c-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6222c-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6222c-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6222c-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6222c-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6222c-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
