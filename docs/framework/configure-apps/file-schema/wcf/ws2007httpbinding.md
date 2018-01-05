---
title: '&lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a92ab5b85a65793473dcafbd67ac710912a476f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="169ed-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="169ed-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="169ed-103">Doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="169ed-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="169ed-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="169ed-104">\<system.serviceModel></span></span>  
<span data-ttu-id="169ed-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="169ed-105">\<bindings></span></span>  
<span data-ttu-id="169ed-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="169ed-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169ed-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="169ed-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="169ed-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="169ed-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="169ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="169ed-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="169ed-110">Attributes</span></span>  
  
|<span data-ttu-id="169ed-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="169ed-111">Attribute</span></span>|<span data-ttu-id="169ed-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ed-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="169ed-113">İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="169ed-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="169ed-115">Tanımlama bilgileri kullanan ASP.NET Web Hizmetleri ile (ASMX) etkileşim kurarken, bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="169ed-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="169ed-116">Bu, sunucunun döndürür tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="169ed-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="169ed-117">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="169ed-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="169ed-119">A <xref:System.TimeSpan> tamamlamak bir kapatma işlemi için zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="169ed-120">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="169ed-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="169ed-121">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="169ed-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="169ed-122">Tekdüzen Kaynak Tanımlayıcıları (URI'ler) ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="169ed-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="169ed-123">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="169ed-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="169ed-124">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="169ed-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="169ed-125">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="169ed-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="169ed-126">Varsayılan 524.288 (512 × 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="169ed-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="169ed-127">Birçok bölümlerini [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="169ed-127">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="169ed-128">Çöp toplama arabellekleri için olduğu gibi oluşturma ve her defa arabellek yok etme, pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="169ed-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="169ed-129">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve işiniz bittiğinde havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="169ed-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="169ed-130">Oluşturma ve yok etme arabellekleri yükünü önler.</span><span class="sxs-lookup"><span data-stu-id="169ed-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="169ed-131">Bu bağlama ile yapılandırılan bir kanal alabilir üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="169ed-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="169ed-132">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="169ed-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="169ed-133">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="169ed-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="169ed-134">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="169ed-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="169ed-135">İleti kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="169ed-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="169ed-136">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="169ed-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="169ed-137">-   `Text`: Bir metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="169ed-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="169ed-138">-   `Mtom`: Bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="169ed-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="169ed-139">Varsayılan, `Text` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="169ed-140">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="169ed-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="169ed-141">Bağlama yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="169ed-141">The configuration name of the binding.</span></span> <span data-ttu-id="169ed-142">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="169ed-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="169ed-143">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="169ed-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="169ed-144">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="169ed-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="169ed-145">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="169ed-146">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="169ed-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="169ed-147">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="169ed-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="169ed-148">HTTP proxy adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="169ed-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="169ed-149">Varsa `useSystemWebProxy` olan `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="169ed-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="169ed-150">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="169ed-151">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="169ed-152">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="169ed-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="169ed-153">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="169ed-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="169ed-154">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="169ed-155">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="169ed-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="169ed-156">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="169ed-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="169ed-157">Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="169ed-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="169ed-158">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="169ed-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="169ed-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian kodlama.</span><span class="sxs-lookup"><span data-stu-id="169ed-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="169ed-160">-   `Utf16TextEncoding`: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="169ed-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="169ed-161">-   `Utf8TextEncoding`: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="169ed-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="169ed-162">Varsayılan, `Utf8TextEncoding` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="169ed-163">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="169ed-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="169ed-164">Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="169ed-165">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="169ed-166">Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmayacağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="169ed-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="169ed-167">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="169ed-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="169ed-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ed-168">Child Elements</span></span>  
  
|<span data-ttu-id="169ed-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="169ed-169">Element</span></span>|<span data-ttu-id="169ed-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ed-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="169ed-171">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="169ed-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="169ed-172">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="169ed-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="169ed-173">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="169ed-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="169ed-174">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="169ed-174">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="169ed-175">Bu bağlama ile yapılandırılan uç noktaları işleyebilir SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="169ed-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="169ed-176">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="169ed-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="169ed-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="169ed-177">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="169ed-178">Güvenilir oturumlar kanal uç noktaları arasında kurulan olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="169ed-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="169ed-179">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ed-179">Parent Elements</span></span>  
  
|<span data-ttu-id="169ed-180">Öğe</span><span class="sxs-lookup"><span data-stu-id="169ed-180">Element</span></span>|<span data-ttu-id="169ed-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ed-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="169ed-182">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="169ed-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="169ed-183">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="169ed-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169ed-184">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="169ed-184">Remarks</span></span>  
 <span data-ttu-id="169ed-185">`WS2007HttpBinding` Bir sistem tarafından sağlanan bir bağlamayı benzer ekler `WSHttpBinding` ancak kuruluş terfi, yapılandırılmış bilgi standartları (OASIS) standart sürümleri ReliableSession, güvenlik ve TransactionFlow protokollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="169ed-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="169ed-186">Nesne modeli veya varsayılan ayarlarını herhangi bir değişiklik, bu bağlama kullanılırken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="169ed-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="169ed-187">Örnek</span><span class="sxs-lookup"><span data-stu-id="169ed-187">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="169ed-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="169ed-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="169ed-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="169ed-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="169ed-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="169ed-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="169ed-191">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="169ed-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="169ed-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="169ed-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
