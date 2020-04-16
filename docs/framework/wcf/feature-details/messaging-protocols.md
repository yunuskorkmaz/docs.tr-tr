---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463825"
---
# <a name="messaging-protocols"></a><span data-ttu-id="7b688-102">Mesajlaşma Protokolleri</span><span class="sxs-lookup"><span data-stu-id="7b688-102">Messaging Protocols</span></span>

<span data-ttu-id="7b688-103">Windows Communication Foundation (WCF) kanal yığını, dahili ileti gösterimini tel biçimine dönüştürmek ve belirli bir aktarım kullanarak göndermek için kodlama ve aktarım kanalları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="7b688-104">Web hizmetleri birlikte çalışabilirlik için kullanılan en yaygın aktarım HTTP'dir ve Web hizmetleri tarafından kullanılan en yaygın kodlamalar XML tabanlı SOAP 1.1, SOAP 1.2 ve İleti İletim OptimizasyonU Mekanizması 'dır (MTOM).</span><span class="sxs-lookup"><span data-stu-id="7b688-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="7b688-105">Bu konu, aşağıdaki protokoller için WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>uygulama ayrıntılarını kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b688-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="7b688-106">Belirtim/belge:</span><span class="sxs-lookup"><span data-stu-id="7b688-106">Specification/document:</span></span>

- [<span data-ttu-id="7b688-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="7b688-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="7b688-108">[SOAP 1.1 HTTP Ciltleme](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="7b688-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="7b688-109">[SOAP 1.2 HTTP Ciltleme](https://www.w3.org/TR/soap12-part2) Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="7b688-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="7b688-110">Bu konu, aşağıdaki protokoller için WCF uygulama ayrıntılarını kapsar <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="7b688-111">Şartname/Belge:</span><span class="sxs-lookup"><span data-stu-id="7b688-111">Specification/Document:</span></span>

- [<span data-ttu-id="7b688-112">Xml</span><span class="sxs-lookup"><span data-stu-id="7b688-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="7b688-113">SABUN 1.1</span><span class="sxs-lookup"><span data-stu-id="7b688-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="7b688-114">SOAP 1.2 Çekirdek</span><span class="sxs-lookup"><span data-stu-id="7b688-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="7b688-115">WS-Adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="7b688-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="7b688-116">W3C Web Hizmetleri Adresleme 1.0 - Çekirdek</span><span class="sxs-lookup"><span data-stu-id="7b688-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="7b688-117">W3C Web Hizmetleri Adresleme 1.0 - SOAP Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b688-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="7b688-118">W3C Web Hizmetleri Adresleme 1.0 - WSDL Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b688-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="7b688-119">W3C Web Hizmetleri Adresleme 1.0 - Metadata</span><span class="sxs-lookup"><span data-stu-id="7b688-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="7b688-120">WSDL SOAP1.1 Ciltleme</span><span class="sxs-lookup"><span data-stu-id="7b688-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="7b688-121">WSDL SOAP1.2 Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b688-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="7b688-122">Bu konu, <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> aşağıdaki protokoller için WCF uygulama ayrıntılarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="7b688-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="7b688-123">Belirtim/belge:</span><span class="sxs-lookup"><span data-stu-id="7b688-123">Specification/document:</span></span>

- [<span data-ttu-id="7b688-124">XOP</span><span class="sxs-lookup"><span data-stu-id="7b688-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="7b688-125">MTOM + SABUN 1.2 Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b688-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="7b688-126">MTOM SABUN 1.1 Ciltleme</span><span class="sxs-lookup"><span data-stu-id="7b688-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="7b688-127">MTOM WS-Politika İddiası</span><span class="sxs-lookup"><span data-stu-id="7b688-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="7b688-128">Bu konu boyunca aşağıdaki XML ad alanları ve ilişkili önekler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7b688-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="7b688-129">Ön ek</span><span class="sxs-lookup"><span data-stu-id="7b688-129">Prefix</span></span> | <span data-ttu-id="7b688-130">Namespace Uniform Resource Tanımlayıcı (URI)</span><span class="sxs-lookup"><span data-stu-id="7b688-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="7b688-131">s11</span><span class="sxs-lookup"><span data-stu-id="7b688-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="7b688-132">s12</span><span class="sxs-lookup"><span data-stu-id="7b688-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="7b688-133">Wsa</span><span class="sxs-lookup"><span data-stu-id="7b688-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="7b688-134">wsam</span><span class="sxs-lookup"><span data-stu-id="7b688-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="7b688-135">wsap</span><span class="sxs-lookup"><span data-stu-id="7b688-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="7b688-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="7b688-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="7b688-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="7b688-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="7b688-138">xop</span><span class="sxs-lookup"><span data-stu-id="7b688-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="7b688-139">xmime</span><span class="sxs-lookup"><span data-stu-id="7b688-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="7b688-140">Dp</span><span class="sxs-lookup"><span data-stu-id="7b688-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="7b688-141">SABUN 1.1 ve SABUN 1.2</span><span class="sxs-lookup"><span data-stu-id="7b688-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="7b688-142">Zarf ve İşleme Modeli</span><span class="sxs-lookup"><span data-stu-id="7b688-142">Envelope and Processing Model</span></span>
<span data-ttu-id="7b688-143">WCF, Temel Profil 1.1 (BP11) ve Temel Profil 1.0 'dan (SSBP10) sonra SOAP 1.1 zarf işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="7b688-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="7b688-144">SOAP 1.2 Zarf işleme, SOAP12-Part1'den sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="7b688-145">Bu bölümde, WCF tarafından BP11 ve SOAP12-Part1 ile ilgili olarak alınan bazı uygulama seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b688-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="7b688-146">Zorunlu Üstbilgi İşleme</span><span class="sxs-lookup"><span data-stu-id="7b688-146">Mandatory Header Processing</span></span>
<span data-ttu-id="7b688-147">WCF, SOAP 1.1 `mustUnderstand` ve SOAP 1.2 belirtimlerinde açıklanan başlıkların işlenmesi için aşağıdaki varyasyonlarla birlikte kurallara uyar.</span><span class="sxs-lookup"><span data-stu-id="7b688-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="7b688-148">WCF kanal yığınına giren bir ileti, Metin İleti Kodlaması, Güvenlik, Güvenilir İleti ve Hareketler gibi ilişkili bağlama öğeleri tarafından yapılandırılan tek tek kanallar tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="7b688-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="7b688-149">Her kanal ilişkili ad alanından üstbilgi tanır ve anlaşıldığı şekilde işaretler.</span><span class="sxs-lookup"><span data-stu-id="7b688-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="7b688-150">İleti sevk irsaliyesi girdikten sonra, ilgili ileti/işlem sözleşmesitarafından beklenen üstleri okur ve anlaşıldı işaretler.</span><span class="sxs-lookup"><span data-stu-id="7b688-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="7b688-151">Daha sonra, kalan üstbilginin anlaşılmadığını ancak özel `mustUnderstand` durum olarak işaretlenip işaretlenmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="7b688-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="7b688-152">Alıcıyı hedefleyen `mustUnderstand` üstbilgileri içeren iletiler alıcı uygulama kodu tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="7b688-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="7b688-153">Bu tür katmanlı işleme altyapı katmanları ve SOAP düğümü uygulama katmanları arasında ayrım sağlar:</span><span class="sxs-lookup"><span data-stu-id="7b688-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="7b688-154">B1111: İleti WCF altyapı kanalı yığını tarafından işlendikten sonra ancak uygulama tarafından işlenmeden önce anlaşılamayan üstbilgi algılanır</span><span class="sxs-lookup"><span data-stu-id="7b688-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="7b688-155">`mustUnderstand` Başlık değeri SOAP 1.1 ile SOAP 1.2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b688-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="7b688-156">Temel Profil 1.1, `mustUnderstand` SOAP 1.1 iletileri için değerin 0 veya 1 olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b688-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="7b688-157">SOAP 1.2, 0, `false`1 `true` ve değerler olarak izin verir, ancak değerlerin `xs:boolean` kanonik bir temsilini yayan önerir (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="7b688-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="7b688-158">B1112: WCF, `mustUnderstand` SOAP zarfının SOAP 1.1 ve SOAP 1.2 versiyonları için 0 ve 1 değerlerini yayır.</span><span class="sxs-lookup"><span data-stu-id="7b688-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="7b688-159">`xs:boolean` WCF `mustUnderstand` üstbilgi için tüm değer alanını kabul eder `false`(0, 1, , `true`)</span><span class="sxs-lookup"><span data-stu-id="7b688-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="7b688-160">SABUN Arızaları</span><span class="sxs-lookup"><span data-stu-id="7b688-160">SOAP Faults</span></span>
<span data-ttu-id="7b688-161">Aşağıda WCF'ye özgü SOAP hata uygulamalarının bir listesi verem.</span><span class="sxs-lookup"><span data-stu-id="7b688-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="7b688-162">B2121: WCF aşağıdaki SOAP 1.1 `s11:mustUnderstand`Arıza `s11:Client`Kodları `s11:Server`döndürür: , , ve .</span><span class="sxs-lookup"><span data-stu-id="7b688-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="7b688-163">B2122: WCF aşağıdaki SOAP 1.2 `s12:MustUnderstand`Arıza `s12:Sender`Kodları `s12:Receiver`döndürür: , , ve .</span><span class="sxs-lookup"><span data-stu-id="7b688-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="7b688-164">HTTP Ciltleme</span><span class="sxs-lookup"><span data-stu-id="7b688-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="7b688-165">SOAP 1.1 HTTP Ciltleme</span><span class="sxs-lookup"><span data-stu-id="7b688-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="7b688-166">WCF aşağıdaki açıklamalar ile Temel Profil 1.1 belirtimi bölüm 3.4 aşağıdaki SOAP1.1 HTTP bağlama uygular:</span><span class="sxs-lookup"><span data-stu-id="7b688-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="7b688-167">B2211: WCF hizmeti HTTP POST isteklerinin yeniden yönlendirilmesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="7b688-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="7b688-168">B2212: WCF müşterileri HTTP Çerezleri'ni 3.4.8 uyarınca destekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="7b688-169">SOAP 1.2 HTTP Ciltleme</span><span class="sxs-lookup"><span data-stu-id="7b688-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="7b688-170">WCF aşağıdaki açıklamalar ile SOAP 1.2-part 2 (SOAP12Part2) belirtiminde açıklandığı gibi SOAP 1.2 HTTP bağlama uygular.</span><span class="sxs-lookup"><span data-stu-id="7b688-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="7b688-171">SOAP `application/soap+xml` 1.2, ortam türü için isteğe bağlı bir eylem parametresi tanıttı.</span><span class="sxs-lookup"><span data-stu-id="7b688-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="7b688-172">Bu parametre, WS-Adresleme kullanılmadığında SOAP iletisinin gövdesinin ayrıştırılmasına gerek kalmadan ileti gönderimi optimize etmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="7b688-173">R2221: `application/soap+xml` Bir SOAP 1.2 isteğinde mevcut olduğunda eylem `soapAction` parametresi, `wsoap12:operation` ilgili WSDL bağlama içindeki öğedeki öznitelikle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="7b688-174">R2222: `application/soap+xml` Bir SOAP 1.2 iletisi üzerinde mevcut `wsa:Action` olduğunda, ws-Adresleme 2004/08 veya WS-Adresleme 1.0 kullanıldığında eylem parametresi eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="7b688-175">WS Adresi devre dışı bırakıldığında ve gelen istek bir eylem `Action` parametresi içermiyorsa, ileti belirtilmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="7b688-176">WS-Adresleme</span><span class="sxs-lookup"><span data-stu-id="7b688-176">WS-Addressing</span></span>
<span data-ttu-id="7b688-177">WCF WS-Adresleme 3 sürümleri uygular:</span><span class="sxs-lookup"><span data-stu-id="7b688-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="7b688-178">WS-Adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="7b688-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="7b688-179">W3C Web Hizmetleri Adresleme 1.0 Çekirdekli (ADDR10-CORE) ve SABUN Bağlama (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="7b688-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="7b688-180">WS-Adresleme 1.0 - Meta veriler</span><span class="sxs-lookup"><span data-stu-id="7b688-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="7b688-181">Bitiş Noktası Referansları</span><span class="sxs-lookup"><span data-stu-id="7b688-181">Endpoint References</span></span>
<span data-ttu-id="7b688-182">WCF'nin uyguladığı WS Adresi'nin tüm sürümleri uç noktaları açıklamak için uç nokta başvurularını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="7b688-183">Uç Nokta Referansları ve WS Adresleme Sürümleri</span><span class="sxs-lookup"><span data-stu-id="7b688-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="7b688-184">WCF, WS-Addressing'i ve özellikle `EndpointReference` öğeve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust) kullanan bir dizi altyapı protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="7b688-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="7b688-185">WCF, WS-Addressing'in her iki sürümünün de diğer altyapı protokolleriyle kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="7b688-186">WCF uç noktaları, bitiş noktası başına WS adreslemenin bir sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="7b688-187">R3111 için, WCF `EndpointReference` bitiş noktasıyla değiştirilen iletilerde kullanılan öğe veya tür için ad alanı, bu bitiş noktası tarafından uygulanan WS-Adresleme sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="7b688-188">Örneğin, bir WCF bitiş noktası WS-ReliableMessaging `AcksTo` uygularsa, üstbilgi içinde `CreateSequenceResponse` böyle bir bitiş noktası `EncodingBinding` tarafından döndürülen öğe, bu bitiş noktası için belirttiği WS Adresleme sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="7b688-189">Uç Nokta Referansları ve Meta veriler</span><span class="sxs-lookup"><span data-stu-id="7b688-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="7b688-190">Bir dizi senaryo, belirli bir bitiş noktası için meta verilerin iletişimini veya meta verilere başvuruyu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b688-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="7b688-191">B3121: WCF, WS-MetadataExchange (MEX) belirtiminde Bölüm 6'da açıklanan mekanizmaları, değer veya referans olarak uç nokta referansları için meta verileri içerecek şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="7b688-192">Bir WCF hizmetinin, belirteç veren kuruluş tarafından verilen Güvenlik İddiaları İşaretleyici Dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirdiği bir senaryo `http://sts.fabrikam123.com`düşünün.</span><span class="sxs-lookup"><span data-stu-id="7b688-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="7b688-193">WCF bitiş noktası belirteç veren `sp:IssuedToken` işaret eden `sp:Issuer` iç içe bir setir ile iddia kullanarak bu kimlik doğrulama gereksinimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b688-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="7b688-194">`sp:Issuer` Sermesi erişen istemci uygulamaları, belirteç veren bitiş noktasıyla nasıl iletişim kuracağını bermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b688-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="7b688-195">İstemcinin belirteç veren hakkında meta verileri bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b688-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="7b688-196">WCF, MEX'te tanımlanan uç nokta referans meta veri uzantılarını kullanarak belirteç veren meta verilerine bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="7b688-197">İleti Adresleme Üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="7b688-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="7b688-198">İleti Üstbilgi</span><span class="sxs-lookup"><span data-stu-id="7b688-198">Message Headers</span></span>
<span data-ttu-id="7b688-199">WCF, her iki WS Adresleme sürümü için, `wsa:To`belirtimler , `wsa:ReplyTo` `wsa:Action`, `wsa:MessageID`, `wsa:RelatesTo`ve .</span><span class="sxs-lookup"><span data-stu-id="7b688-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="7b688-200">B3211: Tüm WS Adresleme sürümleri için, WCF onur, ancak kutunun dışında üretmek değil, `wsa:FaultTo` `wsa:From`WS-Adresleme ileti üstbilgileri ve .</span><span class="sxs-lookup"><span data-stu-id="7b688-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="7b688-201">WCF uygulamalarıyla etkileşimedebilen uygulamalar bu ileti üstbilgilerini ekleyebilir ve WCF bunları buna göre işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="7b688-202">Referans Parametreleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="7b688-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="7b688-203">WCF, uç nokta referans parametrelerinin ve referans özelliklerinin ilgili spesifikasyonlara uygun olarak işlenmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="7b688-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="7b688-204">B3221: WS-Addressing 2004/08'i kullanacak şekilde yapılandırıldığında, WCF uç noktaları başvuru özelliklerini işleme ve Referans Parametreleri arasında ayrım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="7b688-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="7b688-205">İleti Değişim Desenleri</span><span class="sxs-lookup"><span data-stu-id="7b688-205">Message Exchange Patterns</span></span>
<span data-ttu-id="7b688-206">Web hizmeti işlemi çağırmasında yer alan iletilerin sırası *ileti alışverişi deseni*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="7b688-207">WCF tek yönlü, istek-yanıt ve çift yönlü ileti alışverişi modellerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="7b688-208">Bu bölümde, kullanılan ileti alışverişi desenine bağlı olarak ileti işlemede WS-Adresleme gereksinimleri açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b688-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="7b688-209">Bu bölüm boyunca, istekte bulundurucu ilk iletiyi gönderir ve yanıtlayan ilk iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="7b688-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="7b688-210">Tek Yönlü İleti</span><span class="sxs-lookup"><span data-stu-id="7b688-210">One-Way Message</span></span>
<span data-ttu-id="7b688-211">Bir WCF bitiş noktası, tek yönlü bir `Action` desen izlemek için verilen iletileri destekleyecek şekilde yapılandırıldığında, WCF bitiş noktası aşağıdaki davranışları ve gereksinimleri izler.</span><span class="sxs-lookup"><span data-stu-id="7b688-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="7b688-212">Aksi belirtilmedikçe, WCF'de desteklenen WS-Addressing'in her iki sürümü için de davranışlar ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7b688-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="7b688-213">R3311: İstekli, `wsa:To`bitiş `wsa:Action`noktası referansı tarafından belirtilen tüm başvuru parametreleri için , ve üstbilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="7b688-214">WS Adresi 2004/08 kullanıldığında ve [başvuru özellikleri] bitiş noktası referansı yla belirtildiğinde, ilgili üstbilginin de iletiye eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b688-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="7b688-215">B3312: İstekli , `MessageID` `ReplyTo`ve `FaultTo` üstbilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="7b688-216">Alıcı altyapısı bunları yok sayacak ve uygulamaya geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="7b688-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="7b688-217">R3313: HTTP kullanıldığında ve HTTP yanıt bacağına mesaj gönderilmediğinde, yanıtlayan boş bir gövde ve HTTP 202 durum kodu içeren bir HTTP yanıtı göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="7b688-218">HTTP aktarım ı kullanımda olduğunda ve işlem sözleşmesi tek yönlü bir ileti beyan ettiğinde, HTTP yanıtı yine de altyapı `SequenceAcknowledgement` iletileri göndermek için kullanılabilir(örneğin, güvenilir ileti bir HTTP yanıtı na ileti gönderebilir).</span><span class="sxs-lookup"><span data-stu-id="7b688-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="7b688-219">B3314: WCF yanıtlayıcısı tek yönlü bir iletiye yanıt olarak hata iletisi göndermez.</span><span class="sxs-lookup"><span data-stu-id="7b688-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="7b688-220">İstek-Yanıt</span><span class="sxs-lookup"><span data-stu-id="7b688-220">Request-Reply</span></span>
<span data-ttu-id="7b688-221">Bir WCF bitiş noktası, istek yanıtı `Action` deseni izlemek için verilen bir ileti için yapılandırıldığında, WCF bitiş noktası aşağıdaki davranışları ve gereksinimleri izler.</span><span class="sxs-lookup"><span data-stu-id="7b688-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="7b688-222">Aksi belirtilmedikçe, WCF'de desteklenen WS-Addressing'in her iki sürümü için de davranışlar ve kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7b688-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="7b688-223">R3321: İstekli, bitiş noktası `wsa:To` `wsa:Action`referansı tarafından belirtilen tüm başvuru parametreleri veya başvuru özellikleri (veya her ikisi) için istek, `wsa:MessageID`ve üstbilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="7b688-224">R3322: WS-Adresleme 2004/08 kullanıldığında, `ReplyTo` isteğe de dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="7b688-225">R3323: WS-Adresleme 1.0 kullanıldığında `ReplyTo` ve istekte bulunmadığında, [adres] özelliğine `http://www.w3.org/2005/08/addressing/anonymous` eşit olan varsayılan uç nokta başvurusu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="7b688-226">R3324: İstekli, `wsa:To`yanıt `wsa:Action`iletisinde üstbilgi ve `wsa:RelatesTo` üstbilginin yanı sıra istekteki `ReplyTo` bitiş noktası referansı tarafından belirtilen tüm başvuru parametreleri veya başvuru özellikleri (veya her ikisi) için üstbilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="7b688-227">Hataları Gideren Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7b688-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="7b688-228">R3411: WCF, WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="7b688-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="7b688-229">Kod</span><span class="sxs-lookup"><span data-stu-id="7b688-229">Code</span></span> | <span data-ttu-id="7b688-230">Nedeni</span><span class="sxs-lookup"><span data-stu-id="7b688-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="7b688-231">İleti, bu `ReplyTo` kanal için kurulan yanıt adresinden farklı bir iletiyle geldi; To üstbilgisinde belirtilen adreste son nokta dinleme yoktur.</span><span class="sxs-lookup"><span data-stu-id="7b688-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="7b688-232">bitiş noktasıyla ilişkili altyapı kanalları veya sevk `Action` irsaliyesi üstbilgide belirtilen eylemi tanımaz.</span><span class="sxs-lookup"><span data-stu-id="7b688-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="7b688-233">R3412: WCF, WS-Adresleme 1.0 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="7b688-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="7b688-234">Kod</span><span class="sxs-lookup"><span data-stu-id="7b688-234">Code</span></span> | <span data-ttu-id="7b688-235">Nedeni</span><span class="sxs-lookup"><span data-stu-id="7b688-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="7b688-236">Yinelenen `wsa:To` `wsa:ReplyTo`, `wsa:From` `wsa:MessageID`veya .</span><span class="sxs-lookup"><span data-stu-id="7b688-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="7b688-237">Aynı `wsa:RelatesTo` `RelationshipType`ile yinelenen .</span><span class="sxs-lookup"><span data-stu-id="7b688-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="7b688-238">Gerekli Adresleme üstbilgisi eksik.</span><span class="sxs-lookup"><span data-stu-id="7b688-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="7b688-239">İleti, bu `ReplyTo` kanal için kurulan yanıt adresinden farklı bir iletiyle geldi.</span><span class="sxs-lookup"><span data-stu-id="7b688-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="7b688-240">To başlığında belirtilen adreste bitiş noktası dinleme yoktur.</span><span class="sxs-lookup"><span data-stu-id="7b688-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="7b688-241">`Action` Üstbilgide belirtilen bir eylem, bitiş noktasıyla ilişkili altyapı kanalları veya gönderen tarafından tanınmaz.</span><span class="sxs-lookup"><span data-stu-id="7b688-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="7b688-242">RM kanalı, bitiş noktasının `CreateSequence` iletinin adreslenen üstbilgileri incelenerek diziyi işlemeyeceğini belirten bu hatayı geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="7b688-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="7b688-243">Önceki tablolardaki kod, `FaultCode` SOAP 1.1'e ve `SubCode` (Code=Sender ile) SOAP 1.2'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="7b688-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="7b688-244">WSDL 1.1 Bağlayıcı ve WS-İlke İddiaları</span><span class="sxs-lookup"><span data-stu-id="7b688-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="7b688-245">WS-Adresleme kullanımını gösteren</span><span class="sxs-lookup"><span data-stu-id="7b688-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="7b688-246">WCF, belirli bir WS Adresleme sürümü için uç nokta desteğini belirtmek için ilke iddialarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="7b688-247">Aşağıdaki ilke iddiasında Endpoint İlkesi Konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08'i kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b688-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="7b688-248">Bu ilke iddiası WS-Adresleme 2004/08 belirtimini genişletiyor.</span><span class="sxs-lookup"><span data-stu-id="7b688-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="7b688-249">Aşağıdaki ilke iddiası, gönderilen/alınan iletilerin WS Adresi 1.0'ı kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b688-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="7b688-250">Aşağıdaki ilke iddiasının bir Bitiş Noktası İlkesi Konusu [WS-PA] vardır ve son noktadan gönderilen ve alınan iletilerin WS Adresi 2004/08'i kullanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b688-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="7b688-251">Öğe `wsaw10:UsingAddressing` [WS-Addressing-WSDL] ödünç ve bu belirtim, bölüm 3.1.2 uygun olarak WS-Politikası bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="7b688-252">Adresleme nin kullanımı WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP Ciltlemelerinin anlambilimini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7b688-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="7b688-253">Örneğin, Adresleme ve WSDL SOAP 1.x HTTP bağlama kullanan bir bitiş noktasına gönderilen bir isteğe yanıt bekleniyorsa, yanıt HTTP yanıtı kullanılarak gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="7b688-254">http yanıtı üzerinden gönderilen yanıtlar için WS-AM iddiası:</span><span class="sxs-lookup"><span data-stu-id="7b688-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="7b688-255">Tam ilke iddiası aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="7b688-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="7b688-256">Ancak, istekte veren ve yanıtlayan arasında iki bağımsız converse HTTP bağlantısı nın kurulmasından yararlanan ileti alışverişi desenleri vardır, örneğin, yanıtlayan tarafından gönderilen istenmeyen tek yönlü iletiler.</span><span class="sxs-lookup"><span data-stu-id="7b688-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="7b688-257">WCF, bir kanalın giriş iletileri için, diğerinin çıkış iletileri için kullanıldığı bir Bileşik Çift Yönlü kanal oluşturabileceği bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="7b688-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="7b688-258">HTTP Transport durumunda, Bileşik Çift yönlü iki converse HTTP bağlantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="7b688-259">İstekçi, yanıtlayana ileti göndermek için bir bağlantı kullanır ve yanıtlayan diğerini iletileri istekte bulunduracak şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="7b688-260">Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am iddiası</span><span class="sxs-lookup"><span data-stu-id="7b688-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="7b688-261">Tam ilke iddiası aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="7b688-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="7b688-262">WSDL 1.1 SOAP 1.x HTTP ciltlerini kullanan uç noktalarda Uç Nokta Politikası Konusu [WS-PA] bulunan aşağıdaki iddianın kullanımı, istektebulunaniletiden yanıtlayana ve yanıtlayana giden iletilere akan iletiler için sırasıyla iki ayrı converse HTTP bağlantısı nın kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b688-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="7b688-263">Önceki deyim, istek iletileri `wsa:ReplyTo` için üstbilgide aşağıdaki gereksinimlere yol açar:</span><span class="sxs-lookup"><span data-stu-id="7b688-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="7b688-264">R3514: Bitiş noktası WSDL 1.1 SOAP `[address]` 1.x `http://www.w3.org/2005/08/addressing/anonymous` HTTP bağlama kullanıyorsa ve `wsap10:UsingAddressing` `wsap:UsingAddressing` `cdp:CompositeDuplex` ekli bir veya bir leştirilmiş bir ilke alternatifi varsa, bitiş noktasına gönderilen istek iletilerinin özelliğine eşit olmayan bir `ReplyTo` üstbilgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="7b688-265">R3515: `ReplyTo` Bitiş noktasına `[address]` gönderilen istek iletilerinin, bitiş noktası WSDL 1.1 SOAP 1.x HTTP bağlayıcısı kullanıyorsa ve `http://www.w3.org/2005/08/addressing/anonymous` `ReplyTo` `wsap10:UsingAddressing` iddia ve hiçbir `cdp:CompositeDuplex` iddiaekli bir ilke alternatifi varsa, özelliği ne eşit sayılsa da hiç üstbilgi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="7b688-266">R3516: Bitiş noktası WSDL 1.1 SOAP `[address]` 1.x `http://www.w3.org/2005/08/addressing/anonymous` HTTP bağlama kullanıyorsa ve iddia içeren `wsap:UsingAddressing` ve hiçbir `cdp:CompositeDuplex` iddiaekli bir ilke alternatifi varsa, bitiş noktasına eşit bir özelliğe sahip bir `ReplyTo` üstbilgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="7b688-267">WS adresi WSDL belirtimi, `<wsaw:Anonymous/>` `wsa:ReplyTo` üstbilgideki gereksinimleri (bölüm 3.2) belirtmek için üç metin değeri (gerekli, isteğe bağlı ve yasak) olan bir öğe tanıtarak benzer iletişim kuralı bağlamalarını açıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="7b688-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="7b688-268">Ne yazık ki, bu tür öğe tanımı, ws-policy bağlamında bir iddia olarak özellikle kullanılabilir değildir, çünkü bir iddia olarak böyle bir öğeyi kullanarak alternatiflerin kesişim desteklemek için etki alanına özgü uzantıları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b688-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="7b688-269">Bu tür öğe tanımı, `ReplyTo` telüzerindeki bitiş noktası davranışının aksine üstbilginin değerini de gösterir ve bu da onu HTTP aktarımına özgü kılar.</span><span class="sxs-lookup"><span data-stu-id="7b688-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="7b688-270">Eylem Tanımı</span><span class="sxs-lookup"><span data-stu-id="7b688-270">Action Definition</span></span>
<span data-ttu-id="7b688-271">WS-Adresleme 2004/08 `wsa:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri için bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="7b688-272">WS Adresi 1.0 WSDL Bağlama (WS-ADDR10-WSDL) benzer bir `wsaw10:Action`öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="7b688-273">İkisi arasındaki tek fark, WS-ADDR'ın 3.3.2 bölümünde ve sırasıyla WS-ADDR10-WSDL'nin 4.4.4 bölümünde açıklanan varsayılan Eylem deseni semantikleridir.</span><span class="sxs-lookup"><span data-stu-id="7b688-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="7b688-274">Ws-Addressing'in farklı sürümlerini kullanarak `portType` aynı (veya sözleşme, WCF terminolojisinde) aynı payı paylaşan iki uç noktaolması makul bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="7b688-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="7b688-275">Ancak, Eylem tarafından tanımlandığı `portType` ve uygulayan uç noktalar arasında `portType`değişmemesi gerektiği göz önüne alındığında, her iki varsayılan eylem desenlerini de desteklemek imkansız hale gelir.</span><span class="sxs-lookup"><span data-stu-id="7b688-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="7b688-276">Bu sorunu çözmek için WCF özniteliğin `Action` tek bir sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="7b688-277">B3521: WCF, `wsaw10:Action` bitiş `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` noktası tarafından kullanılan WS Adresleme sürümünden bağımsız olarak `Action` ilgili iletiler için URI'yi belirlemek için WS-ADDR10-WSDL'de tanımlanan öğeler üzerindeki özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="7b688-278">WSDL Bağlantı Noktası İçinde Uç Nokta Referansı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7b688-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="7b688-279">WS-ADDR10-WSDL bölüm 4.1, `wsdl:port` bitiş noktasını `<wsa10:EndpointReference…/>` WS-Adresleme terimleriyle açıklamak için alt öğeyi içerecek şekilde öğeyi genişletir.</span><span class="sxs-lookup"><span data-stu-id="7b688-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="7b688-280">WCF WS-Adresleme 2004/08 bu yardımcı programı `<wsa:EndpointReference…/>` genişletir, bir `wsdl:port`alt öğe olarak görünmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="7b688-281">R3531: Bir uç nokta, bir ilke `<wsaw10:UsingAddressing/>` iddiası ile `wsdl:port` ekli bir ilke `<wsa10:EndpointReference …/>`alternatifi varsa, karşılık gelen öğe bir alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="7b688-282">R3532: Bir `wsdl:port` alt öğe `<wsa10:EndpointReference …/>` `wsa10:EndpointReference/wsa10:Address` içeriyorsa, alt öğe değeri `@address` kardeş `wsdl:port` / `wsdl:location` öğenin özniteliğinin değeriyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="7b688-283">R3533: Bir uç nokta ilke iddiası `<wsap:UsingAddressing/>` ile ekli `wsdl:port` bir ilke alternatifi varsa, karşılık gelen öğe bir alt öğe `<wsa:EndpointReference …/>`içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="7b688-284">R3534: Bir `wsdl:port` alt öğe `<wsa:EndpointReference …/>` `wsa:EndpointReference/wsa:Address` içeriyorsa, alt öğe değeri `@address` kardeş `wsdl:port` / `wsdl:location` öğenin özniteliğinin değeriyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="7b688-285">WS-Security ile kompozisyon</span><span class="sxs-lookup"><span data-stu-id="7b688-285">Composition with WS-Security</span></span>
<span data-ttu-id="7b688-286">WS-ADDR ve WS-ADDR10'daki güvenlik konuları bölümlerine göre, tüm adresleme ileti üstbilgileri, ileti gövdesi ile birlikte imzalanmalı ve bunları birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="7b688-287">İleti bütünlüğü koruması için WS-Security kullanıldığında, başvuru parametreleri veya özelliklerinden (veya her ikisinden) kaynaklanan WS Adresleme ileti üstbilgileri ve üstbilgileri iletişin gövdesi ile birlikte imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="7b688-288">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7b688-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="7b688-289">Tek Yönlü İleti</span><span class="sxs-lookup"><span data-stu-id="7b688-289">One-Way Message</span></span>
<span data-ttu-id="7b688-290">Bu senaryoda, gönderen alıcıya tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="7b688-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="7b688-291">SOAP 1.2, HTTP 1.1 ve W3C WS-Adresleme 1.0 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="7b688-292">İstek İletisi Yapısı: İleti `wsa10:To` `wsa10:Action` üstbilgisi ve öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7b688-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="7b688-293">İleti gövdesi, uygulama `<app:Ping>` ad alanından belirli bir öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="7b688-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="7b688-294">HTTP Başlıklar: POST'taki `wsa10:To` hedef, öğedeki URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="7b688-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="7b688-295">İçerik Türü üstbilgi, SOAP `application/soap+xml` 1.2'nin gerektirdiği değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7b688-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="7b688-296">Parametreler `charset` `action` ve dahildir.</span><span class="sxs-lookup"><span data-stu-id="7b688-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="7b688-297">İçerik `action` Türü üstbilginin parametresi ileti üstbilgisinin değeriyle `wsa10:Action` eşleşir.</span><span class="sxs-lookup"><span data-stu-id="7b688-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

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

<span data-ttu-id="7b688-298">Alıcı boş bir HTTP yanıtı ve durum 202 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="7b688-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="7b688-299">HTTP yanıtı bir örnek:</span><span class="sxs-lookup"><span data-stu-id="7b688-299">An example of the HTTP response:</span></span>

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

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="7b688-300">SOAP İleti İleti optimizasyonu Mekanizması</span><span class="sxs-lookup"><span data-stu-id="7b688-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="7b688-301">Bu bölümde HTTP SOAP MTOM için WCF uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b688-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="7b688-302">MTOM teknolojisi, geleneksel metin/XML kodlama veya WCF İkili kodlama ile aynı sınıfın SOAP ileti kodlama mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="7b688-303">MTOM aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="7b688-303">MTOM includes the following:</span></span>

- <span data-ttu-id="7b688-304">Base64 kodlanmış ikili verileri içeren XML bilgi öğelerini ayrı ikili parçalarhalinde optimize eden [XOP] tarafından açıklanan bir XML kodlama ve paketleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="7b688-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="7b688-305">XML Bilgi Seti'ni ve XOP paketinin her ikili parçasını ayrı bir MIME parçasına serileştiren XOP paketinin MIME kapsüllemi.</span><span class="sxs-lookup"><span data-stu-id="7b688-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="7b688-306">SOAP 1.x Zarf'a uygulanan bir MIME XOP kodlaması.</span><span class="sxs-lookup"><span data-stu-id="7b688-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="7b688-307">Bir HTTP aktarım bağlama.</span><span class="sxs-lookup"><span data-stu-id="7b688-307">An HTTP transport binding.</span></span>

<span data-ttu-id="7b688-308">MTOM'u WCF ile HTTP dışı taşımalarla kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7b688-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="7b688-309">Ancak, bu konuda biz HTTP üzerinde durulacak.</span><span class="sxs-lookup"><span data-stu-id="7b688-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="7b688-310">MTOM biçimi, MTOM'un kendisini, XOP'u ve MIME'yi kapsayan geniş bir belirtim kümesinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="7b688-311">Bu belirtim kümesinin modülerliği, biçim ve işleme semantikleri üzerinde tam gereksinimleri yeniden yapılandırmayı biraz zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="7b688-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="7b688-312">Bu bölümde MTOM HTTP bağlama için biçim ve işleme gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b688-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="7b688-313">MTOM İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="7b688-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="7b688-314">MTOM iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b688-314">Generating MTOM messages</span></span>
<span data-ttu-id="7b688-315">[XOP] bölüm 3.1 soyut tanımlanmış bir XOP paketine base64 değerleri içeren eleman bilgi öğeleri ile XML kodlama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b688-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="7b688-316">Aşağıdaki adım sırası MTOM'a özgü kodlama işlemini açıklar:</span><span class="sxs-lookup"><span data-stu-id="7b688-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="7b688-317">Kodlanacak SOAP Zarfının `[namespace name]` a `http://www.w3.org/2004/08/xop/include` ve a `[local name]` ile hiçbir öğe bilgi `Include`öğesi içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b688-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="7b688-318">Boş bir MIME paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b688-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="7b688-319">Orijinal XML Bilgi Seti içinde en iyi duruma getirilecek öğe bilgi öğelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7b688-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="7b688-320">Öğelerin optimize edilememesi için, öğe bilgi `[children]` öğesinin oluşturan karakterlerin kanonik biçiminde `xs:base64Binary` olması gerekir (bkz. XSD-2, 3.2.16 base64Binary) ve beyaz alan içeriğinden önce, satır da veya aşağıdaki herhangi bir beyaz boşluk karakteri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="7b688-321">Orijinal SOAP Zarfının bir kopyası olan, ancak önceki adımda tanımlanan her öğebilgi öğesinin çocuklarıyla `xop:Include` birlikte aşağıdaki gibi oluşturulmuş bir öğe bilgi öğesi ile değiştirilen bir XOP SOAP Zarfı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7b688-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="7b688-322">Değiştirilen karakterleri temel 64 kodlanmış veri olarak işleyerek ikili veriye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="7b688-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="7b688-323">Gereksinimleri Karşılayan benzersiz bir İçerik-Kimlik üstbilgi değeri Oluşturun R3133 ve R3134.</span><span class="sxs-lookup"><span data-stu-id="7b688-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="7b688-324">Değer ikili ile Bir İçerik-Transfer-Kodlama MIME üstbilgi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b688-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="7b688-325">Öğe bilgi öğesi en iyi duruma getiriliyorsa (yeni `xop:Include` eklenen öğe bilgi `xmime:contentType` öğesinin [üst öğesi] bir öznitelik bilgi öğesi `xmime:contentType` varsa, öznitelik değeri ile bir İçerik Türü MIME üstbilgisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b688-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="7b688-326">Base64 olarak işlenen değiştirilen karakterlerden deşifre edilen ikili verilerden oluşturulan içerikle oluşan yeni bir ikili MIME parçası oluşturun, 4b'den İçerik-Kimlik üstbilgisi, 4c'den İçerik-Aktarım-Kodlama üstbilgisi, adım 4d'de oluşturulursa İçerik Türü üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="7b688-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="7b688-327">Değeri `href` cid ile `xop:Include` öğeye bir öznitelik ekleyin: uri Adım 4b oluşturulan İçerik-Kimlik üstbilgi değeri türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b688-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="7b688-328">" " ve\<">" karakterleri kaldırın, kalan dizeyi URL'den `cid:`kaldırıp önek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b688-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="7b688-329">Aşağıdaki minimum karakter kümesinin RFC1738 ve RFC2396 tarafından kaçılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b688-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="7b688-330">Diğer karakterler kaçabilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="7b688-331">Adım 4 XOP SOAP Zarf ile bir kök MIME parçası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b688-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="7b688-332">HTTP İçerik Türü üstbilgi de dahil olmak üzere HTTP üstbilgisini yazın.</span><span class="sxs-lookup"><span data-stu-id="7b688-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="7b688-333">MIME paketini yazın.</span><span class="sxs-lookup"><span data-stu-id="7b688-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="7b688-334">MTOM iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="7b688-334">Processing MTOM messages</span></span>
<span data-ttu-id="7b688-335">Bir MTOM iletisinin işlenmesi, önceki "MTOM iletileri oluşturma" bölümünde açıklanan işlemin tam tersidir:</span><span class="sxs-lookup"><span data-stu-id="7b688-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="7b688-336">Kök MIME parçasının İçerik Türüne `application/xop+xml`sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b688-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="7b688-337">Paketin kök MIME kısmını XML belgesi olarak ayrıştarak bir SOAP Zarfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b688-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="7b688-338">Karakter kodlaması, kök `charset` MIME bölümünün İçerik Türü parametresi ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7b688-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="7b688-339">[Çocuk] özelliğinin tek üyesi olarak bir `xop:Include` öğe bilgi öğesi olan inşa SOAP Zarfı'ndaki her öğe bilgi öğesi için:</span><span class="sxs-lookup"><span data-stu-id="7b688-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="7b688-340">Öğenin `cid:` özniteliğideğerindeki tüm URI kaçış dizilerini (RFC 2396) `@href` önekini kaldırın ve kaçışı kaldırın. `xop:Include`</span><span class="sxs-lookup"><span data-stu-id="7b688-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="7b688-341">Sonuç dizesini "\<", ">" olarak ekle.</span><span class="sxs-lookup"><span data-stu-id="7b688-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="7b688-342">Adım 3a'da türetilen dizeyle eşleşen İçerik-Kimlik üstbilgi değeriyle MIME parçasını bulun.</span><span class="sxs-lookup"><span data-stu-id="7b688-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="7b688-343">Adım `xop:Include` 3b'de tanımlanan MIME parçasının varlık gövdesinin kanonik base64 kodlamasını (bkz. XSD-2, 3.2.16 base64Binary) temsil eden karakter bilgileri öğeleriyle her öğenin `children` özelliğinde görünen öğe bilgi öğesini değiştirin (öğe bilgi öğesini `xop:Include` paket parçasından yeniden yapılandırılan verilerle etkili bir şekilde değiştirin).</span><span class="sxs-lookup"><span data-stu-id="7b688-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="7b688-344">HTTP İçerik Türü Üstbilgi</span><span class="sxs-lookup"><span data-stu-id="7b688-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="7b688-345">Aşağıda, MTOM belirtiminde belirtilen gereksinimlerden türetilen ve MTOM ve RFC 2387'den türetilen BIR SOAP 1.x MTOM kodlu iletinin HTTP İçerik Türü üstbilgisinin biçimine ait WCF açıklamalarının bir listesi vettir.</span><span class="sxs-lookup"><span data-stu-id="7b688-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="7b688-346">R4131: BIR HTTP İçerik Türü üstbilginin çok parçalı/ilişkili (büyük/küçük harf duyarsız) değeri ve parametreleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="7b688-347">Parametre adları büyük/küçük harf duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="7b688-348">Parametre sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="7b688-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="7b688-349">MIME iletileri için İçerik Türü üstbilginin tam Backus-Naur Formu (BNF), RFC 2045, bölüm 5.1'de listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b688-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="7b688-350">R4132: HTTP İçerik Türü üstbilginin değeri `application/xop+xml` çift tırnak işaretleriyle kapatılan bir tür parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="7b688-351">RFC 2387'de çift tırnak işaretleri kullanma gereksinimi açık olmasa da, metinde tüm çok parçalı/ilişkili ortam türü\@parametrelerinin büyük olasılıkla " veya "/" gibi ayrılmış karakterler içerdiği ve bu nedenle çift tırnak işaretlerine ihtiyaç duyulduğu gözlemlenir.</span><span class="sxs-lookup"><span data-stu-id="7b688-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="7b688-352">R4133: BIR HTTP İçerik Türü üstbilgi, çift tırnak işaretleriyle kapatılan SOAP 1.x Zarfını içeren MIME bölümünün İçerik-KIMLIK üstbilgisinin değerini içeren bir başlangıç parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="7b688-353">Başlangıç parametresi atlanırsa, ilk MIME parçası SOAP 1.x Zarfı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="7b688-354">R4134: SOAP 1.1 MTOM kodlanmış ileti için http İçerik Türü üstbilgi, çift tırnak işaretleriyle kaplanmış metin/xml değerini içeren başlangıç bilgi parametresini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="7b688-355">R4135: SOAP 1.2 MTOM kodlu ileti için http İçerik Türü üstbilgi, çift tırnak işaretleriyle birlikte başlangıç bilgisi parametresini `application/soap+xml`içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="7b688-356">R4136: BIR SOAP 1.x MTOM kodlanmış ileti için HTTP İçerik Türü üstbilgi, RFC 2046'da tanımlanan MIME sınırı BNF ile eşleşen değere (çift tırnak işaretleriyle kapalı) sınır parametresi, bölüm 5.1.1 olmalıdır</span><span class="sxs-lookup"><span data-stu-id="7b688-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="7b688-357">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="7b688-357">Examples:</span></span>

     <span data-ttu-id="7b688-358">Doğru</span><span class="sxs-lookup"><span data-stu-id="7b688-358">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="7b688-359">Doğru</span><span class="sxs-lookup"><span data-stu-id="7b688-359">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="7b688-360">Yanlış</span><span class="sxs-lookup"><span data-stu-id="7b688-360">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="7b688-361">Infoset MIME Parçası</span><span class="sxs-lookup"><span data-stu-id="7b688-361">Infoset MIME Part</span></span>
<span data-ttu-id="7b688-362">SOAP 1.x Zarf XOP MIME paketinin bir kök parçası olarak kapsüllenir ve genellikle `infoset` parçası olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="7b688-363">R4141: SOAP 1.x Zarf, XOP MIME paketinin bir `infoset` parçası olarak kapsüllenmelidir, adı verilen ve HTTP İçerik Türünden başvurulan.</span><span class="sxs-lookup"><span data-stu-id="7b688-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="7b688-364">R4142: SOAP `Infoset` parçası aşağıdaki MIME başlıklarını `Content-ID` `Content-Transfer-Encoding`içermelidir: , , ve `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="7b688-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="7b688-365">İçerik-ID üstbilgisinin biçimi RFC 2045 tarafından</span><span class="sxs-lookup"><span data-stu-id="7b688-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="7b688-366">RFC 2822'de tanımlandığı yer `msg-id` (RFC 822'nin yerini alan, RFC 2045'te başvurulan) şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="7b688-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="7b688-367">ve " "\<ve ">" içinde yer alan bir e-posta adresidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="7b688-368">Önek `[CFWS]` ve sonek, yorumları taşımak için RFC 2822'ye eklendi ve birlikte çalışabilirliği korumak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="7b688-369">R4143: Infoset MIME parçasının İçerik-ID üstbilgisinin `msg-id` değeri, önek ve sonek `[CFWS]` parçaları atlanmış olan RFC 2822'den gelen üretimi takip etmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="7b688-370">Bir dizi MIME uygulaması, " "\<ve ">" içindeki değerin e-posta `absoluteURI` adresi olması\<için gerekli gereksinimleri gidermiş ve e-posta adresine ek olarak " , ">" olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b688-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="7b688-371">WCF'nin bu sürümü, formun İçerik-ID MIME üstbilgisinin değerlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b688-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="7b688-372">R4144: MTOM işlemciler aşağıdaki rahatlıkla `msg-id`eşleşen İçerik-KIMLIK üstbilgi değerlerini kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="7b688-373">MIME (RFC 2045), MIME bölümünün içeriğinin kodlanması ile iletişim kurmak için İçerik Aktar-Kodlama üstbilgisini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b688-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="7b688-374">İçerik-Aktarım-Kodlama için tanımlanan varsayılan değer, çoğu SOAP iletisi için uygun olmayan 7 bit'tir, bu nedenle daha fazla birlikte çalışabilirlik için İçerik Aktar-Kodlama üstbilgisi gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7b688-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="7b688-375">R4145: SOAP Bilgi Seti bölümü İçerik Aktar-Kodlama üstbilgisini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="7b688-376">R4146: SOAP Envelope karakter kodlaması UTF-8 ise, İçerik Aktarımı-Kodlama üstbilgisinin değeri 8 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="7b688-377">R4147: SOAP Envelope karakter kodlaması UTF-16 ise, İçerik Aktar-Kodlama üstbilgisinin değeri ikili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="7b688-378">[XOP] bölüm 5'e göre,</span><span class="sxs-lookup"><span data-stu-id="7b688-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="7b688-379">R4148: SOAP1.1 Bilgi seti parçası, ortam türü uygulaması/xop+xml ve parametreleri type="text/xml" ve charset ile İçerik Tipi başlık içermelidir</span><span class="sxs-lookup"><span data-stu-id="7b688-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="7b688-380">R4149: SOAP 1.2 Bilgi Seti parçası, ortam türü ve `application/xop+xml` parametreleri`application/soap+xml`type=" `charset`" ve .</span><span class="sxs-lookup"><span data-stu-id="7b688-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="7b688-381">XOP isteğe `charset` bağlı olması `application/xop+xml` için parametre tanımlar iken, `charset` `text/xml` medya türü için parametre bp 1.1 gereksinimi benzer birlikte çalışabilirlik için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="7b688-382">R41410: `type` `charset` SOAP 1.x Infoset bölümünün İçerik Tipi başlığında parametreler bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="7b688-383">MTOM için WCF Uç Nokta Desteği</span><span class="sxs-lookup"><span data-stu-id="7b688-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="7b688-384">MTOM'un amacı, base64 kodlanmış verileri optimize etmek için bir SOAP iletisi kodlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7b688-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="7b688-385">Aşağıdaki kısıtlamaların bir listesi:</span><span class="sxs-lookup"><span data-stu-id="7b688-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="7b688-386">R4151: Base64 kodlanmış verileri içeren tüm öğe bilgileri öğesi en iyi duruma getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="7b688-387">B4152: WCF, base64 kodlanmış veri içeren ve uzunluğu 1024 baytı aşan eleman bilgi öğelerini optimize eder.</span><span class="sxs-lookup"><span data-stu-id="7b688-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="7b688-388">MTOM'u kullanmak üzere yapılandırılan bir WCF bitiş noktası her zaman MTOM kodlu iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="7b688-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="7b688-389">Hiçbir parça gerekli ölçütleri karşılamasa bile, ileti hala MTOM kodludur (SOAP zarfını içeren tek bir MIME parçası olan bir MIME paketi olarak seri hale getirilmiştir).</span><span class="sxs-lookup"><span data-stu-id="7b688-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="7b688-390">MTOM için WS-Politika İddiası</span><span class="sxs-lookup"><span data-stu-id="7b688-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="7b688-391">WCF, MTOM kullanımını bitiş noktasına göre belirtmek için aşağıdaki ilke iddiasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b688-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="7b688-392">R4211: Önceki ilke iddiasında Bir Uç Nokta İlkesi Konusu vardır ve bitiş noktasından gönderilen ve alınan tüm iletilerin MTOM kullanılarak optimize edilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b688-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="7b688-393">B4212: MTOM optimizasyonu kullanmak üzere yapılandırıldığında, WCF bitiş noktası ilgili `wsdl:binding`ilkeekli bir MTOM İlkesi iddiası ekler.</span><span class="sxs-lookup"><span data-stu-id="7b688-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="7b688-394">WS-Security ile kompozisyon</span><span class="sxs-lookup"><span data-stu-id="7b688-394">Composition with WS-Security</span></span>
<span data-ttu-id="7b688-395">MTOM ve WCF İkili XML benzer `text/xml` bir kodlama mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7b688-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="7b688-396">MTOM, WS-Security ve diğer WS-\* protokolleri ile doğal kompozisyon sunar: WS-Security kullanılarak güvenli bir ileti MTOM kullanılarak optimize edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b688-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="7b688-397">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7b688-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="7b688-398">WCF SOAP 1.1 Mesaj MTOM Kullanılarak Kodlanmış</span><span class="sxs-lookup"><span data-stu-id="7b688-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="7b688-399">WCF Secure SOAP 1.2 MTOM Kullanılarak Kodlanmış İleti</span><span class="sxs-lookup"><span data-stu-id="7b688-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="7b688-400">Bu örnekte, WS-Security kullanılarak korunan MTOM ve SOAP 1.2 kullanılarak bir ileti kodlanır.</span><span class="sxs-lookup"><span data-stu-id="7b688-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="7b688-401">Kodlama için tanımlanan ikili `BinarySecurityToken`parçalar, şifreli `CipherValue` imza `EncryptedData` ve şifreli gövdeye karşılık gelen , içeriğidir.</span><span class="sxs-lookup"><span data-stu-id="7b688-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="7b688-402">`CipherValue` Uzunluğu 1024 bayt daha az olduğundan, WCF tarafından optimizasyon için `EncryptedKey` tanımlanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7b688-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

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
