---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732560"
---
# \<webSocketSettings>
<span data-ttu-id="abe76-101">Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="abe76-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="abe76-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abe76-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abe76-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="abe76-103">Attributes and Elements</span></span>  
 <span data-ttu-id="abe76-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abe76-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abe76-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="abe76-105">Attributes</span></span>  
  
|<span data-ttu-id="abe76-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="abe76-106">Attribute</span></span>|<span data-ttu-id="abe76-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abe76-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abe76-108">Createnocertificate Ationonconnection</span><span class="sxs-lookup"><span data-stu-id="abe76-108">createNotificationOnConnection</span></span>|<span data-ttu-id="abe76-109">Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="abe76-110">Disablepayloadmaskeleme</span><span class="sxs-lookup"><span data-stu-id="abe76-110">disablePayloadMasking</span></span>|<span data-ttu-id="abe76-111">Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="abe76-112">Keepaliveınterval</span><span class="sxs-lookup"><span data-stu-id="abe76-112">keepAliveInterval</span></span>|<span data-ttu-id="abe76-113">Canlı tut aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="abe76-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="abe76-114">maxPendingConnections</span></span>|<span data-ttu-id="abe76-115">Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="abe76-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="abe76-116">receiveBufferSize</span></span>|<span data-ttu-id="abe76-117">Alma arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="abe76-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="abe76-118">sendBufferSize</span></span>|<span data-ttu-id="abe76-119">Gönderme arabelleğinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="abe76-120">Alt protokolü</span><span class="sxs-lookup"><span data-stu-id="abe76-120">subProtocol</span></span>|<span data-ttu-id="abe76-121">Web yuvası alt protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="abe76-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="abe76-122">transportUsage</span></span>|<span data-ttu-id="abe76-123">Web Yuvaları ne zaman kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe76-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="abe76-124">transportUsage özniteliği</span><span class="sxs-lookup"><span data-stu-id="abe76-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="abe76-125">Değer</span><span class="sxs-lookup"><span data-stu-id="abe76-125">Value</span></span>|<span data-ttu-id="abe76-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abe76-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="abe76-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="abe76-127">WhenDuplex</span></span>|<span data-ttu-id="abe76-128">Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="abe76-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="abe76-129">Her zaman</span><span class="sxs-lookup"><span data-stu-id="abe76-129">Always</span></span>|<span data-ttu-id="abe76-130">Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="abe76-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="abe76-131">Asla</span><span class="sxs-lookup"><span data-stu-id="abe76-131">Never</span></span>|<span data-ttu-id="abe76-132">Web yuvası protokolünü hiçbir şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="abe76-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abe76-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="abe76-133">Child Elements</span></span>  
 <span data-ttu-id="abe76-134">Yok</span><span class="sxs-lookup"><span data-stu-id="abe76-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abe76-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="abe76-135">Parent Elements</span></span>  
  
|<span data-ttu-id="abe76-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="abe76-136">Element</span></span>|<span data-ttu-id="abe76-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abe76-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="abe76-138">NetHttpBinding belirtir</span><span class="sxs-lookup"><span data-stu-id="abe76-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="abe76-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="abe76-139">Example</span></span>  
 <span data-ttu-id="abe76-140">Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir \<webSocketSettings> .</span><span class="sxs-lookup"><span data-stu-id="abe76-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abe76-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abe76-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="abe76-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="abe76-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="abe76-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="abe76-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="abe76-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="abe76-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
