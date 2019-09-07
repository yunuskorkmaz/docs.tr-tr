---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 9ee6d4b5e623248499adc43bb176d96bfc9cd1a8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399258"
---
# <a name="udpbinding"></a><span data-ttu-id="ac528-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="ac528-101">\<udpBinding></span></span>
<span data-ttu-id="ac528-102"><xref:System.ServiceModel.UdpBinding> Bağlamayı yapılandırmak için kullanılan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ac528-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="ac528-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ac528-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ac528-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ac528-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ac528-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ac528-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ac528-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="ac528-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac528-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac528-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac528-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac528-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ac528-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac528-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac528-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac528-110">Attributes</span></span>  
  
|<span data-ttu-id="ac528-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ac528-111">Attribute</span></span>|<span data-ttu-id="ac528-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac528-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ac528-113">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac528-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ac528-114">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac528-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ac528-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac528-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="ac528-116">Yinelenen ileti geçmişi uzunluğunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="ac528-117">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="ac528-118">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="ac528-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="ac528-119">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="ac528-120">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="ac528-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="ac528-121">Tek bir kanal örneği için Giriş sırasından alınan ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="ac528-122">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ac528-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="ac528-123">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="ac528-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="ac528-124">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac528-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="ac528-125">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="ac528-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="ac528-126">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="ac528-127">Çok noktaya yayın arabirim KIMLIĞINI belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="ac528-128">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ac528-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ac528-129">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac528-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ac528-130">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="ac528-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="ac528-131">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="ac528-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="ac528-132">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ac528-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ac528-133">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ac528-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ac528-134">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac528-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ac528-135">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac528-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ac528-136">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac528-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ac528-137">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac528-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ac528-138">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac528-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ac528-139">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac528-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ac528-140">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac528-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ac528-141">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac528-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ac528-142">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac528-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="ac528-143">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ac528-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ac528-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ac528-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac528-145">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="ac528-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="ac528-146">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="ac528-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="ac528-147">UTF8 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="ac528-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ac528-148">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac528-148">The default is UTF8.</span></span> <span data-ttu-id="ac528-149">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ac528-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="ac528-150">Bağlama için yaşam süresini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ac528-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac528-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac528-151">Child Elements</span></span>  
  
|<span data-ttu-id="ac528-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac528-152">Element</span></span>|<span data-ttu-id="ac528-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac528-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac528-154">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac528-154">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="ac528-155">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac528-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ac528-156">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ac528-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac528-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac528-157">Parent Elements</span></span>  
  
|<span data-ttu-id="ac528-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac528-158">Element</span></span>|<span data-ttu-id="ac528-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac528-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac528-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ac528-160">\<bindings></span></span>](bindings.md)|<span data-ttu-id="ac528-161">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ac528-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac528-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac528-162">Remarks</span></span>  
 <span data-ttu-id="ac528-163">UdpBinding, WCF hizmetlerinin UDP taşıması üzerinden iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ac528-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="ac528-164">İstemcinin bir hizmete ileti gönderdiği ve geri yanıt bekleyebileceği "yangın ve unut" ileti değişimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac528-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac528-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac528-165">Example</span></span>  
 <span data-ttu-id="ac528-166">Aşağıdaki örnek, <xref:System.ServiceModel.UdpBinding> <`udpBinding`> öğesi kullanılarak nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac528-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac528-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac528-167">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="ac528-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ac528-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ac528-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac528-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ac528-170">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac528-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ac528-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ac528-171">\<binding></span></span>](../../../misc/binding.md)
