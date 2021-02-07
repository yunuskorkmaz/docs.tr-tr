---
description: 'Hakkında daha fazla bilgi edinin: <netPeerTcpBinding>'
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 11f1618236c7219143225e2535e272254af6b81d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683911"
---
# \<netPeerTcpBinding>

<span data-ttu-id="870fb-102">Eş kanala özgü TCP mesajlaşma için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="870fb-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="870fb-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="870fb-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="870fb-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="870fb-104">Attributes and Elements</span></span>  

 <span data-ttu-id="870fb-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="870fb-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="870fb-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="870fb-106">Attributes</span></span>  
  
|<span data-ttu-id="870fb-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="870fb-107">Attribute</span></span>|<span data-ttu-id="870fb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="870fb-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="870fb-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="870fb-109">closeTimeout</span></span>|<span data-ttu-id="870fb-110"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="870fb-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="870fb-111">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="870fb-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870fb-112">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="870fb-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="870fb-113">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="870fb-113">listenIPAddress</span></span>|<span data-ttu-id="870fb-114">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="870fb-114">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="870fb-115">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="870fb-115">The default is `null`.</span></span>|  
|<span data-ttu-id="870fb-116">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="870fb-116">maxBufferPoolSize</span></span>|<span data-ttu-id="870fb-117">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="870fb-117">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="870fb-118">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="870fb-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="870fb-119">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="870fb-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="870fb-120">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="870fb-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="870fb-121">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fb-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="870fb-122">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="870fb-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="870fb-123">Değerini</span><span class="sxs-lookup"><span data-stu-id="870fb-123">maxReceivedMessageSize</span></span>|<span data-ttu-id="870fb-124">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="870fb-124">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="870fb-125">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="870fb-125">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="870fb-126">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="870fb-126">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="870fb-127">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="870fb-127">The default is 65536.</span></span>|  
|<span data-ttu-id="870fb-128">name</span><span class="sxs-lookup"><span data-stu-id="870fb-128">name</span></span>|<span data-ttu-id="870fb-129">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="870fb-129">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="870fb-130">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="870fb-130">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="870fb-131">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="870fb-131">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="870fb-132">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="870fb-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="870fb-133">openTimeout</span><span class="sxs-lookup"><span data-stu-id="870fb-133">openTimeout</span></span>|<span data-ttu-id="870fb-134">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="870fb-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="870fb-135">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="870fb-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870fb-136">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="870fb-136">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="870fb-137">port</span><span class="sxs-lookup"><span data-stu-id="870fb-137">port</span></span>|<span data-ttu-id="870fb-138">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="870fb-138">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="870fb-139">Bu değer ve arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="870fb-139">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="870fb-140">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="870fb-140">The default is 0.</span></span>|  
|<span data-ttu-id="870fb-141">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="870fb-141">receiveTimeout</span></span>|<span data-ttu-id="870fb-142"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="870fb-142">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="870fb-143">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="870fb-143">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870fb-144">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="870fb-144">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="870fb-145">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="870fb-145">sendTimeout</span></span>|<span data-ttu-id="870fb-146"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="870fb-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="870fb-147">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="870fb-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870fb-148">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="870fb-148">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="870fb-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="870fb-149">Child Elements</span></span>  
  
|<span data-ttu-id="870fb-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="870fb-150">Element</span></span>|<span data-ttu-id="870fb-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="870fb-151">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="870fb-152">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="870fb-152">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="870fb-153">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="870fb-153">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="870fb-154">Bu bağlama tarafından eş ağ içindeki düğümlerin uç nokta IP adreslerine bir eş ağ KIMLIĞINI çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="870fb-154">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="870fb-155">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="870fb-155">Defines the security settings for the message.</span></span> <span data-ttu-id="870fb-156">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="870fb-156">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="870fb-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="870fb-157">Parent Elements</span></span>  
  
|<span data-ttu-id="870fb-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="870fb-158">Element</span></span>|<span data-ttu-id="870fb-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="870fb-159">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="870fb-160">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="870fb-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="870fb-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="870fb-161">Remarks</span></span>  

 <span data-ttu-id="870fb-162">Bu bağlama, TCP üzerinden eş aktarım kullanarak eşler arası veya çok taraflı uygulamalar oluşturmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="870fb-162">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="870fb-163">Her eş düğüm, bu bağlama türüyle tanımlanmış birden çok eş kanalını barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="870fb-163">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870fb-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="870fb-164">Example</span></span>  

 <span data-ttu-id="870fb-165">Aşağıdaki örnek, bir eş kanal kullanarak çok taraflı iletişim sağlayan NetPeerTcpBinding bağlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="870fb-165">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="870fb-166">Bu bağlamayı kullanmanın ayrıntılı bir senaryosu için bkz. [net peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="870fb-166">For a detailed scenario of using this binding, see [Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="870fb-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="870fb-167">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="870fb-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="870fb-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="870fb-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="870fb-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="870fb-170">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="870fb-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="870fb-171">[NET eş TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="870fb-171">[Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="870fb-172">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="870fb-172">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
