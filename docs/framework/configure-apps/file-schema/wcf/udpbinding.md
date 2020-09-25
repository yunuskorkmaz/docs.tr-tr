---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 730a051e6823a89c05f8eb894b261e93c0511dcc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183645"
---
# \<udpBinding>

<span data-ttu-id="d0702-101">Bağlamayı yapılandırmak için kullanılan bir yapılandırma öğesi <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d0702-101">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="d0702-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0702-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0702-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0702-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d0702-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0702-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0702-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0702-105">Attributes</span></span>  
  
|<span data-ttu-id="d0702-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0702-106">Attribute</span></span>|<span data-ttu-id="d0702-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0702-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d0702-108"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0702-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d0702-109">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0702-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0702-110">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0702-110">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="d0702-111">Yinelenen ileti geçmişi uzunluğunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-111">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="d0702-112">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-112">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="d0702-113">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="d0702-113">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="d0702-114">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-114">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="d0702-115">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="d0702-115">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="d0702-116">Tek bir kanal örneği için Giriş sırasından alınan ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-116">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="d0702-117">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d0702-117">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d0702-118">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="d0702-118">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="d0702-119">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0702-119">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d0702-120">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="d0702-120">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="d0702-121">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-121">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="d0702-122">Çok noktaya yayın arabirim KIMLIĞINI belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-122">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="d0702-123">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d0702-123">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d0702-124">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0702-124">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d0702-125">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0702-125">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d0702-126">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d0702-126">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d0702-127">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0702-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d0702-128">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0702-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0702-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0702-129">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d0702-130"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0702-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d0702-131">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0702-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0702-132">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0702-132">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d0702-133"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0702-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d0702-134">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0702-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0702-135">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0702-135">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="d0702-136">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d0702-136">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d0702-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d0702-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0702-138">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="d0702-138">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="d0702-139">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="d0702-139">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="d0702-140">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="d0702-140">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d0702-141">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0702-141">The default is UTF8.</span></span> <span data-ttu-id="d0702-142">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="d0702-142">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="d0702-143">Bağlama için yaşam süresini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="d0702-143">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0702-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0702-144">Child Elements</span></span>  
  
|<span data-ttu-id="d0702-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0702-145">Element</span></span>|<span data-ttu-id="d0702-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0702-146">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d0702-147">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0702-147">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d0702-148">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="d0702-148">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0702-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0702-149">Parent Elements</span></span>  
  
|<span data-ttu-id="d0702-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0702-150">Element</span></span>|<span data-ttu-id="d0702-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0702-151">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="d0702-152">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d0702-152">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0702-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0702-153">Remarks</span></span>  

 <span data-ttu-id="d0702-154">UdpBinding, WCF hizmetlerinin UDP taşıması üzerinden iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d0702-154">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="d0702-155">İstemcinin bir hizmete ileti gönderdiği ve geri yanıt bekleyebileceği "yangın ve unut" ileti değişimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0702-155">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0702-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0702-156">Example</span></span>  

 <span data-ttu-id="d0702-157">Aşağıdaki örnek, <xref:System.ServiceModel.UdpBinding> <> öğesi kullanılarak nasıl yapılandırılacağını gösterir `udpBinding` .</span><span class="sxs-lookup"><span data-stu-id="d0702-157">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0702-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0702-158">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="d0702-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d0702-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d0702-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0702-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d0702-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d0702-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
