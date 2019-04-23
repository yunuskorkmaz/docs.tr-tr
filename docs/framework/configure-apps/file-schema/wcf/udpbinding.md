---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 84a5bc763f898b3d323a6cee468c6e22d27d85a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229608"
---
# <a name="udpbinding"></a><span data-ttu-id="13350-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="13350-101">\<udpBinding></span></span>
<span data-ttu-id="13350-102">Yapılandırmak için kullanılan bir yapılandırma öğesi <xref:System.ServiceModel.UdpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="13350-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="13350-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="13350-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="13350-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="13350-104">\<bindings></span></span>  
<span data-ttu-id="13350-105">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="13350-105">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13350-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13350-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13350-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13350-107">Attributes and Elements</span></span>  
 <span data-ttu-id="13350-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13350-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13350-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13350-109">Attributes</span></span>  
  
|<span data-ttu-id="13350-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="13350-110">Attribute</span></span>|<span data-ttu-id="13350-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13350-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="13350-112">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="13350-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="13350-113">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="13350-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="13350-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13350-114">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="13350-115">Yinelenen ileti geçmişi uzunluğu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-115">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="13350-116">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan maksimum belleğin belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-116">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="13350-117">Varsayılan değer: 524288 (0x80000) bayt.</span><span class="sxs-lookup"><span data-stu-id="13350-117">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="13350-118">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabellek, bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-118">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="13350-119">65.536 bayt varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="13350-119">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="13350-120">Alınan ancak henüz bir tek bir kanalı örneği için giriş sıradan kaldırıldı iletileri maksimum sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-120">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="13350-121">Bu bağlama ile yapılandırılan bir kanalda alınan iletinin üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu tanımlar. pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="13350-121">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="13350-122">İleti alıcısı için çok büyük ise, gönderici bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="13350-122">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="13350-123">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13350-123">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="13350-124">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="13350-124">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="13350-125">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-125">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="13350-126">Çok noktaya yayın arabirim kimliği. belirten bir tamsayı değeri</span><span class="sxs-lookup"><span data-stu-id="13350-126">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="13350-127">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="13350-127">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="13350-128">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13350-128">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="13350-129">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="13350-129">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="13350-130">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="13350-130">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="13350-131">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="13350-131">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="13350-132">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="13350-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="13350-133">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="13350-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="13350-134">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="13350-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="13350-135">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13350-135">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="13350-136">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="13350-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="13350-137">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="13350-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="13350-138">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13350-138">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="13350-139">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="13350-139">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="13350-140">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="13350-140">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="13350-141">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="13350-141">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="13350-142">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13350-142">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="13350-143">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="13350-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="13350-144">-   BigEndianUnicode: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="13350-144">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="13350-145">-Unicode: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="13350-145">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="13350-146">-   UTF8: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="13350-146">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="13350-147">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="13350-147">The default is UTF8.</span></span> <span data-ttu-id="13350-148">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="13350-148">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="13350-149">Bağlama için yaşam süresi belirten bir timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="13350-149">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13350-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13350-150">Child Elements</span></span>  
  
|<span data-ttu-id="13350-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="13350-151">Element</span></span>|<span data-ttu-id="13350-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13350-152">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13350-153">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13350-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="13350-154">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="13350-154">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="13350-155">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="13350-155">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13350-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13350-156">Parent Elements</span></span>  
  
|<span data-ttu-id="13350-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="13350-157">Element</span></span>|<span data-ttu-id="13350-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13350-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13350-159">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="13350-159">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="13350-160">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="13350-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13350-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13350-161">Remarks</span></span>  
 <span data-ttu-id="13350-162">UdpBinding UDP taşıma iletişim kurmak WCF hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13350-162">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="13350-163">Burada bir istemci bir hizmete ileti gönderir ve yanıt geri bekliyor "Başlat ve unut" ileti alışverişlerinde için sağlar.</span><span class="sxs-lookup"><span data-stu-id="13350-163">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13350-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="13350-164">Example</span></span>  
 <span data-ttu-id="13350-165">Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.UdpBinding> kullanarak <`udpBinding`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="13350-165">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13350-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13350-166">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="13350-167">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="13350-167">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="13350-168">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="13350-168">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="13350-169">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="13350-169">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="13350-170">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="13350-170">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
