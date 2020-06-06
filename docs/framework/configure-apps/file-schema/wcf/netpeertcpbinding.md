---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140736"
---
# \<netPeerTcpBinding>
<span data-ttu-id="154ee-101">Eş kanala özgü TCP mesajlaşma için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="154ee-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="154ee-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="154ee-102">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="154ee-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="154ee-103">Attributes and Elements</span></span>  
 <span data-ttu-id="154ee-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="154ee-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="154ee-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="154ee-105">Attributes</span></span>  
  
|<span data-ttu-id="154ee-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="154ee-106">Attribute</span></span>|<span data-ttu-id="154ee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="154ee-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="154ee-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="154ee-108">closeTimeout</span></span>|<span data-ttu-id="154ee-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="154ee-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="154ee-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="154ee-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="154ee-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="154ee-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="154ee-112">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="154ee-112">listenIPAddress</span></span>|<span data-ttu-id="154ee-113">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="154ee-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="154ee-114">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="154ee-114">The default is `null`.</span></span>|  
|<span data-ttu-id="154ee-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="154ee-115">maxBufferPoolSize</span></span>|<span data-ttu-id="154ee-116">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="154ee-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="154ee-117">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="154ee-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="154ee-118">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="154ee-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="154ee-119">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="154ee-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="154ee-120">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="154ee-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="154ee-121">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="154ee-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="154ee-122">Değerini</span><span class="sxs-lookup"><span data-stu-id="154ee-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="154ee-123">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="154ee-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="154ee-124">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="154ee-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="154ee-125">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="154ee-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="154ee-126">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="154ee-126">The default is 65536.</span></span>|  
|<span data-ttu-id="154ee-127">name</span><span class="sxs-lookup"><span data-stu-id="154ee-127">name</span></span>|<span data-ttu-id="154ee-128">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="154ee-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="154ee-129">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="154ee-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="154ee-130">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="154ee-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="154ee-131">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="154ee-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="154ee-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="154ee-132">openTimeout</span></span>|<span data-ttu-id="154ee-133">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="154ee-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="154ee-134">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="154ee-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="154ee-135">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="154ee-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="154ee-136">port</span><span class="sxs-lookup"><span data-stu-id="154ee-136">port</span></span>|<span data-ttu-id="154ee-137">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="154ee-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="154ee-138">Bu değer ve arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="154ee-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="154ee-139">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="154ee-139">The default is 0.</span></span>|  
|<span data-ttu-id="154ee-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="154ee-140">receiveTimeout</span></span>|<span data-ttu-id="154ee-141"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="154ee-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="154ee-142">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="154ee-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="154ee-143">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="154ee-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="154ee-144">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="154ee-144">sendTimeout</span></span>|<span data-ttu-id="154ee-145"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="154ee-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="154ee-146">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="154ee-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="154ee-147">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="154ee-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="154ee-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="154ee-148">Child Elements</span></span>  
  
|<span data-ttu-id="154ee-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="154ee-149">Element</span></span>|<span data-ttu-id="154ee-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="154ee-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="154ee-151">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="154ee-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="154ee-152">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="154ee-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="154ee-153">Bu bağlama tarafından eş ağ içindeki düğümlerin uç nokta IP adreslerine bir eş ağ KIMLIĞINI çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="154ee-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="154ee-154">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="154ee-154">Defines the security settings for the message.</span></span> <span data-ttu-id="154ee-155">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="154ee-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="154ee-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="154ee-156">Parent Elements</span></span>  
  
|<span data-ttu-id="154ee-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="154ee-157">Element</span></span>|<span data-ttu-id="154ee-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="154ee-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="154ee-159">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="154ee-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="154ee-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="154ee-160">Remarks</span></span>  
 <span data-ttu-id="154ee-161">Bu bağlama, TCP üzerinden eş aktarım kullanarak eşler arası veya çok taraflı uygulamalar oluşturmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="154ee-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="154ee-162">Her eş düğüm, bu bağlama türüyle tanımlanmış birden çok eş kanalını barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="154ee-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="154ee-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="154ee-163">Example</span></span>  
 <span data-ttu-id="154ee-164">Aşağıdaki örnek, bir eş kanal kullanarak çok taraflı iletişim sağlayan NetPeerTcpBinding bağlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="154ee-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="154ee-165">Bu bağlamayı kullanmanın ayrıntılı bir senaryosu için bkz. [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="154ee-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="154ee-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="154ee-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="154ee-167">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="154ee-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="154ee-168">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="154ee-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="154ee-169">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="154ee-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="154ee-170">[NET eş TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="154ee-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="154ee-171">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="154ee-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
