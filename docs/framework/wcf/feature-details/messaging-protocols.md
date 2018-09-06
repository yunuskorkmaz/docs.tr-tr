---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 3e56636e8364eec333f9585a0f62f6510561d1cc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747765"
---
# <a name="messaging-protocols"></a><span data-ttu-id="d7a6e-102">Mesajlaşma Protokolleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-102">Messaging Protocols</span></span>
<span data-ttu-id="d7a6e-103">Windows Communication Foundation (WCF) kanal yığın kodlama ve taşıma kanalları, kablo biçimini iç ileti gösterimine dönüştürmek ve belirli bir kullanarak göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="d7a6e-104">HTTP Web Hizmetleri birlikte çalışabilirlik için kullanılan en yaygın taşıma olduğunda ve XML tabanlı SOAP 1.1 ve SOAP 1.2 ileti aktarım en iyi duruma getirme mekanizması (MTOM) Web Hizmetleri tarafından kullanılan en yaygın kodlamaları desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="d7a6e-105">Bu konuda WCF tarafından kullanılan şu protokoller için uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="d7a6e-106">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="d7a6e-106">Specification/document</span></span>|<span data-ttu-id="d7a6e-107">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="d7a6e-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="d7a6e-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="d7a6e-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="d7a6e-109">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="d7a6e-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="d7a6e-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="d7a6e-111">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="d7a6e-112">http://www.w3.org/TR/soap12-part2/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="d7a6e-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="d7a6e-113">Şu protokoller için bu konuda WCF uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> uyguluyor.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="d7a6e-114">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="d7a6e-114">Specification/Document</span></span>|<span data-ttu-id="d7a6e-115">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="d7a6e-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="d7a6e-116">XML</span><span class="sxs-lookup"><span data-stu-id="d7a6e-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="d7a6e-117">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="d7a6e-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="d7a6e-118">SOAP 1.2 Çekirdek</span><span class="sxs-lookup"><span data-stu-id="d7a6e-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="d7a6e-119">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="d7a6e-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="d7a6e-120">Adresleme 1.0 - çekirdek W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="d7a6e-121">Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="d7a6e-122">Adresleme 1.0 - WSDL bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="d7a6e-123">Adresleme 1.0 - meta verileri W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="d7a6e-124">WSDL SOAP1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="d7a6e-125">WSDL SOAP1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="d7a6e-126">Şu protokoller için bu konuda WCF uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="d7a6e-127">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="d7a6e-127">Specification/document</span></span>|<span data-ttu-id="d7a6e-128">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="d7a6e-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="d7a6e-129">XOP</span><span class="sxs-lookup"><span data-stu-id="d7a6e-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="d7a6e-130">MTOM + SOAP 1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="d7a6e-131">MTOM SOAP 1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="d7a6e-132">MTOM WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="d7a6e-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="d7a6e-134">Bu konu başlığı altında yaptığımız, aşağıdaki XML ad alanları ve ilişkili ön ekleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="d7a6e-135">Ön eki</span><span class="sxs-lookup"><span data-stu-id="d7a6e-135">Prefix</span></span>|<span data-ttu-id="d7a6e-136">Namespace Tekdüzen Kaynak Tanımlayıcısı (URI)</span><span class="sxs-lookup"><span data-stu-id="d7a6e-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="d7a6e-137">s11</span><span class="sxs-lookup"><span data-stu-id="d7a6e-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="d7a6e-138">s12</span><span class="sxs-lookup"><span data-stu-id="d7a6e-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="d7a6e-139">wsa</span><span class="sxs-lookup"><span data-stu-id="d7a6e-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="d7a6e-140">wsam</span><span class="sxs-lookup"><span data-stu-id="d7a6e-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="d7a6e-141">wsap</span><span class="sxs-lookup"><span data-stu-id="d7a6e-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="d7a6e-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="d7a6e-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="d7a6e-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="d7a6e-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="d7a6e-144">XOP</span><span class="sxs-lookup"><span data-stu-id="d7a6e-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="d7a6e-145">xmime</span><span class="sxs-lookup"><span data-stu-id="d7a6e-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="d7a6e-146">dp</span><span class="sxs-lookup"><span data-stu-id="d7a6e-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="d7a6e-147">SOAP 1.1 ve SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="d7a6e-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="d7a6e-148">Zarf ve Model işleme</span><span class="sxs-lookup"><span data-stu-id="d7a6e-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="d7a6e-149">WCF SOAP 1.1 Zarf işleme temel Profil 1.1 (BP11) ve temel Profil 1.0 (SSBP10) uygular.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="d7a6e-150">1.2 Zarf SOAP12 bölüm 1 aşağıdaki işlem uygulanır SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="d7a6e-151">Bu bölümde BP11 ve SOAP12 bölüm 1 ile ilgili WCF tarafından yapılan belirli uygulama seçimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="d7a6e-152">Zorunlu üstbilgiyi işleme</span><span class="sxs-lookup"><span data-stu-id="d7a6e-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="d7a6e-153">WCF üst işleme işaretlenmiş için kuralları aşağıdaki `mustUnderstand` aşağıdaki farklılıklar nedeniyle SOAP 1.1 ve SOAP 1.2 özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="d7a6e-154">WCF kanalı yığın girdiği bir ileti ile ilişkili bağlama öğeleri, örneğin yapılandırılmış tek tek kanalları, ileti metin kodlama, güvenlik, güvenilir Mesajlaşma ve işlemler tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="d7a6e-155">Her kanal, ilişkili ad alanından üstbilgileri tanır ve bunları anladım olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="d7a6e-156">Bir ileti dağıtıcısı girdikten sonra işlem biçimlendirici ve karşılık gelen ileti/işlem anlaşması ve bunları anladım işaretleri tarafından beklenen üst bilgilerini okur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="d7a6e-157">Dağıtıcı kalan üst bilgileri olmayan anladı ancak olarak işaretlenmiş olup olmadığını doğrular `mustUnderstand` ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="d7a6e-158">İçeren iletileri `mustUnderstand` alıcı hedeflenen üstbilgileri alıcı uygulama kodu tarafından işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="d7a6e-159">Gibi katmanlı işleme altyapısı katmanları ve SOAP düğümünün uygulama katmanları arasında ayrım sağlar:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="d7a6e-160">B1111: değil anlaşılan üst bilgileri WCF altyapısı kanal yığını tarafından ileti işlendikten sonra ancak uygulama tarafından işlenmeden önce algılanan</span><span class="sxs-lookup"><span data-stu-id="d7a6e-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="d7a6e-161">`mustUnderstand` Üstbilgi değeri SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="d7a6e-162">Temel Profil 1.1 gerektirir `mustUnderstand` değeri SOAP 1.1 iletileri için 0 veya 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="d7a6e-163">SOAP 1.2 izin verir, 0, 1, `false`, ve `true` gibi değerler, ancak kurallı bir temsilini yayma önerir `xs:boolean` değerleri (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="d7a6e-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="d7a6e-164">B1112: WCF yayan `mustUnderstand` SOAP zarfının değerleri 0 ile 1 hem SOAP 1.1 ve SOAP 1.2 sürümleri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="d7a6e-165">WCF kabul ettiği tüm değerini alan `xs:boolean` için `mustUnderstand` üst bilgisi (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="d7a6e-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="d7a6e-166">SOAP hataları</span><span class="sxs-lookup"><span data-stu-id="d7a6e-166">SOAP Faults</span></span>  
 <span data-ttu-id="d7a6e-167">WCF özel SOAP hatası uygulamalarının listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="d7a6e-168">B2121: WCF aşağıdaki SOAP 1.1 hata kodlarını döndürür: `s11:mustUnderstand`, `s11:Client`, ve `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="d7a6e-169">B2122: WCF aşağıdaki SOAP 1.2 hata kodlarını döndürür: `s12:MustUnderstand`, `s12:Sender`, ve `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="d7a6e-170">HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="d7a6e-171">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="d7a6e-172">WCF ile aşağıdaki Açıklamalar bölümüne 3.4 temel Profil 1.1 belirtiminden SOAP1.1 HTTP bağlaması uygular:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="d7a6e-173">B2211: WCF hizmeti, HTTP POST istekleri yeniden yönlendirme uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="d7a6e-174">B2212: WCF istemcileri 3.4.8 uygun olarak HTTP tanımlama bilgileri destekler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="d7a6e-175">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="d7a6e-176">WCF SOAP 1.2 HTTP bağlaması SOAP 1.2-Bölüm 2 (SOAP12Part2) belirtimiyle aşağıdaki açıklamalar bölümünde anlatıldığı gibi uygular.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="d7a6e-177">SOAP 1.2 bir isteğe bağlı eylem parametresi için sunulan `application/soap+xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="d7a6e-178">Bu parametre, WS-Addressing kullanılmadığında SOAP iletisinin gövdesini ayrıştırılması gerek kalmadan ileti gönderme en iyi duruma getirmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="d7a6e-179">R2221: `application/soap+xml` eylem parametresi SOAP 1.2 istek üzerine varsa eşleşmelidir `soapAction` özniteliği `wsoap12:operation` içinde karşılık gelen WSDL bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="d7a6e-180">R2222: `application/soap+xml` eylem parametresi varsa bir SOAP 1.2 iletinin eşleşmelidir `wsa:Action` WS-Addressing 2004/08 veya WS-Addressing 1.0 ne zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="d7a6e-181">WS-Addressing devre dışı ve gelen bir istek, bir eylem parametresinin içermiyor, ileti `Action` belirtilen olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="d7a6e-182">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="d7a6e-182">WS-Addressing</span></span>  
 <span data-ttu-id="d7a6e-183">WCF WS-Addressing 3 versiyonunu uygular:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="d7a6e-184">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="d7a6e-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="d7a6e-185">W3C Web Hizmetleri 1.0 çekirdek (çekirdek ADDR10) ve SOAP (ADDR10 SOAP) bağlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="d7a6e-186">WS-Addressing 1.0 - meta verileri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="d7a6e-187">Uç nokta başvuruları</span><span class="sxs-lookup"><span data-stu-id="d7a6e-187">Endpoint References</span></span>  
 <span data-ttu-id="d7a6e-188">WCF uygulayan WS-Addressing tüm sürümlerinde uç nokta başvuruları uç noktaları tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="d7a6e-189">Uç nokta başvurular ve WS-Addressing sürümleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="d7a6e-190">WCF altyapısı kurallarının WS-Addressing kullanın ve belirli bir sayı uygulayan `EndpointReference` öğesi ve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="d7a6e-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="d7a6e-191">WCF WS-Addressing diğer altyapı protokollerle iki sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="d7a6e-192">WCF bitiş noktalarını, uç noktası başına bir sürümü, WS-Addressing destekler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="d7a6e-193">R3111, ad alanı için `EndpointReference` öğesi veya bir WCF uç noktasıyla alınıp verilen iletileri kullanılan türü-bu bitiş noktası tarafından uygulanan WS Addressing sürümü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="d7a6e-194">Örneğin, bir WCF uç noktası WS-ReliableMessaging uyguluyorsa `AcksTo` üst bilgisi içinde bir tür bir uç nokta tarafından döndürülen `CreateSequenceResponse` WS-Addressing sürümü kullanır, `EncodingBinding` öğesi için bu endpoint belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="d7a6e-195">Uç nokta başvurular ve meta verileri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="d7a6e-196">Birçok senaryoda meta verileri veya belirli bir uç nokta için meta veri başvurusu iletişim kurmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="d7a6e-197">B3121: WCF 6. Bölüm değere veya başvuruya göre meta veri uç noktası başvurular eklemek için WS-MetadataExchange (MEX) belirtiminde açıklanan mekanizmalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="d7a6e-198">Burada bir WCF Hizmeti belirteci veren tarafından verilen bir güvenlik onaylama işaretleme dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirir bir senaryo düşünün http://sts.fabrikam123.com.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com.</span></span> <span data-ttu-id="d7a6e-199">WCF uç noktayı kullanarak bu kimlik doğrulama gereksinimini açıklar `sp:IssuedToken` onaylama işlemi bir iç içe `sp:Issuer` onaylama için belirteç verenin işaret eden.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-199">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="d7a6e-200">Erişen istemci uygulamalar `sp:Issuer` onaylama belirteci veren uç noktası ile iletişim kurma bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-200">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="d7a6e-201">İstemcinin meta veri belirteci veren hakkında bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-201">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="d7a6e-202">WCF MEX içinde tanımlanan uç nokta başvurusu meta verileri uzantıları kullanarak, belirteci veren meta verilerine bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-202">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a><span data-ttu-id="d7a6e-203">İleti Addressing üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-203">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="d7a6e-204">İleti üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-204">Message Headers</span></span>  
 <span data-ttu-id="d7a6e-205">WS-Addressing iki sürümü de WCF aşağıdaki ileti üstbilgilerini belirtimleri tarafından belirtilen şekilde kullanır `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, ve `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-205">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="d7a6e-206">B3211: Tüm sürümler, WS-Addressing WCF geliştirir. ancak kullanıma hazır, WS-Addressing ileti üstbilgileri üretmez `wsa:FaultTo` ve `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-206">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="d7a6e-207">Bu ileti üstbilgileri ve WCF uygun şekilde işleyecek etkileşim kuran uygulamaları ile WCF uygulamaları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-207">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="d7a6e-208">Başvuru parametreleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-208">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="d7a6e-209">WCF Bitiş noktası başvuru parametreleri ve başvuru p işlenmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-209">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="d7a6e-210">ilgili özellikleri uygun şekilde özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-210">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="d7a6e-211">B3221: WS-Addressing 2004/08 kullanmak için yapılandırıldığında, WCF bitiş noktalarını işlem başvurusu özellikleri ve başvuru parametreleri arasında ayrım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-211">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="d7a6e-212">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-212">Message Exchange Patterns</span></span>  
 <span data-ttu-id="d7a6e-213">Web hizmeti işlemi çağrısını ilgili iletiler dizisini olarak adlandırılır *ileti değişim deseni*.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-213">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="d7a6e-214">WCF destekleyen tek yönlü ve istek-yanıt çift yönlü ileti desenleri exchange.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-214">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="d7a6e-215">Bu bölümde kullanılan ileti değişim deseni bağlı olarak işlenen ileti üzerinde WS-Addressing gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-215">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="d7a6e-216">Bu bölümde boyunca ilk iletiyi istek gönderir ve Yanıtlayıcı ilk iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-216">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="d7a6e-217">Tek yönlü mesaj</span><span class="sxs-lookup"><span data-stu-id="d7a6e-217">One-Way Message</span></span>  
 <span data-ttu-id="d7a6e-218">İletileri desteklemek üzere WCF uç noktasını yapılandırıldığında bir verilen `Action` tek yönlü bir yapıdadır WCF uç noktası aşağıdaki davranışları ve gereksinimleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-218">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="d7a6e-219">Aksi belirtilmediği sürece, hem WS Addressing-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-219">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="d7a6e-220">R3311: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`ve uç nokta başvurusu tarafından belirtilen tüm başvuru parametreleri için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-220">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="d7a6e-221">WS-Addressing 2004/08 kullanılır ve [başvurusu Özellikleri] belirtilen uç nokta başvurusu tarafından ilgili üst bilgiler iletiye çok eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-221">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="d7a6e-222">B3312: İstek sahibinin içerebilir `MessageID`, `ReplyTo`, ve `FaultTo` üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-222">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="d7a6e-223">Alıcı altyapı bunları yoksayar ve uygulamaya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-223">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="d7a6e-224">R3313: HTTP kullanılır ve HTTP yanıt oluşturan üzerinde gönderilen ileti, Yanıtlayıcı boş gövdesi ve 202 HTTP durum kodu ile bir HTTP yanıtı göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-224">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="d7a6e-225">HTTP taşıma kullanımda ve bir ileti tek yönlü işlem anlaşması bildirir, HTTP yanıtı hala altyapı iletileri göndermek için kullanılabilir — örneğin, güvenilir ileti göndermek için bir `SequenceAcknowledgement` bir HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-225">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="d7a6e-226">B3314: WCF Yanıtlayıcı bir hata iletisi tek yönlü bir iletiye yanıt olarak göndermez.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-226">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="d7a6e-227">İstek-Yanıt</span><span class="sxs-lookup"><span data-stu-id="d7a6e-227">Request-Reply</span></span>  
 <span data-ttu-id="d7a6e-228">Bir ileti ile WCF uç noktasını yapılandırıldığında bir verilen `Action` istek-yanıt desenler izleyen WCF uç nokta davranışları ve aşağıdaki gereksinimleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-228">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="d7a6e-229">Aksi belirtilmediği sürece, hem WS Addressing-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-229">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="d7a6e-230">R3321: İstek sahibinin isteği içermelidir `wsa:To`, `wsa:Action`, `wsa:MessageID`ve tüm başvuru parametreleri başvuru özellikler (veya her ikisi) uç noktası başvuru tarafından belirtilen için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-230">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="d7a6e-231">R3322: WS-Addressing 2004/08 kullanıldığında `ReplyTo` ayrıca isteğinde bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-231">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="d7a6e-232">R3323: WS-Addressing 1.0 kullanıldığında ve `ReplyTo` isteğindeki eşit [address] özelliği ile bir varsayılan uç nokta başvurusu yok "http://www.w3.org/2005/08/addressing/anonymous" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-232">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="d7a6e-233">R3324: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`, ve `wsa:RelatesTo` tüm başvuru parametreleri başvuru özellikler (veya her ikisi) tarafından belirtilen üstbilgileri yanı sıra yanıt iletisinin üstbilgilerini `ReplyTo` uç nokta başvurusu İstek.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-233">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="d7a6e-234">Adres hatası Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7a6e-234">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="d7a6e-235">R3411: WCF WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hatalar üretir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-235">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="d7a6e-236">Kod</span><span class="sxs-lookup"><span data-stu-id="d7a6e-236">Code</span></span>|<span data-ttu-id="d7a6e-237">Sebep</span><span class="sxs-lookup"><span data-stu-id="d7a6e-237">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d7a6e-238">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="d7a6e-238">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="d7a6e-239">İle iletinin geldiği bir `ReplyTo` bu kanal için oluşturulan yanıt adresi farklıdır; için üst bilgisinde belirtilen adreste dinleme bitiş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="d7a6e-240">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="d7a6e-240">wsa:ActionNotSupported</span></span>|<span data-ttu-id="d7a6e-241">Altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcısı, belirtilen eylem algılamaz `Action` başlığı.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-241">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="d7a6e-242">R3412: WCF WS-Addressing 1.0 tarafından tanımlanan aşağıdaki hatalar üretir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-242">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="d7a6e-243">Kod</span><span class="sxs-lookup"><span data-stu-id="d7a6e-243">Code</span></span>|<span data-ttu-id="d7a6e-244">Sebep</span><span class="sxs-lookup"><span data-stu-id="d7a6e-244">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d7a6e-245">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="d7a6e-245">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="d7a6e-246">Yinelenen `wsa:To`, `wsa:ReplyTo`, `wsa:From` veya `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-246">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="d7a6e-247">Yinelenen `wsa:RelatesTo` aynı `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-247">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="d7a6e-248">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="d7a6e-248">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="d7a6e-249">Gerekli Addressing üst bilgisi eksik.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-249">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="d7a6e-250">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="d7a6e-250">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="d7a6e-251">İle iletinin geldiği bir `ReplyTo` , bu kanal için oluşturulan yanıt adresi farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-251">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="d7a6e-252">Uç nokta için üst bilgisinde belirtilen adreste dinleme yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-252">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="d7a6e-253">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="d7a6e-253">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="d7a6e-254">Belirtilen eylem `Action` üstbilgi altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcı tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-254">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="d7a6e-255">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="d7a6e-255">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="d7a6e-256">RM kanal uç nokta değil incelenmesi göre sırası işleme gösteren bu hata yeniden gönderir `CreateSequence` ileti adresleme üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-256">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="d7a6e-257">Yukarıdaki tablolarda kod eşlemeleri için `FaultCode` SOAP 1.1 içinde ve `SubCode` (gönderici ile kod =) SOAP 1.2 içinde.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-257">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="d7a6e-258">WSDL 1.1 bağlama ve WS-Policy onaylar</span><span class="sxs-lookup"><span data-stu-id="d7a6e-258">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="d7a6e-259">WS-Addressing kullanımını gösteren</span><span class="sxs-lookup"><span data-stu-id="d7a6e-259">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="d7a6e-260">WCF ilke onaylamalarını belirli bir WS-Addressing sürümü için uç nokta destek belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-260">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="d7a6e-261">Aşağıdaki ilke onaylama, uç noktası İlkesi konu WS-PA ve WS-Addressing 2004/08 uç noktasından alınan iletileri kullanmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-261">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="d7a6e-262">Bu ilke onaylama WS-Addressing 2004/08 belirtimi artırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-262">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="d7a6e-263">Bu, gönderilen/alınan iletileri gösterir. aşağıdaki ilke onaylama, WS-Addressing 1.0 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-263">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="d7a6e-264">Aşağıdaki ilke onay uç noktası İlkesi konu WS-PA ve WS-Addressing 2004/08 uç noktasından alınan iletileri kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-264">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="d7a6e-265">`wsaw10:UsingAddressing` Öğesi [WS-Addressing-WSDL'den] ödünç ve WS-Policy bağlamında bu belirtimini uyduğunuzu kullanılır, Bölüm 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-265">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="d7a6e-266">Adresleme kullanımını WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP bağlamaları semantiği değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-266">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="d7a6e-267">Adresleme ve WSDL SOAP 1.x HTTP bağlaması kullanan bir uç noktasına gönderilen bir istek için yanıt bekleniyorsa, örneğin, yanıtı HTTP yanıt kullanarak gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-267">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="d7a6e-268">Http yanıtı gönderilen yanıtlar için WS-AM onaylama işlemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-268">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="d7a6e-269">Tam İlkesi onayını şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-269">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="d7a6e-270">Ancak, istekte bulunan taraf ile Yanıtlayıcı Yanıtlayıcı tarafından gönderilen Örneğin, istenmeyen tek yönlü iletileri arasında kurulan iki bağımsız listesiyse HTTP bağlantılarını kalmamasını fayda ileti exchange desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-270">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="d7a6e-271">WCF tarafından bileşik çift yönlü kanalı burada bir kanalın giriş iletileri için kullanılır ve diğer çıkış iletileri için kullanılan iki temel taşıma kanalları oluşturabilir bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-271">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="d7a6e-272">HTTP taşıma söz konusu olduğunda bileşik çift yönlü iki ters HTTP bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-272">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="d7a6e-273">İstek sahibinin Yanıtlayıcı için ileti göndermek için bir bağlantı kullanır ve Yanıtlayıcı diğer istemciye iletileri geri göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-273">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="d7a6e-274">Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am olaydır</span><span class="sxs-lookup"><span data-stu-id="d7a6e-274">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="d7a6e-275">Tam İlkesi onayını şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-275">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="d7a6e-276">Yanıtlayıcı ve Yanıtlayıcı istekte bulunan taraf için talep sahibinin akan iletileri için kullanılacak iki ayrı listesiyse HTTP bağlantısı uç noktası İlkesi konu WS-PA WSDL 1.1 SOAP 1.x HTTP bağlantıları kullanan Uç noktalara sahip aşağıdaki onay gerektirir, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-276">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="d7a6e-277">Önceki deyim aşağıdaki gereksinimlere müşteri adayları `wsa:ReplyTo` istek iletilerinin üstbilgisi:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-277">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="d7a6e-278">R3514: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit değildir "http://www.w3.org/2005/08/addressing/anonymous" uç noktası ile bir ilke alternatif bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve varsa bir `wsap10:UsingAddressing` veya `wsap:UsingAddressing` onaylama işlemi eşleşmiş ile `cdp:CompositeDuplex` bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-278">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="d7a6e-279">R3515: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous", veya bir `ReplyTo` tümü, uç nokta bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif varsa üst bilgisi ile `wsap10:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-279">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="d7a6e-280">R3516: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle bir `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous" uç noktası ile bir ilke alternatif bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve varsa `wsap:UsingAddressing` onaylama ve hiçbir `cdp:CompositeDuplex`bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-280">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="d7a6e-281">Bir öğe sunarak benzer protokolü bağlamaları tanımlamak WS-addressing WSDL belirtimi çalışır `<wsaw:Anonymous/>` değerlerle üzerinde gereksinimleri belirtmek için üç metin (gerekli, isteğe bağlı ve yasaklanmış) `wsa:ReplyTo` üst bilgisi (Bölüm 3.2).</span><span class="sxs-lookup"><span data-stu-id="d7a6e-281">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="d7a6e-282">Ne yazık ki, bu tür bir öğe onaylama kullanarak alternatifleri kesişimi desteklemek için etki alanına özgü uzantıları gerektirdiğinden tür öğe tanımı özellikle, WS-Policy bağlamında onaylama kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-282">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="d7a6e-283">Böyle bir öğe tanımı değerini de gösterir. `ReplyTo` HTTP aktarımı belirli kolaylaştırır Tel üzerinde uç nokta davranışı aksine başlığı.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-283">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="d7a6e-284">Eylem tanımı</span><span class="sxs-lookup"><span data-stu-id="d7a6e-284">Action Definition</span></span>  
 <span data-ttu-id="d7a6e-285">WS-Addressing 2004/08 tanımlayan bir `wsa:Action` özniteliğini `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-285">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="d7a6e-286">WS-Addressing 1.0 WSDL bağlama (WS-ADDR10-WSDL) benzer bir öznitelik tanımlar `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-286">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="d7a6e-287">İkisi arasındaki tek fark, sırasıyla bölümü, WS-ADDR 3.3.2 ve WS-ADDR10-WSDL 4.4.4 bölümünde açıklanan varsayılan eylem deseni semantiği ' dir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-287">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="d7a6e-288">Aynı paylaşan iki uç nokta uygun olan `portType` (veya WCF terminolojisinde sözleşme) ancak WS-Addressing'ın farklı sürümleri kullanılarak.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-288">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="d7a6e-289">Ancak bu eylem tarafından tanımlanan koşuluyla, `portType` ve uygulayan uç noktalar genelinde değiştirmemelisiniz `portType`, her iki varsayılan eylem desenleri desteklemesini mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-289">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="d7a6e-290">WCF bu controversy çözmek için tek bir sürümünü destekler `Action` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-290">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="d7a6e-291">B3521: WCF kullanan `wsaw10:Action` özniteliği `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-belirlemek için WSDL içinde tanımlanan öğeleri `Action` bitiş noktası tarafından kullanılan WS-Addressing sürümü bakılmaksızın karşılık gelen iletiler için URI.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-291">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="d7a6e-292">Kullanım uç nokta başvurusu iç WSDL bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="d7a6e-292">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="d7a6e-293">WS ADDR10 WSDL bölümü 4.1 genişletir `wsdl:port` içerecek şekilde öğesi `<wsa10:EndpointReference…/>` WS-Addressing bağlamında uç noktayı tanımlamak için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-293">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="d7a6e-294">WCF üzerinde WS-Addressing 2004/08, bu yardımcı genişletir izin vererek `<wsa:EndpointReference…/>` bir alt öğesi olarak görüntülenmesini `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-294">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="d7a6e-295">R3531: eklenen ilke alternatif bir uç nokta varsa, bir `<wsaw10:UsingAddressing/>` İlkesi onayını, karşılık gelen `wsdl:port` öğesi bir alt öğe içerebilir `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-295">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="d7a6e-296">R3532: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzeyin özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-296">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="d7a6e-297">R3533: eklenen ilke alternatif bir uç nokta varsa `<wsap:UsingAddressing/>` İlkesi onayını, karşılık gelen `wsdl:port` öğesi bir alt öğe içerebilir `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-297">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="d7a6e-298">R3534: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzeyin özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-298">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="d7a6e-299">WS-güvenlik ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7a6e-299">Composition with WS-Security</span></span>  
 <span data-ttu-id="d7a6e-300">WS-ADDR ve WS-ADDR10 göre güvenlik göz önünde bulundurarak bölümlerde, tüm adres ileti üstbilgileri ileti gövdesi ile birlikte birbirine bağlamak için oturum açmış olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-300">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="d7a6e-301">WS-güvenlik ileti bütünlük koruması için kullanıldığında, WS-Addressing ileti üstbilgileri ve bunun yanı sıra üstbilgileri başvuru parametreleri veya özellikleri (veya her ikisi de) sonuçlandı ileti gövdesi ile birlikte oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-301">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d7a6e-302">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d7a6e-302">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="d7a6e-303">Tek yönlü mesaj</span><span class="sxs-lookup"><span data-stu-id="d7a6e-303">One-Way Message</span></span>  
 <span data-ttu-id="d7a6e-304">Bu senaryoda, gönderenin alıcı için tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-304">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="d7a6e-305">SOAP 1.2, HTTP 1.1 ve 1.0, W3C WS-Addressing kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-305">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="d7a6e-306">İstek iletisi yapısı: İleti üstbilgilerini içeren `wsa10:To` ve `wsa10:Action` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-306">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="d7a6e-307">Belirli bir ileti gövdesini içeren `<app:Ping>` uygulama ad alanından öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-307">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="d7a6e-308">HTTP üstbilgileri: POST hedef URI eşleşen `wsa10:To` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-308">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="d7a6e-309">Content-Type üstbilgisi değeri olan `application/soap+xml` SOAP 1.2 gerektirdiği.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-309">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="d7a6e-310">Parametreleri `charset` ve `action` dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-310">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="d7a6e-311">`action` Content-Type üstbilgisi parametresinin değerini eşleşen `wsa10:Action` ileti üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-311">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 <span data-ttu-id="d7a6e-312">Alıcı, bir boş bir HTTP yanıtı ve durum 202 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-312">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="d7a6e-313">HTTP yanıt örneği:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-313">An example of the HTTP response:</span></span>  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="d7a6e-314">SOAP ileti aktarım en iyi duruma getirme mekanizması</span><span class="sxs-lookup"><span data-stu-id="d7a6e-314">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="d7a6e-315">Bu bölümde, HTTP SOAP MTOM için WCF uygulama ayrıntılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-315">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="d7a6e-316">MTOM, SOAP ileti kodlama mekanizması geleneksel metin/XML kodlama veya WCF ikili kodlama aynı sınıfta teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-316">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="d7a6e-317">MTOM aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-317">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="d7a6e-318">Bir XML encoding ve paketleme mekanizması [XOP] tarafından açıklanan ikili ayrı bölümlere base64 ile kodlanmış ikili verileri içeren XML bilgi öğeleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-318">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="d7a6e-319">Bir MIME kapsülleme XOP paketinin XML bilgi kümesi ve her ikili XOP paketin parçası ayrı bir MIME bölümü serileştirir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-319">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="d7a6e-320">SOAP için uygulanan bir MIME XOP kodlama 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-320">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="d7a6e-321">HTTP aktarım bağlama.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-321">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="d7a6e-322">MTOM olmayan HTTP taşımaları WCF ile kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-322">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="d7a6e-323">Ancak, bu konudaki şu HTTP üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-323">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="d7a6e-324">MTOM biçim belirtimleri MTOM kendisi, XOP ve MIME kapsayan çok sayıda yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-324">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="d7a6e-325">Bu belirtimi kümesi tanılanmasını biçimi ve işleme semantiğine gereksinimlerinin tamamı yeniden oluşturmak biraz zor yapar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-325">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="d7a6e-326">Bu bölümde MTOM HTTP bağlaması biçimi ve işleme gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-326">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="d7a6e-327">İleti MTOM kodlama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-327">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="d7a6e-328">MTOM iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7a6e-328">Generating MTOM messages</span></span>  
 <span data-ttu-id="d7a6e-329">[XOP] bölümü 3.1 bağlamalarında tanımlanmış bir XOP pakete base64 değerler içeren öğe bilgi öğelerle XML kodlama işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-329">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="d7a6e-330">Aşağıdaki adımlar dizisini özel MTOM kodlama işlemi açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-330">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="d7a6e-331">Kodlanmış SOAP Zarfı ile hiçbir öğe bilgi öğe içerdiğinden emin olun bir `[namespace name]` , "http://www.w3.org/2004/08/xop/include" ve `[local name]` , `Include`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-331">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="d7a6e-332">Boş bir MIME paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-332">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="d7a6e-333">Orijinal XML bilgi kümesi içinde en iyi duruma getirilmesi öğesi bilgi öğelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-333">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="d7a6e-334">Öğeleri en iyi duruma getirilmesi karakter oluşturan `[children]` öğesi bilgilerini öğenin kurallı biçiminde olması gerekir `xs:base64Binary` (bkz XSD-2, 3.2.16 base64Binary) ve, satır içi, önceki herhangi bir boşluk karakteri içermemelidir veya boşluk olmayan içeriği takip.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-334">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>  
  
4.  <span data-ttu-id="d7a6e-335">Özgün SOAP Zarfı kopyası olan bir XOP SOAP Zarfı oluşturun, ancak her öğe bilgileri çocuğunu önceki adımda tanımlanan öğe yerine bir `xop:Include` öğe bilgi öğe şu şekilde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-335">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="d7a6e-336">Değiştirilen karakter ikili verileri, base64 kodlu veriler olarak işleyerek dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-336">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="d7a6e-337">R3133 ve R3134 gereksinimlerini karşılayan benzersiz bir Content-ID üst bilgi değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-337">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="d7a6e-338">MIME içerik Transfer-Encoding üstbilgi ikili değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-338">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="d7a6e-339">Öğe bilgileri öğe iyileştirilen, ([üst] yeni eklenen `xop:Include` öğe bilgi öğe) sahip bir `xmime:contentType` öznitelik bilgisi öğesi, değeri ile bir MIME Content-Type üstbilgisini oluşturmak `xmime:contentType` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-339">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="d7a6e-340">Yeni bir ikili MIME bölümü, işlenen base64 4b Content-ID başlığından, üst bilgi içeriği Transfer-Encoding 4 c, adım 4 d oluşturursa Content-Type üst bilgisi olarak değiştirilen karakter gelen çözülmüş ikili verileri tarafından oluşturulmuş içerik ile oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-340">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="d7a6e-341">Ekleme bir `href` özniteliğini `xop:Include` değeri CID öğeyle: Content-ID üst bilgi değeri adım 4b'de oluşturulan URI türetilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-341">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="d7a6e-342">Kapsayan Kaldır "\<" ve ">" karakterleri, URL-kalan dize ve ön ek Ekle kaçış `cid:`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-342">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="d7a6e-343">Aşağıdaki en düşük karakter kümesi RFC1738 ve RFC2396 tarafından Atlanan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-343">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="d7a6e-344">Diğer karakterler Atlanan.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-344">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="d7a6e-345">Adım 4'teki XOP SOAP Zarfı ile bir kök MIME bölümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-345">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="d7a6e-346">HTTP Content-Type üst bilgisi dahil olmak üzere HTTP üst bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-346">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="d7a6e-347">MIME paket yazın.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-347">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="d7a6e-348">MTOM iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="d7a6e-348">Processing MTOM messages</span></span>  
 <span data-ttu-id="d7a6e-349">Bir MTOM işleme iletisi tam önceki açıklanan işlemi tersidir "oluşturma MTOM iletileri" bölümünde:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-349">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="d7a6e-350">MIME bölümü kök Content-Type olduğundan `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-350">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="d7a6e-351">SOAP Zarfı MIME bölümü bir XML belgesi olarak paketin kök ayrıştırarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-351">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="d7a6e-352">Karakter kodlamasını göre belirlenir `charset` Content-Type MIME bölümü kök parametresi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-352">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="d7a6e-353">Oluşturulan SOAP Zarfı içinde her öğe bilgi öğe için olan, kendi [alt] özelliğini tek üyesi olarak bir `xop:Include` öğe bilgi öğe:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-353">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="d7a6e-354">Kaldırma `cid:` önek ve tüm URI kaçış dizileri (RFC 2396) değerini unescape `@href` özniteliği `xop:Include` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-354">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="d7a6e-355">Sonuç dizesinde alın "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="d7a6e-355">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="d7a6e-356">Adım 3a adımında türetilmiş dizesiyle eşleşen Content-ID üst bilgi değeri ile MIME bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-356">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="d7a6e-357">Değiştirin `xop:Include` görünür öğe bilgi öğe `children` özellik kurallı base64 kodlama temsil eden karakter bilgi öğeleri ile her bir öğenin (bkz XSD-2, 3.2.16 base64Binary) varlık gövdesinin MIME bölümü Adım 3b içinde tanımlanan (etkili bir şekilde değiştirin `xop:Include` paket bölümünden reconstructed veri öğesi bilgi öğe).</span><span class="sxs-lookup"><span data-stu-id="d7a6e-357">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="d7a6e-358">HTTP Content-Type üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="d7a6e-358">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="d7a6e-359">Aşağıdaki biçimi için WCF açıklamalar MTOM belirtimini içinde belirtilen gereksinimleri türetilen bir SOAP iletisinin 1.x MTOM kodlu HTTP Content-Type üstbilgisinin bir listesidir ve MTOM ve RFC 2387 türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-359">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="d7a6e-360">R4131: Bir HTTP Content-Type üstbilgisi değeri multipart/related (büyük-küçük harf duyarsız) ve parametreleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-360">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="d7a6e-361">Parametre adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-361">Parameter names are case-insensitive.</span></span> <span data-ttu-id="d7a6e-362">Parametre sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-362">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="d7a6e-363">Content-Type üstbilgisi MIME iletileri için tam Backus-Naur Form (BNF) bölümü 5.1, RFC 2045 listelenir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-363">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="d7a6e-364">R4132: Bir HTTP Content-Type üstbilgisi değeri ile bir tür parametresi olmalıdır `application/xop+xml` çift tırnak işareti içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-364">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="d7a6e-365">Çift tırnak işareti kullanma gereksinimi RFC 2387 açık olsa da, tüm multipart/related medya tür parametreleri büyük olasılıkla gibi ayrılmış karakterler içeren metin uygulamasını gözlediğini "\@" veya "/" ve bu nedenle çift tırnak gerekir işaretler.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-365">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="d7a6e-366">R4133: Başlangıç parametresi SOAP içeren MIME bölümünün içerik kimliği-üstbilgisinin değeri ile bir HTTP Content-Type üst bilgisi olmalıdır 1.x Zarf çift tırnak işareti içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-366">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="d7a6e-367">Başlangıç parametresi atlanırsa, SOAP ilk MIME bölümü içermelidir 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-367">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="d7a6e-368">R4134: Kodlanmış SOAP 1.1 MTOM iletisi için bir HTTP Content-Type üstbilgisi değeri çift tırnak işaretleri arasına metin/XML, başlangıç bilgileri parametresiyle içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-368">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="d7a6e-369">R4135: SOAP 1.2 MTOM olarak kodlanmış bir ileti için bir HTTP Content-Type üstbilgisi değeri başlangıç bilgileri parametresiyle içermelidir `application/soap+xml`çift tırnak işareti içine alınan.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-369">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="d7a6e-370">R4136: MTOM kodlanmış SOAP 1.x iletisi için HTTP Content-Type üstbilgisi sınır parametresi BNF RFC 2046, 5.1.1 bölümünde tanımlanmış MIME sınır eşleşen (çift tırnak işareti içine alınmış) değerine sahip olması gerekir</span><span class="sxs-lookup"><span data-stu-id="d7a6e-370">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="d7a6e-371">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-371">Examples:</span></span>  
  
     <span data-ttu-id="d7a6e-372">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="d7a6e-372">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="d7a6e-373">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="d7a6e-373">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="d7a6e-374">YANLIŞ</span><span class="sxs-lookup"><span data-stu-id="d7a6e-374">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="d7a6e-375">Bilgi kümesi MIME bölümü</span><span class="sxs-lookup"><span data-stu-id="d7a6e-375">Infoset MIME Part</span></span>  
 <span data-ttu-id="d7a6e-376">SOAP Zarfı XOP MIME paket kök bir parçası olarak saklanır ve genellikle çağrılır 1.x `infoset` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-376">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="d7a6e-377">R4141: SOAP Zarfı adlı XOP MIME paketi kök bir parçası olarak kapsüllenmelidir 1.x `infoset` bölümü ve gelen HTTP Content-Type başvurulan.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-377">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="d7a6e-378">R4142: SOAP `Infoset` bölümü şu MIME üst bilgilerini içermesi gerekir: `Content-ID`, `Content-Transfer-Encoding`, ve `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-378">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="d7a6e-379">Content-ID üst bilgisinin biçimi RFC 2045 tanımlanır</span><span class="sxs-lookup"><span data-stu-id="d7a6e-379">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="d7a6e-380">Burada `msg-id` RFC 2822 (yani, RFC 822, RFC 2045 başvurulan yerini alır) olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-380">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="d7a6e-381">ve etkili bir şekilde bir e-posta adresi içine alınmış "\<" ve ">".</span><span class="sxs-lookup"><span data-stu-id="d7a6e-381">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="d7a6e-382">`[CFWS]` Önek ve sonek 2822 açıklamaları yürütmek için RFC eklendi ve birlikte çalışabilirlik korumak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-382">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="d7a6e-383">R4143: Sonrası bilgi kümesi MIME bölümünün içerik kimliği-üstbilgisinin değerini izlemelidir `msg-id` ile RFC 2822 üretimden `[CFWS]` atlanmış önek ve sonek bölümleri.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-383">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="d7a6e-384">MIME uygulamaları birkaç esnek içine alınmış değer gereksinimleri "\<" ve ">" e-posta adresi olabilir ve kullanılan `absoluteURI` içine "\<", ">" Ek e-posta adresi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-384">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="d7a6e-385">Bu sürüm WCF MIME Content-ID üst bilgisi biçiminde değerleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-385">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="d7a6e-386">R4144: İçerik kimliği-üstbilgi değerleri aşağıdaki rahat eşleşen MTOM işlemci kabul etmelidir `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-386">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="d7a6e-387">MIME bölümünün içerik kodlama iletişim kurmak için içerik Transfer-Encoding üstbilgisi MIME (RFC 2045) sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-387">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="d7a6e-388">Content-Transfer-Encoding için tanımlanan varsayılan içerik Transfer-Encoding başlığı büyük birlikte çalışabilirlik için gerekli olan SOAP iletilerin çoğu için uygun değil, bu nedenle 7 bit:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-388">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="d7a6e-389">R4145: SOAP bilgi bölümü içeriği Transfer-Encoding üst bilgisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-389">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="d7a6e-390">R4146: UTF-8 karakter kodlaması SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini 8 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-390">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="d7a6e-391">R4147: UTF-16 karakter kodlamasını SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini ikili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-391">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="d7a6e-392">[XOP göre] 5 bölümüne,</span><span class="sxs-lookup"><span data-stu-id="d7a6e-392">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="d7a6e-393">R4148: Content-Type üstbilgisi medya türü application/xop + xml SOAP1.1 bilgi bölümü içermelidir ve tür parametreleri = "text/xml" ve karakter kümesi</span><span class="sxs-lookup"><span data-stu-id="d7a6e-393">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="d7a6e-394">R4149: Content-Type üstbilgisi medya türü ile SOAP 1.2 bilgi bölümü içermelidir `application/xop+xml` ve tür parametreleri = "`application/soap+xml`" ve `charset`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-394">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="d7a6e-395">XOP açıklarken `charset` parametresi için `application/xop+xml` isteğe bağlı olacak şekilde BP 1.1 gereksinimini benzer birlikte çalışabilirliği için gerekli `charset` parametresi için `text/xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-395">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="d7a6e-396">R41410: `type` ve `charset` parametreleri SOAP 1.x bilgi bölümü Content-Type üst bilgisi mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-396">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="d7a6e-397">MTOM WCF uç nokta desteği</span><span class="sxs-lookup"><span data-stu-id="d7a6e-397">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="d7a6e-398">MTOM amacı, bir SOAP ileti base64 ile kodlanmış verileri En İyileştir şifrelemektir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-398">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="d7a6e-399">Kısıtlamalar bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-399">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="d7a6e-400">R4151: base64 ile kodlanmış verileri içeren herhangi bir öğe bilgi öğe iyileştirilmiş olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-400">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="d7a6e-401">B4152: WCF base64 olarak kodlanmış veriler içeren ve uzunluğu 1024 bayt aşan öğesi bilgi öğelerini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-401">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="d7a6e-402">MTOM kullanacak şekilde yapılandırılmış bir WCF uç nokta her zaman MTOM kodlanmış iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-402">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="d7a6e-403">Hiçbir parçasının gerekli ölçütleri karşılayan bile ileti (bir MIME paketi olarak SOAP Zarfı içeren tek bir MIME bölümü ile seri hale getirilmiş) hala MTOM kodlanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-403">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="d7a6e-404">MTOM için WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="d7a6e-404">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="d7a6e-405">WCF MTOM kullanım bitiş noktası tarafından belirtmek için aşağıdaki İlkesi onayını kullanır:</span><span class="sxs-lookup"><span data-stu-id="d7a6e-405">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="d7a6e-406">R4211: Önceki İlkesi onayını bir uç noktası İlkesi konu ve uç noktasından alınan ve gönderilen tüm iletilerin MTOM kullanarak iyileştirilmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-406">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="d7a6e-407">B4212: MTOM iyileştirme'yi kullanmak üzere yapılandırıldığında, bir WCF uç nokta MTOM ilke onaylama karşılık gelen iliştirilmiş ilke ekler `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-407">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="d7a6e-408">WS-güvenlik ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7a6e-408">Composition with WS-Security</span></span>  
 <span data-ttu-id="d7a6e-409">MTOM olan benzer bir kodlama mekanizması `text/xml` ve WCF ikili XML.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-409">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="d7a6e-410">MTOM sunar doğal bileşim WS-güvenlik ve diğer WS-\* protokoller: WS güvenliği kullanılarak güvenli bir ileti MTOM kullanılarak iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-410">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d7a6e-411">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d7a6e-411">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="d7a6e-412">WCF SOAP 1.1 ileti MTOM kullanılarak kodlanır</span><span class="sxs-lookup"><span data-stu-id="d7a6e-412">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="d7a6e-413">Güvenli WCF SOAP 1.2 MTOM kullanarak ileti kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-413">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="d7a6e-414">Bu örnekte, bir ileti MTOM ve WS-güvenlik kullanarak korumalı bir SOAP 1.2 kullanılarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-414">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="d7a6e-415">Kodlama içeriğini için tanımlanan ikili parçaları `BinarySecurityToken`, `CipherValue` , `EncryptedData` karşılık gelen şifrelenmiş imzası ve şifrelenmiş gövdesi.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-415">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="d7a6e-416">Unutmayın `CipherValue` , `EncryptedKey` uzunluğunu daha az sonra 1024 bayt olduğundan iyileştirme için WCF tarafından tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="d7a6e-416">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
