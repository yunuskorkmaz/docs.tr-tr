---
title: '&lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: d89d0aeb68aed91b28ca7358a6140e171d3b36b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="72a34-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="72a34-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="72a34-103">WS-Federasyon destekleyen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="72a34-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="72a34-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72a34-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="72a34-105">\<bindings></span></span>  
<span data-ttu-id="72a34-106">wsFederationBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="72a34-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a34-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72a34-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72a34-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72a34-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72a34-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72a34-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72a34-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72a34-110">Attributes</span></span>  
  
|<span data-ttu-id="72a34-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="72a34-111">Attribute</span></span>|<span data-ttu-id="72a34-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72a34-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72a34-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="72a34-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="72a34-114">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="72a34-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="72a34-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="72a34-115">The default is `false`.</span></span>|  
|<span data-ttu-id="72a34-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="72a34-116">closeTimeout</span></span>|<span data-ttu-id="72a34-117">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="72a34-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="72a34-118">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72a34-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72a34-119">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="72a34-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="72a34-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="72a34-120">hostnameComparisonMode</span></span>|<span data-ttu-id="72a34-121">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="72a34-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="72a34-122">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="72a34-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="72a34-123">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="72a34-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="72a34-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="72a34-124">maxBufferPoolSize</span></span>|<span data-ttu-id="72a34-125">Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="72a34-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="72a34-126">Varsayılan 524.288 (512 \* 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="72a34-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="72a34-127">Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="72a34-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="72a34-128">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="72a34-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="72a34-129">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="72a34-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="72a34-130">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="72a34-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="72a34-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="72a34-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="72a34-132">Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="72a34-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="72a34-133">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="72a34-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="72a34-134">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72a34-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="72a34-135">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="72a34-135">The default is 65536.</span></span>|  
|<span data-ttu-id="72a34-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="72a34-136">messageEncoding</span></span>|<span data-ttu-id="72a34-137">İleti kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="72a34-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="72a34-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="72a34-139">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="72a34-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="72a34-140">-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="72a34-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="72a34-141">Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="72a34-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="72a34-142">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="72a34-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="72a34-143">name</span><span class="sxs-lookup"><span data-stu-id="72a34-143">name</span></span>|<span data-ttu-id="72a34-144">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="72a34-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="72a34-145">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72a34-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="72a34-146">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72a34-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="72a34-147">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="72a34-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="72a34-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="72a34-148">openTimeout</span></span>|<span data-ttu-id="72a34-149">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="72a34-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="72a34-150">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72a34-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72a34-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="72a34-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="72a34-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="72a34-152">privactyNoticeAt</span></span>|<span data-ttu-id="72a34-153">Gizlilik bildirimi bulunduğu olduğu bir URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="72a34-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="72a34-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="72a34-154">privactyNoticeVersion</span></span>|<span data-ttu-id="72a34-155">Geçerli gizlilik bildirimi sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="72a34-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="72a34-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="72a34-156">proxyAddress</span></span>|<span data-ttu-id="72a34-157">HTTP proxy adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="72a34-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="72a34-158">Varsa `useDefaultWebProxy` olan `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="72a34-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="72a34-159">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="72a34-159">The default is `null`.</span></span>|  
|<span data-ttu-id="72a34-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="72a34-160">receiveTimeout</span></span>|<span data-ttu-id="72a34-161">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="72a34-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="72a34-162">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72a34-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72a34-163">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="72a34-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="72a34-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="72a34-164">sendTimeout</span></span>|<span data-ttu-id="72a34-165">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="72a34-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="72a34-166">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72a34-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72a34-167">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="72a34-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="72a34-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="72a34-168">textEncoding</span></span>|<span data-ttu-id="72a34-169">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="72a34-170">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="72a34-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="72a34-171">-BigEndianUnicode: Unicode BigEndian kodlama.</span><span class="sxs-lookup"><span data-stu-id="72a34-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="72a34-172">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="72a34-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="72a34-173">-UTF8: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="72a34-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="72a34-174">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="72a34-174">The default is UTF8.</span></span> <span data-ttu-id="72a34-175">Bu öznitelik türünde <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="72a34-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="72a34-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="72a34-176">transactionFlow</span></span>|<span data-ttu-id="72a34-177">Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="72a34-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="72a34-178">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="72a34-178">The default is `false`.</span></span>|  
|<span data-ttu-id="72a34-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="72a34-179">useDefaultWebProxy</span></span>|<span data-ttu-id="72a34-180">Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="72a34-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="72a34-181">Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlanmamış) bu özniteliği ise `true`.</span><span class="sxs-lookup"><span data-stu-id="72a34-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="72a34-182">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="72a34-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72a34-183">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72a34-183">Child Elements</span></span>  
  
|<span data-ttu-id="72a34-184">Öğe</span><span class="sxs-lookup"><span data-stu-id="72a34-184">Element</span></span>|<span data-ttu-id="72a34-185">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72a34-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72a34-186">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="72a34-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="72a34-187">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-187">Defines the security settings for the message.</span></span> <span data-ttu-id="72a34-188">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="72a34-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="72a34-189">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="72a34-189">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="72a34-190">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="72a34-191">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="72a34-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="72a34-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="72a34-192">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="72a34-193">Güvenilir oturumlar kanal uç noktaları arasında kurulan olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="72a34-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72a34-194">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72a34-194">Parent Elements</span></span>  
  
|<span data-ttu-id="72a34-195">Öğe</span><span class="sxs-lookup"><span data-stu-id="72a34-195">Element</span></span>|<span data-ttu-id="72a34-196">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72a34-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72a34-197">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="72a34-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="72a34-198">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="72a34-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a34-199">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72a34-199">Remarks</span></span>  
 <span data-ttu-id="72a34-200">Federasyon kimlikleri kimlik doğrulama ve yetkilendirme için birden çok sistemler arasında paylaşmak için yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="72a34-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="72a34-201">Bu kimlikleri, kullanıcılar veya makinelerin başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="72a34-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="72a34-202">Karma mod güvenliği yanı sıra SOAP Güvenliği Federasyon HTTP destekler, ancak özel olarak taşıma güvenliği kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="72a34-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="72a34-203">Bu bağlama WS-Federasyon protokolü için Windows Communication Foundation (WCF) desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="72a34-204">Bu bağlama ile yapılandırılan hizmetler HTTP aktarımı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72a34-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="72a34-205">Bağlamaları bağlama öğelerinin yığınını oluşur.</span><span class="sxs-lookup"><span data-stu-id="72a34-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="72a34-206">Yığın öğelerini bağlama</span><span class="sxs-lookup"><span data-stu-id="72a34-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="72a34-207">`wsFederationHttpBinding` içerdiği aynıdır `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="72a34-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="72a34-208">zaman [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) varsayılan değer olarak ayarlı <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="72a34-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="72a34-209">`wsFederationHttpBinding` İleti güvenlik ayarlarını ayrıntılarını denetimleri [ \<ileti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72a34-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="72a34-210">Unutmayın [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) öğesi bağlama oluşturulduktan sonra yalnızca bağlama tarafından kullanılan güvenlik değiştirilemez olarak get erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="72a34-211">`wsFederationHttpBinding` Ayarlamak ve gizlilik bildirimi bulunduğu URI almak için bir privactyNoticeAt özniteliği de sağlar.</span><span class="sxs-lookup"><span data-stu-id="72a34-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="72a34-212">İlke güvenliğini sağlamanın, Federasyon senaryolarında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72a34-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="72a34-213">İlke kötü amaçlı kullanıcılara karşı korumak için HTTPS gibi güvenlik çeşit kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="72a34-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="72a34-214">Bu bağlama kullanarak Federasyon senaryolarında hizmet ilkesi potansiyel olarak verilen (SAML) belirteç belirtece yerleştirmek ve benzeri için talep türünü şifrelemek için kullanılacak anahtarı gibi önemli bilgileri var.</span><span class="sxs-lookup"><span data-stu-id="72a34-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="72a34-215">Bu ilke değiştirilmiş, bir saldırganın başka oynama, bilgi ifşası ve diğer kötü amaçlı davranışlar yol verilen belirteç anahtarı Bul.</span><span class="sxs-lookup"><span data-stu-id="72a34-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="72a34-216">Bunu önlemek için ilke hizmetinden (HTTPS kullanan güvenli bir şekilde örneğin) olarak alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72a34-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="72a34-217">Bu bağlama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72a34-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72a34-218">Örnek</span><span class="sxs-lookup"><span data-stu-id="72a34-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72a34-219">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72a34-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="72a34-220">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72a34-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="72a34-221">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="72a34-221">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72a34-222">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="72a34-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="72a34-223">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="72a34-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="72a34-224">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="72a34-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
