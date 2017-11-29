---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8eb4d28885308c400c445ae71019373ec92ed27a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="6e49a-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6e49a-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="6e49a-103">Yapılandırmak için kullanılan bir yapılandırma öğesi <xref:System.ServiceModel.UdpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="6e49a-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="6e49a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6e49a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e49a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6e49a-105">\<bindings></span></span>  
<span data-ttu-id="6e49a-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="6e49a-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e49a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e49a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e49a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e49a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6e49a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e49a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e49a-110">Attributes</span></span>  
  
|<span data-ttu-id="6e49a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e49a-111">Attribute</span></span>|<span data-ttu-id="6e49a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e49a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6e49a-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6e49a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6e49a-114">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6e49a-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="6e49a-116">Yinelenen ileti geçmişi uzunluğu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6e49a-117">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="6e49a-118">Varsayılan değer 524288 (0x80000): bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6e49a-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="6e49a-119">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirtir bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="6e49a-120">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="6e49a-121">Alınan ancak henüz bir tek kanal örneğinin giriş sıradan çıkarılan iletilerin sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6e49a-122">Bu bağlama ile yapılandırılan kanalda alınan bir ileti için üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6e49a-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6e49a-123">İleti alıcı için çok büyük ise gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="6e49a-124">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e49a-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6e49a-125">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="6e49a-126">En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="6e49a-127">Çok noktaya yayın arabirimi kimliğini belirtir. bir tamsayı değeri</span><span class="sxs-lookup"><span data-stu-id="6e49a-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="6e49a-128">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="6e49a-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6e49a-129">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6e49a-130">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6e49a-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="6e49a-131">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="6e49a-132">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6e49a-133">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6e49a-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6e49a-134">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6e49a-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6e49a-135">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6e49a-136">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6e49a-137">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6e49a-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6e49a-138">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6e49a-139">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6e49a-140">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6e49a-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6e49a-141">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6e49a-142">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="6e49a-143">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e49a-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6e49a-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6e49a-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6e49a-145">-BigEndianUnicode: Unicode BigEndian kodlama.</span><span class="sxs-lookup"><span data-stu-id="6e49a-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6e49a-146">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="6e49a-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="6e49a-147">-UTF8: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="6e49a-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6e49a-148">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6e49a-148">The default is UTF8.</span></span> <span data-ttu-id="6e49a-149">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="6e49a-150">Bağlama için yaşam süresi belirten bir timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="6e49a-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e49a-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e49a-151">Child Elements</span></span>  
  
|<span data-ttu-id="6e49a-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e49a-152">Element</span></span>|<span data-ttu-id="6e49a-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e49a-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e49a-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="6e49a-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="6e49a-155">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e49a-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6e49a-156">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6e49a-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e49a-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e49a-157">Parent Elements</span></span>  
  
|<span data-ttu-id="6e49a-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e49a-158">Element</span></span>|<span data-ttu-id="6e49a-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e49a-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e49a-160">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6e49a-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="6e49a-161">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6e49a-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e49a-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e49a-162">Remarks</span></span>  
 <span data-ttu-id="6e49a-163">UdpBinding UDP taşıma iletişim kurmak WCF hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e49a-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="6e49a-164">Burada bir istemci bir hizmete bir ileti gönderir ve yanıt geri bekliyor "yangın ve unut" ileti alışverişlerinde için sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e49a-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e49a-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e49a-165">Example</span></span>  
 <span data-ttu-id="6e49a-166">Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.ServiceModel.UdpBinding> kullanarak <`udpBinding`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e49a-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e49a-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e49a-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="6e49a-168">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="6e49a-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6e49a-169">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6e49a-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6e49a-170">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="6e49a-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6e49a-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6e49a-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
