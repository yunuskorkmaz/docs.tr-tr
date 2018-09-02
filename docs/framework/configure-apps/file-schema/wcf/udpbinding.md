---
title: '&lt;udpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: e17919ead6d6f7656c39d18b0ce1817c18da524a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421687"
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="7d582-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7d582-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="7d582-103">Yapılandırmak için kullanılan bir yapılandırma öğesi <xref:System.ServiceModel.UdpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="7d582-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="7d582-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d582-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d582-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7d582-105">\<bindings></span></span>  
<span data-ttu-id="7d582-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="7d582-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d582-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d582-107">Syntax</span></span>  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d582-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d582-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d582-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d582-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d582-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d582-110">Attributes</span></span>  
  
|<span data-ttu-id="7d582-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d582-111">Attribute</span></span>|<span data-ttu-id="7d582-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d582-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7d582-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d582-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7d582-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d582-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d582-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d582-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="7d582-116">Yinelenen ileti geçmişi uzunluğu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7d582-117">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan maksimum belleğin belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="7d582-118">Varsayılan değer: 524288 (0x80000) bayt.</span><span class="sxs-lookup"><span data-stu-id="7d582-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7d582-119">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabellek, bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="7d582-120">65.536 bayt varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7d582-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="7d582-121">Alınan ancak henüz bir tek bir kanalı örneği için giriş sıradan kaldırıldı iletileri maksimum sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7d582-122">Bu bağlama ile yapılandırılan bir kanalda alınan iletinin üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu tanımlar. pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7d582-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7d582-123">İleti alıcısı için çok büyük ise, gönderici bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="7d582-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="7d582-124">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d582-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7d582-125">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="7d582-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="7d582-126">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="7d582-127">Çok noktaya yayın arabirim kimliği. belirten bir tamsayı değeri</span><span class="sxs-lookup"><span data-stu-id="7d582-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="7d582-128">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7d582-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7d582-129">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d582-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7d582-130">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7d582-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7d582-131">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="7d582-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7d582-132">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="7d582-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7d582-133">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d582-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7d582-134">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d582-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7d582-135">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d582-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d582-136">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d582-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7d582-137">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d582-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7d582-138">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d582-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d582-139">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d582-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7d582-140">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d582-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7d582-141">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d582-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d582-142">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d582-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7d582-143">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d582-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7d582-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7d582-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7d582-145">-BigEndianUnicode: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="7d582-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7d582-146">-Unicode: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="7d582-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7d582-147">-UTF8: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="7d582-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7d582-148">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7d582-148">The default is UTF8.</span></span> <span data-ttu-id="7d582-149">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7d582-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="7d582-150">Bağlama için yaşam süresi belirten bir timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="7d582-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d582-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d582-151">Child Elements</span></span>  
  
|<span data-ttu-id="7d582-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d582-152">Element</span></span>|<span data-ttu-id="7d582-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d582-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d582-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="7d582-154">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7d582-155">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d582-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7d582-156">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7d582-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d582-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d582-157">Parent Elements</span></span>  
  
|<span data-ttu-id="7d582-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d582-158">Element</span></span>|<span data-ttu-id="7d582-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d582-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d582-160">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7d582-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7d582-161">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="7d582-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d582-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d582-162">Remarks</span></span>  
 <span data-ttu-id="7d582-163">UdpBinding UDP taşıma iletişim kurmak WCF hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d582-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="7d582-164">Burada bir istemci bir hizmete ileti gönderir ve yanıt geri bekliyor "Başlat ve unut" ileti alışverişlerinde için sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d582-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d582-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d582-165">Example</span></span>  
 <span data-ttu-id="7d582-166">Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.UdpBinding> kullanarak <`udpBinding`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="7d582-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d582-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d582-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="7d582-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7d582-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7d582-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7d582-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7d582-170">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="7d582-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7d582-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7d582-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
