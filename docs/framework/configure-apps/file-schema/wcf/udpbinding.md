---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 743eaa281fef233ddc2e8af5cee890bd10ce0963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941189"
---
# <a name="udpbinding"></a><span data-ttu-id="7f725-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="7f725-101">\<udpBinding></span></span>
<span data-ttu-id="7f725-102"><xref:System.ServiceModel.UdpBinding> Bağlamayı yapılandırmak için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="7f725-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="7f725-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f725-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f725-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7f725-104">\<bindings></span></span>  
<span data-ttu-id="7f725-105">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="7f725-105">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f725-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f725-106">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f725-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f725-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7f725-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7f725-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f725-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7f725-109">Attributes</span></span>  
  
|<span data-ttu-id="7f725-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7f725-110">Attribute</span></span>|<span data-ttu-id="7f725-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f725-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7f725-112">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7f725-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7f725-113">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f725-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7f725-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7f725-114">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="7f725-115">Yinelenen ileti geçmişi uzunluğunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-115">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7f725-116">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-116">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="7f725-117">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="7f725-117">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7f725-118">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-118">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="7f725-119">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="7f725-119">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="7f725-120">Tek bir kanal örneği için Giriş sırasından alınan ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-120">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7f725-121">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7f725-121">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7f725-122">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="7f725-122">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="7f725-123">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f725-123">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7f725-124">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="7f725-124">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="7f725-125">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-125">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="7f725-126">Çok noktaya yayın arabirim KIMLIĞINI belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-126">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="7f725-127">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7f725-127">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7f725-128">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f725-128">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7f725-129">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="7f725-129">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7f725-130">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="7f725-130">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7f725-131">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7f725-131">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7f725-132">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="7f725-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7f725-133">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7f725-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7f725-134">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f725-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7f725-135">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7f725-135">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7f725-136">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7f725-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7f725-137">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f725-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7f725-138">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7f725-138">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7f725-139">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7f725-139">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7f725-140">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f725-140">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7f725-141">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7f725-141">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7f725-142">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7f725-142">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7f725-143">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7f725-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7f725-144">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="7f725-144">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7f725-145">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="7f725-145">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7f725-146">UTF8 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="7f725-146">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7f725-147">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7f725-147">The default is UTF8.</span></span> <span data-ttu-id="7f725-148">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7f725-148">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="7f725-149">Bağlama için yaşam süresini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="7f725-149">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f725-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f725-150">Child Elements</span></span>  
  
|<span data-ttu-id="7f725-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f725-151">Element</span></span>|<span data-ttu-id="7f725-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f725-152">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f725-153">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f725-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="7f725-154">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7f725-154">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7f725-155">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7f725-155">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f725-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f725-156">Parent Elements</span></span>  
  
|<span data-ttu-id="7f725-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f725-157">Element</span></span>|<span data-ttu-id="7f725-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f725-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f725-159">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7f725-159">\<bindings></span></span>](bindings.md)|<span data-ttu-id="7f725-160">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7f725-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f725-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f725-161">Remarks</span></span>  
 <span data-ttu-id="7f725-162">UdpBinding, WCF hizmetlerinin UDP taşıması üzerinden iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7f725-162">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="7f725-163">İstemcinin bir hizmete ileti gönderdiği ve geri yanıt bekleyebileceği "yangın ve unut" ileti değişimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f725-163">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f725-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f725-164">Example</span></span>  
 <span data-ttu-id="7f725-165">Aşağıdaki örnek, <xref:System.ServiceModel.UdpBinding> <`udpBinding`> öğesi kullanılarak nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f725-165">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="7f725-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f725-166">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="7f725-167">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7f725-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7f725-168">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7f725-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7f725-169">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7f725-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7f725-170">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7f725-170">\<binding></span></span>](../../../misc/binding.md)
