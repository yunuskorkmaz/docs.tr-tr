---
description: 'Hakkında daha fazla bilgi edinin: <udpBinding>'
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 33f8f6abaebe24364273ab43e7ef9ade39a969b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749226"
---
# \<udpBinding>

<span data-ttu-id="e889e-102">Bağlamayı yapılandırmak için kullanılan bir yapılandırma öğesi <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="e889e-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="e889e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e889e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e889e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e889e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e889e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e889e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e889e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e889e-106">Attributes</span></span>  
  
|<span data-ttu-id="e889e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e889e-107">Attribute</span></span>|<span data-ttu-id="e889e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e889e-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e889e-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e889e-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e889e-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e889e-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e889e-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e889e-111">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="e889e-112">Yinelenen ileti geçmişi uzunluğunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-112">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e889e-113">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-113">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="e889e-114">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="e889e-114">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="e889e-115">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-115">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="e889e-116">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="e889e-116">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="e889e-117">Tek bir kanal örneği için Giriş sırasından alınan ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-117">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e889e-118">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e889e-118">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e889e-119">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="e889e-119">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="e889e-120">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e889e-120">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e889e-121">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="e889e-121">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="e889e-122">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-122">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="e889e-123">Çok noktaya yayın arabirim KIMLIĞINI belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-123">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="e889e-124">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e889e-124">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e889e-125">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e889e-125">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e889e-126">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e889e-126">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e889e-127">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="e889e-127">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e889e-128">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e889e-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e889e-129">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e889e-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e889e-130">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e889e-130">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e889e-131"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e889e-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e889e-132">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e889e-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e889e-133">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e889e-133">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e889e-134"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e889e-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e889e-135">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e889e-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e889e-136">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e889e-136">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e889e-137">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e889e-137">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e889e-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e889e-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e889e-139">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="e889e-139">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="e889e-140">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="e889e-140">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="e889e-141">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="e889e-141">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="e889e-142">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e889e-142">The default is UTF8.</span></span> <span data-ttu-id="e889e-143">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="e889e-143">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="e889e-144">Bağlama için yaşam süresini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="e889e-144">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e889e-145">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e889e-145">Child Elements</span></span>  
  
|<span data-ttu-id="e889e-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="e889e-146">Element</span></span>|<span data-ttu-id="e889e-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e889e-147">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="e889e-148">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e889e-148">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e889e-149">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="e889e-149">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e889e-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e889e-150">Parent Elements</span></span>  
  
|<span data-ttu-id="e889e-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="e889e-151">Element</span></span>|<span data-ttu-id="e889e-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e889e-152">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="e889e-153">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e889e-153">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e889e-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e889e-154">Remarks</span></span>  

 <span data-ttu-id="e889e-155">UdpBinding, WCF hizmetlerinin UDP taşıması üzerinden iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e889e-155">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="e889e-156">İstemcinin bir hizmete ileti gönderdiği ve geri yanıt bekleyebileceği "yangın ve unut" ileti değişimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e889e-156">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e889e-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="e889e-157">Example</span></span>  

 <span data-ttu-id="e889e-158">Aşağıdaki örnek, <xref:System.ServiceModel.UdpBinding> <> öğesi kullanılarak nasıl yapılandırılacağını gösterir `udpBinding` .</span><span class="sxs-lookup"><span data-stu-id="e889e-158">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e889e-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e889e-159">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e889e-160">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e889e-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e889e-161">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e889e-161">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e889e-162">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e889e-162">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
