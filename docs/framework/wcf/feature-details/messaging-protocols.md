---
title: "Mesajlaşma Protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4052971746086061cb2ed091bd13c962318b2d89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="messaging-protocols"></a><span data-ttu-id="e8094-102">Mesajlaşma Protokolleri</span><span class="sxs-lookup"><span data-stu-id="e8094-102">Messaging Protocols</span></span>
<span data-ttu-id="e8094-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanal yığını iç ileti gösterimi kablo biçimine dönüştürme ve belirli bir kullanarak göndermek için kodlama ve taşıma kanalları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="e8094-104">HTTP Web Hizmetleri birlikte çalışabilirlik için kullanılan en yaygın aktarım olduğunu ve Web Hizmetleri tarafından kullanılan en yaygın Kodlamalar XML tabanlı SOAP 1.1 ve SOAP 1.2 ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="e8094-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="e8094-105">Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tarafından işe aşağıdaki protokolleri için uygulama ayrıntılarını <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e8094-105">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="e8094-106">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="e8094-106">Specification/document</span></span>|<span data-ttu-id="e8094-107">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="e8094-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="e8094-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="e8094-108">HTTP 1.1</span></span>|<span data-ttu-id="e8094-109">http://www.ietf.org/rfc/rfc2616.txt</span><span class="sxs-lookup"><span data-stu-id="e8094-109">http://www.ietf.org/rfc/rfc2616.txt</span></span>|  
|<span data-ttu-id="e8094-110">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-110">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="e8094-111">http://www.w3.org/TR/2000/Note-SOAP-20000508/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="e8094-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="e8094-112">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-112">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="e8094-113">http://www.w3.org/TR/soap12-part2/, Bölüm 7</span><span class="sxs-lookup"><span data-stu-id="e8094-113">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="e8094-114">Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ayrıntıları aşağıdaki protokoller için <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8094-114">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="e8094-115">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="e8094-115">Specification/Document</span></span>|<span data-ttu-id="e8094-116">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="e8094-116">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="e8094-117">XML</span><span class="sxs-lookup"><span data-stu-id="e8094-117">XML</span></span>|<span data-ttu-id="e8094-118">http://www.w3.org/TR/rec-XML</span><span class="sxs-lookup"><span data-stu-id="e8094-118">http://www.w3.org/TR/REC-xml</span></span>|  
|<span data-ttu-id="e8094-119">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="e8094-119">SOAP 1.1</span></span>|<span data-ttu-id="e8094-120">http://www.w3.org/TR/2000/Note-SOAP-20000508/</span><span class="sxs-lookup"><span data-stu-id="e8094-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span></span>|  
|<span data-ttu-id="e8094-121">SOAP 1.2 Çekirdek</span><span class="sxs-lookup"><span data-stu-id="e8094-121">SOAP 1.2 Core</span></span>|<span data-ttu-id="e8094-122">http://www.w3.org/TR/soap12-part1/</span><span class="sxs-lookup"><span data-stu-id="e8094-122">http://www.w3.org/TR/soap12-part1/</span></span>|  
|<span data-ttu-id="e8094-123">WS-adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="e8094-123">WS-Addressing 2004/08</span></span>|<span data-ttu-id="e8094-124">http://www.w3.org/Submission/2004/SUBM-WS-Addressing-20040810/</span><span class="sxs-lookup"><span data-stu-id="e8094-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span></span>|  
|<span data-ttu-id="e8094-125">Adresleme 1.0 - çekirdek W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-125">W3C Web Services Addressing 1.0 - Core</span></span>|<span data-ttu-id="e8094-126">http://www.w3.org/TR/2006/rec-ws-addr-Core-20060509</span><span class="sxs-lookup"><span data-stu-id="e8094-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span></span>|  
|<span data-ttu-id="e8094-127">Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-127">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|<span data-ttu-id="e8094-128">http://www.w3.org/TR/2006/rec-ws-addr-SOAP-20060509</span><span class="sxs-lookup"><span data-stu-id="e8094-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span></span>|  
|<span data-ttu-id="e8094-129">Adresleme 1.0 - WSDL bağlama W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-129">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|<span data-ttu-id="e8094-130">http://www.w3.org/TR/2006/CR-ws-addr-WSDL-20060529/</span><span class="sxs-lookup"><span data-stu-id="e8094-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span></span>|  
<span data-ttu-id="e8094-131">W3C Web adresleme 1.0 - meta veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-131">W3C Web Services Addressing 1.0 - Metadata</span></span>|<span data-ttu-id="e8094-132">http://www.w3.org/TR/ws-addr-metadata/</span><span class="sxs-lookup"><span data-stu-id="e8094-132">http://www.w3.org/TR/ws-addr-metadata/</span></span>|  
|<span data-ttu-id="e8094-133">WSDL SOAP1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-133">WSDL SOAP1.1 Binding</span></span>|<span data-ttu-id="e8094-134">http://www.w3.org/TR/WSDL/</span><span class="sxs-lookup"><span data-stu-id="e8094-134">http://www.w3.org/TR/wsdl/</span></span>|  
|<span data-ttu-id="e8094-135">WSDL SOAP1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-135">WSDL SOAP1.2 Binding</span></span>|<span data-ttu-id="e8094-136">http://www.w3.org/Submission/wsdl11soap12/</span><span class="sxs-lookup"><span data-stu-id="e8094-136">http://www.w3.org/Submission/wsdl11soap12/</span></span>|  
  
 <span data-ttu-id="e8094-137">Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ayrıntıları aşağıdaki protokoller için <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-137">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="e8094-138">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="e8094-138">Specification/document</span></span>|<span data-ttu-id="e8094-139">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="e8094-139">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="e8094-140">XOP</span><span class="sxs-lookup"><span data-stu-id="e8094-140">XOP</span></span>|<span data-ttu-id="e8094-141">http://www.w3.org/TR/xop10/</span><span class="sxs-lookup"><span data-stu-id="e8094-141">http://www.w3.org/TR/xop10/</span></span>|  
|<span data-ttu-id="e8094-142">MTOM + SOAP 1.2 bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-142">MTOM + SOAP 1.2 Binding</span></span>|<span data-ttu-id="e8094-143">http://www.w3.org/TR/soap12-MTOM/</span><span class="sxs-lookup"><span data-stu-id="e8094-143">http://www.w3.org/TR/soap12-mtom/</span></span>|  
|<span data-ttu-id="e8094-144">MTOM SOAP 1.1 bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-144">MTOM SOAP 1.1 Binding</span></span>|<span data-ttu-id="e8094-145">http://www.w3.org/Submission/soap11mtom10/</span><span class="sxs-lookup"><span data-stu-id="e8094-145">http://www.w3.org/Submission/soap11mtom10/</span></span>|  
|<span data-ttu-id="e8094-146">MTOM WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="e8094-146">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="e8094-147">http://www.w3.org/Submission/2006/SUBM-ws-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="e8094-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="e8094-148">Aşağıdaki XML ad alanları ve ilişkili önekleri bu konu boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8094-148">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="e8094-149">önek</span><span class="sxs-lookup"><span data-stu-id="e8094-149">Prefix</span></span>|<span data-ttu-id="e8094-150">Namespace Tekdüzen Kaynak Tanımlayıcısı (URI)</span><span class="sxs-lookup"><span data-stu-id="e8094-150">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="e8094-151">S11</span><span class="sxs-lookup"><span data-stu-id="e8094-151">s11</span></span>|<span data-ttu-id="e8094-152">http://schemas.xmlsoap.org/SOAP/Envelope</span><span class="sxs-lookup"><span data-stu-id="e8094-152">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="e8094-153">s12</span><span class="sxs-lookup"><span data-stu-id="e8094-153">s12</span></span>|<span data-ttu-id="e8094-154">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="e8094-154">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="e8094-155">wsa</span><span class="sxs-lookup"><span data-stu-id="e8094-155">wsa</span></span>|<span data-ttu-id="e8094-156">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="e8094-156">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="e8094-157">wsam</span><span class="sxs-lookup"><span data-stu-id="e8094-157">wsam</span></span>|<span data-ttu-id="e8094-158">http://www.w3.org/2007/05/Addressing/metadata</span><span class="sxs-lookup"><span data-stu-id="e8094-158">http://www.w3.org/2007/05/addressing/metadata</span></span>|  
|<span data-ttu-id="e8094-159">wsap</span><span class="sxs-lookup"><span data-stu-id="e8094-159">wsap</span></span>|<span data-ttu-id="e8094-160">http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing</span><span class="sxs-lookup"><span data-stu-id="e8094-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span></span>|  
|<span data-ttu-id="e8094-161">wsa10</span><span class="sxs-lookup"><span data-stu-id="e8094-161">wsa10</span></span>|<span data-ttu-id="e8094-162">http://www.w3.org/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="e8094-162">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="e8094-163">wsaw10</span><span class="sxs-lookup"><span data-stu-id="e8094-163">wsaw10</span></span>|<span data-ttu-id="e8094-164">http://www.w3.org/2006/05/Addressing/WSDL</span><span class="sxs-lookup"><span data-stu-id="e8094-164">http://www.w3.org/2006/05/addressing/wsdl</span></span>|  
|<span data-ttu-id="e8094-165">XOP</span><span class="sxs-lookup"><span data-stu-id="e8094-165">xop</span></span>|<span data-ttu-id="e8094-166">http://www.w3.org/2004/08/XOP/include</span><span class="sxs-lookup"><span data-stu-id="e8094-166">http://www.w3.org/2004/08/xop/include</span></span>|  
|<span data-ttu-id="e8094-167">xmime</span><span class="sxs-lookup"><span data-stu-id="e8094-167">xmime</span></span>|<span data-ttu-id="e8094-168">http://www.w3.org/2004/06/xmlmime</span><span class="sxs-lookup"><span data-stu-id="e8094-168">http://www.w3.org/2004/06/xmlmime</span></span><br /><br /> <span data-ttu-id="e8094-169">http://www.w3.org/2005/05/xmlmime</span><span class="sxs-lookup"><span data-stu-id="e8094-169">http://www.w3.org/2005/05/xmlmime</span></span>|  
<span data-ttu-id="e8094-170">dp</span><span class="sxs-lookup"><span data-stu-id="e8094-170">dp</span></span>|<span data-ttu-id="e8094-171">http://schemas.microsoft.com/NET/2006/06/Duplex</span><span class="sxs-lookup"><span data-stu-id="e8094-171">http://schemas.microsoft.com/net/2006/06/duplex</span></span>|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="e8094-172">SOAP 1.1 ve SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="e8094-172">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="e8094-173">Zarf ve Model işleme</span><span class="sxs-lookup"><span data-stu-id="e8094-173">Envelope and Processing Model</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-174">Temel Profil 1.1 (BP11) ve temel Profil 1.0 (SSBP10) aşağıdaki SOAP 1.1 Zarf işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="e8094-174"> implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="e8094-175">SOAP 1.2 Zarf SOAP12 bölüm 1 aşağıdaki işlem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-175">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="e8094-176">Bu bölümde tarafından gerçekleştirilecek belirli uygulama seçimler açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] BP11 ve SOAP12 bölüm 1 sabittir.</span><span class="sxs-lookup"><span data-stu-id="e8094-176">This section explains certain implementation choices taken by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="e8094-177">Zorunlu üstbilgiyi işleme</span><span class="sxs-lookup"><span data-stu-id="e8094-177">Mandatory Header Processing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-178">üstbilgiler işleniyor işaretlenmiş için kurallara `mustUnderstand` SOAP 1.1 ve SOAP 1.2 belirtimlere, aşağıdaki farklılıkları açıklanan.</span><span class="sxs-lookup"><span data-stu-id="e8094-178"> follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="e8094-179">Girer bir ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal yığını ilişkili bağlama öğeleri tarafından örneğin yapılandırılmış tek tek kanalları, ileti metin kodlaması, güvenlik, güvenilir Mesajlaşma ve işlemler tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="e8094-179">A message that enters the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="e8094-180">Her bir kanala ilişkili ad alanından üstbilgileri tanır ve anladım olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="e8094-180">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="e8094-181">Bir ileti dağıtıcısı girdikten sonra karşılık gelen ileti işlem başına Sözleşme ve bunları anladım işaretleri tarafından beklenen üstbilgileri işlemini biçimlendiricisi okur.</span><span class="sxs-lookup"><span data-stu-id="e8094-181">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="e8094-182">Dağıtıcı kalan tüm üstbilgileri değil anladı ancak olarak işaretlenmiş olup olmadığını doğrular sonra `mustUnderstand` ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8094-182">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="e8094-183">İçeren iletileri `mustUnderstand` recipient öğesinde hedeflenen üstbilgileri alıcı uygulama kodu tarafından işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="e8094-183">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="e8094-184">Gibi katmanlı işleme altyapısı katmanları ve SOAP düğümünün uygulama katmanları arasında ayrım sağlar:</span><span class="sxs-lookup"><span data-stu-id="e8094-184">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="e8094-185">B1111: değil anlaşılır üstbilgileri tarafından işlenen iletisi sonra algılanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı kanal yığını, ancak uygulama tarafından işlenmeden önce</span><span class="sxs-lookup"><span data-stu-id="e8094-185">B1111: Headers that are not understood are detected after the message is processed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="e8094-186">`mustUnderstand` Üstbilgi değeri SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8094-186">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="e8094-187">Temel Profil 1.1 gerektirir `mustUnderstand` değer 0 veya 1 SOAP 1.1 iletileri için olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-187">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="e8094-188">SOAP 1.2 sağlar 0, 1, `false`, ve `true` olarak değerleri ancak kurallı gösterimi yayma önerir `xs:boolean` değerleri (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="e8094-188">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="e8094-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yayar `mustUnderstand` SOAP zarfının değerleri 0 ile 1 SOAP 1.1 ve SOAP 1.2 sürümleri için.</span><span class="sxs-lookup"><span data-stu-id="e8094-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-190">tüm değer alan kabul `xs:boolean` için `mustUnderstand` üstbilgi (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="e8094-190"> accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="e8094-191">SOAP hataları</span><span class="sxs-lookup"><span data-stu-id="e8094-191">SOAP Faults</span></span>  
 <span data-ttu-id="e8094-192">Bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirli bir SOAP hatası uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="e8094-192">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="e8094-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki SOAP 1.1 hata kodlarını döndürür: `s11:mustUnderstand`, `s11:Client`, ve `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="e8094-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="e8094-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki SOAP 1.2 hata kodlarını döndürür: `s12:MustUnderstand`, `s12:Sender`, ve `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="e8094-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="e8094-195">HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-195">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="e8094-196">SOAP 1.1 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-196">SOAP 1.1 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-197">Temel Profil 1.1 belirtimini aşağıdaki açıklamalar 3.4 bölümle aşağıdaki SOAP1.1 HTTP bağlaması uygular:</span><span class="sxs-lookup"><span data-stu-id="e8094-197"> implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="e8094-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, HTTP POST isteklerini yeniden yönlendirilmesini uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="e8094-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="e8094-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri 3.4.8 uygun olarak HTTP tanımlama bilgilerini destekleyen.</span><span class="sxs-lookup"><span data-stu-id="e8094-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="e8094-200">SOAP 1.2 HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="e8094-200">SOAP 1.2 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-201">SOAP 1.2 HTTP bağlaması SOAP 1.2 bölümü 2 (SOAP12Part2) belirtimiyle aşağıdaki açıklamalar bölümünde açıklandığı gibi uygular.</span><span class="sxs-lookup"><span data-stu-id="e8094-201"> implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="e8094-202">SOAP 1.2 sunulan bir isteğe bağlı eylem parametresi için `application/soap+xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="e8094-202">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="e8094-203">Bu parametre WS adresleme kullanılmadığı SOAP ileti gövdesini ayrıştırılması gerek kalmadan ileti gönderme en iyi duruma getirmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-203">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="e8094-204">R2221: `application/soap+xml` eylem parametresi SOAP 1.2 istek üzerine varsa eşleşmelidir `soapAction` özniteliği `wsoap12:operation` öğesi içinde karşılık gelen WSDL bağlama.</span><span class="sxs-lookup"><span data-stu-id="e8094-204">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="e8094-205">R2222: `application/soap+xml` eylem parametresi, bir SOAP 1.2 iletideki varsa eşleşmelidir `wsa:Action` WS adresleme 2004/08 veya WS adresleme 1.0 ne zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8094-205">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="e8094-206">WS-adresleme devre dışıdır ve gelen istek bir eylem parametresinin içermediğinden, ileti `Action` belirtilen olarak sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="e8094-206">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="e8094-207">WS-adresleme</span><span class="sxs-lookup"><span data-stu-id="e8094-207">WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-208">WS-adresleme 3 sürümlerini uygular:</span><span class="sxs-lookup"><span data-stu-id="e8094-208"> implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="e8094-209">WS-adresleme 2004/08</span><span class="sxs-lookup"><span data-stu-id="e8094-209">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="e8094-210">1.0 çekirdek (ADDR10 çekirdekli) ve (SOAP ADDR10) bağlama SOAP adresleme W3C Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-210">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="e8094-211">WS-adresleme 1.0 - meta verileri</span><span class="sxs-lookup"><span data-stu-id="e8094-211">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="e8094-212">Uç nokta başvuruları</span><span class="sxs-lookup"><span data-stu-id="e8094-212">Endpoint References</span></span>  
 <span data-ttu-id="e8094-213">WS-adresleme'nin tüm sürümleri, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayan uç noktaları tanımlamak için uç nokta başvuruları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8094-213">All versions of WS-Addressing that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="e8094-214">Uç nokta başvuruları ve WS adresleme sürümleri</span><span class="sxs-lookup"><span data-stu-id="e8094-214">Endpoint References and WS-Addressing Versions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-215">WS-adresleme kullanan altyapı protokolleri ve belirli bir sayı uygulayan `EndpointReference` öğesi ve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="e8094-215"> implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-216">Her iki sürümü WS-adresleme diğer altyapı protokollerle kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="e8094-216"> supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-217">uç noktaları bir sürümü WS adresleme uç nokta başına destekler.</span><span class="sxs-lookup"><span data-stu-id="e8094-217"> endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="e8094-218">R3111, ad alanı için `EndpointReference` öğesi veya türü ile değiştirilen iletilerin kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta WS adresleme-bu bitiş noktası tarafından uygulanan sürümü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-218">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="e8094-219">Örneğin, varsa bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint uygulayan WS-ReliableMessaging `AcksTo` gibi bir uç nokta içinde tarafından döndürülen üstbilgi `CreateSequenceResponse` WS adresleme sürümünü kullanır, `EncodingBinding` öğesi için bu uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8094-219">For example, if a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="e8094-220">Uç nokta başvuruları ve meta veriler</span><span class="sxs-lookup"><span data-stu-id="e8094-220">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="e8094-221">Çeşitli senaryoları meta veriler veya belirli bir uç nokta için meta veriler için bir başvuru iletişim kurmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8094-221">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="e8094-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-MetadataExchange (MEX) belirtimi değere veya başvuruya göre meta veri uç noktası başvurular eklemek için Bölüm 6 açıklanan mekanizmaları uygular.</span><span class="sxs-lookup"><span data-stu-id="e8094-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="e8094-223">Bir senaryo düşünün burada bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti Belirteç Verenin http://sts.fabrikam123.com, tarafından verilmiş bir güvenlik onaylar biçimlendirme dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Endpoint kullanarak bu kimlik doğrulama gereksinimini açıklar `sp:IssuedToken` onaylama işlemi bir iç içe `sp:Issuer` Belirteç Verenin işaret eden onaylama.</span><span class="sxs-lookup"><span data-stu-id="e8094-223">Consider a scenario where a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="e8094-224">Erişim istemci uygulamaları `sp:Issuer` onaylama Belirteç Verenin bitiş noktası ile iletişim kurma bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8094-224">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="e8094-225">İstemcinin meta verileri Belirteç Verenin hakkında bilmek ister.</span><span class="sxs-lookup"><span data-stu-id="e8094-225">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="e8094-226">MEX içinde tanımlanmış uç nokta başvuru meta veri uzantılarını kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Belirteç Verenin meta veriler için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8094-226">Using the endpoint reference metadata extensions defined in MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="e8094-227">İleti adresleme üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="e8094-227">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="e8094-228">İleti üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="e8094-228">Message Headers</span></span>  
 <span data-ttu-id="e8094-229">Her iki WS adresleme sürümleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki ileti üstbilgilerini belirtimleri tarafından belirlenen şekilde kullanır `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, ve `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="e8094-229">For both WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="e8094-230">B3211: WS adresleme tüm sürümleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] korur, ancak ileti üstbilgilerini WS adresleme kutudan çıktığı oluşturmadığı `wsa:FaultTo` ve `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="e8094-230">B3211: For all WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="e8094-231">Etkileşim uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, bu ileti üstbilgilerini ekleyebilir ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buna uygun olarak işleyecek.</span><span class="sxs-lookup"><span data-stu-id="e8094-231">Applications that interact with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can add these message headers and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="e8094-232">Başvuru parametreleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="e8094-232">Reference Parameters and Properties</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-233">uç nokta başvuru parametreleri ve başvuru p Implements işlenmesini</span><span class="sxs-lookup"><span data-stu-id="e8094-233"> implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="e8094-234">ilgili belirtimlerine uygun olarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-234">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="e8094-235">B3221: WS adresleme 2004/08 kullanmak üzere yapılandırıldığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktalar değil ayırt başvuru özellikleri ve başvuru parametreleri işleme arasında.</span><span class="sxs-lookup"><span data-stu-id="e8094-235">B3221: When configured to use WS-Addressing 2004/08, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="e8094-236">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="e8094-236">Message Exchange Patterns</span></span>  
 <span data-ttu-id="e8094-237">Web hizmeti işlemi çağırma yer alan iletileri dizisi olarak adlandırılır *ileti değişim deseni*.</span><span class="sxs-lookup"><span data-stu-id="e8094-237">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-238">tek yönlü destekler, istek-yanıt ve çift yönlü iletisi desenleri exchange.</span><span class="sxs-lookup"><span data-stu-id="e8094-238"> supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="e8094-239">Bu bölümde kullanılan ileti değişim deseni bağlı olarak işleme iletideki WS adreslendirme gereksinimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e8094-239">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="e8094-240">Bu bölümde genelinde istek sahibinin ilk ileti gönderir ve Yanıtlayıcı ilk iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="e8094-240">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="e8094-241">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="e8094-241">One-Way Message</span></span>  
 <span data-ttu-id="e8094-242">Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint iletilerle desteklemek üzere yapılandırılmış bir belirli `Action` tek yönlü bir deseni izlemesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası aşağıdaki aşağıdaki davranışları ve gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-242">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="e8094-243">WS-adresleme her iki sürümü de desteklenen aksi belirtilmediği sürece, davranışları ve kuralları uygula [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e8094-243">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="e8094-244">R3311: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`ve uç nokta başvuru tarafından belirtilen tüm başvuru parametreleri için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="e8094-244">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="e8094-245">Ne zaman WS adresleme 2004/08 kullanılır ve karşılık gelen üstbilgileri iletiye çok eklenmelidir [başvuru Özellikleri] uç nokta başvuruya göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-245">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="e8094-246">B3312: İstek sahibinin içerebilir `MessageID`, `ReplyTo`, ve `FaultTo` üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="e8094-246">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="e8094-247">Alıcı altyapı bunları göz ardı eder ve uygulamaya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-247">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="e8094-248">R3313: HTTP kullanılır ve hiçbir ileti üzerinde HTTP yanıt leg gönderilen Yanıtlayıcı boş bir gövde ve bir HTTP 202 durum kodu ile bir HTTP yanıtının göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8094-248">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="e8094-249">HTTP taşıma kullanımda ve işlem sözleşmesi bir ileti tek yönlü bildirir, HTTP yanıtı hala altyapı ileti göndermek için kullanılabilir — örneğin, güvenilir Mesajlaşma gönderebilirsiniz bir `SequenceAcknowledgement` bir HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="e8094-249">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="e8094-250">B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı göndermez bir hata iletisi tek yönlü iletisine yanıt olarak.</span><span class="sxs-lookup"><span data-stu-id="e8094-250">B3314: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="e8094-251">İstek-Yanıt</span><span class="sxs-lookup"><span data-stu-id="e8094-251">Request-Reply</span></span>  
 <span data-ttu-id="e8094-252">Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bitiş noktası içeren bir ileti için yapılandırılmış bir belirli `Action` istek-yanıt deseni izlemesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası aşağıdaki davranışları ve aşağıdaki gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-252">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="e8094-253">WS-adresleme her iki sürümü de desteklenen aksi belirtilmediği sürece, davranışları ve kuralları uygula [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e8094-253">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="e8094-254">R3321: İstek sahibinin istekte içermelidir `wsa:To`, `wsa:Action`, `wsa:MessageID`ve tüm başvuru parametreleri başvuru özellikler (veya her ikisi) uç noktası başvuru tarafından belirtilen için üstbilgiler.</span><span class="sxs-lookup"><span data-stu-id="e8094-254">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="e8094-255">R3322: WS adresleme 2004/08 kullanıldığında `ReplyTo` istekte de eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e8094-255">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="e8094-256">R3323: WS adresleme 1.0 kullanıldığında ve `ReplyTo` olduğu istekte mevcut değil, varsayılan uç nokta başvuru "http://www.w3.org/2005/08/addressing/anonymous" eşit [address] özelliği ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8094-256">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="e8094-257">R3324: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`, ve `wsa:RelatesTo` yanıt iletisi üstbilgilerinde yanı sıra tüm başvuru parametreleri başvuru özellikler (veya her ikisi) tarafından belirtilen üstbilgilerini `ReplyTo` bitiş noktası başvurusu İstek.</span><span class="sxs-lookup"><span data-stu-id="e8094-257">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="e8094-258">Adresleme hataları Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8094-258">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="e8094-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS adresleme 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="e8094-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="e8094-260">Kod</span><span class="sxs-lookup"><span data-stu-id="e8094-260">Code</span></span>|<span data-ttu-id="e8094-261">Sebep</span><span class="sxs-lookup"><span data-stu-id="e8094-261">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="e8094-262">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="e8094-262">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="e8094-263">İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı; Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8094-263">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="e8094-264">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="e8094-264">wsa:ActionNotSupported</span></span>|<span data-ttu-id="e8094-265">Altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcısı belirtilen eylem algılamaz `Action` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="e8094-265">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="e8094-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS adresleme 1.0 tarafından tanımlanan aşağıdaki hataları üretir.</span><span class="sxs-lookup"><span data-stu-id="e8094-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="e8094-267">Kod</span><span class="sxs-lookup"><span data-stu-id="e8094-267">Code</span></span>|<span data-ttu-id="e8094-268">Sebep</span><span class="sxs-lookup"><span data-stu-id="e8094-268">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="e8094-269">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="e8094-269">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="e8094-270">Yinelenen `wsa:To`, `wsa:ReplyTo`, `wsa:From` veya `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="e8094-270">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="e8094-271">Yinelenen `wsa:RelatesTo` aynı `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="e8094-271">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="e8094-272">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="e8094-272">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="e8094-273">Gerekli adresleme üstbilgisi eksik.</span><span class="sxs-lookup"><span data-stu-id="e8094-273">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="e8094-274">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="e8094-274">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="e8094-275">İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı.</span><span class="sxs-lookup"><span data-stu-id="e8094-275">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="e8094-276">Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8094-276">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="e8094-277">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="e8094-277">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="e8094-278">Belirtilen eylem `Action` üstbilgi altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcı tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="e8094-278">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="e8094-279">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="e8094-279">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="e8094-280">Uç nokta incelenmesi temel sıralı işlemez belirten bu hataya geri RM kanalı gönderir `CreateSequence` ileti üstbilgilerini adresleme.</span><span class="sxs-lookup"><span data-stu-id="e8094-280">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="e8094-281">Yukarıdaki tablolarda kod eşlemeleri için `FaultCode` içinde SOAP 1.1 ve `SubCode` (koduyla gönderen =) SOAP 1.2 içindeki.</span><span class="sxs-lookup"><span data-stu-id="e8094-281">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="e8094-282">WSDL 1.1 bağlama ve WS-ilke onaylamalarını</span><span class="sxs-lookup"><span data-stu-id="e8094-282">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="e8094-283">WS-adresleme kullanımını gösteren</span><span class="sxs-lookup"><span data-stu-id="e8094-283">Indicating Use of WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-284">özel bir WS adresleme sürüm için uç nokta destek belirtmek için ilke onaylamalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-284"> uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="e8094-285">Aşağıdaki ilke onaylama uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8094-285">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="e8094-286">Bu ilke onaylama WS adresleme 2004/08 belirtimi artırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8094-286">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="e8094-287">Bu, gönderilen ve alınan iletileri gösterir aşağıdaki ilke onaylama WS adresleme 1.0 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8094-287">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="e8094-288">Aşağıdaki ilke onaylama bir uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8094-288">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="e8094-289">`wsaw10:UsingAddressing` Öğesi [WS-adresleme-WSDL] ödünç ve WS-Policy bağlamında bu belirtimi uyumlu kullanılır, Bölüm 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="e8094-289">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="e8094-290">Adresleme kullanımını WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP bağlamaları semantiği değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e8094-290">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="e8094-291">Bir yanıt adresleme ve WSDL SOAP 1.x HTTP bağlama kullanan bir uç nokta için gönderilen bir istek bekleniyorsa, örneğin, yanıt HTTP yanıtı kullanarak gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e8094-291">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="e8094-292">Http yanıtı gönderilen yanıtlar için WS-AM onayı ifade eder:</span><span class="sxs-lookup"><span data-stu-id="e8094-292">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="e8094-293">Tam İlkesi onaylama şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="e8094-293">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="e8094-294">Ancak, istek sahibinin ve Yanıtlayıcı Yanıtlayıcı tarafından gönderilen Örneğin, istenmeyen tek yönlü iletileri arasında kurulan iki bağımsız ters HTTP bağlantılarını kalmaktan fayda ileti exchange desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e8094-294">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-295">iki temel taşıma kanalları burada bir kanal giriş iletileri için kullanılır ve çıktı iletiler için kullanılan başka bir bileşik çift yönlü kanal kurabilir bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="e8094-295"> offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="e8094-296">HTTP taşıma söz konusu olduğunda, bileşik çift yönlü iki ters HTTP bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8094-296">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="e8094-297">Yanıtlayıcı iletileri göndermek için bir bağlantı istek sahibinin kullanır ve Yanıtlayıcı diğer iletiler istemciye geri gönderilecek kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-297">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="e8094-298">Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am onayı ifade eder</span><span class="sxs-lookup"><span data-stu-id="e8094-298">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="e8094-299">Tam İlkesi onaylama şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="e8094-299">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="e8094-300">Talep sahibinin Yanıtlayıcı ve istekte bulunan kişinin Yanıtlayıcı akan iletileri için kullanılacak iki ayrı ters HTTP bağlantılarını WSDL 1.1 SOAP 1.x HTTP bağlamaları kullanan uç noktalarda uç nokta İlkesi konu [WS-PA] olan aşağıdaki onay kullanımını, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e8094-300">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="e8094-301">Önceki deyimi aşağıdaki gereksinimleri müşteri adayları `wsa:ReplyTo` başlığı istek iletileri için:</span><span class="sxs-lookup"><span data-stu-id="e8094-301">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="e8094-302">R3514: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit değil "http://www.w3.org/2005/08/addressing/anonymous" uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ile varsa bir `wsap10:UsingAddressing` veya `wsap:UsingAddressing` onaylama eşleşmiş ile `cdp:CompositeDuplex` bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8094-302">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="e8094-303">R3515: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous" ya da yok bir `ReplyTo` tümü, uç nokta WSDL 1.1 kullanıyorsa, üst bilgisi SOAP 1.x HTTP bağlama ve bir ilke alternatif ile sahip `wsap10:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="e8094-303">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="e8094-304">R3516: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle bir `[address]` özelliği "uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ilevarsahttp://www.w3.org/2005/08/addressing/anonymous"eşit`wsap:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.</span><span class="sxs-lookup"><span data-stu-id="e8094-304">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="e8094-305">Bir öğenin sunarak benzer protokolü bağlamaları tanımlamak WS adresleme WSDL belirtimi çalışır `<wsaw:Anonymous/>` değerlerle üzerinde gereksinimleri göstermek için üç metinsel (gerekli, isteğe bağlı ve yasaklanmış) `wsa:ReplyTo` üstbilgi (Bölüm 3.2).</span><span class="sxs-lookup"><span data-stu-id="e8094-305">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="e8094-306">Ne yazık ki, bu tür bir öğe onayı ifade kullanarak alternatifleri kesişimi desteklemek için etki alanına özgü uzantılar gerektirdiğinden böyle öğesi tanımı bir onaylama WS-İlkesi ' nin bağlamında özellikle kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e8094-306">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="e8094-307">Bu tür öğesi tanımı değerini de gösterir `ReplyTo` HTTP aktarımı için belirli kolaylaştırır Tel üzerinde uç noktası davranışı aksine üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="e8094-307">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="e8094-308">Eylem tanımı</span><span class="sxs-lookup"><span data-stu-id="e8094-308">Action Definition</span></span>  
 <span data-ttu-id="e8094-309">WS-adresleme 2004/08 tanımlayan bir `wsa:Action` için öznitelik `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-309">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="e8094-310">WS-adresleme 1.0 WSDL bağlama (WS-ADDR10-WSDL) benzer bir öznitelik tanımlar `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="e8094-310">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="e8094-311">İkisi arasındaki tek fark sırasıyla Bölüm WS-ADDR 3.3.2 ve WS-ADDR10-WSDL 4.4.4 bölümünde açıklanan varsayılan eylem düzeni semantiği ' dir.</span><span class="sxs-lookup"><span data-stu-id="e8094-311">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="e8094-312">Aynı paylaşan iki uç nokta uygun olan `portType` (veya sözleşme, içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminolojisi) ancak WS adresleme farklı sürümlerini kullanan.</span><span class="sxs-lookup"><span data-stu-id="e8094-312">It is a reasonable to have two endpoints that share the same `portType` (or contract, in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="e8094-313">Ancak eylem tarafından tanımlanan o `portType` ve uygulayan uç noktalar arasında değiştirmemelisiniz `portType`, her iki varsayılan eylem desenleri desteklemesini mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="e8094-313">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="e8094-314">Bu controversy gidermek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tek bir sürümünü destekleyen `Action` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e8094-314">To resolve this controversy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="e8094-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan `wsaw10:Action` özniteliği `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-belirlemek için WSDL içinde tanımlanan öğeleri `Action` bitiş noktası tarafından kullanılan WS adresleme sürümü yedeklemiş karşılık gelen iletiler için URI.</span><span class="sxs-lookup"><span data-stu-id="e8094-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="e8094-316">Kullanım uç noktası başvuru iç WSDL bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="e8094-316">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="e8094-317">WS ADDR10 WSDL bölüm 4.1 genişletir `wsdl:port` eklenecek öğe `<wsa10:EndpointReference…/>` uç nokta WS adresleme koşullarını tanımlamak için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-317">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-318">Bu yardımcı program WS adresleme 2004/08 üzerinde genişletir izin vererek `<wsa:EndpointReference…/>` bir alt öğesi görüntülenmesini `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="e8094-318"> expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="e8094-319">R3531: iliştirilmiş ilke alternatif bir uç nokta varsa, bir `<wsaw10:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="e8094-319">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="e8094-320">R3532: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-320">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="e8094-321">R3533: bir uç nokta iliştirilmiş ilke alternatif varsa `<wsap:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="e8094-321">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="e8094-322">R3534: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-322">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="e8094-323">WS güvenliği ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8094-323">Composition with WS-Security</span></span>  
 <span data-ttu-id="e8094-324">WS-ADDR ve WS-ADDR10 güvenlik göz önünde bulundurarak bölümlere göre tüm adresleme ileti üstbilgilerini birlikte ileti gövdesi birbirine bağlamak için imzalanması için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-324">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="e8094-325">WS güvenliği ileti bütünlüğü koruma için kullanıldığında, ileti gövdesi birlikte WS adresleme ileti üstbilgilerini yanı sıra üstbilgileri başvuru parametreleri veya özellikler (veya her ikisi de) sonuçlandı imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8094-325">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e8094-326">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e8094-326">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="e8094-327">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="e8094-327">One-Way Message</span></span>  
 <span data-ttu-id="e8094-328">Bu senaryoda, gönderenin alıcı için tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="e8094-328">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="e8094-329">SOAP 1.2, HTTP 1.1 ve 1.0 W3C WS adresleme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8094-329">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="e8094-330">İstek iletisi yapısı: İleti üstbilgilerini dahil `wsa10:To` ve `wsa10:Action` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-330">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="e8094-331">Belirli bir ileti gövdesini içeren `<app:Ping>` uygulama ad alanından öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-331">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="e8094-332">HTTP üstbilgileri: POST hedef URI eşleşen `wsa10:To` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-332">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="e8094-333">Content-Type üstbilgisi değeri olan `application/soap+xml` SOAP 1.2 gerektirdiği.</span><span class="sxs-lookup"><span data-stu-id="e8094-333">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="e8094-334">Parametreleri `charset` ve `action` dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-334">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="e8094-335">`action` Content-Type üstbilgisi parametresinin değeri ile eşleşen `wsa10:Action` ileti üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="e8094-335">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="e8094-336">Alıcı boş HTTP yanıt ve durum 202 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="e8094-336">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="e8094-337">HTTP yanıt örneği:</span><span class="sxs-lookup"><span data-stu-id="e8094-337">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="e8094-338">SOAP iletisi iletim iyileştirme mekanizması</span><span class="sxs-lookup"><span data-stu-id="e8094-338">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="e8094-339">Bu bölümde açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP SOAP MTOM uygulama ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="e8094-339">This section describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="e8094-340">MTOM teknolojidir SOAP iletisi kodlama mekanizması geleneksel text/XML kodlama olarak aynı sınıfın veya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ikili kodlama.</span><span class="sxs-lookup"><span data-stu-id="e8094-340">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary encoding.</span></span> <span data-ttu-id="e8094-341">MTOM aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e8094-341">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="e8094-342">Bir XML kodlama ve [XOP] tarafından açıklanan paketleme mekanizması ayrı ikili parçalara base64 ile kodlanmış ikili veri içeren XML bilgi öğeleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="e8094-342">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="e8094-343">MIME kapsülleme XML bilgi ve her ikili XOP paketinin parçası ayrı bir MIME bölüm içinde serileştiren XOP paketi.</span><span class="sxs-lookup"><span data-stu-id="e8094-343">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="e8094-344">SOAP için uygulanan bir MIME XOP kodlama 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="e8094-344">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="e8094-345">Bir HTTP aktarım bağlama.</span><span class="sxs-lookup"><span data-stu-id="e8094-345">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="e8094-346">MTOM olmayan HTTP taşımaları ile birlikte kullanmak da mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8094-346">It is possible to use MTOM with non-HTTP transports with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e8094-347">Ancak, bu konudaki şu HTTP odaklanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-347">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="e8094-348">MTOM biçim belirtim MTOM kendisi, XOP ve MIME kapsayan büyük kümesi yararlanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-348">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="e8094-349">Bu belirtimi kümesinin modülerlik biçimi ve işleme semantiğini tam gereksinimlerine yeniden oluşturmak biraz zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e8094-349">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="e8094-350">Bu bölümde MTOM HTTP bağlaması için biçimi ve işleme gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8094-350">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="e8094-351">İleti MTOM kodlama</span><span class="sxs-lookup"><span data-stu-id="e8094-351">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="e8094-352">MTOM iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8094-352">Generating MTOM messages</span></span>  
 <span data-ttu-id="e8094-353">[XOP] bölümü 3.1 bağlamalarında tanımlanmış bir XOP pakete base64 değerler içeren öğesi bilgi öğelerle XML kodlama işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-353">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="e8094-354">Aşağıdaki adımlar dizisini özel MTOM kodlama işlemi açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e8094-354">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="e8094-355">Kodlanacak SOAP Zarfı hiçbir öğe bilgi öğe ile içerdiğinden emin olun bir `[namespace name]` "http://www.w3.org/2004/08/xop/include" olarak ve bir `[local name]` , `Include`.</span><span class="sxs-lookup"><span data-stu-id="e8094-355">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="e8094-356">Boş bir MIME paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8094-356">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="e8094-357">Özgün XML bilgi içinde en iyi duruma getirilmesi öğesi bilgi öğeleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e8094-357">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="e8094-358">Öğeleri en iyi duruma getirilmesi karakterleri oluşturan `[children]` öğesi bilgilerinin öğesi kurallı biçiminde olmalı `xs:base64Binary` (XSD-2, 3.2.16 bkz base64Binary) ve, satır içi, önceki herhangi bir boşluk karakteri içermemelidir veya boşluk olmayan içerik aşağıdaki.</span><span class="sxs-lookup"><span data-stu-id="e8094-358">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="e8094-359">Özgün SOAP Zarfı kopyası olan bir XOP SOAP Zarfı oluşturun, ancak her öğe bilgileri alt öğeleri önceki adımda belirlediğiniz öğesi olarak değiştirilir. bir `xop:Include` olarak öğe bilgi öğe:</span><span class="sxs-lookup"><span data-stu-id="e8094-359">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="e8094-360">Değiştirilen karakterleri base64 kodlu veriler olarak işleyerek ikili verisine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e8094-360">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="e8094-361">R3133 ve R3134 gereksinimleri karşılayan benzersiz bir Content-ID üstbilgi değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8094-361">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="e8094-362">İkili değeri olan bir Content-Transfer-Encoding MIME üstbilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8094-362">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="e8094-363">Öğe bilgileri öğe iyileştirilen varsa ([üst] yeni eklenen `xop:Include` öğe bilgi öğe) sahip bir `xmime:contentType` özniteliği bilgi öğesi, bir Content-Type MIME üstbilgisi değeri ile oluşturun `xmime:contentType` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e8094-363">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="e8094-364">İşlenen base64, 4b Content-ID başlığından, 4 c, adım 4 d oluşturursa Content-Type üstbilgisi Content-Transfer-Encoding başlığından değiştirilen karakter gelen kodunu çözdü ikili verileri tarafından oluşturulmuş içeriğe sahip yeni bir ikili MIME bölümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8094-364">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="e8094-365">Ekleme bir `href` özniteliğini `xop:Include` değeri CID bir öğesiyle: 4b adımında oluşturulan Content-ID üstbilgi değeri türetilen URI.</span><span class="sxs-lookup"><span data-stu-id="e8094-365">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="e8094-366">Kapsayan Kaldır "\<" ve ">" URL-kalan dize ve önekini ekleyin kaçış karakterleri `cid:`.</span><span class="sxs-lookup"><span data-stu-id="e8094-366">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="e8094-367">Aşağıdaki minimum karakter kümesi RFC1738 ve RFC2396 tarafından Atlanan için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e8094-367">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="e8094-368">Diğer karakterler kaçışlı.</span><span class="sxs-lookup"><span data-stu-id="e8094-368">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="e8094-369">Adım 4 XOP SOAP Zarfı içeren bir kök MIME bölümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8094-369">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="e8094-370">HTTP Content-Type üstbilgisi de dahil olmak üzere HTTP üst bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="e8094-370">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="e8094-371">MIME paket yazma.</span><span class="sxs-lookup"><span data-stu-id="e8094-371">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="e8094-372">MTOM iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="e8094-372">Processing MTOM messages</span></span>  
 <span data-ttu-id="e8094-373">Bir MTOM işleme ileti tam önceki açıklanan sürecin tersidir "üretme MTOM iletileri" bölümü:</span><span class="sxs-lookup"><span data-stu-id="e8094-373">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="e8094-374">Kök MIME bölümü Content-Type olduğundan `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="e8094-374">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="e8094-375">SOAP zarfını paketi bir XML belgesi olarak MIME parçası kök ayrıştırarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8094-375">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="e8094-376">Karakter kodlamasını tarafından belirlenir `charset` Kök MIME bölümü Content-Type parametresi.</span><span class="sxs-lookup"><span data-stu-id="e8094-376">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="e8094-377">Oluşturulan SAOP zarfına her öğe bilgi öğe için olan, kendi [alt] özelliğini tek üyesi olarak bir `xop:Include` öğe bilgi öğe:</span><span class="sxs-lookup"><span data-stu-id="e8094-377">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="e8094-378">Kaldırma `cid:` öneki ve tüm URI kaçış sıraları (RFC 2396) değerinde unescape `@href` özniteliği `xop:Include` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8094-378">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="e8094-379">Sonuç dizesinde alın "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="e8094-379">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="e8094-380">Adım 3a türetilmiş dizesiyle eşleşen Content-ID üstbilgi değeri olan MIME bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="e8094-380">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="e8094-381">Değiştir `xop:Include` görünür öğe bilgi öğe `children` kurallı base64 kodlaması temsil karakter bilgi öğelerinin bulunduğu her öğesinin özelliği (XSD-2, 3.2.16 bkz base64Binary) MIME bölümü varlık gövdesinin Adım 3b'de tanımlanan (etkili bir şekilde yerine `xop:Include` öğe bilgi öğe paket bölümünden yeniden verilerle).</span><span class="sxs-lookup"><span data-stu-id="e8094-381">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="e8094-382">HTTP Content-Type üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="e8094-382">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="e8094-383">Bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 1.x MTOM olarak kodlanmış bir ileti HTTP Content-Type üstbilgisinin biçimi için açıklamalar MTOM belirtimi kendisini belirtilen gereksinimleri türetilmiş ve MTOM ve RFC 2387 türetilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-383">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="e8094-384">R4131: Bir HTTP Content-Type üstbilgisi değeri multipart/related (büyük küçük harf duyarsız) ve parametrelerini olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-384">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="e8094-385">Parametre adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-385">Parameter names are case-insensitive.</span></span> <span data-ttu-id="e8094-386">Parametre sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="e8094-386">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="e8094-387">Content-Type üstbilgisi MIME iletileri için tam Backus-Naur formu'nı (BNF) bölümü 5.1, RFC 2045 listelenir.</span><span class="sxs-lookup"><span data-stu-id="e8094-387">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="e8094-388">R4132: Bir HTTP Content-Type üstbilgisi değeri olan bir tür parametresi olmalıdır `application/xop+xml` çift tırnak işaretleri içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-388">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="e8094-389">Çift tırnak işaretleri kullanma zorunluluğu RFC 2387 açık olmamasına karşın, tüm parametreleri büyük olasılıkla içeren multipart/related medya türü gibi karakterler ayrılmış metin gözlemleyen "@" or "/" ve bu nedenle çift tırnak işareti gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e8094-389">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="e8094-390">R4133: Başlangıç parametresi SOAP içeren MIME bölümü Content-ID üstbilgisi değeri ile bir HTTP Content-Type üstbilgisi olmalıdır 1.x Zarf, çift tırnak işaretleri içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-390">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="e8094-391">Başlangıç parametresi atlanırsa, ilk MIME bölümü SOAP içermelidir 1.x Zarf.</span><span class="sxs-lookup"><span data-stu-id="e8094-391">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="e8094-392">R4134: Text/xml, çift tırnak işaretleri içine değeriyle başlangıç bilgileri parametresi SOAP 1.1 kodlanmış MTOM iletisi için bir HTTP Content-Type üstbilgisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8094-392">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="e8094-393">R4135: SOAP 1.2 MTOM olarak kodlanmış bir ileti için bir HTTP Content-Type üstbilgisi değeri başlatma bilgisi parametresiyle içermelidir `application/soap+xml`, çift tırnak işaretleri içine alarak.</span><span class="sxs-lookup"><span data-stu-id="e8094-393">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="e8094-394">R4136: HTTP Content-Type üstbilgisi SOAP 1.x MTOM olarak kodlanmış bir ileti için sınır parametresi BNF bölüm 5.1.1, RFC 2046 tanımlanmış MIME sınır eşleşen (çift tırnak işaretleri içine) değerine sahip olması gerekir</span><span class="sxs-lookup"><span data-stu-id="e8094-394">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="e8094-395">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="e8094-395">Examples:</span></span>  
  
     <span data-ttu-id="e8094-396">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="e8094-396">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="e8094-397">DÜZELTİN</span><span class="sxs-lookup"><span data-stu-id="e8094-397">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="e8094-398">YANLIŞ</span><span class="sxs-lookup"><span data-stu-id="e8094-398">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="e8094-399">Bilgi MIME bölümü</span><span class="sxs-lookup"><span data-stu-id="e8094-399">Infoset MIME Part</span></span>  
 <span data-ttu-id="e8094-400">SOAP zarfını XOP MIME paketinin kök bir parçası kapsüllenmiş ve genellikle adlı 1.x `infoset` bölümü.</span><span class="sxs-lookup"><span data-stu-id="e8094-400">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="e8094-401">R4141: SOAP adlı XOP MIME paketi kök bir parçası olarak Zarf kapsüllenmiş 1.x `infoset` bölümü ve gelen HTTP Content-Type başvurulan.</span><span class="sxs-lookup"><span data-stu-id="e8094-401">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="e8094-402">R4142: SOAP `Infoset` bölümü aşağıdaki MIME Üstbilgileri içermelidir: `Content-ID`, `Content-Transfer-Encoding`, ve `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="e8094-402">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="e8094-403">Content-ID üstbilgi biçimi RFC 2045 tanımlanır</span><span class="sxs-lookup"><span data-stu-id="e8094-403">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="e8094-404">Burada `msg-id` (yani RFC 822, RFC 2045 başvurulan yerini) RFC 2822 olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="e8094-404">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="e8094-405">ve etkili bir şekilde bir e-posta adresi içine alınmış "\<" ve ">".</span><span class="sxs-lookup"><span data-stu-id="e8094-405">and is effectively an e-mail address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="e8094-406">`[CFWS]` Önek ve sonek 2822 açıklamaları taşımak için RFC eklendi ve birlikte çalışabilirlik korumak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-406">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="e8094-407">R4143: Bilgi MIME bölümü Content-ID üstbilgisinin değerini izlemelisiniz `msg-id` ile RFC 2822 üretimden `[CFWS]` atlanmış önek ve sonek bölümleri.</span><span class="sxs-lookup"><span data-stu-id="e8094-407">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="e8094-408">MIME uygulamaları sayısı rahat gereksinimleri içine alınmış bir değer için "\<" ve ">" bir e-posta adresi ve kullanılan `absoluteURI` içine "\<", ">" e-posta adresi yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="e8094-408">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an e-mail address and used `absoluteURI` enclosed in "\<" , ">" in addition to the e-mail address.</span></span> <span data-ttu-id="e8094-409">Bu sürümü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formun Content-ID MIME üstbilgi değerleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="e8094-409">This version of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="e8094-410">R4144: Content-ID üstbilgi değerleri aşağıdaki rahat eşleşen MTOM işlemciler kabul etmelidir `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="e8094-410">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="e8094-411">MIME (RFC 2045) MIME bölümü içeriğini kodlama iletişim kurmak için Content-Transfer-Encoding üstbilgisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8094-411">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="e8094-412">Content-Transfer-Encoding için tanımlanan varsayılan içerik Transfer-Encoding üstbilgisi büyük birlikte çalışabilirlik için gerektiği şekilde SOAP iletilerin çoğu için uygun olmayan 7 bit:</span><span class="sxs-lookup"><span data-stu-id="e8094-412">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="e8094-413">R4145: İçeriği Transfer-Encoding üstbilgisi SOAP bilgi bölümü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="e8094-413">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="e8094-414">R4146: SOAP Zarfı karakter kodlamasını UTF-8 ise Content-Transfer-Encoding üstbilgisinin değerini 8 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-414">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="e8094-415">R4147: UTF-16 karakter kodlamasını SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini ikili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-415">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="e8094-416">[XOP göre] bölüm 5,</span><span class="sxs-lookup"><span data-stu-id="e8094-416">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="e8094-417">Tür parametreleri ve R4148: Content-Type üstbilgisi medya türü uygulama/xop + xml ile SOAP1.1 bilgi bölümü içermelidir = "text/xml" ve charset</span><span class="sxs-lookup"><span data-stu-id="e8094-417">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="e8094-418">R4149: Medya türüyle Content-Type üstbilgisi SOAP 1.2 bilgi bölümü içermelidir `application/xop+xml` ve tür parametreleri = "`application/soap+xml`" ve `charset`.</span><span class="sxs-lookup"><span data-stu-id="e8094-418">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="e8094-419">XOP açıklarken `charset` parametresi için `application/xop+xml` isteğe bağlı olacak şekilde birlikte çalışabilirliğini BP 1.1 gereksinimini benzer gerektiğinde `charset` parametresi için `text/xml` medya türü.</span><span class="sxs-lookup"><span data-stu-id="e8094-419">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="e8094-420">R41410: `type` ve `charset` parametreleri SOAP 1.x bilgi bölümü Content-Type üstbilgisi mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8094-420">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="e8094-421">WCF Bitiş noktası MTOM desteği</span><span class="sxs-lookup"><span data-stu-id="e8094-421">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="e8094-422">Base64 ile kodlanmış verileri en iyi duruma getirmek için bir SOAP iletisi kodlanacak MTOM amacı budur.</span><span class="sxs-lookup"><span data-stu-id="e8094-422">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="e8094-423">Kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="e8094-423">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="e8094-424">R4151: base64 ile kodlanmış verileri içeren herhangi bir öğe bilgi öğesini en iyi duruma.</span><span class="sxs-lookup"><span data-stu-id="e8094-424">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="e8094-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] base64 ile kodlanmış verileri içeren ve uzunluğu 1024 bayt aşan öğesi bilgi öğeleri en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="e8094-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="e8094-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MTOM kullanmak üzere yapılandırılmış uç nokta her zaman MTOM olarak kodlanmış iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="e8094-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="e8094-427">Hiçbir bölümleri gereken ölçütleri karşılayan olsa bile, ileti (SOAP Zarfı içeren tek bir MIME bölümü ile bir MIME paketi olarak serileştirilmiş) hala MTOM kodlanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-427">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="e8094-428">MTOM WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="e8094-428">WS-Policy Assertion for MTOM</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e8094-429">MTOM kullanım bitiş noktası tarafından belirtmek için aşağıdaki ilke onaylama kullanır:</span><span class="sxs-lookup"><span data-stu-id="e8094-429"> uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="e8094-430">R4211: Önceki ilke onaylama bir uç nokta İlkesi konu ve gönderilen ve uç noktasından alınan tüm iletileri MTOM kullanılarak iyileştirilmiş gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8094-430">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="e8094-431">B4212: MTOM iyileştirme'yi kullanmak üzere yapılandırıldığında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint karşılık gelen iliştirilmiş ilke MTOM İlkesi onaylama ekler `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="e8094-431">B4212: When configured to use MTOM optimization, an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="e8094-432">WS güvenliği ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8094-432">Composition with WS-Security</span></span>  
 <span data-ttu-id="e8094-433">MTOM mekanizmasıdır benzer bir kodlama `text/xml` ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ikili XML.</span><span class="sxs-lookup"><span data-stu-id="e8094-433">MTOM is an encoding mechanism that is similar to `text/xml` and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary XML.</span></span> <span data-ttu-id="e8094-434">MTOM sunar doğal birleşim WS güvenliği ve diğer WS-* protokolleri: WS güvenliği kullanarak güvenli bir ileti MTOM kullanılarak iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8094-434">MTOM offers natural composition with WS-Security and other WS-* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e8094-435">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e8094-435">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="e8094-436">WCF SOAP 1.1 ileti MTOM kullanılarak kodlanmış</span><span class="sxs-lookup"><span data-stu-id="e8094-436">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="e8094-437">MTOM kullanılarak ileti WCF güvenli SOAP 1.2 kodlanmış</span><span class="sxs-lookup"><span data-stu-id="e8094-437">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="e8094-438">Bu örnekte, bir ileti MTOM ve WS-Security tarafından korunan SOAP 1.2 kullanılarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="e8094-438">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="e8094-439">Kodlama içeriğini için tanımlanan ikili parçaları `BinarySecurityToken`, `CipherValue` , `EncryptedData` karşılık gelen şifrelenmiş imza ve şifrelenmiş gövde.</span><span class="sxs-lookup"><span data-stu-id="e8094-439">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="e8094-440">Unutmayın `CipherValue` , `EncryptedKey` en iyi duruma getirme tarafından tanımlanmadı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uzunluğu sonra daha az 1024 bayt olduğundan.</span><span class="sxs-lookup"><span data-stu-id="e8094-440">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because its length is less then 1024 bytes.</span></span>  
  
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
