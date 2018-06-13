---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: c900c8fde8b13b4766fb245de2bab46b5601f135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496643"
---
# <a name="messaging-protocols"></a><span data-ttu-id="ff4f1-102">Mesajlaşma Protokolleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-102">Messaging Protocols</span></span>
<span data-ttu-id="ff4f1-103">Windows Communication Foundation (WCF) kanal yığını iç ileti gösterimi kablo biçimine dönüştürme ve belirli bir kullanarak göndermek için kodlama ve taşıma kanalları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="ff4f1-104">HTTP Web Hizmetleri birlikte çalışabilirlik için kullanılan en yaygın aktarım olduğunu ve Web Hizmetleri tarafından kullanılan en yaygın Kodlamalar XML tabanlı SOAP 1.1 ve SOAP 1.2 ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ff4f1-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ff4f1-105">Bu konu, WCF uygulaması tarafından işe aşağıdaki protokolleri ayrıntılarını kapsar <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="ff4f1-106">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-106">Specification/document</span></span>|<span data-ttu-id="ff4f1-107">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="ff4f1-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ff4f1-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="ff4f1-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="ff4f1-109">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="ff4f1-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="ff4f1-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="ff4f1-111">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="ff4f1-112">http://www.w3.org/TR/soap12-part2/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="ff4f1-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="ff4f1-113">Bu konuda aşağıdaki protokolleri WCF uygulama ayrıntılarını kapsar <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="ff4f1-114">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-114">Specification/Document</span></span>|<span data-ttu-id="ff4f1-115">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="ff4f1-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ff4f1-116">XML</span><span class="sxs-lookup"><span data-stu-id="ff4f1-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="ff4f1-117">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="ff4f1-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="ff4f1-118">SOAP 1.2 Çekirdek</span><span class="sxs-lookup"><span data-stu-id="ff4f1-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="ff4f1-119">WS-adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="ff4f1-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="ff4f1-120">Adresleme 1.0 - çekirdek W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="ff4f1-121">Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="ff4f1-122">Adresleme 1.0 - WSDL bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="ff4f1-123">W3C Web adresleme 1.0 - meta veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="ff4f1-124">WSDL SOAP1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="ff4f1-125">WSDL SOAP1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="ff4f1-126">Bu konuda aşağıdaki protokolleri WCF uygulama ayrıntılarını kapsar <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="ff4f1-127">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-127">Specification/document</span></span>|<span data-ttu-id="ff4f1-128">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="ff4f1-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ff4f1-129">XOP</span><span class="sxs-lookup"><span data-stu-id="ff4f1-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="ff4f1-130">MTOM + SOAP 1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="ff4f1-131">MTOM SOAP 1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="ff4f1-132">MTOM WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="ff4f1-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="ff4f1-134">Aşağıdaki XML ad alanları ve ilişkili önekleri bu konu boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="ff4f1-135">önek</span><span class="sxs-lookup"><span data-stu-id="ff4f1-135">Prefix</span></span>|<span data-ttu-id="ff4f1-136">Namespace Tekdüzen Kaynak Tanımlayıcısı (URI)</span><span class="sxs-lookup"><span data-stu-id="ff4f1-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="ff4f1-137">s11</span><span class="sxs-lookup"><span data-stu-id="ff4f1-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="ff4f1-138">s12</span><span class="sxs-lookup"><span data-stu-id="ff4f1-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="ff4f1-139">wsa</span><span class="sxs-lookup"><span data-stu-id="ff4f1-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="ff4f1-140">wsam</span><span class="sxs-lookup"><span data-stu-id="ff4f1-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="ff4f1-141">wsap</span><span class="sxs-lookup"><span data-stu-id="ff4f1-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="ff4f1-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="ff4f1-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="ff4f1-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="ff4f1-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="ff4f1-144">XOP</span><span class="sxs-lookup"><span data-stu-id="ff4f1-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="ff4f1-145">xmime</span><span class="sxs-lookup"><span data-stu-id="ff4f1-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="ff4f1-146">dp</span><span class="sxs-lookup"><span data-stu-id="ff4f1-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="ff4f1-147">SOAP 1.1 ve SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="ff4f1-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="ff4f1-148">Zarf ve Model işleme</span><span class="sxs-lookup"><span data-stu-id="ff4f1-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="ff4f1-149">WCF SOAP 1.1 Zarf işleme temel Profil 1.1 (BP11) ve temel Profil 1.0 (SSBP10) aşağıdaki uygular.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="ff4f1-150">SOAP 1.2 Zarf SOAP12 bölüm 1 aşağıdaki işlem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="ff4f1-151">Bu bölümde BP11 ve SOAP12 bölüm 1 açısından WCF tarafından yapılan belirli uygulama seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="ff4f1-152">Zorunlu üstbilgiyi işleme</span><span class="sxs-lookup"><span data-stu-id="ff4f1-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="ff4f1-153">WCF üstbilgileri işleme işaretlenmiş için kuralları aşağıdaki `mustUnderstand` SOAP 1.1 ve SOAP 1.2 belirtimlere, aşağıdaki farklılıkları açıklanan.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="ff4f1-154">WCF kanalı yığın girer bir ileti ilişkili bağlama öğeleri tarafından örneğin yapılandırılmış tek tek kanalları, ileti metin kodlaması, güvenlik, güvenilir Mesajlaşma ve işlemler tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="ff4f1-155">Her bir kanala ilişkili ad alanından üstbilgileri tanır ve anladım olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="ff4f1-156">Bir ileti dağıtıcısı girdikten sonra karşılık gelen ileti işlem başına Sözleşme ve bunları anladım işaretleri tarafından beklenen üstbilgileri işlemini biçimlendiricisi okur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="ff4f1-157">Dağıtıcı kalan tüm üstbilgileri değil anladı ancak olarak işaretlenmiş olup olmadığını doğrular sonra `mustUnderstand` ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="ff4f1-158">İçeren iletileri `mustUnderstand` recipient öğesinde hedeflenen üstbilgileri alıcı uygulama kodu tarafından işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="ff4f1-159">Gibi katmanlı işleme altyapısı katmanları ve SOAP düğümünün uygulama katmanları arasında ayrım sağlar:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="ff4f1-160">B1111: değil anlaşılır üstbilgileri ileti WCF altyapı kanal yığını tarafından işlendikten sonra ancak uygulama tarafından işlenmeden önce algılandı</span><span class="sxs-lookup"><span data-stu-id="ff4f1-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="ff4f1-161">`mustUnderstand` Üstbilgi değeri SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="ff4f1-162">Temel Profil 1.1 gerektirir `mustUnderstand` değer 0 veya 1 SOAP 1.1 iletileri için olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="ff4f1-163">SOAP 1.2 sağlar 0, 1, `false`, ve `true` olarak değerleri ancak kurallı gösterimi yayma önerir `xs:boolean` değerleri (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="ff4f1-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="ff4f1-164">B1112: WCF yayar `mustUnderstand` SOAP zarfının değerleri 0 ile 1 SOAP 1.1 ve SOAP 1.2 sürümleri için.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="ff4f1-165">WCF kabul eder tüm değer alanının `xs:boolean` için `mustUnderstand` üstbilgi (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="ff4f1-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="ff4f1-166">SOAP hataları</span><span class="sxs-lookup"><span data-stu-id="ff4f1-166">SOAP Faults</span></span>  
 <span data-ttu-id="ff4f1-167">WCF özel SOAP hataya uygulamaları listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="ff4f1-168">B2121: WCF aşağıdaki SOAP 1.1 hata kodlarını döndürür: `s11:mustUnderstand`, `s11:Client`, ve `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="ff4f1-169">B2122: WCF aşağıdaki SOAP 1.2 hata kodlarını döndürür: `s12:MustUnderstand`, `s12:Sender`, ve `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="ff4f1-170">HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="ff4f1-171">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="ff4f1-172">WCF temel Profil 1.1 belirtimini aşağıdaki açıklamalar 3.4 bölümle aşağıdaki SOAP1.1 HTTP bağlaması uygular:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="ff4f1-173">B2211: WCF Hizmeti HTTP POST isteklerini yeniden yönlendirilmesini uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="ff4f1-174">B2212: WCF istemcileri HTTP tanımlama bilgilerini 3.4.8 uygun olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="ff4f1-175">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="ff4f1-176">WCF SOAP 1.2 HTTP bağlaması SOAP 1.2 bölümü 2 (SOAP12Part2) belirtimiyle aşağıdaki açıklamalar bölümünde açıklandığı gibi uygular.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="ff4f1-177">SOAP 1.2 sunulan bir isteğe bağlı eylem parametresi için `application/soap+xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="ff4f1-178">Bu parametre WS adresleme kullanılmadığı SOAP ileti gövdesini ayrıştırılması gerek kalmadan ileti gönderme en iyi duruma getirmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="ff4f1-179">R2221: `application/soap+xml` eylem parametresi SOAP 1.2 istek üzerine varsa eşleşmelidir `soapAction` özniteliği `wsoap12:operation` öğesi içinde karşılık gelen WSDL bağlama.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="ff4f1-180">R2222: `application/soap+xml` eylem parametresi, bir SOAP 1.2 iletideki varsa eşleşmelidir `wsa:Action` WS adresleme 2004/08 veya WS adresleme 1.0 ne zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="ff4f1-181">WS-adresleme devre dışıdır ve gelen istek bir eylem parametresinin içermediğinden, ileti `Action` belirtilen olarak sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="ff4f1-182">WS-adresleme</span><span class="sxs-lookup"><span data-stu-id="ff4f1-182">WS-Addressing</span></span>  
 <span data-ttu-id="ff4f1-183">WCF WS adresleme 3 sürümlerini uygular:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="ff4f1-184">WS-adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="ff4f1-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="ff4f1-185">1.0 çekirdek (ADDR10 çekirdekli) ve (SOAP ADDR10) bağlama SOAP adresleme W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="ff4f1-186">WS-adresleme 1.0 - meta verileri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="ff4f1-187">Uç nokta başvuruları</span><span class="sxs-lookup"><span data-stu-id="ff4f1-187">Endpoint References</span></span>  
 <span data-ttu-id="ff4f1-188">WCF uygulayan WS-adresleme'nin tüm sürümleri uç nokta başvuruları uç noktaları tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="ff4f1-189">Uç nokta başvuruları ve WS adresleme sürümleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="ff4f1-190">WCF uygulayan WS adresleme kullanan altyapı protokolleri ve belirli bir sayı `EndpointReference` öğesi ve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="ff4f1-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="ff4f1-191">WCF her iki sürümü WS-adresleme diğer altyapı protokollerle kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="ff4f1-192">WCF uç noktaları bir sürümü WS adresleme uç nokta başına destekler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="ff4f1-193">R3111, ad alanı için `EndpointReference` öğesi veya türü WCF Bitiş noktası ile değiştirilen iletilerin kullanılan WS adresleme-bu bitiş noktası tarafından uygulanan sürümü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="ff4f1-194">Örneğin, bir WCF uç noktası WS-ReliableMessaging uyguluyorsa `AcksTo` gibi bir uç nokta içinde tarafından döndürülen üstbilgi `CreateSequenceResponse` WS adresleme sürümünü kullanır, `EncodingBinding` öğesi için bu uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="ff4f1-195">Uç nokta başvuruları ve meta veriler</span><span class="sxs-lookup"><span data-stu-id="ff4f1-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="ff4f1-196">Çeşitli senaryoları meta veriler veya belirli bir uç nokta için meta veriler için bir başvuru iletişim kurmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="ff4f1-197">B3121: WCF WS-MetadataExchange (MEX) belirtimi değere veya başvuruya göre meta veri uç noktası başvurular eklemek için Bölüm 6 açıklanan mekanizmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="ff4f1-198">Burada bir WCF Hizmeti gerektirir Belirteç Verenin tarafından verilen bir güvenlik onaylar biçimlendirme dili (SAML) belirteci kullanarak kimlik doğrulaması bir senaryo düşünün http://sts.fabrikam123.com. WCF Bitiş noktası kullanarak bu kimlik doğrulama gereksinimini açıklar `sp:IssuedToken` onaylama işlemi bir iç içe `sp:Issuer` Belirteç Verenin işaret eden onaylama.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="ff4f1-199">Erişim istemci uygulamaları `sp:Issuer` onaylama Belirteç Verenin bitiş noktası ile iletişim kurma bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-199">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="ff4f1-200">İstemcinin meta verileri Belirteç Verenin hakkında bilmek ister.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-200">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="ff4f1-201">MEX içinde tanımlanmış uç nokta başvuru meta verileri uzantıları kullanarak, WCF Belirteç Verenin meta veriler için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-201">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="ff4f1-202">İleti adresleme üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-202">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="ff4f1-203">İleti üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-203">Message Headers</span></span>  
 <span data-ttu-id="ff4f1-204">Belirtimleri tarafından belirlenen şekilde WCF hem WS adresleme sürümleri için aşağıdaki ileti üstbilgilerini kullandığı `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, ve `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-204">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="ff4f1-205">B3211: WS adresleme tüm sürümleri için WCF korur, ancak ileti üstbilgilerini WS adresleme kutudan çıktığı oluşturmadığı `wsa:FaultTo` ve `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-205">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="ff4f1-206">Bu ileti üstbilgilerini ve WCF buna uygun olarak işleyecek etkileşim WCF uygulamaları uygulamalarla ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-206">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="ff4f1-207">Başvuru parametreleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-207">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="ff4f1-208">WCF Bitiş noktası başvuru parametreleri ve başvuru p işlenmesini uygular</span><span class="sxs-lookup"><span data-stu-id="ff4f1-208">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="ff4f1-209">ilgili belirtimlerine uygun olarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-209">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="ff4f1-210">B3221: WS adresleme 2004/08 kullanmak üzere yapılandırıldığında, WCF uç noktaları başvuru özellikleri ve başvuru parametreleri işleme arasında ayrım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-210">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="ff4f1-211">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="ff4f1-212">Web hizmeti işlemi çağırma yer alan iletileri dizisi olarak adlandırılır *ileti değişim deseni*.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-212">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="ff4f1-213">WCF destekleyen tek yönlü ve istek-yanıt çift yönlü ileti desenleri exchange.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-213">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="ff4f1-214">Bu bölümde kullanılan ileti değişim deseni bağlı olarak işleme iletideki WS adreslendirme gereksinimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-214">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="ff4f1-215">Bu bölümde genelinde istek sahibinin ilk ileti gönderir ve Yanıtlayıcı ilk iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-215">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ff4f1-216">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-216">One-Way Message</span></span>  
 <span data-ttu-id="ff4f1-217">Ne zaman bir WCF uç noktası iletilerle desteklemek üzere yapılandırılmış bir belirli `Action` tek yönlü bir yol izler, WCF uç noktası aşağıdaki davranışları ve gereksinimleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-217">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="ff4f1-218">Aksi belirtilmediği sürece, hem WS adresleme-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-218">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="ff4f1-219">R3311: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`ve uç nokta başvuru tarafından belirtilen tüm başvuru parametreleri için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-219">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="ff4f1-220">Ne zaman WS adresleme 2004/08 kullanılır ve karşılık gelen üstbilgileri iletiye çok eklenmelidir [başvuru Özellikleri] uç nokta başvuruya göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-220">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="ff4f1-221">B3312: İstek sahibinin içerebilir `MessageID`, `ReplyTo`, ve `FaultTo` üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-221">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="ff4f1-222">Alıcı altyapı bunları göz ardı eder ve uygulamaya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-222">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="ff4f1-223">R3313: HTTP kullanılır ve hiçbir ileti üzerinde HTTP yanıt leg gönderilen Yanıtlayıcı boş bir gövde ve bir HTTP 202 durum kodu ile bir HTTP yanıtının göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-223">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="ff4f1-224">HTTP taşıma kullanımda ve işlem sözleşmesi bir ileti tek yönlü bildirir, HTTP yanıtı hala altyapı ileti göndermek için kullanılabilir — örneğin, güvenilir Mesajlaşma gönderebilirsiniz bir `SequenceAcknowledgement` bir HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-224">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="ff4f1-225">B3314: WCF Yanıtlayıcı bir hata iletisi tek yönlü iletisine yanıt olarak göndermez.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-225">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="ff4f1-226">İstek-Yanıt</span><span class="sxs-lookup"><span data-stu-id="ff4f1-226">Request-Reply</span></span>  
 <span data-ttu-id="ff4f1-227">Bir ileti için bir WCF uç noktası yapılandırıldığında bir verilen `Action` istek-yanıt modeli izleyen WCF uç noktası davranışları ve aşağıdaki gereksinimleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-227">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="ff4f1-228">Aksi belirtilmediği sürece, hem WS adresleme-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-228">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="ff4f1-229">R3321: İstek sahibinin istekte içermelidir `wsa:To`, `wsa:Action`, `wsa:MessageID`ve tüm başvuru parametreleri başvuru özellikler (veya her ikisi) uç noktası başvuru tarafından belirtilen için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-229">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="ff4f1-230">R3322: WS adresleme 2004/08 kullanıldığında `ReplyTo` istekte de eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-230">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="ff4f1-231">R3323: WS adresleme 1.0 kullanıldığında ve `ReplyTo` eşit [address] özelliğiyle varsayılan uç nokta başvuru isteğinde yok "http://www.w3.org/2005/08/addressing/anonymous" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-231">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="ff4f1-232">R3324: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`, ve `wsa:RelatesTo` yanıt iletisi üstbilgilerinde yanı sıra tüm başvuru parametreleri başvuru özellikler (veya her ikisi) tarafından belirtilen üstbilgilerini `ReplyTo` bitiş noktası başvurusu İstek.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-232">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="ff4f1-233">Adresleme hataları Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff4f1-233">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="ff4f1-234">R3411: WCF WS adresleme 2004/08 tarafından tanımlanan aşağıdaki hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-234">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="ff4f1-235">Kod</span><span class="sxs-lookup"><span data-stu-id="ff4f1-235">Code</span></span>|<span data-ttu-id="ff4f1-236">Sebep</span><span class="sxs-lookup"><span data-stu-id="ff4f1-236">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ff4f1-237">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="ff4f1-237">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="ff4f1-238">İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı; Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-238">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="ff4f1-239">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="ff4f1-239">wsa:ActionNotSupported</span></span>|<span data-ttu-id="ff4f1-240">Altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcısı belirtilen eylem algılamaz `Action` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-240">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="ff4f1-241">R3412: WCF WS adresleme 1.0 tarafından tanımlanan aşağıdaki hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-241">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="ff4f1-242">Kod</span><span class="sxs-lookup"><span data-stu-id="ff4f1-242">Code</span></span>|<span data-ttu-id="ff4f1-243">Sebep</span><span class="sxs-lookup"><span data-stu-id="ff4f1-243">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ff4f1-244">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="ff4f1-244">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="ff4f1-245">Yinelenen `wsa:To`, `wsa:ReplyTo`, `wsa:From` veya `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-245">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="ff4f1-246">Yinelenen `wsa:RelatesTo` aynı `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-246">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="ff4f1-247">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="ff4f1-247">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="ff4f1-248">Gerekli adresleme üstbilgisi eksik.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-248">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="ff4f1-249">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="ff4f1-249">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="ff4f1-250">İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-250">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="ff4f1-251">Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-251">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="ff4f1-252">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="ff4f1-252">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="ff4f1-253">Belirtilen eylem `Action` üstbilgi altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcı tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-253">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="ff4f1-254">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="ff4f1-254">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="ff4f1-255">Uç nokta incelenmesi temel sıralı işlemez belirten bu hataya geri RM kanalı gönderir `CreateSequence` ileti üstbilgilerini adresleme.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-255">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="ff4f1-256">Yukarıdaki tablolarda kod eşlemeleri için `FaultCode` içinde SOAP 1.1 ve `SubCode` (koduyla gönderen =) SOAP 1.2 içindeki.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-256">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="ff4f1-257">WSDL 1.1 bağlama ve WS-ilke onaylamalarını</span><span class="sxs-lookup"><span data-stu-id="ff4f1-257">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="ff4f1-258">WS-adresleme kullanımını gösteren</span><span class="sxs-lookup"><span data-stu-id="ff4f1-258">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="ff4f1-259">WCF ilke onaylamalarını WS adresleme belirli bir sürüm için uç nokta destek göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-259">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="ff4f1-260">Aşağıdaki ilke onaylama uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-260">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="ff4f1-261">Bu ilke onaylama WS adresleme 2004/08 belirtimi artırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-261">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="ff4f1-262">Bu, gönderilen ve alınan iletileri gösterir aşağıdaki ilke onaylama WS adresleme 1.0 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-262">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="ff4f1-263">Aşağıdaki ilke onaylama bir uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-263">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="ff4f1-264">`wsaw10:UsingAddressing` Öğesi [WS-adresleme-WSDL] ödünç ve WS-Policy bağlamında bu belirtimi uyumlu kullanılır, Bölüm 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-264">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="ff4f1-265">Adresleme kullanımını WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP bağlamaları semantiği değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-265">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="ff4f1-266">Bir yanıt adresleme ve WSDL SOAP 1.x HTTP bağlama kullanan bir uç nokta için gönderilen bir istek bekleniyorsa, örneğin, yanıt HTTP yanıtı kullanarak gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-266">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="ff4f1-267">Http yanıtı gönderilen yanıtlar için WS-AM onayı ifade eder:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-267">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="ff4f1-268">Tam İlkesi onaylama şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-268">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="ff4f1-269">Ancak, istek sahibinin ve Yanıtlayıcı Yanıtlayıcı tarafından gönderilen Örneğin, istenmeyen tek yönlü iletileri arasında kurulan iki bağımsız ters HTTP bağlantılarını kalmaktan fayda ileti exchange desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-269">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="ff4f1-270">WCF iki temel taşıma kanalları burada bir kanal giriş iletileri için kullanılır ve çıktı iletiler için kullanılan başka bir bileşik çift yönlü kanal kurabilir bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-270">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="ff4f1-271">HTTP taşıma söz konusu olduğunda, bileşik çift yönlü iki ters HTTP bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-271">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="ff4f1-272">Yanıtlayıcı iletileri göndermek için bir bağlantı istek sahibinin kullanır ve Yanıtlayıcı diğer iletiler istemciye geri gönderilecek kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-272">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="ff4f1-273">Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am onayı ifade eder</span><span class="sxs-lookup"><span data-stu-id="ff4f1-273">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="ff4f1-274">Tam İlkesi onaylama şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-274">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="ff4f1-275">Talep sahibinin Yanıtlayıcı ve istekte bulunan kişinin Yanıtlayıcı akan iletileri için kullanılacak iki ayrı ters HTTP bağlantılarını WSDL 1.1 SOAP 1.x HTTP bağlamaları kullanan uç noktalarda uç nokta İlkesi konu [WS-PA] olan aşağıdaki onay kullanımını, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-275">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="ff4f1-276">Önceki deyimi aşağıdaki gereksinimleri müşteri adayları `wsa:ReplyTo` başlığı istek iletileri için:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-276">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="ff4f1-277">R3514: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit değil "http://www.w3.org/2005/08/addressing/anonymous" uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ile varsa bir `wsap10:UsingAddressing` veya `wsap:UsingAddressing` onaylama işlemi eşleşmiş ile `cdp:CompositeDuplex` bağlı.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-277">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="ff4f1-278">R3515: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous", veya bir `ReplyTo` tümü, uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif varsa üst bilgisi ile `wsap10:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-278">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="ff4f1-279">R3516: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle bir `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous" uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ile varsa `wsap:UsingAddressing` onaylama ve hiçbir `cdp:CompositeDuplex`bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-279">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="ff4f1-280">Bir öğenin sunarak benzer protokolü bağlamaları tanımlamak WS adresleme WSDL belirtimi çalışır `<wsaw:Anonymous/>` değerlerle üzerinde gereksinimleri göstermek için üç metinsel (gerekli, isteğe bağlı ve yasaklanmış) `wsa:ReplyTo` üstbilgi (Bölüm 3.2).</span><span class="sxs-lookup"><span data-stu-id="ff4f1-280">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="ff4f1-281">Ne yazık ki, bu tür bir öğe onayı ifade kullanarak alternatifleri kesişimi desteklemek için etki alanına özgü uzantılar gerektirdiğinden böyle öğesi tanımı bir onaylama WS-İlkesi ' nin bağlamında özellikle kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-281">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="ff4f1-282">Bu tür öğesi tanımı değerini de gösterir `ReplyTo` HTTP aktarımı için belirli kolaylaştırır Tel üzerinde uç noktası davranışı aksine üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-282">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="ff4f1-283">Eylem tanımı</span><span class="sxs-lookup"><span data-stu-id="ff4f1-283">Action Definition</span></span>  
 <span data-ttu-id="ff4f1-284">WS-adresleme 2004/08 tanımlayan bir `wsa:Action` için öznitelik `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-284">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="ff4f1-285">WS-adresleme 1.0 WSDL bağlama (WS-ADDR10-WSDL) benzer bir öznitelik tanımlar `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-285">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="ff4f1-286">İkisi arasındaki tek fark sırasıyla Bölüm WS-ADDR 3.3.2 ve WS-ADDR10-WSDL 4.4.4 bölümünde açıklanan varsayılan eylem düzeni semantiği ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-286">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="ff4f1-287">Aynı paylaşan iki uç nokta uygun olan `portType` (veya sözleşmede WCF terminolojisi) ancak WS adresleme farklı sürümlerini kullanan.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-287">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="ff4f1-288">Ancak eylem tarafından tanımlanan o `portType` ve uygulayan uç noktalar arasında değiştirmemelisiniz `portType`, her iki varsayılan eylem desenleri desteklemesini mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-288">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="ff4f1-289">WCF bu controversy gidermek için tek bir sürümünü destekleyen `Action` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-289">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="ff4f1-290">B3521: WCF kullanan `wsaw10:Action` özniteliği `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-belirlemek için WSDL içinde tanımlanan öğeleri `Action` bitiş noktası tarafından kullanılan WS adresleme sürümü yedeklemiş karşılık gelen iletiler için URI.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-290">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="ff4f1-291">Kullanım uç noktası başvuru iç WSDL bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="ff4f1-291">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="ff4f1-292">WS ADDR10 WSDL bölüm 4.1 genişletir `wsdl:port` eklenecek öğe `<wsa10:EndpointReference…/>` uç nokta WS adresleme koşullarını tanımlamak için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-292">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="ff4f1-293">WCF genişletir. Bu yardımcı program WS adresleme 2004/08 üzerinde izin verme `<wsa:EndpointReference…/>` bir alt öğesi görüntülenmesini `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-293">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="ff4f1-294">R3531: iliştirilmiş ilke alternatif bir uç nokta varsa, bir `<wsaw10:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-294">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="ff4f1-295">R3532: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-295">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="ff4f1-296">R3533: bir uç nokta iliştirilmiş ilke alternatif varsa `<wsap:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-296">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="ff4f1-297">R3534: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-297">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="ff4f1-298">WS güvenliği ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff4f1-298">Composition with WS-Security</span></span>  
 <span data-ttu-id="ff4f1-299">WS-ADDR ve WS-ADDR10 güvenlik göz önünde bulundurarak bölümlere göre tüm adresleme ileti üstbilgilerini birlikte ileti gövdesi birbirine bağlamak için imzalanması için önerilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-299">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="ff4f1-300">WS güvenliği ileti bütünlüğü koruma için kullanıldığında, ileti gövdesi birlikte WS adresleme ileti üstbilgilerini yanı sıra üstbilgileri başvuru parametreleri veya özellikler (veya her ikisi de) sonuçlandı imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-300">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ff4f1-301">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ff4f1-301">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ff4f1-302">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-302">One-Way Message</span></span>  
 <span data-ttu-id="ff4f1-303">Bu senaryoda, gönderenin alıcı için tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-303">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="ff4f1-304">SOAP 1.2, HTTP 1.1 ve 1.0 W3C WS adresleme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-304">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="ff4f1-305">İstek iletisi yapısı: İleti üstbilgilerini dahil `wsa10:To` ve `wsa10:Action` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-305">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="ff4f1-306">Belirli bir ileti gövdesini içeren `<app:Ping>` uygulama ad alanından öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-306">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="ff4f1-307">HTTP üstbilgileri: POST hedef URI eşleşen `wsa10:To` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-307">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="ff4f1-308">Content-Type üstbilgisi değeri olan `application/soap+xml` SOAP 1.2 gerektirdiği.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-308">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="ff4f1-309">Parametreleri `charset` ve `action` dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-309">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="ff4f1-310">`action` Content-Type üstbilgisi parametresinin değeri ile eşleşen `wsa10:Action` ileti üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-310">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="ff4f1-311">Alıcı boş HTTP yanıt ve durum 202 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-311">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="ff4f1-312">HTTP yanıt örneği:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-312">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="ff4f1-313">SOAP iletisi iletim iyileştirme mekanizması</span><span class="sxs-lookup"><span data-stu-id="ff4f1-313">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="ff4f1-314">Bu bölümde, HTTP SOAP MTOM için WCF uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-314">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="ff4f1-315">MTOM, SOAP iletisi kodlama mekanizması geleneksel text/XML kodlama veya WCF ikili kodlama aynı sınıfta teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-315">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="ff4f1-316">MTOM aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-316">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="ff4f1-317">Bir XML kodlama ve [XOP] tarafından açıklanan paketleme mekanizması ayrı ikili parçalara base64 ile kodlanmış ikili veri içeren XML bilgi öğeleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-317">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="ff4f1-318">MIME kapsülleme XML bilgi ve her ikili XOP paketinin parçası ayrı bir MIME bölüm içinde serileştiren XOP paketi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-318">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="ff4f1-319">SOAP için uygulanan bir MIME XOP kodlama 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-319">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="ff4f1-320">Bir HTTP aktarım bağlama.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-320">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="ff4f1-321">WCF ile HTTP olmayan taşımalar ile MTOM kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-321">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="ff4f1-322">Ancak, bu konudaki şu HTTP odaklanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-322">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="ff4f1-323">MTOM biçim belirtim MTOM kendisi, XOP ve MIME kapsayan büyük kümesi yararlanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-323">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="ff4f1-324">Bu belirtimi kümesinin modülerlik biçimi ve işleme semantiğini tam gereksinimlerine yeniden oluşturmak biraz zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-324">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="ff4f1-325">Bu bölümde MTOM HTTP bağlaması için biçimi ve işleme gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-325">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="ff4f1-326">İleti MTOM kodlama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-326">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="ff4f1-327">MTOM iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff4f1-327">Generating MTOM messages</span></span>  
 <span data-ttu-id="ff4f1-328">[XOP] bölümü 3.1 bağlamalarında tanımlanmış bir XOP pakete base64 değerler içeren öğesi bilgi öğelerle XML kodlama işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-328">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="ff4f1-329">Aşağıdaki adımlar dizisini özel MTOM kodlama işlemi açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-329">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="ff4f1-330">Kodlanacak SOAP Zarfı hiçbir öğe bilgi öğe ile içerdiğinden emin olun bir `[namespace name]` , "http://www.w3.org/2004/08/xop/include" ve `[local name]` , `Include`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-330">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="ff4f1-331">Boş bir MIME paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-331">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="ff4f1-332">Özgün XML bilgi içinde en iyi duruma getirilmesi öğesi bilgi öğeleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-332">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="ff4f1-333">Öğeleri en iyi duruma getirilmesi karakterleri oluşturan `[children]` öğesi bilgilerinin öğesi kurallı biçiminde olmalı `xs:base64Binary` (XSD-2, 3.2.16 bkz base64Binary) ve, satır içi, önceki herhangi bir boşluk karakteri içermemelidir veya boşluk olmayan içerik aşağıdaki.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-333">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="ff4f1-334">Özgün SOAP Zarfı kopyası olan bir XOP SOAP Zarfı oluşturun, ancak her öğe bilgileri alt öğeleri önceki adımda belirlediğiniz öğesi olarak değiştirilir. bir `xop:Include` olarak öğe bilgi öğe:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-334">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="ff4f1-335">Değiştirilen karakterleri base64 kodlu veriler olarak işleyerek ikili verisine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-335">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="ff4f1-336">R3133 ve R3134 gereksinimleri karşılayan benzersiz bir Content-ID üstbilgi değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-336">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="ff4f1-337">İkili değeri olan bir Content-Transfer-Encoding MIME üstbilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-337">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="ff4f1-338">Öğe bilgileri öğe iyileştirilen varsa ([üst] yeni eklenen `xop:Include` öğe bilgi öğe) sahip bir `xmime:contentType` özniteliği bilgi öğesi, bir Content-Type MIME üstbilgisi değeri ile oluşturun `xmime:contentType` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-338">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="ff4f1-339">İşlenen base64, 4b Content-ID başlığından, 4 c, adım 4 d oluşturursa Content-Type üstbilgisi Content-Transfer-Encoding başlığından değiştirilen karakter gelen kodunu çözdü ikili verileri tarafından oluşturulmuş içeriğe sahip yeni bir ikili MIME bölümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-339">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="ff4f1-340">Ekleme bir `href` özniteliğini `xop:Include` değeri CID bir öğesiyle: 4b adımında oluşturulan Content-ID üstbilgi değeri türetilen URI.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-340">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="ff4f1-341">Kapsayan Kaldır "\<" ve ">" URL-kalan dize ve önekini ekleyin kaçış karakterleri `cid:`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-341">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="ff4f1-342">Aşağıdaki minimum karakter kümesi RFC1738 ve RFC2396 tarafından Atlanan için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-342">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="ff4f1-343">Diğer karakterler kaçışlı.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-343">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="ff4f1-344">Adım 4 XOP SOAP Zarfı içeren bir kök MIME bölümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-344">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="ff4f1-345">HTTP Content-Type üstbilgisi de dahil olmak üzere HTTP üst bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-345">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="ff4f1-346">MIME paket yazma.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-346">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="ff4f1-347">MTOM iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="ff4f1-347">Processing MTOM messages</span></span>  
 <span data-ttu-id="ff4f1-348">Bir MTOM işleme ileti tam önceki açıklanan sürecin tersidir "üretme MTOM iletileri" bölümü:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-348">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="ff4f1-349">Kök MIME bölümü Content-Type olduğundan `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-349">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="ff4f1-350">SOAP zarfını paketi bir XML belgesi olarak MIME parçası kök ayrıştırarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-350">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="ff4f1-351">Karakter kodlamasını tarafından belirlenir `charset` Kök MIME bölümü Content-Type parametresi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-351">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="ff4f1-352">Oluşturulan SAOP zarfına her öğe bilgi öğe için olan, kendi [alt] özelliğini tek üyesi olarak bir `xop:Include` öğe bilgi öğe:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-352">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="ff4f1-353">Kaldırma `cid:` öneki ve tüm URI kaçış sıraları (RFC 2396) değerinde unescape `@href` özniteliği `xop:Include` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-353">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="ff4f1-354">Sonuç dizesinde alın "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="ff4f1-354">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="ff4f1-355">Adım 3a türetilmiş dizesiyle eşleşen Content-ID üstbilgi değeri olan MIME bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-355">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="ff4f1-356">Değiştir `xop:Include` görünür öğe bilgi öğe `children` kurallı base64 kodlaması temsil karakter bilgi öğelerinin bulunduğu her öğesinin özelliği (XSD-2, 3.2.16 bkz base64Binary) MIME bölümü varlık gövdesinin Adım 3b'de tanımlanan (etkili bir şekilde yerine `xop:Include` öğe bilgi öğe paket bölümünden yeniden verilerle).</span><span class="sxs-lookup"><span data-stu-id="ff4f1-356">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="ff4f1-357">HTTP Content-Type üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="ff4f1-357">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="ff4f1-358">Aşağıdaki biçimi için WCF açıklamalar MTOM belirtimi kendisini belirtilen gereksinimleri türetilmiş SOAP 1.x MTOM kodlu bir iletinin HTTP Content-Type üstbilgisinin listesidir ve MTOM ve RFC 2387 türetilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-358">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="ff4f1-359">R4131: Bir HTTP Content-Type üstbilgisi değeri multipart/related (büyük küçük harf duyarsız) ve parametrelerini olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-359">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="ff4f1-360">Parametre adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-360">Parameter names are case-insensitive.</span></span> <span data-ttu-id="ff4f1-361">Parametre sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-361">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="ff4f1-362">Content-Type üstbilgisi MIME iletileri için tam Backus-Naur formu'nı (BNF) bölümü 5.1, RFC 2045 listelenir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-362">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="ff4f1-363">R4132: Bir HTTP Content-Type üstbilgisi değeri olan bir tür parametresi olmalıdır `application/xop+xml` çift tırnak işaretleri içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-363">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="ff4f1-364">Çift tırnak işaretleri kullanma zorunluluğu RFC 2387 açık olmamasına karşın, tüm parametreleri büyük olasılıkla içeren multipart/related medya türü gibi karakterler ayrılmış metin gözlemleyen "@" or "/" ve bu nedenle çift tırnak işareti gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-364">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="ff4f1-365">R4133: Başlangıç parametresi SOAP içeren MIME bölümü Content-ID üstbilgisi değeri ile bir HTTP Content-Type üstbilgisi olmalıdır 1.x Zarf, çift tırnak işaretleri içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-365">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="ff4f1-366">Başlangıç parametresi atlanırsa, ilk MIME bölümü SOAP içermelidir 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-366">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="ff4f1-367">R4134: Text/xml, çift tırnak işaretleri içine değeriyle başlangıç bilgileri parametresi SOAP 1.1 kodlanmış MTOM iletisi için bir HTTP Content-Type üstbilgisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-367">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="ff4f1-368">R4135: SOAP 1.2 MTOM olarak kodlanmış bir ileti için bir HTTP Content-Type üstbilgisi değeri başlatma bilgisi parametresiyle içermelidir `application/soap+xml`, çift tırnak işaretleri içine alarak.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-368">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="ff4f1-369">R4136: HTTP Content-Type üstbilgisi SOAP 1.x MTOM olarak kodlanmış bir ileti için sınır parametresi BNF bölüm 5.1.1, RFC 2046 tanımlanmış MIME sınır eşleşen (çift tırnak işaretleri içine) değerine sahip olması gerekir</span><span class="sxs-lookup"><span data-stu-id="ff4f1-369">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="ff4f1-370">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-370">Examples:</span></span>  
  
     <span data-ttu-id="ff4f1-371">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="ff4f1-371">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="ff4f1-372">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="ff4f1-372">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="ff4f1-373">YANLIŞ</span><span class="sxs-lookup"><span data-stu-id="ff4f1-373">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="ff4f1-374">Bilgi MIME bölümü</span><span class="sxs-lookup"><span data-stu-id="ff4f1-374">Infoset MIME Part</span></span>  
 <span data-ttu-id="ff4f1-375">SOAP zarfını XOP MIME paketinin kök bir parçası kapsüllenmiş ve genellikle adlı 1.x `infoset` bölümü.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-375">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="ff4f1-376">R4141: SOAP adlı XOP MIME paketi kök bir parçası olarak Zarf kapsüllenmiş 1.x `infoset` bölümü ve gelen HTTP Content-Type başvurulan.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-376">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="ff4f1-377">R4142: SOAP `Infoset` bölümü aşağıdaki MIME Üstbilgileri içermelidir: `Content-ID`, `Content-Transfer-Encoding`, ve `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-377">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="ff4f1-378">Content-ID üstbilgi biçimi RFC 2045 tanımlanır</span><span class="sxs-lookup"><span data-stu-id="ff4f1-378">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="ff4f1-379">Burada `msg-id` (yani RFC 822, RFC 2045 başvurulan yerini) RFC 2822 olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-379">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="ff4f1-380">ve etkili bir şekilde bir e-posta adresi içine alınmış "\<" ve ">".</span><span class="sxs-lookup"><span data-stu-id="ff4f1-380">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="ff4f1-381">`[CFWS]` Önek ve sonek 2822 açıklamaları taşımak için RFC eklendi ve birlikte çalışabilirlik korumak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-381">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="ff4f1-382">R4143: Bilgi MIME bölümü Content-ID üstbilgisinin değerini izlemelisiniz `msg-id` ile RFC 2822 üretimden `[CFWS]` atlanmış önek ve sonek bölümleri.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-382">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="ff4f1-383">MIME uygulamaları sayısı rahat gereksinimleri içine alınmış bir değer için "\<" ve ">" bir e-posta adresi ve kullanılan `absoluteURI` içine "\<", ">" e-posta adresi yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-383">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="ff4f1-384">Bu sürüm WCF formun Content-ID MIME üstbilgisinin değerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-384">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="ff4f1-385">R4144: Content-ID üstbilgi değerleri aşağıdaki rahat eşleşen MTOM işlemciler kabul etmelidir `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-385">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="ff4f1-386">MIME (RFC 2045) MIME bölümü içeriğini kodlama iletişim kurmak için Content-Transfer-Encoding üstbilgisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-386">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="ff4f1-387">Content-Transfer-Encoding için tanımlanan varsayılan içerik Transfer-Encoding üstbilgisi büyük birlikte çalışabilirlik için gerektiği şekilde SOAP iletilerin çoğu için uygun olmayan 7 bit:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-387">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="ff4f1-388">R4145: İçeriği Transfer-Encoding üstbilgisi SOAP bilgi bölümü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-388">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="ff4f1-389">R4146: SOAP Zarfı karakter kodlamasını UTF-8 ise Content-Transfer-Encoding üstbilgisinin değerini 8 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-389">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="ff4f1-390">R4147: UTF-16 karakter kodlamasını SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini ikili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-390">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="ff4f1-391">[XOP göre] bölüm 5,</span><span class="sxs-lookup"><span data-stu-id="ff4f1-391">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="ff4f1-392">Tür parametreleri ve R4148: Content-Type üstbilgisi medya türü uygulama/xop + xml ile SOAP1.1 bilgi bölümü içermelidir = "text/xml" ve charset</span><span class="sxs-lookup"><span data-stu-id="ff4f1-392">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="ff4f1-393">R4149: Medya türüyle Content-Type üstbilgisi SOAP 1.2 bilgi bölümü içermelidir `application/xop+xml` ve tür parametreleri = "`application/soap+xml`" ve `charset`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-393">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="ff4f1-394">XOP açıklarken `charset` parametresi için `application/xop+xml` isteğe bağlı olacak şekilde birlikte çalışabilirliğini BP 1.1 gereksinimini benzer gerektiğinde `charset` parametresi için `text/xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-394">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="ff4f1-395">R41410: `type` ve `charset` parametreleri SOAP 1.x bilgi bölümü Content-Type üstbilgisi mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-395">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="ff4f1-396">WCF Bitiş noktası MTOM desteği</span><span class="sxs-lookup"><span data-stu-id="ff4f1-396">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="ff4f1-397">Base64 ile kodlanmış verileri en iyi duruma getirmek için bir SOAP iletisi kodlanacak MTOM amacı budur.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-397">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="ff4f1-398">Kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-398">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="ff4f1-399">R4151: base64 ile kodlanmış verileri içeren herhangi bir öğe bilgi öğesini en iyi duruma.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-399">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="ff4f1-400">B4152: WCF base64 ile kodlanmış verileri içeren ve uzunluğu 1024 bayt aşan öğesi bilgi öğeleri en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-400">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="ff4f1-401">MTOM kullanmak üzere yapılandırılmış bir WCF uç noktası her zaman MTOM olarak kodlanmış iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-401">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="ff4f1-402">Hiçbir bölümleri gereken ölçütleri karşılayan olsa bile, ileti (SOAP Zarfı içeren tek bir MIME bölümü ile bir MIME paketi olarak serileştirilmiş) hala MTOM kodlanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-402">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="ff4f1-403">MTOM WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="ff4f1-403">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="ff4f1-404">WCF MTOM kullanım bitiş noktası tarafından belirtmek için aşağıdaki ilke onaylama kullanır:</span><span class="sxs-lookup"><span data-stu-id="ff4f1-404">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="ff4f1-405">R4211: Önceki ilke onaylama bir uç nokta İlkesi konu ve gönderilen ve uç noktasından alınan tüm iletileri MTOM kullanılarak iyileştirilmiş gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-405">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="ff4f1-406">B4212: MTOM iyileştirme kullanmak üzere yapılandırıldığında, bir WCF uç nokta MTOM İlkesi onaylama karşılık gelen iliştirilmiş ilke ekler `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-406">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="ff4f1-407">WS güvenliği ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff4f1-407">Composition with WS-Security</span></span>  
 <span data-ttu-id="ff4f1-408">MTOM mekanizmasıdır benzer bir kodlama `text/xml` ve WCF ikili XML.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-408">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="ff4f1-409">MTOM sunar doğal birleşim WS güvenliği ve diğer WS-\* protokolleri: WS güvenliği kullanarak güvenli bir ileti MTOM kullanılarak iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-409">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ff4f1-410">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ff4f1-410">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="ff4f1-411">WCF SOAP 1.1 ileti MTOM kullanılarak kodlanmış</span><span class="sxs-lookup"><span data-stu-id="ff4f1-411">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="ff4f1-412">MTOM kullanılarak ileti WCF güvenli SOAP 1.2 kodlanmış</span><span class="sxs-lookup"><span data-stu-id="ff4f1-412">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="ff4f1-413">Bu örnekte, bir ileti MTOM ve WS-Security tarafından korunan SOAP 1.2 kullanılarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-413">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="ff4f1-414">Kodlama içeriğini için tanımlanan ikili parçaları `BinarySecurityToken`, `CipherValue` , `EncryptedData` karşılık gelen şifrelenmiş imza ve şifrelenmiş gövde.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-414">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="ff4f1-415">Unutmayın `CipherValue` , `EncryptedKey` uzunluğu sonra daha az 1024 bayt olduğundan iyileştirme için WCF tarafından tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="ff4f1-415">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
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
