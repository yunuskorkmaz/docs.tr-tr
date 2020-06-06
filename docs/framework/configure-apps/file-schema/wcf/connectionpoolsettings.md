---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400476"
---
# \<connectionPoolSettings>
<span data-ttu-id="5b66a-101">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="5b66a-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b66a-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b66a-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b66a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5b66a-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b66a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b66a-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b66a-105">Attributes</span></span>  
  
|<span data-ttu-id="5b66a-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b66a-106">Attribute</span></span>|<span data-ttu-id="5b66a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b66a-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="5b66a-108">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="5b66a-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="5b66a-109">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="5b66a-110">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-110">The default is a "default" string.</span></span> <span data-ttu-id="5b66a-111">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b66a-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="5b66a-112"><xref:System.TimeSpan>Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="5b66a-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="5b66a-113">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="5b66a-114">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5b66a-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="5b66a-115">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="5b66a-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="5b66a-116">`idleTimeout`Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="5b66a-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="5b66a-117">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="5b66a-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="5b66a-118">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="5b66a-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="5b66a-119">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="5b66a-120">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b66a-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b66a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b66a-121">Child Elements</span></span>  
 <span data-ttu-id="5b66a-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b66a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b66a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b66a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5b66a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b66a-124">Element</span></span>|<span data-ttu-id="5b66a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b66a-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="5b66a-126">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b66a-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b66a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b66a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5b66a-128">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="5b66a-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5b66a-129">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="5b66a-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5b66a-130">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5b66a-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5b66a-131">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5b66a-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5b66a-132">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5b66a-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
