---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55073232"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="4a981-102">Güvenilir Mesajlaşma Protokolü sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="4a981-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="4a981-103">Bu konu, Windows Communication Foundation (WCF) uygulama ayrıntılarını WS-ReliableMessaging içermektedir. Şubat 2007 (sürüm 1.1) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a981-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="4a981-104">WCF WS-ReliableMessaging kısıtlamaları ve bu konuda açıklanan açıklamalar izler.</span><span class="sxs-lookup"><span data-stu-id="4a981-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="4a981-105">İle başlayarak WS-ReliableMessaging sürüm 1.1 protokolünü uygulandığını unutmayın [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a981-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="4a981-106">WS-ReliableMessaging protokolü WCF uygulandığına Şubat 2007 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="4a981-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="4a981-107">Kolaylık olması için konunun aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="4a981-108">Başlatan: WS güvenilir ileti sırası oluşturma başlatan istemci.</span><span class="sxs-lookup"><span data-stu-id="4a981-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="4a981-109">Yanıtlayıcı: Hizmet başlatanın isteği alır.</span><span class="sxs-lookup"><span data-stu-id="4a981-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="4a981-110">Bu belge, aşağıdaki tabloda ad alanlarını ve önekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="4a981-111">Ön eki</span><span class="sxs-lookup"><span data-stu-id="4a981-111">Prefix</span></span>|<span data-ttu-id="4a981-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4a981-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="4a981-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="4a981-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="4a981-114">netrm</span><span class="sxs-lookup"><span data-stu-id="4a981-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="4a981-115">s</span><span class="sxs-lookup"><span data-stu-id="4a981-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="4a981-116">wsa</span><span class="sxs-lookup"><span data-stu-id="4a981-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="4a981-117">wsse</span><span class="sxs-lookup"><span data-stu-id="4a981-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="4a981-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="4a981-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="4a981-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="4a981-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="4a981-120">WSP</span><span class="sxs-lookup"><span data-stu-id="4a981-120">wsp</span></span>|<span data-ttu-id="4a981-121">(WS-Policy 1.2 veya WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="4a981-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="4a981-122">İleti</span><span class="sxs-lookup"><span data-stu-id="4a981-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="4a981-123">Dizisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-123">Sequence Creation</span></span>  
 <span data-ttu-id="4a981-124">WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` iletileri güvenilir bir Mesajlaşma kurmak için sıra.</span><span class="sxs-lookup"><span data-stu-id="4a981-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="4a981-125">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="4a981-126">B1101: WCF başlatıcı olarak aynı uç nokta başvurusu kullanır `CreateSequence` iletinin `ReplyTo`, `AcksTo` ve `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="4a981-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="4a981-127">R1102: `AcksTo`, `ReplyTo` Ve `Offer/Endpoint` uç nokta başvurularının `CreateSequence` ileti octet-wise eşleşecek şekilde aynı dize temsilleri adresi değerlerle sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a981-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="4a981-128">WCF Yanıtlayıcı doğrular URI kısmı `AcksTo`, `ReplyTo` ve `Endpoint` uç nokta başvuruları özdeş bir dizisini oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="4a981-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="4a981-129">R1103: `AcksTo`, `ReplyTo` Ve `Offer/Endpoint` uç nokta başvurularının `CreateSequence` ileti başvuru parametrelerinin aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a981-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="4a981-130">WCF zorunlu değildir, ancak bu başvuruyu varsayar parametrelerinin `AcksTo`, `ReplyTo` ve `Offer/Endpoint` uç nokta başvuruda bulunan `CreateSequence` aynıdır ve başvuru parametreleri kullanan `ReplyTo` için uç nokta başvurusu onayları ve ters sıra iletileri.</span><span class="sxs-lookup"><span data-stu-id="4a981-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="4a981-131">B1104: WCF Başlatıcı isteğe bağlı oluşturmaz `Expires` veya `Offer/Expires` öğesinde `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="4a981-132">B1105: Erişirken `CreateSequence` WCF Yanıtlayıcı ileti kullanan `Expires` değerini `CreateSequence` öğesi olarak `Expires` değerini `CreateSequenceResponse` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="4a981-133">Aksi durumda, WCF Yanıtlayıcı okur ve yoksayar `Expires` ve `Offer/Expires` değerleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="4a981-134">B1106: Erişirken `CreateSequenceResponse` ileti WCF Başlatıcı okur isteğe bağlı `Expires` değer ancak bunları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="4a981-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="4a981-135">B1107: WCF Başlatıcı hem Yanıtlayıcı her zaman isteğe bağlı Oluştur `IncompleteSequenceBehavior` öğesinde `CreateSequence/Offer` ve `CreateSequenceResponse` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="4a981-136">B1108: WCF kullanan yalnızca `DiscardFollowingFirstGap` ve `NoDiscard` değerler `IncompleteSequenceBehavior` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="4a981-137">WS-ReliableMessaging yararlanan `Offer` iki oturum form bağıntılı dizileri gruplarıdır kurmak için bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="4a981-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="4a981-138">B1109: Varsa `CreateSequence` içeren bir `Offer` öğesi, tek yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt vererek bir `CreateSequenceResponse` olmadan bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="4a981-139">B1110: Güvenilir bir Mesajlaşma Yanıtlayıcı sunulan dizisi reddederse, WCF Başlatıcı yeni kurulan dizisi hataları.</span><span class="sxs-lookup"><span data-stu-id="4a981-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="4a981-140">B1111: Varsa `CreateSequence` içermeyen bir `Offer` öğe, çift yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt vererek bir `CreateSequenceRefused` hata.</span><span class="sxs-lookup"><span data-stu-id="4a981-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="4a981-141">R1112: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `[address]` özelliği `CreateSequenceResponse/Accept/AcksTo` uç nokta Başvurusu ' % s'hedef URI eşleşmelidir, `CreateSequence` ileti baytı.</span><span class="sxs-lookup"><span data-stu-id="4a981-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="4a981-142">R1113: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması, her iki dizileri için Yanıtlayıcı başlatıcıdan akan tüm iletileri aynı uç nokta başvurusu gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a981-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="4a981-143">WCF WS-ReliableMessaging Başlarıcı ve Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="4a981-144">Güvenilir oturum açmak için tek yönlü, istek-yanıt ve tam WCF WS-ReliableMessaging uygulamasını sağlar çift yönlü Mesajlaşma desenleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="4a981-145">WS-ReliableMessaging `Offer` mekanizmasını `CreateSequence` ve `CreateSequenceResponse` iki bağıntılı listesiyse serileri ve tüm uç noktalar iletisi için uygun bir oturumu Protokolü sağlar bilgisayarlarıyla oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="4a981-146">WCF oturum tutarlılığı için uçtan uca koruma dahil olmak üzere oturum için güvenlik garantisi sunduğundan, aynı hedefe yönelik aynı taraf iletiler ulaşmasını sağlamak pratik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4a981-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="4a981-147">Bu, "ardışık-yedekleme" dizisi bildirimleri, uygulama iletilerinde de sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a981-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="4a981-148">Bu nedenle, kısıtlamaları R1102 R1112 ve R1113 WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a981-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="4a981-149">Örneği bir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-149">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="4a981-150">Örneği bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a><span data-ttu-id="4a981-151">Bir dizi kapatma</span><span class="sxs-lookup"><span data-stu-id="4a981-151">Closing a Sequence</span></span>  
 <span data-ttu-id="4a981-152">WCF kullanan `CloseSequence` ve `CloseSequenceResponse` iletileri güvenilir Mesajlaşma kaynak tarafından başlatılan bir kapatma işlemi için.</span><span class="sxs-lookup"><span data-stu-id="4a981-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="4a981-153">WCF güvenilir Mesajlaşma hedef kapatma başlatılmaz ve WCF güvenilir Mesajlaşma kaynak güvenilir Mesajlaşma hedef tarafından başlatılan bir kapatma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4a981-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="4a981-154">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="4a981-155">B1201: WCF güvenilir Mesajlaşma kaynağı her zaman gönderdiği bir `CloseSequence` dizisi kapatmak için ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="4a981-156">B1202: Güvenilir Mesajlaşma kaynak göndermeden önce onay sırası iletilerin tam aralığının bekler `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="4a981-157">B1203: Güvenilir Mesajlaşma kaynağı her zaman isteğe bağlı içerir `LastMsgNumber` öğe dizisi iletileri içermediği sürece.</span><span class="sxs-lookup"><span data-stu-id="4a981-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="4a981-158">R1204: Güvenilir Mesajlaşma hedef kapatma göndererek gerçekleştirmemelidir bir `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="4a981-159">B1205: Alma bağlı bir `CloseSequence` ileti WCF güvenilir Mesajlaşma kaynak dizisi eksik olarak değerlendirir ve bir hata gönderir.</span><span class="sxs-lookup"><span data-stu-id="4a981-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="4a981-160">Örneği bir `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-160">An example of a `CloseSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a><span data-ttu-id="4a981-161">Sonlandırma sırası</span><span class="sxs-lookup"><span data-stu-id="4a981-161">Sequence Termination</span></span>  
 <span data-ttu-id="4a981-162">WCF öncelikle kullanır `TerminateSequence/TerminateSequenceResponse` tamamladıktan sonra el sıkışması `CloseSequence/CloseSequenceResponse` anlaşması.</span><span class="sxs-lookup"><span data-stu-id="4a981-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="4a981-163">WCF güvenilir Mesajlaşma hedef sonlandırma başlatılmaz ve güvenilir Mesajlaşma kaynak, hedef tarafından başlatılan bir güvenilir Mesajlaşma sonlandırma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4a981-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="4a981-164">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="4a981-165">B1301: Yalnızca WCF Başlatıcı gönderir `TerminateSequence` ileti başarıyla tamamlanmasından sonra `CloseSequence/CloseSequenceResponse` anlaşması.</span><span class="sxs-lookup"><span data-stu-id="4a981-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="4a981-166">R1302: WCF doğrular `LastMsgNumber` öğedir tutarlı tamamında `CloseSequence` ve `TerminateSequence` iletileri için belirli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4a981-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="4a981-167">Diğer bir deyişle `LastMsgNumber` değil tüm mevcut `CloseSequence` ve `TerminateSequence` iletileri veya mevcut ve tüm aynı `CloseSequence` ve `TerminateSequence` iletileri.</span><span class="sxs-lookup"><span data-stu-id="4a981-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="4a981-168">B1303: Alırken bir `TerminateSequence` sonra ileti `CloseSequence/CloseSequenceResponse` güvenilir Mesajlaşma hedef el sıkışması, yanıt veren ile bir `TerminateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="4a981-169">Güvenilir Mesajlaşma kaynak göndermeden önce son onayı olduğundan `TerminateSequence` ileti güvenilir Mesajlaşma hedef bilir olmadan emin olabilirsiniz dizisi sona ereceğini ve kaynaklara hemen geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="4a981-170">B1304: Alırken bir `TerminateSequence` öncesinde ileti `CloseSequence/CloseSequenceResponse` WCF güvenilir Mesajlaşma hedef el sıkışması, yanıt veren ile bir `TerminateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="4a981-171">Güvenilir Mesajlaşma hedef dizideki tutarsızlık olduğunu belirlerse, güvenilir Mesajlaşma hedef istemcinin alma olanağı sağlamak için kaynakları tekrar kullanılabilir hale getirme önce bir uygulamayı hedef belirtilen saat bekler son onayı.</span><span class="sxs-lookup"><span data-stu-id="4a981-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="4a981-172">Aksi halde, güvenilir Mesajlaşma hedef kaynaklar hemen geri kazanır ve uygulama hedef sıra yükselterek şüpheli ile biten gösterir `Faulted` olay.</span><span class="sxs-lookup"><span data-stu-id="4a981-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="4a981-173">Örneği bir `TerminateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-173">An example of a `TerminateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a><span data-ttu-id="4a981-174">Diziler</span><span class="sxs-lookup"><span data-stu-id="4a981-174">Sequences</span></span>  
 <span data-ttu-id="4a981-175">Dizilerine uygulama kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a981-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="4a981-176">B1401:WCF oluşturur ve erişimleri numaraları daha yüksek sıralı `xs:long`'s maksimum kapsamlı değeri, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="4a981-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="4a981-177">Örneği bir `Sequence` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="4a981-178">İstek onayı</span><span class="sxs-lookup"><span data-stu-id="4a981-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="4a981-179">WCF kullanan `AckRequested` tutma mekanizması olarak başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="4a981-180">Örneği bir `AckRequested` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="4a981-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4a981-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="4a981-182">WCF WS-Reliable Mesajlaşma sağlanan sıralı onayları için bir "ardışık" mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="4a981-183">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="4a981-184">R1601: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` üst bilgisi için hedeflenen alıcı aktarılan herhangi bir uygulama iletisi içinde eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="4a981-185">Uzak uç noktada bir paketle gönderilen erişebilir `SequenceAcknowledgement` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="4a981-186">B1602: WCF oluşturmaz `SequenceAcknowledgement` içeren üst bilgiler `Nack` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="4a981-187">WCF doğrular ve her `Nack` öğesi bir sıra numarası içeriyor, ancak Aksi halde yoksayar `Nack` öğe ve değer.</span><span class="sxs-lookup"><span data-stu-id="4a981-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="4a981-188">Örneği bir `SequenceAcknowledgement` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="4a981-189">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="4a981-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="4a981-190">Bir listesi WS-ReliableMessaging hataları WCF uygulaması için geçerli olan sınırlamalar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4a981-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="4a981-191">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4a981-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="4a981-192">B1701: WCF oluşturmaz `MessageNumberRollover` hataları.</span><span class="sxs-lookup"><span data-stu-id="4a981-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="4a981-193">B1702: Hizmet uç noktası, bağlantı sınırına ulaştığında ve yeni bağlantı işlenemiyor, SOAP 1.2 WCF iç içe bir oluşturur `CreateSequenceRefused` alt kod, hata `netrm:ConnectionLimitReached`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4a981-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="4a981-194">WS-Addressing hataları</span><span class="sxs-lookup"><span data-stu-id="4a981-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="4a981-195">WS-Addressing WS-ReliableMessaging kullandığından WCF WS-ReliableMessaging uygulama oluşturabilir ve WS-Addressing hataları iletme.</span><span class="sxs-lookup"><span data-stu-id="4a981-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="4a981-196">Bu bölüm, WCF açıkça oluşturur ve WS-ReliableMessaging katmanında iletir WS-Addressing hataları kapsar:</span><span class="sxs-lookup"><span data-stu-id="4a981-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="4a981-197">B1801:WCF oluşturur ve iletir `Message Addressing Header Required` aşağıdakilerden biri doğruysa, hata:</span><span class="sxs-lookup"><span data-stu-id="4a981-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="4a981-198">A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `MessageId` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="4a981-199">A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `ReplyTo` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="4a981-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, veya `TerminateSequenceResponse` ileti eksik bir `RelatesTo` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="4a981-201">B1802:WCF oluşturur ve iletir `Endpoint Unavailable` , dinleme bitiş noktası yoktur belirtmek için hata adresleme üstbilgilerinde incelenmesi göre sırası işleyebilir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="4a981-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="4a981-202">İletişim kuralı oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="4a981-203">WS-Addressing ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="4a981-204">WCF WS-Addressing iki sürümlerini destekler: WS-Addressing 2004/08 WS-ADDR ve W3C WS-Addressing 1.0 önerileri [WS-ADDR-CORE] ve [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="4a981-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="4a981-205">While WS-ReliableMessaging belirtimi bahsetmeleri yalnızca WS-Addressing 2004/08, onu kısıtlamaz kullanılacak WS-Addressing sürümü.</span><span class="sxs-lookup"><span data-stu-id="4a981-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="4a981-206">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a981-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="4a981-207">R2101: WS-Addressing 2004/08 hem WS-Addressing 1.0 WS-Reliable Mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a981-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="4a981-208">R2102: Belirli bir WS-ReliableMessaging dizisi veya bir çift ters dizileri kullanılarak bağıntılı boyunca bir tek WS-Addressing sürümü kullanılmalıdır `Offer` mekanizması.</span><span class="sxs-lookup"><span data-stu-id="4a981-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="4a981-209">SOAP ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-209">Composition with SOAP</span></span>  
 <span data-ttu-id="4a981-210">WCF SOAP 1.1 ve SOAP 1.2 WS-Reliable Mesajlaşma ile kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="4a981-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="4a981-211">WS-güvenlik ve WS-SecureConversation ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="4a981-212">WCF ile WS-Secure Conversation güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve oluşturma'yı kullanarak WS-ReliableMessaging dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a981-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="4a981-213">WS-ReliableMessaging 1.1 protokolü, WS-güvenlik 1.1 ve WS-Secure konuşma 1.3 Protokolü birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a981-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="4a981-214">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a981-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="4a981-215">R2301: Bir WS-ReliableMessaging dizisini bütünlüğünün yanı sıra bütünlüğünü ve tek tek iletilerin gizliliğini korumak için WS-Secure Conversation kullanılmalıdır WCF gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4a981-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="4a981-216">R2302:AWS-Secure Conversation oturumu WS-ReliableMessaging sequence(s) kurmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a981-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="4a981-217">R2303: WS-ReliableMessaging dizisi ömrü oturumunun ömrü, WS-Secure Conversation aşarsa `SecurityContextToken` kullanarak WS-Secure Conversation gerekir yenilenmiş karşılık gelen WS-Secure konuşma yenileme bağlama kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="4a981-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="4a981-218">B2304:WS-ReliableMessaging dizisi veya bir çift bağlantılı listesiyse dizileri tek bir WS-SecureConversation oturumuna bağlı her zaman.</span><span class="sxs-lookup"><span data-stu-id="4a981-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="4a981-219">R2305: WS-Secure Conversation ile oluşan, gerektiren WCF Yanıtlayıcı `CreateSequence` iletisi içeren `wsse:SecurityTokenReference` öğesi ve `wsrm:UsesSequenceSTR` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="4a981-220">Örneği bir `UsesSequenceSTR` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="4a981-221">SSL/TLS oturumlarını ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="4a981-222">WCF ile SSL/TLS oturumları oluşturma desteklemez:</span><span class="sxs-lookup"><span data-stu-id="4a981-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="4a981-223">B2401: WCF oluşturmaz `wsrm:UsesSequenceSSL` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="4a981-224">R2402: Güvenilir bir Mesajlaşma Başlatıcı değil göndermelisiniz bir `CreateSequence` ile ileti bir `wsrm:UsesSequenceSSL` WCF Yanıtlayıcı için üst bilgi.</span><span class="sxs-lookup"><span data-stu-id="4a981-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="4a981-225">WS-Policy ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a981-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="4a981-226">WCF WS-Policy iki sürümlerini destekler: WS-Policy 1.2 ve WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="4a981-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="4a981-227">WS-ReliableMessaging WS-ilke onaylama</span><span class="sxs-lookup"><span data-stu-id="4a981-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="4a981-228">WCF kullanan WS-ReliableMessaging WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özelliklerini tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="4a981-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="4a981-229">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a981-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="4a981-230">B3001: WCF ekler `wsrmn:RMAssertion` WS-Policy onaylama için `wsdl:binding` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="4a981-231">WCF destekleyen iki ek `wsdl:binding` ve `wsdl:port` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4a981-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="4a981-232">B3002: WCF hiçbir zaman oluşturur `wsp:Optional` etiketi.</span><span class="sxs-lookup"><span data-stu-id="4a981-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="4a981-233">B3003: Erişirken `wsrmp:RMAssertion` WCF WS-Policy onaylama yoksayar `wsp:Optional` etiketleyin ve WS-RM ilke zorunlu olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4a981-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="4a981-234">R3004: WCF ile SSL/TLS oturumlarını compose değil çünkü belirten ilke WCF kabul etmiyor `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="4a981-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="4a981-235">B3005: WCF her zaman oluşturur `wsrmp:DeliveryAssurance` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="4a981-236">B3006: WCF her zaman belirtir `wsrmp:ExactlyOnce` teslim güvencesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="4a981-237">B3007: WCF oluşturur ve WS-ReliableMessaging onaylama aşağıdaki özelliklerini okur ve bunlar üzerindeki denetimi WCF sağlar`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="4a981-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="4a981-238">Örneği bir `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="4a981-238">An example of a `RMAssertion`.</span></span>  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="4a981-239">Akış denetimi WS-ReliableMessaging uzantısı</span><span class="sxs-lookup"><span data-stu-id="4a981-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="4a981-240">WCF WS-ReliableMessaging genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="4a981-241">Akış denetimi etkin ayarlayarak <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="4a981-241">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="4a981-242">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a981-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="4a981-243">B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="4a981-244">B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirilmiş olsa, WCF gerektirmez bir `netrm:BufferRemaining` öğesinde `SequenceAcknowledgement` başlığı.</span><span class="sxs-lookup"><span data-stu-id="4a981-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="4a981-245">B4003: WCF güvenilir Mesajlaşma hedef kullanan `netrm:BufferRemaining` kaç yeni, iletileri göstermek için ara belleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="4a981-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="4a981-246">B4004:when güvenilir Mesajlaşma akış denetimi etkin olduğunda, WCF güvenilir Mesajlaşma kaynak değerini kullanır `netrm:BufferRemaining` kısıtlama ileti aktarım için.</span><span class="sxs-lookup"><span data-stu-id="4a981-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="4a981-247">B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile kapsamlı 4096 arasında ve 0 arasında tamsayı değerlerini okur ve `xs:int`'s `maxInclusive` 214748364 kapsamlı değeri.</span><span class="sxs-lookup"><span data-stu-id="4a981-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="4a981-248">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="4a981-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="4a981-249">Bu bölümde, WS-ReliableMessaging farklı ileti Exchange desenleri için kullanıldığında, WCF'ın davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a981-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="4a981-250">Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="4a981-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="4a981-251">Adreslenebilir olmayan Başlatıcı: Başlatıcı bir güvenlik duvarı ardında kaldığı; Yanıtlayıcı Başlatıcısı yalnızca HTTP yanıtları için ileti teslim edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a981-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="4a981-252">Başlatıcı adreslenebilir: Başlatıcı hem Yanıtlayıcı HTTP isteklerini gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantı kurulur.</span><span class="sxs-lookup"><span data-stu-id="4a981-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="4a981-253">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="4a981-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="4a981-254">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a981-254">Binding</span></span>  
 <span data-ttu-id="4a981-255">WCF bir HTTP kanalı üzerinden bir dizisi kullanırken bir yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a981-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="4a981-256">WCF HTTP isteklerini yanıtlayan gelen tüm iletileri Başlatıcı iletmek için tüm ileti başlatıcıdan Yanıtlayıcı ve HTTP yanıtları aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="4a981-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-258">WCF Başlatıcı ileten bir `CreateSequence` ileti olmadan `Offer` öğe üzerinde bir HTTP isteği ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4a981-259">WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ileti olmadan `Accept` HTTP yanıtını öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="4a981-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4a981-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="4a981-261">WCF Başlatıcı yanıtlama bir onayları tüm iletileri işleyen `CreateSequence` iletisi ve hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="4a981-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="4a981-262">WCF Yanıtlayıcı her zaman HTTP yanıtını tüm dizisi için tek başına bir bildirim gönderir ve `AckRequested` iletileri.</span><span class="sxs-lookup"><span data-stu-id="4a981-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="4a981-263">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="4a981-264">WCF Başlatıcı ileten bir `CloseSequence` bekliyor ve bir HTTP isteği iletisi `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4a981-265">WCF Yanıtlayıcı iletir `CloseSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="4a981-266">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-267">WCF Başlatıcı ileten bir `TerminateSequence` bekliyor ve bir HTTP isteği iletisi `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4a981-268">WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="4a981-269">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="4a981-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="4a981-270">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a981-270">Binding</span></span>  
 <span data-ttu-id="4a981-271">WCF sağlayan bir dizisi üzerinde kullanırken bir yönlü ileti değişim deseni gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="4a981-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4a981-272">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4a981-273">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="4a981-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="4a981-274">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-275">WCF Başlatıcı ileten bir `CreateSequence` ileti olmadan `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="4a981-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4a981-276">WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ileti olmadan `Accept` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="4a981-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="4a981-277">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="4a981-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="4a981-278">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a981-278">Binding</span></span>  
 <span data-ttu-id="4a981-279">WCF sağlayan iki kullanarak tam olarak zaman uyumsuz, çift yönlü ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="4a981-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4a981-280">Bu ileti değişim deseni ile karışık `Request/Reply`, `Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni.</span><span class="sxs-lookup"><span data-stu-id="4a981-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="4a981-281">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4a981-282">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="4a981-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="4a981-283">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-284">WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="4a981-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4a981-285">WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir dizi oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="4a981-286">Dizisi ömrü</span><span class="sxs-lookup"><span data-stu-id="4a981-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="4a981-287">WCF iki diziyi bir tam yönlü oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4a981-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="4a981-288">Bir sıralı hataları bir hata oluşturma sırasında uzak uç noktanın hem dizileri hata WCF bekliyor.</span><span class="sxs-lookup"><span data-stu-id="4a981-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="4a981-289">Bir sıralı hataları bir hataya okuma sırasında WCF hem dizileri hataları.</span><span class="sxs-lookup"><span data-stu-id="4a981-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="4a981-290">WCF giden kendi dizisi kapatın ve gelen kendi sıra üzerinde iletileri işleme devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a981-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="4a981-291">Buna karşılık, WCF gelen dizisi kapatma işlemi ve bu giden kendi sıra üzerinde iletileri göndermeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a981-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="4a981-292">İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="4a981-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="4a981-293">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a981-293">Binding</span></span>  
 <span data-ttu-id="4a981-294">WCF tek yönlü sağlar ve istek-yanıt ileti değişim deseni iki kullanarak tek HTTP kanalı serileri.</span><span class="sxs-lookup"><span data-stu-id="4a981-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="4a981-295">WCF HTTP isteklerini yanıtlayan gelen tüm iletileri Başlatıcı iletmek için tüm ileti başlatıcıdan Yanıtlayıcı ve HTTP yanıtları aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="4a981-296">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-297">WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4a981-298">WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` HTTP yanıtını öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="4a981-299">Tek yönlü mesaj</span><span class="sxs-lookup"><span data-stu-id="4a981-299">One-way Message</span></span>  
 <span data-ttu-id="4a981-300">WCF Başlatıcı bir tek yönlü mesaj alışverişi başarıyla tamamlamak için bir istek sırası iletisi HTTP isteğini iletir ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="4a981-301">`SequenceAcknowledgement` Aktarılan iletiyi kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a981-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="4a981-302">WCF Yanıtlayıcı bir bildirim, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt.</span><span class="sxs-lookup"><span data-stu-id="4a981-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="4a981-303">İki şekilde iletileri</span><span class="sxs-lookup"><span data-stu-id="4a981-303">Two Way Messages</span></span>  
 <span data-ttu-id="4a981-304">İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteğini bir istek sırası iletisi aktarır ve HTTP yanıtını yanıt sırası iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="4a981-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="4a981-305">Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi sıkan aktarılan.</span><span class="sxs-lookup"><span data-stu-id="4a981-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="4a981-306">WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt.</span><span class="sxs-lookup"><span data-stu-id="4a981-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="4a981-307">Tek yönlü iletileri varlığını ve uygulama yanıt zamanlaması nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası ile hiçbir bağıntısı vardır.</span><span class="sxs-lookup"><span data-stu-id="4a981-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="4a981-308">Yanıt yeniden deneniyor</span><span class="sxs-lookup"><span data-stu-id="4a981-308">Retrying Replies</span></span>  
 <span data-ttu-id="4a981-309">WCF için iki yönlü ileti exchange Protokolü bağıntısı HTTP isteği-yanıt bağıntısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="4a981-310">Bu nedenle, WCF Başlatıcı istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor durdurmaz ancak yerine ne zaman HTTP yanıtı yürüten bir `SequenceAcknowledgement`, uygulama yanıtı veya hata.</span><span class="sxs-lookup"><span data-stu-id="4a981-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="4a981-311">WCF Yanıtlayıcı yanıt, yanıt bağıntılı isteğin HTTP yanıtını yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="4a981-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="4a981-312">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="4a981-313">Tüm yanıt sırası iletileri ve tüm one-way isteğini sırası iletileri için onayları aldıktan sonra WCF Başlatıcı ileten bir `CloseSequence` iletisi için HTTP isteğinde istek sırası ve bekliyor `CloseSequenceResponse` HTTP yanıtını.</span><span class="sxs-lookup"><span data-stu-id="4a981-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="4a981-314">İstek sırası örtük olarak kapatılmadan yanıt sırası kapatır.</span><span class="sxs-lookup"><span data-stu-id="4a981-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="4a981-315">WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `CloseSequence` iletisi ve yanıt sırası yok bir `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="4a981-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="4a981-316">Tüm yanıtlar onaylanmalarını ve iletir WCF Yanıtlayıcı sağlar `CloseSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="4a981-317">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-318">Alma sonra `CloseSequenceResponse` WCF Başlatıcı ileti iletir bir `TerminateSequence` iletisi için HTTP isteğinde istek sırası ve bekliyor `TerminateSequenceResponse` HTTP yanıtını.</span><span class="sxs-lookup"><span data-stu-id="4a981-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="4a981-319">Gibi `CloseSequence` değişimi, örtük olarak istek sırası sonlandırma yanıt sırası sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4a981-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="4a981-320">WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `TerminateSequence` iletisi ve yanıt sırası yok bir `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="4a981-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="4a981-321">WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="4a981-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="4a981-322">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="4a981-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="4a981-323">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a981-323">Binding</span></span>  
 <span data-ttu-id="4a981-324">WCF sağlayan iki kullanarak istek-yanıt ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="4a981-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4a981-325">Bu ileti değişim deseni ile karışık `Duplex, Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni.</span><span class="sxs-lookup"><span data-stu-id="4a981-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="4a981-326">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a981-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4a981-327">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="4a981-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="4a981-328">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4a981-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="4a981-329">WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="4a981-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4a981-330">WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir dizi oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a981-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="4a981-331">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="4a981-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="4a981-332">Aşağıdaki, tüm ilişkili istekleri ve yanıtları için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4a981-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="4a981-333">WCF sağlar, tüm uygulama istek iletileri ayı bir `ReplyTo` uç nokta başvurusu ve `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="4a981-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="4a981-334">WCF her uygulama istek iletisi kullanıcının yerel uç nokta başvurusu geçerli `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4a981-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="4a981-335">Yerel uç nokta başvurusu `CreateSequence` iletinin `ReplyTo` başlatıcısının ve `CreateSequence` iletinin `To` Yanıtlayıcı için.</span><span class="sxs-lookup"><span data-stu-id="4a981-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="4a981-336">WCF sağlar, gelen istek iletisi ayı bir `MessageId` ve `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4a981-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="4a981-337">WCF sağlar `ReplyTo` daha önce tanımlanan tüm uygulama istek iletisi uç nokta Başvurusu'nın URI eşleşen yerel uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="4a981-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="4a981-338">WCF sağlar tüm yanıtlar doğru ayı `RelatesTo` ve `To` aşağıdaki üst bilgileri `wsa` bağıntı kuralları istek/yanıt.</span><span class="sxs-lookup"><span data-stu-id="4a981-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
