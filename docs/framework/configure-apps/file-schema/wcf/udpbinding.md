---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429838"
---
# <a name="udpbinding"></a><span data-ttu-id="8ec92-101">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="8ec92-101">\<udpBinding></span></span>
<span data-ttu-id="8ec92-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="8ec92-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ec92-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ec92-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ec92-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ec92-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8ec92-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8ec92-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding>**</span><span class="sxs-lookup"><span data-stu-id="8ec92-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec92-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ec92-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ec92-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec92-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ec92-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ec92-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ec92-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ec92-110">Attributes</span></span>  
  
|<span data-ttu-id="8ec92-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ec92-111">Attribute</span></span>|<span data-ttu-id="8ec92-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ec92-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="8ec92-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8ec92-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8ec92-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ec92-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8ec92-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="8ec92-116">An integer value that specifies the duplicate message history length.</span><span class="sxs-lookup"><span data-stu-id="8ec92-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="8ec92-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span><span class="sxs-lookup"><span data-stu-id="8ec92-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="8ec92-118">The default value is 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="8ec92-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="8ec92-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="8ec92-120">The default value is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="8ec92-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="8ec92-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span><span class="sxs-lookup"><span data-stu-id="8ec92-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="8ec92-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="8ec92-123">The sender receives a SOAP fault if the message is too large for the receiver.</span><span class="sxs-lookup"><span data-stu-id="8ec92-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="8ec92-124">The receiver drops the message and creates an entry of the event in the trace log.</span><span class="sxs-lookup"><span data-stu-id="8ec92-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8ec92-125">The default is 65,536 bytes.</span><span class="sxs-lookup"><span data-stu-id="8ec92-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="8ec92-126">An integer value that specifies the maximum number of retransmit messages.</span><span class="sxs-lookup"><span data-stu-id="8ec92-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="8ec92-127">An integer value that specifies the multicast interface ID.</span><span class="sxs-lookup"><span data-stu-id="8ec92-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="8ec92-128">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8ec92-129">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8ec92-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="8ec92-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8ec92-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8ec92-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="8ec92-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8ec92-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8ec92-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ec92-134">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8ec92-134">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8ec92-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8ec92-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8ec92-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ec92-137">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="8ec92-137">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="8ec92-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8ec92-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8ec92-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ec92-140">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8ec92-140">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="8ec92-141">Sets the character set encoding to be used for emitting messages on the binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-141">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8ec92-142">Valid values include the following:</span><span class="sxs-lookup"><span data-stu-id="8ec92-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ec92-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="8ec92-144">-   Unicode: 16-bit encoding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-144">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="8ec92-145">-   UTF8: 8-bit encoding</span><span class="sxs-lookup"><span data-stu-id="8ec92-145">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="8ec92-146">The default is UTF8.</span><span class="sxs-lookup"><span data-stu-id="8ec92-146">The default is UTF8.</span></span> <span data-ttu-id="8ec92-147">This attribute is of type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-147">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="8ec92-148">A timespan value that specifies the time to live for the binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-148">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ec92-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec92-149">Child Elements</span></span>  
  
|<span data-ttu-id="8ec92-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ec92-150">Element</span></span>|<span data-ttu-id="8ec92-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ec92-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ec92-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ec92-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="8ec92-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span><span class="sxs-lookup"><span data-stu-id="8ec92-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8ec92-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8ec92-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ec92-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec92-155">Parent Elements</span></span>  
  
|<span data-ttu-id="8ec92-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ec92-156">Element</span></span>|<span data-ttu-id="8ec92-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ec92-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ec92-158">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8ec92-158">\<bindings></span></span>](bindings.md)|<span data-ttu-id="8ec92-159">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="8ec92-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ec92-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ec92-160">Remarks</span></span>  
 <span data-ttu-id="8ec92-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span><span class="sxs-lookup"><span data-stu-id="8ec92-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="8ec92-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span><span class="sxs-lookup"><span data-stu-id="8ec92-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec92-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ec92-163">Example</span></span>  
 <span data-ttu-id="8ec92-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span><span class="sxs-lookup"><span data-stu-id="8ec92-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ec92-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec92-165">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="8ec92-166">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8ec92-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8ec92-167">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8ec92-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8ec92-168">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ec92-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8ec92-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="8ec92-169">\<binding></span></span>](bindings.md)
