---
description: 'Hakkında daha fazla bilgi edinin: <connectionPoolSettings>'
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 5acf2d800f1a18f45750d0fabd23516f987b2c5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782175"
---
# \<connectionPoolSettings>

<span data-ttu-id="bef16-102">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bef16-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="bef16-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="bef16-103">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef16-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef16-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bef16-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bef16-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef16-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bef16-106">Attributes</span></span>  
  
|<span data-ttu-id="bef16-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bef16-107">Attribute</span></span>|<span data-ttu-id="bef16-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bef16-108">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="bef16-109">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="bef16-109">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="bef16-110">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bef16-110">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="bef16-111">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="bef16-111">The default is a "default" string.</span></span> <span data-ttu-id="bef16-112">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bef16-112">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="bef16-113"><xref:System.TimeSpan>Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="bef16-113">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="bef16-114">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bef16-114">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="bef16-115">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bef16-115">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="bef16-116">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="bef16-116">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="bef16-117">`idleTimeout`Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="bef16-117">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="bef16-118">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="bef16-118">The default is 10.</span></span><br /><br /> <span data-ttu-id="bef16-119">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="bef16-119">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="bef16-120">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bef16-120">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="bef16-121">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bef16-121">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bef16-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef16-122">Child Elements</span></span>  

 <span data-ttu-id="bef16-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="bef16-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bef16-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef16-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bef16-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="bef16-125">Element</span></span>|<span data-ttu-id="bef16-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bef16-126">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="bef16-127">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bef16-127">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bef16-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bef16-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bef16-129">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="bef16-129">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="bef16-130">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="bef16-130">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bef16-131">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bef16-131">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bef16-132">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="bef16-132">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bef16-133">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bef16-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
