---
description: 'Hakkında daha fazla bilgi edinin: <wsDualHttpBinding>'
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 14a575d867f2fcd3754d28616e8e2b9d3903f1fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682117"
---
# \<wsDualHttpBinding>

<span data-ttu-id="336ff-102">Çift yönlü hizmet sözleşmeleri veya SOAP aracıları üzerinden iletişim için uygun olan güvenli, güvenilir ve birlikte çalışabilen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-102">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="336ff-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="336ff-103">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="336ff-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="336ff-104">Attributes and Elements</span></span>  

 <span data-ttu-id="336ff-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="336ff-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="336ff-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="336ff-106">Attributes</span></span>  
  
|<span data-ttu-id="336ff-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="336ff-107">Attribute</span></span>|<span data-ttu-id="336ff-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ff-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="336ff-109">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="336ff-109">bypassProxyOnLocal</span></span>|<span data-ttu-id="336ff-110">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="336ff-110">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="336ff-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="336ff-111">The default is `false`.</span></span>|  
|<span data-ttu-id="336ff-112">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="336ff-112">clientBaseAddress</span></span>|<span data-ttu-id="336ff-113">Hizmetten gelen yanıt iletileri için istemcinin dinlediği temel adresi ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="336ff-113">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="336ff-114">Belirtilmişse, bu adres (artı bir channelGUID) dinlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="336ff-114">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="336ff-115">Değer belirtilmezse, istemci taban adresi, aktarıma özgü bir şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="336ff-115">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="336ff-116">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="336ff-116">The default is `null`.</span></span>|  
|<span data-ttu-id="336ff-117">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="336ff-117">closeTimeout</span></span>|<span data-ttu-id="336ff-118"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="336ff-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="336ff-119">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="336ff-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="336ff-120">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-120">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="336ff-121">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="336ff-121">hostnameComparisonMode</span></span>|<span data-ttu-id="336ff-122">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ff-122">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="336ff-123">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="336ff-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="336ff-124">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="336ff-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="336ff-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="336ff-125">maxBufferPoolSize</span></span>|<span data-ttu-id="336ff-126">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="336ff-126">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="336ff-127">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="336ff-127">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="336ff-128">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="336ff-128">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="336ff-129">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="336ff-129">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="336ff-130">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="336ff-130">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="336ff-131">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="336ff-131">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="336ff-132">Değerini</span><span class="sxs-lookup"><span data-stu-id="336ff-132">maxReceivedMessageSize</span></span>|<span data-ttu-id="336ff-133">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="336ff-133">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="336ff-134">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="336ff-134">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="336ff-135">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="336ff-135">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="336ff-136">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-136">The default is 65536.</span></span>|  
|<span data-ttu-id="336ff-137">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="336ff-137">messageEncoding</span></span>|<span data-ttu-id="336ff-138">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-138">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="336ff-139">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="336ff-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="336ff-140">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="336ff-140">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="336ff-141">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="336ff-141">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="336ff-142">-Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="336ff-142">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="336ff-143">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="336ff-143">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="336ff-144">name</span><span class="sxs-lookup"><span data-stu-id="336ff-144">name</span></span>|<span data-ttu-id="336ff-145">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="336ff-145">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="336ff-146">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="336ff-146">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="336ff-147">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="336ff-147">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="336ff-148">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="336ff-148">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="336ff-149">openTimeout</span><span class="sxs-lookup"><span data-stu-id="336ff-149">openTimeout</span></span>|<span data-ttu-id="336ff-150">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="336ff-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="336ff-151">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="336ff-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="336ff-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-152">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="336ff-153">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="336ff-153">proxyAddress</span></span>|<span data-ttu-id="336ff-154">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="336ff-154">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="336ff-155">`useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="336ff-155">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="336ff-156">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="336ff-156">The default is `null`.</span></span>|  
|<span data-ttu-id="336ff-157">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="336ff-157">receiveTimeout</span></span>|<span data-ttu-id="336ff-158"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="336ff-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="336ff-159">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="336ff-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="336ff-160">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-160">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="336ff-161">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="336ff-161">sendTimeout</span></span>|<span data-ttu-id="336ff-162"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="336ff-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="336ff-163">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="336ff-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="336ff-164">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="336ff-165">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="336ff-165">textEncoding</span></span>|<span data-ttu-id="336ff-166">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-166">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="336ff-167">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="336ff-167">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="336ff-168">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="336ff-168">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="336ff-169">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="336ff-169">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="336ff-170">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="336ff-170">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="336ff-171">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="336ff-171">The default is UTF8.</span></span> <span data-ttu-id="336ff-172">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="336ff-172">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="336ff-173">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="336ff-173">transactionFlow</span></span>|<span data-ttu-id="336ff-174">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="336ff-174">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="336ff-175">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="336ff-175">The default is `false`.</span></span>|  
|<span data-ttu-id="336ff-176">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="336ff-176">useDefaultWebProxy</span></span>|<span data-ttu-id="336ff-177">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="336ff-177">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="336ff-178">Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="336ff-178">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="336ff-179">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="336ff-179">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="336ff-180">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="336ff-180">Child Elements</span></span>  
  
|<span data-ttu-id="336ff-181">Öğe</span><span class="sxs-lookup"><span data-stu-id="336ff-181">Element</span></span>|<span data-ttu-id="336ff-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ff-182">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="336ff-183">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-183">Defines the security settings for the binding.</span></span> <span data-ttu-id="336ff-184">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="336ff-184">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="336ff-185">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-185">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="336ff-186">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="336ff-186">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="336ff-187">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ff-187">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="336ff-188">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="336ff-188">Parent Elements</span></span>  
  
|<span data-ttu-id="336ff-189">Öğe</span><span class="sxs-lookup"><span data-stu-id="336ff-189">Element</span></span>|<span data-ttu-id="336ff-190">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ff-190">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="336ff-191">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="336ff-191">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336ff-192">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="336ff-192">Remarks</span></span>  

 <span data-ttu-id="336ff-193">, `WSDualHttpBinding` Web hizmeti protokolleri için aynı desteği, `WSHttpBinding` ancak çift yönlü sözleşmelerle birlikte kullanmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="336ff-193">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="336ff-194">`WSDualHttpBinding` yalnızca SOAP güvenliğini destekler ve güvenilir mesajlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="336ff-194">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="336ff-195">Bu bağlama, istemcinin hizmet için bir geri çağırma uç noktası sağlayan ortak bir URI 'ye sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="336ff-195">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="336ff-196">Bu, özniteliği tarafından sağlanır `clientBaseAddress` .</span><span class="sxs-lookup"><span data-stu-id="336ff-196">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="336ff-197">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ff-197">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="336ff-198">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="336ff-198">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="336ff-199">Bu bağlama, bir veya daha fazla SOAP aracıları aracılığıyla güvenilir bir şekilde iletişim kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="336ff-199">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="336ff-200">Bu bağlama, varsayılan olarak, güvenilirlik için WS-ReliableMessaging, ileti güvenliği ve kimlik doğrulaması için WS-Security, ileti teslimi için HTTP ve metin/XML ileti kodlaması içeren bir çalışma zamanı yığını üretir.</span><span class="sxs-lookup"><span data-stu-id="336ff-200">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="336ff-201">Örnek</span><span class="sxs-lookup"><span data-stu-id="336ff-201">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="336ff-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="336ff-202">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="336ff-203">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="336ff-203">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="336ff-204">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="336ff-204">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="336ff-205">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="336ff-205">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
