---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812061"
---
# <a name="messaging-protocols"></a><span data-ttu-id="849af-102">Mesajlaşma Protokolleri</span><span class="sxs-lookup"><span data-stu-id="849af-102">Messaging Protocols</span></span>

<span data-ttu-id="849af-103">Windows Communication Foundation (WCF) kanal yığını, iç ileti gösterimini kendi tel biçimine dönüştürmek ve belirli bir aktarımı kullanarak göndermek için kodlama ve taşıma kanalları kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="849af-104">Web Hizmetleri birlikte çalışabilirliği için kullanılan en yaygın aktarım HTTP ve Web Hizmetleri tarafından kullanılan en yaygın Kodlamalar XML tabanlı SOAP 1,1, SOAP 1,2 ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="849af-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="849af-105">Bu konu, tarafından kullanılan aşağıdaki protokollerin WCF uygulama ayrıntılarını içerir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="849af-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="849af-106">Belirtim/belge:</span><span class="sxs-lookup"><span data-stu-id="849af-106">Specification/document:</span></span>

- [<span data-ttu-id="849af-107">HTTP 1,1</span><span class="sxs-lookup"><span data-stu-id="849af-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="849af-108">[SOAP 1,1 http bağlama](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="849af-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="849af-109">[SOAP 1,2 http bağlama](https://www.w3.org/TR/soap12-part2) Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="849af-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="849af-110">Bu konuda, ve kullanan aşağıdaki protokollerin WCF uygulama ayrıntıları ele <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> alınmaktadır <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="849af-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="849af-111">Belirtim/belge:</span><span class="sxs-lookup"><span data-stu-id="849af-111">Specification/Document:</span></span>

- [<span data-ttu-id="849af-112">XML</span><span class="sxs-lookup"><span data-stu-id="849af-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="849af-113">SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="849af-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="849af-114">SOAP 1,2 Core</span><span class="sxs-lookup"><span data-stu-id="849af-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="849af-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="849af-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="849af-116">W3C Web Hizmetleri adresleme 1,0-çekirdek</span><span class="sxs-lookup"><span data-stu-id="849af-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="849af-117">W3C Web Hizmetleri adresleme 1,0-SOAP bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="849af-118">W3C Web Hizmetleri adresleme 1,0-WSDL bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="849af-119">W3C Web Hizmetleri adresleme 1,0-meta veriler</span><span class="sxs-lookup"><span data-stu-id="849af-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="849af-120">WSDL SOAP 1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="849af-121">WSDL SOAP 1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="849af-122">Bu konuda, kullanan aşağıdaki protokollerin WCF uygulama ayrıntıları ele alınmaktadır <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="849af-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="849af-123">Belirtim/belge:</span><span class="sxs-lookup"><span data-stu-id="849af-123">Specification/document:</span></span>

- [<span data-ttu-id="849af-124">XOP ıNCLUDE</span><span class="sxs-lookup"><span data-stu-id="849af-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="849af-125">MTOM + SOAP 1,2 bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="849af-126">MTOM SOAP 1,1 bağlaması</span><span class="sxs-lookup"><span data-stu-id="849af-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="849af-127">MTOM WS-Ilke onaylama</span><span class="sxs-lookup"><span data-stu-id="849af-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="849af-128">Aşağıdaki XML ad alanları ve ilgili ön ekler Bu konu başlığı altında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="849af-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="849af-129">Ön ek</span><span class="sxs-lookup"><span data-stu-id="849af-129">Prefix</span></span> | <span data-ttu-id="849af-130">Ad alanı Tekdüzen Kaynak tanımlayıcısı (URI)</span><span class="sxs-lookup"><span data-stu-id="849af-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="849af-131">s11</span><span class="sxs-lookup"><span data-stu-id="849af-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="849af-132">S12</span><span class="sxs-lookup"><span data-stu-id="849af-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="849af-133">WSA</span><span class="sxs-lookup"><span data-stu-id="849af-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="849af-134">wsam</span><span class="sxs-lookup"><span data-stu-id="849af-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="849af-135">wsap</span><span class="sxs-lookup"><span data-stu-id="849af-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="849af-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="849af-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="849af-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="849af-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="849af-138">XOP Include</span><span class="sxs-lookup"><span data-stu-id="849af-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="849af-139">xmime</span><span class="sxs-lookup"><span data-stu-id="849af-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="849af-140">UDP</span><span class="sxs-lookup"><span data-stu-id="849af-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="849af-141">SOAP 1,1 ve SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="849af-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="849af-142">Zarf ve Işleme modeli</span><span class="sxs-lookup"><span data-stu-id="849af-142">Envelope and Processing Model</span></span>
<span data-ttu-id="849af-143">WCF, temel profil 1,1 (BP11) ve temel profil 1,0 (SSBP10) için SOAP 1,1 zarfı işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="849af-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="849af-144">SOAP 1,2 zarf işleme, SOAP12-part1 sonrasında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="849af-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="849af-145">Bu bölümde, BP11 ve SOAP12-part1 ile ilgili olarak WCF tarafından alınan bazı uygulama seçimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="849af-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="849af-146">Zorunlu üstbilgi Işleme</span><span class="sxs-lookup"><span data-stu-id="849af-146">Mandatory Header Processing</span></span>
<span data-ttu-id="849af-147">WCF, `mustUnderstand` soap 1,1 ve soap 1,2 belirtimleri bölümünde açıklanan üstbilgileri işlemek için aşağıdaki çeşitlerle kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="849af-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="849af-148">WCF kanal yığınına giren bir ileti, ilişkili bağlama öğeleri tarafından yapılandırılan tek tek kanallar tarafından işlenir; Örneğin, SMS mesajı Encoding, Security, güvenilir mesajlaşma ve Işlemler.</span><span class="sxs-lookup"><span data-stu-id="849af-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="849af-149">Her kanal, ilişkili ad alanındaki üst bilgileri tanır ve bunları anlamış olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="849af-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="849af-150">İleti dağıtıcıya girdiğinde, işlem biçimlendirici ilgili ileti/işlem sözleşmesi tarafından beklenen üstbilgileri okur ve anladım.</span><span class="sxs-lookup"><span data-stu-id="849af-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="849af-151">Ardından dağıtıcı, kalan tüm üstbilgilerin anlaşılmadığını ancak olarak işaretlendiğini doğrular `mustUnderstand` ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="849af-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="849af-152">`mustUnderstand`Alıcıya hedeflenen üst bilgiler içeren iletiler, alıcı uygulama kodu tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="849af-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="849af-153">Bu tür katmanlı işleme, altyapı katmanları ile SOAP düğümünün uygulama katmanları arasında ayrım yapılmasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="849af-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="849af-154">B1111: anlaşılmayan üstbilgiler, ileti WCF altyapı kanal yığını tarafından işlendikten sonra, ancak uygulama tarafından işlenmeden önce algılanır</span><span class="sxs-lookup"><span data-stu-id="849af-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="849af-155">`mustUnderstand`Üstbilgi DEĞERI soap 1,1 Ile soap 1,2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="849af-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="849af-156">Temel profil 1,1, `mustUnderstand` SOAP 1,1 iletileri için değerin 0 veya 1 olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="849af-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="849af-157">SOAP 1,2, 0, 1, `false` ve değerlerine izin verir `true` , ancak değerlerin kurallı bir gösterimini `xs:boolean` (,) yaymanızı önerir `false` `true` .</span><span class="sxs-lookup"><span data-stu-id="849af-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="849af-158">B1112: WCF SOAP `mustUnderstand` zarfının hem soap 1,1 hem de soap 1,2 sürümleri için 0 ve 1 değerlerini yayar.</span><span class="sxs-lookup"><span data-stu-id="849af-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="849af-159">WCF, üst bilgi için tüm değer alanını kabul eder `xs:boolean` `mustUnderstand` (0, 1, `false` , `true` )</span><span class="sxs-lookup"><span data-stu-id="849af-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="849af-160">SOAP hataları</span><span class="sxs-lookup"><span data-stu-id="849af-160">SOAP Faults</span></span>
<span data-ttu-id="849af-161">WCF 'e özgü SOAP hata uygulamalarının listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="849af-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="849af-162">B2121: WCF şu SOAP 1,1 hata kodlarını döndürür: `s11:mustUnderstand` , `s11:Client` , ve `s11:Server` .</span><span class="sxs-lookup"><span data-stu-id="849af-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="849af-163">B2122: WCF şu SOAP 1,2 hata kodlarını döndürür: `s12:MustUnderstand` , `s12:Sender` , ve `s12:Receiver` .</span><span class="sxs-lookup"><span data-stu-id="849af-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="849af-164">HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="849af-165">SOAP 1,1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="849af-166">WCF, aşağıdaki açıklığa kavuşturun temel profil 1,1 belirtim bölümünde 3,4 SOAP 1.1 HTTP bağlamasını uygular:</span><span class="sxs-lookup"><span data-stu-id="849af-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="849af-167">B2211: WCF hizmeti HTTP POST isteklerinin yeniden yönlendirilmesini uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="849af-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="849af-168">B2212: WCF istemcileri, 3.4.8 'e göre HTTP tanımlama bilgilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="849af-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="849af-169">SOAP 1,2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="849af-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="849af-170">WCF, SOAP 1,2-Part 2 (SOAP12Part2) belirtiminde aşağıda açıklandığı şekilde SOAP 1,2 HTTP bağlamasını uygular.</span><span class="sxs-lookup"><span data-stu-id="849af-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="849af-171">SOAP 1,2, medya türü için isteğe bağlı bir eylem parametresi sunmuştur `application/soap+xml` .</span><span class="sxs-lookup"><span data-stu-id="849af-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="849af-172">Bu parametre, WS-Addressing kullanılmazsa SOAP iletisi gövdesinin ayrıştırılmasını gerektirmeden ileti gönderimi iyileştirmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="849af-173">R2221: `application/soap+xml` BIR SOAP 1,2 isteğinde mevcut olduğunda Action parametresi, `soapAction` `wsoap12:operation` karşılık gelen wsdl bağlamasının içindeki öğe özniteliğiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="849af-174">R2222: `application/soap+xml` BIR SOAP 1,2 iletisinde mevcut olduğunda Action parametresi, `wsa:Action` ws-Addressing 2004/08 veya ws-Addressing 1,0 kullanıldığında eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="849af-175">WS-Addressing devre dışı olduğunda ve gelen istek bir eylem parametresi içermiyorsa, ileti `Action` belirtilmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="849af-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="849af-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="849af-176">WS-Addressing</span></span>
<span data-ttu-id="849af-177">WCF, WS-Addressing 3 sürümünü uygular:</span><span class="sxs-lookup"><span data-stu-id="849af-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="849af-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="849af-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="849af-179">W3C Web Hizmetleri adresleme 1,0 Core (ADDR10-CORE) ve SOAP Binding (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="849af-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="849af-180">WS-Addressing 1,0-meta veriler</span><span class="sxs-lookup"><span data-stu-id="849af-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="849af-181">Uç nokta başvuruları</span><span class="sxs-lookup"><span data-stu-id="849af-181">Endpoint References</span></span>
<span data-ttu-id="849af-182">WCF 'nin uyguladığı tüm WS-Addressing sürümleri uç noktaları tanımlayan uç nokta başvurularını kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="849af-183">Uç nokta başvuruları ve WS-Addressing sürümleri</span><span class="sxs-lookup"><span data-stu-id="849af-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="849af-184">WCF, WS-Addressing ve belirli bir `EndpointReference` öğe ve `W3C.WsAddressing.EndpointReferenceType` Sınıf (ÖRNEĞIN, WS-RELIABLEMESSAGING, ws-SecureConversation ve WS-Trust) kullanan bir dizi altyapı protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="849af-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="849af-185">WCF, diğer altyapı protokolleriyle her iki WS-Addressing sürümünün kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="849af-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="849af-186">WCF uç noktaları, uç nokta başına bir WS-Addressing sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="849af-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="849af-187">R3111 için, `EndpointReference` BIR WCF uç noktası ile değiş tokuş edilen iletilerde kullanılan öğe veya tür için ad alanı, bu uç nokta tarafından uygulanan ws-Addressing sürümüyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="849af-188">Örneğin, bir WCF uç noktası WS-ReliableMessaging ' i uygularsa, `AcksTo` içinde böyle bir uç nokta tarafından döndürülen üst bilgi, `CreateSequenceResponse` `EncodingBinding` Bu uç nokta IÇIN öğenin belirttiği ws-Addressing sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="849af-189">Uç nokta başvuruları ve meta verileri</span><span class="sxs-lookup"><span data-stu-id="849af-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="849af-190">Bir dizi senaryo, belirli bir uç nokta için meta verilerin veya bir meta verilerin bir başvurusunun iletişim kurmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="849af-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="849af-191">B3121: WCF, WS-MetadataExchange (MEX) belirtimi Bölüm 6 ' da açıklanan mekanizmaları kullanır. Bu, bir değere veya başvuruya göre uç nokta başvuruları için meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="849af-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="849af-192">WCF hizmetinin, ' de belirteç veren tarafından verilen güvenlik onayları biçimlendirme dili (SAML) belirtecini kullanarak kimlik doğrulaması gerektirdiğini bir senaryoya göz önünde bulundurun `http://sts.fabrikam123.com` .</span><span class="sxs-lookup"><span data-stu-id="849af-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="849af-193">WCF uç noktası `sp:IssuedToken` `sp:Issuer` , belirteç verene işaret eden iç içe onaylama ile onaylama kullanarak bu kimlik doğrulama gereksinimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="849af-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="849af-194">Onay işaretine erişen istemci uygulamaların `sp:Issuer` , belirteç verenin uç noktasıyla nasıl iletişim kuracağını bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="849af-195">İstemcinin belirteç veren ile ilgili meta verileri bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="849af-196">WCF 'de tanımlanan uç nokta başvurusu meta veri uzantılarını kullanarak WCF, belirteç verenin meta verilerine bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="849af-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="849af-197">İleti adresleme üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="849af-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="849af-198">İleti üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="849af-198">Message Headers</span></span>
<span data-ttu-id="849af-199">Her iki ws-Addressing sürümünde, WCF,,, ve belirtimleri tarafından belirtilen aşağıdaki ileti üstbilgilerini `wsa:To` kullanır `wsa:ReplyTo` `wsa:Action` `wsa:MessageID` `wsa:RelatesTo` .</span><span class="sxs-lookup"><span data-stu-id="849af-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="849af-200">B3211: tüm WS-Addressing sürümleri Için WCF, ancak WS-Addressing ileti üst bilgilerini `wsa:FaultTo` ve `wsa:From` .</span><span class="sxs-lookup"><span data-stu-id="849af-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="849af-201">WCF uygulamalarıyla etkileşime geçen uygulamalar, bu ileti üstbilgilerini ekleyebilir ve WCF bunları uygun şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="849af-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="849af-202">Başvuru parametreleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="849af-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="849af-203">WCF, ilgili belirtimlere uygun olarak uç nokta başvuru parametrelerinin ve başvuru özelliklerinin işlenmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="849af-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="849af-204">B3221: WS-Addressing 2004/08 kullanacak şekilde yapılandırıldığında, WCF uç noktaları işleme başvuru özelliklerini ve başvuru parametrelerini ayırt etmez.</span><span class="sxs-lookup"><span data-stu-id="849af-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="849af-205">İleti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="849af-205">Message Exchange Patterns</span></span>
<span data-ttu-id="849af-206">Web hizmeti işlem çağrısına dahil olan iletilerin sırası *ileti değişim düzeniyle*adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="849af-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="849af-207">WCF tek yönlü, istek-yanıt ve çift yönlü ileti değişimi düzenlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="849af-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="849af-208">Bu bölüm, kullanılan ileti değişimi düzenine bağlı olarak ileti işleme üzerindeki WS-Addressing gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="849af-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="849af-209">Bu bölümün tamamında, istek sahibi ilk iletiyi gönderir ve yanıtlayanın ilk iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="849af-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="849af-210">Tek yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="849af-210">One-Way Message</span></span>
<span data-ttu-id="849af-211">Bir WCF uç noktası, tek yönlü bir model izlemek için verilen iletileri destekleyecek şekilde yapılandırıldığında `Action` , WCF uç noktası aşağıdaki davranışları ve gereksinimleri izler.</span><span class="sxs-lookup"><span data-stu-id="849af-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="849af-212">Aksi belirtilmediği takdirde, WCF 'de desteklenen her iki WS-Addressing sürümü için davranışlar ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="849af-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="849af-213">R3311: istek sahibi, `wsa:To` `wsa:Action` uç nokta başvurusu tarafından belirtilen tüm başvuru parametreleri için, ve üst bilgilerini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="849af-214">WS-Addressing 2004/08 kullanıldığında ve [başvuru özellikleri] bitiş noktası başvurusuyla belirtildiğinde, ilgili üst bilgilerin iletiye de eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="849af-215">B3312: talep eden `MessageID` , `ReplyTo` ve `FaultTo` üst bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="849af-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="849af-216">Alıcı altyapısı onları yoksayacak ve uygulamaya geçirilecektir.</span><span class="sxs-lookup"><span data-stu-id="849af-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="849af-217">R3313: HTTP kullanıldığında ve HTTP yanıt baındaki bir ileti gönderilmediği zaman, yanıtlayanın boş bir gövdeye ve HTTP 202 durum koduna sahip bir HTTP yanıtı gönderebilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="849af-218">HTTP taşıması kullanımda olduğunda ve işlem anlaşması bir ileti tek yönlü olarak bildirilse de, HTTP yanıtı altyapı iletilerini göndermek için kullanılabilir. Örneğin, güvenilir mesajlaşma, `SequenceAcknowledgement` HTTP yanıtına bir ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="849af-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="849af-219">B3314: WCF Yanıtlayıcı, tek yönlü bir iletiye yanıt olarak hata iletisi göndermez.</span><span class="sxs-lookup"><span data-stu-id="849af-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="849af-220">İstek-Yanıt</span><span class="sxs-lookup"><span data-stu-id="849af-220">Request-Reply</span></span>
<span data-ttu-id="849af-221">Bir WCF uç noktası, `Action` istek-yanıt modelini izlemek için verilen bir ileti için yapılandırıldığında, WCF uç noktası aşağıdaki davranışları ve gereksinimleri izler.</span><span class="sxs-lookup"><span data-stu-id="849af-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="849af-222">Aksi belirtilmediği takdirde, WCF 'de desteklenen her iki WS-Addressing sürümü için davranışlar ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="849af-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="849af-223">R3321: talep `wsa:To` `wsa:Action` eden, `wsa:MessageID` tüm başvuru parametreleri için istek,, ve üst bilgileri ve uç nokta başvurusu tarafından belirtilen başvuru özelliklerini (veya her ikisi) içermelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="849af-224">R3322: WS-Addressing 2004/08 kullanıldığında, `ReplyTo` isteğe da eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="849af-225">R3323: WS-Addressing 1,0 kullanıldığında ve istekte yoksa `ReplyTo` , ' e eşit olan [address] özelliğine sahip bir varsayılan uç nokta başvurusu `http://www.w3.org/2005/08/addressing/anonymous` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="849af-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="849af-226">R3324: talep `wsa:To` `wsa:Action` eden, yanıt iletisindeki,, ve `wsa:RelatesTo` üst bilgilerin yanı sıra, `ReplyTo` istekteki uç nokta başvurusuyla belirtilen tüm başvuru parametreleri veya başvuru özellikleri (ya da her ikisi) için üst bilgiler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="849af-227">Web Hizmetleri adresleme hataları</span><span class="sxs-lookup"><span data-stu-id="849af-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="849af-228">R3411: WCF, WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="849af-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="849af-229">Kod</span><span class="sxs-lookup"><span data-stu-id="849af-229">Code</span></span> | <span data-ttu-id="849af-230">Nedeni</span><span class="sxs-lookup"><span data-stu-id="849af-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="849af-231">İleti, `ReplyTo` Bu kanal için belirlenen yanıt adresinden farklı bir ile ulaştı; bitiş üstbilgisinde belirtilen adreste dinleme yapan bir uç nokta yok.</span><span class="sxs-lookup"><span data-stu-id="849af-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="849af-232">uç noktayla ilişkili altyapı kanalları veya dağıtıcı üst bilgide belirtilen eylemi tanımıyor `Action` .</span><span class="sxs-lookup"><span data-stu-id="849af-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="849af-233">R3412: WCF, WS-Addressing 1,0 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="849af-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="849af-234">Kod</span><span class="sxs-lookup"><span data-stu-id="849af-234">Code</span></span> | <span data-ttu-id="849af-235">Nedeni</span><span class="sxs-lookup"><span data-stu-id="849af-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="849af-236">Yinelenen `wsa:To` , `wsa:ReplyTo` , `wsa:From` veya `wsa:MessageID` .</span><span class="sxs-lookup"><span data-stu-id="849af-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="849af-237">`wsa:RelatesTo`Aynı ile yineleniyor `RelationshipType` .</span><span class="sxs-lookup"><span data-stu-id="849af-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="849af-238">Gerekli adresleme üst bilgisi eksik.</span><span class="sxs-lookup"><span data-stu-id="849af-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="849af-239">İleti, `ReplyTo` Bu kanal için belirlenen yanıt adresinden farklı bir ile ulaştı.</span><span class="sxs-lookup"><span data-stu-id="849af-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="849af-240">' In üst bilgisinde belirtilen adreste dinleme yapan bir uç nokta yok.</span><span class="sxs-lookup"><span data-stu-id="849af-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="849af-241">Üst bilgide belirtilen bir eylem, `Action` uç noktayla ilişkili altyapı kanalları veya dağıtıcı tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="849af-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="849af-242">RM kanalı bu hatayı geri gönderir ve uç noktanın, `CreateSequence` iletinin adres üst bilgilerinin incelenmesi için sırayı işlemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="849af-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="849af-243">Yukarıdaki tablolardaki kod SOAP 1,2 ' de `FaultCode` soap 1,1 ve `SubCode` (Code = sender ile) ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="849af-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="849af-244">WSDL 1,1 bağlama ve WS-Policy onayları</span><span class="sxs-lookup"><span data-stu-id="849af-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="849af-245">WS-Addressing kullanımını belirtir</span><span class="sxs-lookup"><span data-stu-id="849af-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="849af-246">WCF, belirli bir WS-Addressing sürümü için uç nokta desteğini göstermek üzere ilke onayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="849af-247">Aşağıdaki ilke onaylamanın uç nokta Ilkesi konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08 kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="849af-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="849af-248">Bu ilke onaylama işlemi WS-Addressing 2004/08 belirtimini genişletmelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="849af-249">Aşağıdaki ilke onaylama işlemi, gönderilen/alınan iletilerin WS-Addressing 1,0 kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="849af-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="849af-250">Aşağıdaki ilke onaylamanın bir uç nokta Ilkesi konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08 kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="849af-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="849af-251">`wsaw10:UsingAddressing`Öğesi [ws-Addressing-WSDL] öğesinden ödünç verilir ve bu belirtim, Bölüm 3.1.2 ile uyumlu WS-Policy bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="849af-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="849af-252">Adresleme kullanımı, WSDL 1,1, SOAP 1,1 ve SOAP 1,2 HTTP bağlamalarının semantiğini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="849af-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="849af-253">Örneğin, bir yanıtın, adresleme ve WSDL SOAP 1. x HTTP bağlama kullanan bir uç noktaya gönderilen bir istek olması bekleniyorsa, yanıt HTTP yanıtı kullanılarak gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="849af-254">Http yanıtı üzerinden gönderilen yanıtlar için, WS-har onaylama:</span><span class="sxs-lookup"><span data-stu-id="849af-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="849af-255">Tüm ilke onaylama işlemi şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="849af-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="849af-256">Bununla birlikte, istek sahibi ve Yanıtlayıcı arasında iki bağımsız listesiyse http bağlantısının (örneğin, Yanıtlayıcı tarafından gönderilen istenmeyen tek yönlü iletiler) olmasına yönelik ileti alışverişi desenleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="849af-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="849af-257">WCF, iki temel taşıma kanalının bir kanalın giriş iletileri için kullanıldığı ve çıkış iletileri için kullanıldığı bir bileşik çift yönlü kanal oluşturmasının sağladığı bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="849af-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="849af-258">HTTP taşıması durumunda, bileşik çift yönlü iki listesiyse http bağlantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="849af-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="849af-259">İstek sahibi, yanıtlaya ileti göndermek için bir bağlantı kullanır ve Yanıtlayıcı, iletileri istek sahibine geri göndermek için diğerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="849af-260">Ayrı http istekleri üzerinden gönderilen yanıtlar için, WS-har onaylama işlemi</span><span class="sxs-lookup"><span data-stu-id="849af-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="849af-261">Tüm ilke onaylama işlemi şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="849af-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="849af-262">WSDL 1,1 SOAP 1. x http bağlamaları kullanan uç noktalarda uç nokta ilkesi konusunun [ws-PA] sahip olduğu aşağıdaki onaylama işleminin kullanılması, istek sahibinin, sırasıyla yanıtlayanın ve yanıtlayanın istek temelli olarak yanıtlamanın kullanıldığı iletiler için iki ayrı listesiyse http bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="849af-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="849af-263">Önceki ifade, istek iletileri üstbilgisinde aşağıdaki gereksinimlere yol gösterir `wsa:ReplyTo` :</span><span class="sxs-lookup"><span data-stu-id="849af-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="849af-264">R3514: uç nokta `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` BIR WSDL 1,1 SOAP 1. x http bağlamasını kullanıyorsa ve ekli ile bağlanmış bir ilke alternatifi olan bir uç noktaya gönderilen istek iletilerinin, özelliği eşit olmayan bir üst bilgisine sahip olması gerekir `wsap10:UsingAddressing` `wsap:UsingAddressing` `cdp:CompositeDuplex` .</span><span class="sxs-lookup"><span data-stu-id="849af-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="849af-265">R3515: bir uç nokta bir `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` `ReplyTo` WSDL 1,1 SOAP 1. x http bağlamasını kullanıyorsa ve bir ilke alternatifi `wsap10:UsingAddressing` ve onaylama ve onaylama olmadan bir ilke alternatifi `cdp:CompositeDuplex` varsa, bir uç noktaya gönderilen istek iletilerinin bir üst bilgisine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="849af-266">R3516: uç nokta `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` BIR WSDL 1,1 SOAP 1. x HTTP bağlaması kullanıyorsa ve onaylama ve onaylama olmadan bir ilke alternatifi varsa, bir uç noktaya gönderilen istek iletilerinin bir özelliği olan bir üst bilgisine sahip olması gerekir `wsap:UsingAddressing` `cdp:CompositeDuplex` .</span><span class="sxs-lookup"><span data-stu-id="849af-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="849af-267">WS-Addressing WSDL belirtimi, `<wsaw:Anonymous/>` `wsa:ReplyTo` üst bilgide (Bölüm 3,2) üç metinsel değer içeren bir öğe (gerekli, isteğe bağlı ve yasaklanmış) girerek benzer protokol bağlamalarını açıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="849af-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="849af-268">Ne yazık ki, bu tür öğe tanımı özellikle WS-Policy bağlamında bir onaylama işlemi olarak kullanılamaz, çünkü bu tür bir öğeyi onaylama olarak kullanma alternatiflerini desteklemek için etki alanına özgü uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="849af-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="849af-269">Bu tür öğe tanımı Ayrıca `ReplyTo` , ana hat üzerindeki uç nokta davranışına karşılık olarak, http taşımasına özel hale getiren üst bilgi değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="849af-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="849af-270">Eylem tanımı</span><span class="sxs-lookup"><span data-stu-id="849af-270">Action Definition</span></span>
<span data-ttu-id="849af-271">WS-Addressing 2004/08 `wsa:Action` , öğeler için bir özniteliği tanımlar `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` .</span><span class="sxs-lookup"><span data-stu-id="849af-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="849af-272">WS-Addressing 1,0 WSDL bağlama (WS-ADDR10-WSDL), benzer bir özniteliği tanımlar `wsaw10:Action` .</span><span class="sxs-lookup"><span data-stu-id="849af-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="849af-273">İkisi arasındaki tek fark, sırasıyla WS-ADDR 3.3.2 of WS-ADDR ve Section 4.4.4 bölümünde açıklanan varsayılan eylem deseninin semantiklerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="849af-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="849af-274">Aynı `portType` (veya aynı zamanda, WCF terminolojisinde olan), ancak farklı ws-Addressing sürümlerini kullanan iki uç nokta olması mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="849af-275">Ancak, bu eylem tarafından tanımlanır `portType` ve öğesini uygulayan uç noktalar genelinde değişmemelidir `portType` , her iki varsayılan eylem desenini desteklemek imkansız olur.</span><span class="sxs-lookup"><span data-stu-id="849af-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="849af-276">Bu Controversy 'yi çözmek için, WCF özniteliğin tek bir sürümünü destekler `Action` .</span><span class="sxs-lookup"><span data-stu-id="849af-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="849af-277">B3521: WCF, `wsaw10:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` `Action` uç nokta tarafından kullanılan ws-Addressing sürümünden bağımsız olarak, karşılık gelen iletiler için URI 'yi BELIRLEMEDE WS-ADDR10-WSDL ' d e tanımlanan öğeler üzerinde özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="849af-278">WSDL bağlantı noktası Içinde uç nokta başvurusu kullan</span><span class="sxs-lookup"><span data-stu-id="849af-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="849af-279">WS-ADDR10-WSDL Bölüm 4,1, `wsdl:port` ÖĞEYI `<wsa10:EndpointReference…/>` ws-Addressing koşullarında bitiş noktasını tanımlayacak alt öğe içerecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="849af-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="849af-280">WCF, bu yardımcı programı WS-Addressing 2004/08 ' de genişleterek `<wsa:EndpointReference…/>` alt öğesi olarak görünmesine izin verir `wsdl:port` .</span><span class="sxs-lookup"><span data-stu-id="849af-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="849af-281">R3531: bir uç nokta, ilke onaylama işlemi ile bağlı bir ilke alternatifi içeriyorsa `<wsaw10:UsingAddressing/>` , karşılık gelen `wsdl:port` öğe bir alt öğe içerebilir `<wsa10:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="849af-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="849af-282">R3532: bir `wsdl:port` alt öğe içeriyorsa `<wsa10:EndpointReference …/>` , `wsa10:EndpointReference/wsa10:Address` alt öğe değeri `@address` eşdüzey öğenin özniteliğinin değeriyle eşleşmelidir `wsdl:port` / `wsdl:location` .</span><span class="sxs-lookup"><span data-stu-id="849af-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="849af-283">R3533: bir uç nokta, ilke onaylama ile ilişkili bir ilke alternatifi içeriyorsa `<wsap:UsingAddressing/>` , karşılık gelen `wsdl:port` öğe bir alt öğe içerebilir `<wsa:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="849af-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="849af-284">R3534: bir `wsdl:port` alt öğe içeriyorsa `<wsa:EndpointReference …/>` , `wsa:EndpointReference/wsa:Address` alt öğe değeri `@address` eşdüzey öğenin özniteliğinin değeriyle eşleşmelidir `wsdl:port` / `wsdl:location` .</span><span class="sxs-lookup"><span data-stu-id="849af-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="849af-285">WS-Security ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="849af-285">Composition with WS-Security</span></span>
<span data-ttu-id="849af-286">WS-ADDR ve WS-ADDR10 ' deki güvenlik değerlendirmesi bölümlerine göre, tüm adresleme ileti başlıklarının birlikte bağlamak için ileti gövdesinde birlikte imzalanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="849af-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="849af-287">İleti bütünlüğü koruması için WS-Security kullanıldığında, WS-Addressing ileti üstbilgileri ve başvuru parametrelerinden veya özelliklerden (ya da her ikisi) kaynaklanan üstbilgilerin ileti gövdesinde birlikte imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="849af-288">Örnekler</span><span class="sxs-lookup"><span data-stu-id="849af-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="849af-289">Tek yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="849af-289">One-Way Message</span></span>
<span data-ttu-id="849af-290">Bu senaryoda, gönderici alıcıya tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="849af-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="849af-291">SOAP 1,2, HTTP 1,1 ve W3C WS-Addressing 1,0 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="849af-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="849af-292">Istek Iletisi yapısı: ileti üstbilgileri `wsa10:To` ve `wsa10:Action` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="849af-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="849af-293">İleti gövdesi `<app:Ping>` , uygulama ad alanından belirli bir öğeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="849af-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="849af-294">HTTP üstbilgileri: POSTADAKI hedef, öğesindeki URI ile eşleşir `wsa10:To` .</span><span class="sxs-lookup"><span data-stu-id="849af-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="849af-295">Content-Type üst bilgisinin `application/soap+xml` SOAP 1,2 için gereken şekilde değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="849af-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="849af-296">Parametreler `charset` ve `action` dahildir.</span><span class="sxs-lookup"><span data-stu-id="849af-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="849af-297">`action`Content-Type üstbilgisinin parametresi, `wsa10:Action` ileti üstbilgisinin değeriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="849af-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```http
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

<span data-ttu-id="849af-298">Alıcı, boş bir HTTP yanıtı ve 202 durumu ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="849af-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="849af-299">HTTP yanıtına bir örnek:</span><span class="sxs-lookup"><span data-stu-id="849af-299">An example of the HTTP response:</span></span>

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="849af-300">SOAP Ileti Iletimi Iyileştirme mekanizması</span><span class="sxs-lookup"><span data-stu-id="849af-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="849af-301">Bu bölümde, HTTP SOAP MTOM için WCF uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="849af-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="849af-302">MTOM teknolojisi, geleneksel metin/XML kodlaması veya WCF Ikili kodlaması ile aynı sınıfın SOAP ileti kodlama mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="849af-303">MTOM şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="849af-303">MTOM includes the following:</span></span>

- <span data-ttu-id="849af-304">Base64 kodlamalı ikili verileri içeren XML bilgi öğelerini ayrı ikili parçalara ayıran XML kodlama ve paketleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="849af-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="849af-305">XML bilgi kümesini ve XOP Package her bir ikili parçasını seri hale getirilen XOP paketini ayrı bir MIME bölümüne diztiren bir MIME kapsülleme.</span><span class="sxs-lookup"><span data-stu-id="849af-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="849af-306">SOAP 1. x zarfı için uygulanan bir MIME XOP kodlaması.</span><span class="sxs-lookup"><span data-stu-id="849af-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="849af-307">HTTP taşıma bağlaması.</span><span class="sxs-lookup"><span data-stu-id="849af-307">An HTTP transport binding.</span></span>

<span data-ttu-id="849af-308">WCF ile HTTP olmayan aktarımlarla MTOM kullanılması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="849af-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="849af-309">Bununla birlikte, bu konu başlığında HTTP 'ye odaklanacağız.</span><span class="sxs-lookup"><span data-stu-id="849af-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="849af-310">MTOM biçimi, MTOM kendisini, XOP ve MIME 'yi kapsayan büyük bir belirtim kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="849af-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="849af-311">Bu belirtim kümesinin modülerliği, tam gereksinimlerin biçim ve işleme semantiğinin yeniden ayarlanabilmesini oldukça zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="849af-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="849af-312">Bu bölümde, MTOM HTTP bağlamasının biçim ve işleme gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="849af-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="849af-313">MTOM Ileti kodlaması</span><span class="sxs-lookup"><span data-stu-id="849af-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="849af-314">MTOM iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="849af-314">Generating MTOM messages</span></span>
<span data-ttu-id="849af-315">[XOP] Bölüm 3,1, bir soyut olarak tanımlanmış bir XOP Package içinde Base64 değerleri içeren öğe bilgi öğeleriyle XML kodlama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="849af-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="849af-316">Aşağıdaki adımlar dizisi, MTOM 'e özgü kodlama işlemini açıklar:</span><span class="sxs-lookup"><span data-stu-id="849af-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="849af-317">Kodlanacak SOAP zarfının, ve içeren bir öğe bilgisi öğesi olmadığından emin olun `[namespace name]` `http://www.w3.org/2004/08/xop/include` `[local name]` `Include` .</span><span class="sxs-lookup"><span data-stu-id="849af-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="849af-318">Boş bir MIME paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="849af-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="849af-319">Özgün XML Infoset içinde, en iyi duruma getirilecek öğe bilgisi öğelerini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="849af-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="849af-320">Öğelerin en iyi duruma getirilmesi için, `[children]` öğe bilgileri öğesini oluşturan karakterlerin kurallı biçiminde olması gerekir `xs:base64Binary` (bkz. xsd-2, 3.2.16 base64Binary) ve boşluk olmayan veya sonrasında boşluk olmayan hiçbir boşluk karakteri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="849af-321">Özgün SOAP zarfının bir kopyası olan bir XOP SOAP Zarfı oluşturun, ancak önceki adımda tanımlanan her öğe bilgi öğesinin alt öğeleri `xop:Include` aşağıdaki şekilde oluşturulmuş bir öğe bilgisi öğesiyle değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="849af-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="849af-322">Değiştirilmiş karakterleri Base64 ile kodlanmış veriler olarak işleyerek ikili verilere dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="849af-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="849af-323">R3133 ve R3134 gereksinimlerini karşılayan benzersiz bir Içerik KIMLIĞI üst bilgisi değeri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="849af-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="849af-324">Binary değeri olan Content-Transfer-Encoding MIME üst bilgisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="849af-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="849af-325">En iyi duruma getirilen öğe bilgisi öğesi (yeni eklenen öğe bilgileri öğesinin [üst] `xop:Include` ) bir `xmime:contentType` öznitelik bilgisi öğesi içeriyorsa, özniteliği değeri olan bir Content-Type MIME üst bilgisi oluşturun `xmime:contentType` .</span><span class="sxs-lookup"><span data-stu-id="849af-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="849af-326">Base64 olarak işlenen ve adım 4d ' de oluşturulduysa, 4c 'den Content-Transfer-Encoding üst bilgisi, Content-Transfer-Encoding üst bilgisinden (örneğin,)</span><span class="sxs-lookup"><span data-stu-id="849af-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="849af-327">`href` `xop:Include` Öğeye CID değeri olan bir öznitelik ekleyin: Adım 4B Içinde oluşturulan Content-ID üstbilgi değerinden türetilmiş URI.</span><span class="sxs-lookup"><span data-stu-id="849af-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="849af-328">Kapsayan " \<" and "> " karakterlerini kaldırın, URL 'yi kalan dizeyi kaçış ve ön eki ekleme `cid:` .</span><span class="sxs-lookup"><span data-stu-id="849af-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="849af-329">Aşağıdaki en küçük karakter kümesinin RFC1738 ve RFC2396 tarafından kaçılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="849af-330">Diğer karakterlerin kaçışlı olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="849af-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="849af-331">4. adımda XOP SOAP Zarfı ile bir kök MIME bölümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="849af-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="849af-332">HTTP Content-Type üst bilgisi dahil HTTP üst bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="849af-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="849af-333">MIME paketini yazın.</span><span class="sxs-lookup"><span data-stu-id="849af-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="849af-334">MTOM iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="849af-334">Processing MTOM messages</span></span>
<span data-ttu-id="849af-335">Bir MTOM iletisinin işlenmesi, önceki "MTOM iletileri oluşturma" bölümünde açıklanan işlemin tam tersidir:</span><span class="sxs-lookup"><span data-stu-id="849af-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="849af-336">Kök MIME bölümünün Içerik türüyle aynı olduğundan emin olun `application/xop+xml` .</span><span class="sxs-lookup"><span data-stu-id="849af-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="849af-337">Paketin kök MIME bölümünü bir XML belgesi olarak ayrıştırarak bir SOAP Zarfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="849af-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="849af-338">Karakter kodlaması, `charset` kök MIME bölümünün Içerik türünün parametresine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="849af-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="849af-339">Oluşturulan SOAP zarfının içindeki her öğe bilgi öğesi için, [children] özelliğinin tek üyesi olarak bir `xop:Include` öğe bilgisi öğesi olarak:</span><span class="sxs-lookup"><span data-stu-id="849af-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="849af-340">Öneki kaldırın `cid:` ve öğenin özniteliği değerindeki tüm URI kaçış dizilerini (RFC 2396) kaldırın `@href` `xop:Include` .</span><span class="sxs-lookup"><span data-stu-id="849af-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="849af-341">Sonuç dizesini "" içine alın \<", "> .</span><span class="sxs-lookup"><span data-stu-id="849af-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="849af-342">Content-ID üst bilgisi değeri ile birlikte, adım 3A ' da türetilmiş dizeyle eşleşen MIME bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="849af-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="849af-343">`xop:Include`Her bir öğenin özelliğinde görünen öğe bilgisi öğesini, `children` adım 3b'de tanımlanan MIME bölümünün varlık gövdesinin (bkz. xsd-2, 3.2.16 base64Binary), adım 3B ' de tanımlanan MIME bölümünün varlık gövdesinin (bkz `xop:Include` ., öğe bilgileri öğesini paket bölümünden yeniden yapılandırılmış verilerle değiştirin</span><span class="sxs-lookup"><span data-stu-id="849af-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="849af-344">HTTP Content-Type üst bilgisi</span><span class="sxs-lookup"><span data-stu-id="849af-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="849af-345">Aşağıda, MTOM belirtiminde belirtilen gereksinimlerden türetilmiş ve MTOM ve RFC 2387 ' den türetilen bir SOAP 1. x MTOM kodlu iletinin HTTP Content-Type üstbilgisinin biçimi için WCF açıklığa kavuşturininin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="849af-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="849af-346">R4131: bir HTTP Content-Type üst bilgisi, çok parçalı/ilgili (büyük/küçük harf duyarsız) ve parametrelerinin parametrelerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="849af-347">Parametre adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="849af-348">Parametre sırası önemli değil.</span><span class="sxs-lookup"><span data-stu-id="849af-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="849af-349">MIME iletileri için Content-Type üstbilgisinin tam Backus-Naur form (BNF), RFC 2045, Bölüm 5,1 ' de listelenir.</span><span class="sxs-lookup"><span data-stu-id="849af-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="849af-350">R4132: bir HTTP Content-Type üst bilgisinde `application/xop+xml` çift tırnak işareti içine alınmış değere sahip bir tür parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="849af-351">Çift tırnak işaretlerini kullanma gereksinimi RFC 2387 ' de açık olmadığından, büyük olasılıkla çok parçalı/ilgili medya türü parametrelerinin tümünün " \@ " veya "/" gibi ayrılmış karakterler içermesi ve bu nedenle çift tırnak işaretleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="849af-352">R4133: bir HTTP Content-Type üst bilgisinde, çift tırnak işareti içine alınmış SOAP 1. x zarfı içeren MIME bölümünün Content-ID üstbilgisinin değeri ile bir start parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="849af-353">Başlangıç parametresi atlanırsa, ilk MIME bölümünün SOAP 1. x zarfı içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="849af-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="849af-354">R4134: SOAP 1,1 MTOM kodlamalı bir ileti için bir HTTP Content-Type üst bilgisi, metin/xml değeri olan Start-Info parametresini çift tırnak işareti içine almalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="849af-355">R4135: SOAP 1,2 MTOM kodlu bir ileti için bir HTTP Content-Type üst bilgisi, değeri çift tırnak içine alınmış olan Start-Info parametresini içermelidir `application/soap+xml` .</span><span class="sxs-lookup"><span data-stu-id="849af-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="849af-356">R4136: bir SOAP 1. x MTOM kodlu ileti için HTTP Content-Type üst bilgisi, RFC 2046, Bölüm 5.1.1 ' de tanımlanan (çift tırnak işaretleri içine alınmış) bir sınır parametresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="849af-357">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="849af-357">Examples:</span></span>

     <span data-ttu-id="849af-358">DÜZELTMEYE</span><span class="sxs-lookup"><span data-stu-id="849af-358">CORRECT</span></span>

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="849af-359">DÜZELTMEYE</span><span class="sxs-lookup"><span data-stu-id="849af-359">CORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="849af-360">OLMAYAN</span><span class="sxs-lookup"><span data-stu-id="849af-360">INCORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="849af-361">Bilgi kümesi MIME bölümü</span><span class="sxs-lookup"><span data-stu-id="849af-361">Infoset MIME Part</span></span>
<span data-ttu-id="849af-362">SOAP 1. x zarfı, XOP MIME paketinin kök parçası olarak kapsüllenir ve genellikle bölüm olarak adlandırılır `infoset` .</span><span class="sxs-lookup"><span data-stu-id="849af-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="849af-363">R4141: SOAP 1. x zarfı, ' ın parçası olarak adlandırılan `infoset` ve http Content-Type ' dan başvurulan, XOP MIME paketinin kök parçası olarak kapsüllenmelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="849af-364">R4142: SOAP `Infoset` bölümü AŞAĞıDAKI MIME üstbilgilerini içermelidir: `Content-ID` , `Content-Transfer-Encoding` , ve `Content-Type` .</span><span class="sxs-lookup"><span data-stu-id="849af-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="849af-365">Content-ID üstbilgisinin biçimi RFC 2045 tarafından şu şekilde tanımlanır</span><span class="sxs-lookup"><span data-stu-id="849af-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="849af-366">`msg-id`, rfc 2822 ' de (rfc 2045 ' de başvurulur olan rfc 822 ' de bulunur) şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="849af-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="849af-367">ve "" içine alınmış etkin bir e-posta adresidir \<" and  "> .</span><span class="sxs-lookup"><span data-stu-id="849af-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="849af-368">`[CFWS]`Ön ek ve sonek, açıklama taşımak IÇIN RFC 2822 ' ye eklenmiştir ve birlikte çalışabilirliği korumak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="849af-369">R4143: Infoset MIME bölümü için Content-ID üstbilgisinin değeri, `msg-id` RFC 2822 `[CFWS]` ' den ön ek ve sonek bölümleri atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="849af-370">"" İçinde bir e-posta adresi \<" and "> olması ve `absoluteURI` \<" , "> e-posta adresine ek olarak "" içinde kullanılması için "" içinde yer alan değer için gevşek gereksinimlere sahıp bir dizi MIME uygulaması.</span><span class="sxs-lookup"><span data-stu-id="849af-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="849af-371">WCF 'nin bu sürümü, formun Content-ID MIME üstbilgisinin değerlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="849af-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="849af-372">R4144: MTOM işlemcileri, aşağıdaki gevşek ile eşleşen Içerik KIMLIĞI üst bilgi değerlerini kabul etmelidir `msg-id` .</span><span class="sxs-lookup"><span data-stu-id="849af-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="849af-373">MIME (RFC 2045), MIME bölümünün içeriğinin kodlanmasını iletmek için Content-Transfer-Encoding üst bilgisini sağlar.</span><span class="sxs-lookup"><span data-stu-id="849af-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="849af-374">Content-Transfer-Encoding için tanımlanan varsayılan değer 7 bittir, bu da çoğu SOAP iletisi için uygun değildir, bu nedenle daha fazla birlikte çalışabilirlik için Content-Transfer-Encoding üst bilgisi gereklidir:</span><span class="sxs-lookup"><span data-stu-id="849af-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="849af-375">R4145: SOAP bilgi kümesi bölümü Content-Transfer-Encoding üst bilgisini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="849af-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="849af-376">R4146: SOAP Zarf karakter kodlaması UTF-8 ise Content-Transfer-Encoding üstbilgisinin değeri 8 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="849af-377">R4147: SOAP Zarf karakter kodlaması UTF-16 ise, Content-Transfer-Encoding üst bilgisinin değeri binary olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="849af-378">[XOP] Bölüm 5 ' e göre,</span><span class="sxs-lookup"><span data-stu-id="849af-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="849af-379">R4148: SOAP 1.1 Infoset bölümü, medya türü application/xop + xml ve Parameters Type = "text/xml" ve charset olan Content-Type üst bilgisi içermelidir</span><span class="sxs-lookup"><span data-stu-id="849af-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="849af-380">R4149: SOAP 1,2 Infoset bölümü, medya türü `application/xop+xml` ve parametre türü = "" olan Content-Type üst bilgisini içermelidir `application/soap+xml` `charset` .</span><span class="sxs-lookup"><span data-stu-id="849af-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="849af-381">XOP, için `charset` parametresini `application/xop+xml` isteğe bağlı olarak tanımladığında, `charset` medya türü için parametresindeki BP 1,1 gereksinimine benzer şekilde birlikte çalışabilirlik için bu gereklidir `text/xml` .</span><span class="sxs-lookup"><span data-stu-id="849af-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="849af-382">R41410: `type` ve `charset` parametreleri soap 1. x Infoset bölümünün Content-Type üstbilgisinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="849af-383">MTOM için WCF uç noktası desteği</span><span class="sxs-lookup"><span data-stu-id="849af-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="849af-384">MTOM 'in amacı, Base64 kodlamalı verileri iyileştirmek için bir SOAP iletisi kodlayasağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="849af-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="849af-385">Kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="849af-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="849af-386">R4151: Base64 kodlamalı verileri içeren herhangi bir öğe bilgisi öğesi iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="849af-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="849af-387">B4152: WCF, Base64 kodlamalı verileri içeren ve 1024 baytlık uzunluğu aşan öğe bilgisi öğelerini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="849af-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="849af-388">MTOM 'i kullanacak şekilde yapılandırılmış bir WCF uç noktası, her zaman MTOM kodlu iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="849af-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="849af-389">Gerekli ölçütlere uyan hiçbir bölüm olmasa bile, ileti hala MTOM kodlamalı (SOAP Zarfı içeren tek bir MIME parçası ile bir MIME paketi olarak serileştirilir).</span><span class="sxs-lookup"><span data-stu-id="849af-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="849af-390">MTOM için WS-Policy assertion</span><span class="sxs-lookup"><span data-stu-id="849af-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="849af-391">WCF, uç noktaya göre MTOM kullanımını göstermek için aşağıdaki ilke onayını kullanır:</span><span class="sxs-lookup"><span data-stu-id="849af-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="849af-392">R4211: Yukarıdaki ilke onaylaması bir uç nokta Ilkesi konusuna sahiptir ve uç noktadan gönderilen ve alınan tüm iletilerin MTOM kullanılarak iyileştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="849af-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="849af-393">B4212: MTOM iyileştirmesi kullanacak şekilde yapılandırıldığında, bir WCF uç noktası karşılık gelen ilkeye bir MTOM Ilke onayı ekler `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="849af-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="849af-394">WS-Security ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="849af-394">Composition with WS-Security</span></span>
<span data-ttu-id="849af-395">MTOM, `text/xml` ve WCF IKILI XML 'e benzer bir kodlama mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="849af-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="849af-396">MTOM, WS-Security ve diğer WS-\* protokolleriyle doğal bileşim sunar: WS-Security kullanılarak güvenliği sağlanmış bir ileti, MTOM kullanılarak iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="849af-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="849af-397">Örnekler</span><span class="sxs-lookup"><span data-stu-id="849af-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="849af-398">MTOM kullanılarak kodlanan WCF SOAP 1,1 Iletisi</span><span class="sxs-lookup"><span data-stu-id="849af-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```http
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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="849af-399">MTOM kullanılarak WCF güvenli SOAP 1,2 Iletisi kodlandı</span><span class="sxs-lookup"><span data-stu-id="849af-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="849af-400">Bu örnekte, bir ileti, MTOM ve WS-Security kullanılarak korunan SOAP 1,2 kullanılarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="849af-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="849af-401">Kodlama için tanımlanan ikili parçalar, `BinarySecurityToken` `CipherValue` `EncryptedData` şifreli imzaya ve şifrelenmiş gövdeye karşılık gelen öğesinin içeriğidir.</span><span class="sxs-lookup"><span data-stu-id="849af-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="849af-402">`CipherValue`Öğesinin `EncryptedKey` uzunluğu daha az 1024 bayt olduğu için WCF tarafından iyileştirmede tanımlanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="849af-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```http
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
