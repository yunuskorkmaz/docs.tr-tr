---
description: 'Daha fazla bilgi edinin: güvenilir mesajlaşma Protokolü sürüm 1,1'
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 07d1ffb4347c7481944bc5d1c2ccef0940f18071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632912"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="ff83a-103">Güvenilir Mesajlaşma Protokolü sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="ff83a-103">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="ff83a-104">Bu konuda, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-ReliableMessaging Şubat 2007 (sürüm 1,1) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntıları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-104">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="ff83a-105">WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-ReliableMessaging belirtimini izler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-105">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="ff83a-106">WS-ReliableMessaging sürüm 1,1 protokolünün .NET Framework 3,5 ' den başlayarak uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff83a-106">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="ff83a-107">WS-ReliableMessaging Şubat 2007 protokolü, tarafından WCF 'de uygulanır <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="ff83a-107">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="ff83a-108">Kolaylık olması için, konusu aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="ff83a-108">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="ff83a-109">Başlatıcı: WS-Reliable Ileti sırası oluşturmayı Başlatan istemci.</span><span class="sxs-lookup"><span data-stu-id="ff83a-109">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="ff83a-110">Yanıtlayıcı: başlatıcısının isteklerini alan hizmet.</span><span class="sxs-lookup"><span data-stu-id="ff83a-110">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="ff83a-111">Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-111">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="ff83a-112">Ön ek</span><span class="sxs-lookup"><span data-stu-id="ff83a-112">Prefix</span></span>|<span data-ttu-id="ff83a-113">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ff83a-113">Namespace</span></span>|
|-|-|
|<span data-ttu-id="ff83a-114">WSRM</span><span class="sxs-lookup"><span data-stu-id="ff83a-114">wsrm</span></span>|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|<span data-ttu-id="ff83a-115">Netra</span><span class="sxs-lookup"><span data-stu-id="ff83a-115">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="ff83a-116">s</span><span class="sxs-lookup"><span data-stu-id="ff83a-116">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="ff83a-117">WSA</span><span class="sxs-lookup"><span data-stu-id="ff83a-117">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="ff83a-118">WSO</span><span class="sxs-lookup"><span data-stu-id="ff83a-118">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|<span data-ttu-id="ff83a-119">wsrmp</span><span class="sxs-lookup"><span data-stu-id="ff83a-119">wsrmp</span></span>|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|<span data-ttu-id="ff83a-120">netrmp</span><span class="sxs-lookup"><span data-stu-id="ff83a-120">netrmp</span></span>|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|<span data-ttu-id="ff83a-121">WSP</span><span class="sxs-lookup"><span data-stu-id="ff83a-121">wsp</span></span>|<span data-ttu-id="ff83a-122">(WS-Policy 1,2 ya da WS-Policy 1,5)</span><span class="sxs-lookup"><span data-stu-id="ff83a-122">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="ff83a-123">Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="ff83a-123">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="ff83a-124">Sıra oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff83a-124">Sequence Creation</span></span>

<span data-ttu-id="ff83a-125">WCF `CreateSequence` , `CreateSequenceResponse` güvenilir bir mesajlaşma sırası oluşturmak için ve iletilerini uygular.</span><span class="sxs-lookup"><span data-stu-id="ff83a-125">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="ff83a-126">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-126">The following constraints apply:</span></span>

- <span data-ttu-id="ff83a-127">B1101: WCF başlatıcısı, `CreateSequence` ileti `ReplyTo` `AcksTo` ve ile aynı uç nokta başvurusunu kullanır `Offer/Endpoint` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-127">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="ff83a-128">R1102: `AcksTo` `ReplyTo` `Offer/Endpoint` ileti içindeki ve uç nokta başvurularının, `CreateSequence` sekizli temelinde eşleşecek şekilde özdeş dize gösterimlerine sahip adres değerleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-128">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="ff83a-129">WCF Yanıtlayıcı, `AcksTo` `ReplyTo` `Endpoint` bir sıra oluşturmadan önce ve uç nokta başvurularının URI bölümünün özdeş olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="ff83a-129">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="ff83a-130">R1103: `AcksTo` `ReplyTo` `Offer/Endpoint` ileti içindeki ve uç nokta başvuruları `CreateSequence` aynı başvuru parametreleri kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-130">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="ff83a-131">WCF zorunlu değildir, ancak ' ın başvuru parametrelerinin `AcksTo` `ReplyTo` ve `Offer/Endpoint` bitiş noktası başvurularının aynı olduğunu varsayar `CreateSequence` ve, `ReplyTo` bildirimlerin ve listesiyse iletileri için uç nokta başvurusundan başvuru parametrelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-131">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="ff83a-132">B1104: WCF Başlatıcısı `Expires` ileti içinde isteğe bağlı veya öğe oluşturmaz `Offer/Expires` `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-132">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="ff83a-133">B1105: `CreateSequence` iletiye erişirken, WCF Yanıtlayıcı öğesindeki `Expires` değeri `CreateSequence` `Expires` öğesindeki değer olarak kullanır `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-133">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="ff83a-134">Aksi takdirde, WCF Yanıtlayıcı ve değerlerini okur ve `Expires` yoksayar `Offer/Expires` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-134">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="ff83a-135">B1106: `CreateSequenceResponse` iletiye erişirken, WCF başlatıcısı isteğe bağlı değeri okur, `Expires` ancak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-135">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="ff83a-136">B1107: WCF başlatıcısı ve Yanıtlayıcı her zaman `IncompleteSequenceBehavior` ve öğelerinde isteğe bağlı öğesini oluşturur `CreateSequence/Offer` `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-136">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="ff83a-137">B1108: WCF yalnızca `DiscardFollowingFirstGap` `NoDiscard` öğesi içindeki ve değerlerini kullanır `IncompleteSequenceBehavior` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-137">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="ff83a-138">WS-ReliableMessaging, `Offer` bir oturum oluşturan iki dönüştürüce bağıntılı diziyi oluşturmak için mekanizmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-138">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="ff83a-139">B1109: `CreateSequence` bir öğesi varsa `Offer` , WCF Yanıtlayıcının bir öğesi olmadan bir ile yanıt vererek sunulan sırayı reddettiğini bir şekilde alır `CreateSequenceResponse` `Accept` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-139">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="ff83a-140">B1110: güvenilir bir mesajlaşma Yanıtlayıcısı sunulan sırayı reddederse, WCF başlatıcısı yeni oluşturulan sırayı hata.</span><span class="sxs-lookup"><span data-stu-id="ff83a-140">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="ff83a-141">B1111: `CreateSequence` bir `Offer` öğesi içermiyorsa, ıkı yönlü WCF Yanıtlayıcısı bir hatayla yanıt vererek sunulan sırayı reddeder `CreateSequenceRefused` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-141">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="ff83a-142">R1112: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `[address]` `CreateSequenceResponse/Accept/AcksTo` uç nokta başvurusunun özelliği `CreateSequence` byte için ileti baytının hedef URI 'siyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-142">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="ff83a-143">R1113: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , her iki sıranın üzerindeki tüm iletilerin aynı uç nokta başvurusuna gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-143">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="ff83a-144">WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-ReliableMessaging kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-144">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="ff83a-145">WCF WS-ReliableMessaging uygulama, tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-145">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="ff83a-146">`Offer`Ve üzerindeki WS-ReliableMessaging mekanizması `CreateSequence` , `CreateSequenceResponse` iki bağıntılı dönüştürme sırası oluşturmanıza ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-146">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="ff83a-147">WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe ulaşmasını sağlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-147">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="ff83a-148">Bu Ayrıca, uygulama iletilerinde "Piggy-," sıralı bildirimleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-148">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="ff83a-149">Bu nedenle, R1102, R1112 ve R1113 kısıtlamaları WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-149">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="ff83a-150">`CreateSequence`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-150">An example of a `CreateSequence` message.</span></span>

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

<span data-ttu-id="ff83a-151">`CreateSequenceResponse`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-151">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="closing-a-sequence"></a><span data-ttu-id="ff83a-152">Bir diziyi kapatma</span><span class="sxs-lookup"><span data-stu-id="ff83a-152">Closing a Sequence</span></span>

<span data-ttu-id="ff83a-153">WCF, `CloseSequence` `CloseSequenceResponse` güvenilir bir mesajlaşma kaynağı tarafından başlatılan kapatmalar için ve iletilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-153">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="ff83a-154">WCF güvenilir mesajlaşma hedefi kapatmaları başlatmaz ve WCF güvenilir mesajlaşma kaynağı, güvenilir mesajlaşma hedefi ile başlatılan bir kapanışı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ff83a-154">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="ff83a-155">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-155">The following constraints apply:</span></span>

- <span data-ttu-id="ff83a-156">B1201: WCF güvenilir mesajlaşma kaynağı, `CloseSequence` diziyi kapatmak için her zaman bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-156">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="ff83a-157">B1202: güvenilir mesajlaşma kaynağı iletiyi göndermeden önce tam dizi iletilerinin onay istemini bekler `CloseSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-157">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="ff83a-158">B1203: güvenilir mesajlaşma kaynağı, dizi ileti içermiyorsa her zaman isteğe bağlı `LastMsgNumber` öğeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-158">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="ff83a-159">R1204: güvenilir mesajlaşma hedefi bir ileti göndererek kapatmaları başlatmamalıdır `CloseSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-159">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="ff83a-160">B1205: bir ileti alındıktan sonra `CloseSequence` , WCF güvenilir mesajlaşma kaynağı, diziyi tamamlanmamış olarak değerlendirir ve bir hata gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-160">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="ff83a-161">`CloseSequence`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-161">An example of a `CloseSequence` message.</span></span>

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
```

<span data-ttu-id="ff83a-162">Örnek `CloseSequenceResponse` ileti:</span><span class="sxs-lookup"><span data-stu-id="ff83a-162">Example `CloseSequenceResponse` message:</span></span>

```xml
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

### <a name="sequence-termination"></a><span data-ttu-id="ff83a-163">Sıra sonlandırma</span><span class="sxs-lookup"><span data-stu-id="ff83a-163">Sequence Termination</span></span>

<span data-ttu-id="ff83a-164">WCF öncelikle `TerminateSequence/TerminateSequenceResponse` el sıkışma tamamlandıktan sonra el sıkışmasını kullanır `CloseSequence/CloseSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-164">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="ff83a-165">WCF güvenilir mesajlaşma hedefi sonlandırmayı başlatmaz ve güvenilir mesajlaşma kaynağı, güvenilir bir mesajlaşma hedefi tarafından başlatılan sonlandırmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ff83a-165">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="ff83a-166">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-166">The following constraints apply:</span></span>

- <span data-ttu-id="ff83a-167">B1301: WCF başlatıcısı yalnızca `TerminateSequence` el sıkışma başarıyla tamamlandıktan sonra iletiyi gönderir `CloseSequence/CloseSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-167">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="ff83a-168">R1302: WCF, `LastMsgNumber` `CloseSequence` `TerminateSequence` belirtilen bir sıra için, öğenin tüm ve iletileri arasında tutarlı olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="ff83a-168">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="ff83a-169">Bu, `LastMsgNumber` tüm `CloseSequence` ve `TerminateSequence` iletilerde bulunmayan ya da tüm `CloseSequence` ve iletilerle aynı `TerminateSequence` olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-169">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="ff83a-170">B1303: `TerminateSequence` el sıkışma sonrasında bir ileti alındığında `CloseSequence/CloseSequenceResponse` , güvenilir mesajlaşma hedefi bir iletiyle yanıt verir `TerminateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-170">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ff83a-171">Güvenilir Mesajlaşma kaynağında iletiyi göndermeden önce son onay bulunduğundan `TerminateSequence` , güvenilir mesajlaşma hedefi, dizinin bittiğini şüpheli olmadan bilir ve kaynakları hemen geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-171">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="ff83a-172">B1304: `TerminateSequence` El sıkışmadan önce bir ileti alındığında `CloseSequence/CloseSequenceResponse` , WCF güvenilir mesajlaşma hedefi bir iletiyle yanıt verir `TerminateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-172">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ff83a-173">Güvenilir Mesajlaşma hedefi dizide herhangi bir tutarsızlık olmadığını belirlerse, güvenilir mesajlaşma hedefi, istemcinin son onayı almasına izin vermek için, geri kazanma kaynaklarından önce uygulama hedefi belirtilen bir süre bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-173">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="ff83a-174">Aksi takdirde, güvenilir mesajlaşma hedefi geri kazanır kaynakları hemen ve olay, etkinliğin bir hata vererek şüpheli şekilde sona erdiğini uygulamanın hedefini gösterir `Faulted` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-174">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="ff83a-175">`TerminateSequence`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-175">An example of a `TerminateSequence` message.</span></span>

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
```

<span data-ttu-id="ff83a-176">Örnek `TerminateSequenceResponse` ileti:</span><span class="sxs-lookup"><span data-stu-id="ff83a-176">Example `TerminateSequenceResponse` message:</span></span>

```xml
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

### <a name="sequences"></a><span data-ttu-id="ff83a-177">Diziler</span><span class="sxs-lookup"><span data-stu-id="ff83a-177">Sequences</span></span>

<span data-ttu-id="ff83a-178">Diziler için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-178">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="ff83a-179">B1401: WCF `xs:long` , en yüksek kapsamlı değer olan 9223372036854775807 ' den fazla olmayan sıra numarası üretir ve erişir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-179">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="ff83a-180">`Sequence`Üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-180">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="ff83a-181">İstek onayı</span><span class="sxs-lookup"><span data-stu-id="ff83a-181">Request Acknowledgement</span></span>

<span data-ttu-id="ff83a-182">WCF `AckRequested` üstbilgiyi etkin tut mekanizması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-182">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="ff83a-183">`AckRequested`Üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-183">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="ff83a-184">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ff83a-184">SequenceAcknowledgement</span></span>

<span data-ttu-id="ff83a-185">WCF, WS-Reliable mesajlaşma 'da sunulan sıra bildirimleri için bir "Piggy-Back" mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-185">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="ff83a-186">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-186">The following constraints apply:</span></span>

- <span data-ttu-id="ff83a-187">R1601: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `SequenceAcknowledgement` üst bilgi, istenen alıcıya iletilen herhangi bir uygulama iletisine dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-187">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="ff83a-188">Uzak uç noktanın, bir pıof tarafından desteklenen bir üstbilgiye erişebilmesi gerekir `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-188">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ff83a-189">B1602: WCF `SequenceAcknowledgement` öğeleri içeren üst bilgiler oluşturmaz `Nack` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-189">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="ff83a-190">WCF her `Nack` bir öğenin bir sıra numarası içerdiğini doğrular, aksi takdirde `Nack` öğe ve değeri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-190">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="ff83a-191">`SequenceAcknowledgement`Üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-191">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="ff83a-192">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="ff83a-192">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="ff83a-193">Aşağıda, WS-ReliableMessaging hatalarının WCF uygulaması için uygulanan kısıtlamaların bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-193">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="ff83a-194">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-194">The following constraints apply:</span></span>

- <span data-ttu-id="ff83a-195">B1701: WCF `MessageNumberRollover` hata oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-195">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="ff83a-196">B1702: SOAP 1,2 üzerinde, hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, WCF `CreateSequenceRefused` `netrm:ConnectionLimitReached` Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş bir hata alt kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff83a-196">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="ff83a-197">WS-Addressing hataları</span><span class="sxs-lookup"><span data-stu-id="ff83a-197">WS-Addressing Faults</span></span>

<span data-ttu-id="ff83a-198">WS-ReliableMessaging WS-Addressing kullandığından, WCF WS-ReliableMessaging uygulama WS-Addressing hataları oluşturabilir ve iletebilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-198">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="ff83a-199">Bu bölümde, WCF 'nin WS-ReliableMessaging katmanında açıkça oluşturduğu ve ilettiği WS-Addressing hataları ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ff83a-199">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="ff83a-200">B1801: WCF, `Message Addressing Header Required` aşağıdakilerden biri doğru olduğunda hatayı oluşturur ve iletir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-200">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="ff83a-201">Bir `CreateSequence` `CloseSequence` veya `TerminateSequence` iletisinde `MessageId` üstbilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="ff83a-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="ff83a-202">Bir `CreateSequence` `CloseSequence` veya `TerminateSequence` iletisinde `ReplyTo` üstbilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="ff83a-202">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="ff83a-203">Bir `CreateSequenceResponse` , `CloseSequenceResponse` veya `TerminateSequenceResponse` iletisinde `RelatesTo` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="ff83a-203">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="ff83a-204">B1802: WCF hatayı üretir ve iletir `Endpoint Unavailable` . Bu, iletideki adresleme üstbilgilerinin incelenmesi temelinde diziyi işleyebilmesinin bir uç nokta dinleme olmadığını gösterir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-204">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="ff83a-205">Protokol oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff83a-205">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="ff83a-206">WS-Addressing oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff83a-206">Composition with WS-Addressing</span></span>

<span data-ttu-id="ff83a-207">WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="ff83a-207">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="ff83a-208">WS-ReliableMessaging belirtimi yalnızca WS-Addressing 2004/08 ' i bahsetirken, WS-Addressing sürümü kullanılmak üzere kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-208">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="ff83a-209">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-209">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ff83a-210">R2101: WS-Addressing 2004/08 ve WS-Addressing 1,0, WS-Reliable mesajlaşma ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-210">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="ff83a-211">R2102: tek bir WS-Addressing, belirli bir WS-ReliableMessaging sırasının tamamında ya da mekanizma kullanılarak bağıntılı bir convero dizileri çifti kullanılmalıdır `Offer` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-211">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="ff83a-212">SOAP ile bileşim</span><span class="sxs-lookup"><span data-stu-id="ff83a-212">Composition with SOAP</span></span>

<span data-ttu-id="ff83a-213">WCF, WS-Reliable mesajlaşma ile hem SOAP 1,1 hem de SOAP 1,2 kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-213">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="ff83a-214">WS-Security ve WS-SecureConversation oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff83a-214">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="ff83a-215">WCF, güvenli aktarım (HTTPS), WS-güvenlik ile bileşim ve WS-Secure konuşmayla bileşim kullanarak WS-ReliableMessaging dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-215">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="ff83a-216">WS-ReliableMessaging 1,1 protokolü WS-Security 1,1 ve WS-Secure konuşma 1,3 Protokolü birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-216">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="ff83a-217">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-217">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ff83a-218">R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak bir WS-ReliableMessaging sırasının bütünlüğünü korumak Için, WCF WS-Secure konuşmanın kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-218">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="ff83a-219">R2302: AWS-Secure konuşma oturumunun WS-ReliableMessaging sıra (ler) oluşturmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-219">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="ff83a-220">R2303: WS-ReliableMessaging dizisi ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, `SecurityContextToken` WS-Secure konuşması kullanılarak belirlenen, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-220">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="ff83a-221">B2304: WS-ReliableMessaging dizisi veya bir çift bağıntılı dönüştürme dizileri her zaman tek bir WS-SecureConversation oturumuna bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-221">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="ff83a-222">R2305: WS-Secure konuşmasıyla birlikte kullanıldığında, WCF Yanıtlayıcı `CreateSequence` iletinin `wsse:SecurityTokenReference` öğesini ve başlığını içermesini gerektirir `wsrm:UsesSequenceSTR` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-222">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="ff83a-223">`UsesSequenceSTR`Üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="ff83a-223">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="ff83a-224">SSL/TLS oturumlarıyla bileşim</span><span class="sxs-lookup"><span data-stu-id="ff83a-224">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="ff83a-225">WCF, SSL/TLS oturumları ile oluşturmayı desteklemez:</span><span class="sxs-lookup"><span data-stu-id="ff83a-225">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="ff83a-226">B2401: WCF `wsrm:UsesSequenceSSL` üstbilgiyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-226">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="ff83a-227">R2402: güvenilir bir mesajlaşma Başlatıcısı `CreateSequence` , `wsrm:UsesSequenceSSL` bir WCF Yanıtlayıcının üst bilgisine sahip bir ileti göndermemelidir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-227">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="ff83a-228">WS-Policy oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff83a-228">Composition with WS-Policy</span></span>

<span data-ttu-id="ff83a-229">WCF iki WS-Policy sürümünü destekler: WS-Policy 1,2 ve WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="ff83a-229">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="ff83a-230">WS-ReliableMessaging WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="ff83a-230">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="ff83a-231">WCF, `wsrm:RMAssertion` uç nokta özelliklerini anlatmak için WS-ReliableMessaging WS-Policy onaylama kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-231">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="ff83a-232">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-232">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ff83a-233">B3001: WCF `wsrmn:RMAssertion` öğelere WS-Policy onay ekler `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-233">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="ff83a-234">WCF her iki Eki `wsdl:binding` ve `wsdl:port` öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-234">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="ff83a-235">B3002: WCF hiçbir şekilde `wsp:Optional` etiket oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-235">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="ff83a-236">B3003: `wsrmp:RMAssertion` WS-Policy assertion 'a erişirken, WCF `wsp:Optional` etiketi YOKSAYAR ve WS-RM ilkesini zorunlu olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-236">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="ff83a-237">R3004: WCF, SSL/TLS oturumları ile oluşturulmadığından, WCF tarafından belirten ilkeyi kabul etmez `wsrmp:SequenceTransportSecurity` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-237">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="ff83a-238">B3005: WCF her zaman `wsrmp:DeliveryAssurance` öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff83a-238">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="ff83a-239">B3006: WCF her zaman `wsrmp:ExactlyOnce` Teslimat güvencesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-239">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="ff83a-240">B3007: WCF WS-ReliableMessaging onaylama işlemi için aşağıdaki özellikleri oluşturup okur ve WCF üzerinde denetim sağlar `ReliableSessionBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="ff83a-240">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="ff83a-241">Bir örneği `RMAssertion` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-241">An example of a `RMAssertion`.</span></span>

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

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="ff83a-242">Akış denetim WS-ReliableMessaging uzantısı</span><span class="sxs-lookup"><span data-stu-id="ff83a-242">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="ff83a-243">WCF, sıralı ileti akışı üzerinde isteğe bağlı ek daha sıkı denetim sağlamak için WS-ReliableMessaging genişletilebilirliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-243">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="ff83a-244">Akış denetimi <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği olarak ayarlanarak etkinleştirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-244">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="ff83a-245">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-245">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ff83a-246">B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF, `netrm:BufferRemaining` `SequenceAcknowledgement` Aşağıdaki örnekte gösterildiği gibi, üstbilginin öğe genişletilebilirliği içinde bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff83a-246">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="ff83a-247">B4002: güvenilir mesajlaşma akışı denetimi etkin olsa bile, WCF `netrm:BufferRemaining` üst bilgide bir öğe gerektirmez `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-247">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ff83a-248">B4003: WCF güvenilir mesajlaşma hedefi `netrm:BufferRemaining` , kaç yeni iletinin arabelleğe alınacağını göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-248">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="ff83a-249">B4004: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF güvenilir mesajlaşma kaynağı `netrm:BufferRemaining` ileti aktarımını azaltmak için değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-249">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="ff83a-250">B4005: WCF `netrm:BufferRemaining` , dahil 0 ve 4096 arasında tamsayı değerler üretir ve 0 214748364 ile arasında bir tamsayı değeri okur `xs:int` `maxInclusive` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-250">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="ff83a-251">İleti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="ff83a-251">Message Exchange Patterns</span></span>

<span data-ttu-id="ff83a-252">Bu bölümde, farklı Ileti değişimi desenleri için WS-ReliableMessaging kullanıldığında WCF 'nin davranışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-252">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="ff83a-253">Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ff83a-253">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="ff83a-254">Adreslenebilir Başlatıcı: Başlatıcı bir güvenlik duvarının arkasında; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-254">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="ff83a-255">Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-255">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="ff83a-256">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff83a-256">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ff83a-257">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff83a-257">Binding</span></span>

<span data-ttu-id="ff83a-258">WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-258">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="ff83a-259">WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-259">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ff83a-260">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-260">CreateSequence Exchange</span></span>

<span data-ttu-id="ff83a-261">WCF Başlatıcısı `CreateSequence` http isteğinde hiçbir öğe içermeyen bir ileti iletir `Offer` ve `CreateSequenceResponse` http yanıtında ileti bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-261">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ff83a-262">WCF Yanıtlayıcı bir sıra oluşturur ve `CreateSequenceResponse` ILETIYI `Accept` http yanıtında hiçbir öğe olmadan iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-262">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="ff83a-263">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ff83a-263">SequenceAcknowledgement</span></span>

<span data-ttu-id="ff83a-264">WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri işler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-264">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="ff83a-265">WCF Yanıtlayıcı her zaman HTTP yanıtında tüm sıra ve iletilere tek başına bir onay aktarır `AckRequested` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-265">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ff83a-266">CloseSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-266">CloseSequence Exchange</span></span>

<span data-ttu-id="ff83a-267">WCF Başlatıcısı `CloseSequence` HTTP isteğine bir ileti iletir ve `CreateSequenceResponse` http yanıtında ileti bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-267">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ff83a-268">WCF Yanıtlayıcı `CloseSequenceResponse` ILETIYI http yanıtında iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-268">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ff83a-269">TerminateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-269">TerminateSequence Exchange</span></span>

<span data-ttu-id="ff83a-270">WCF Başlatıcısı `TerminateSequence` HTTP isteğine bir ileti iletir ve `TerminateSequenceResponse` http yanıtında ileti bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-270">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ff83a-271">WCF Yanıtlayıcı `TerminateSequenceResponse` ILETIYI http yanıtında iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-271">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="ff83a-272">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff83a-272">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ff83a-273">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff83a-273">Binding</span></span>

<span data-ttu-id="ff83a-274">WCF, tek yönlü bir ileti değişim modelini bir gelen ve bir giden HTTP kanalı üzerinden tek bir sıra kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-274">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ff83a-275">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-275">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ff83a-276">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-276">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ff83a-277">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-277">CreateSequence Exchange</span></span>

<span data-ttu-id="ff83a-278">WCF başlatıcısı, `CreateSequence` http isteğinde hiçbir öğe bulunmayan bir ileti iletir `Offer` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-278">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ff83a-279">WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` iletiyi `Accept` bir http isteği üzerinde hiçbir öğe olmadan iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-279">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="ff83a-280">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff83a-280">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ff83a-281">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff83a-281">Binding</span></span>

<span data-ttu-id="ff83a-282">WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz, iki yönlü bir ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-282">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ff83a-283">Bu ileti değişim `Request/Reply` `Addressable` şekli, Başlatıcı ileti değişim düzeniyle sınırlı bir şekilde karışık olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-283">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ff83a-284">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-284">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ff83a-285">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ff83a-286">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-286">CreateSequence Exchange</span></span>

<span data-ttu-id="ff83a-287">WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi ile bir ileti iletir `Offer` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-287">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ff83a-288">WCF Yanıtlayıcı `CreateSequence` öğesinin bir öğesi olmasını sağlar `Offer` , sonra bir dizi oluşturur ve `CreateSequenceResponse` iletiyi bir öğesi ile iletir `Accept` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-288">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="ff83a-289">Sıra ömrü</span><span class="sxs-lookup"><span data-stu-id="ff83a-289">Sequence Lifetime</span></span>

<span data-ttu-id="ff83a-290">WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-290">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="ff83a-291">Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-291">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="ff83a-292">Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-292">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="ff83a-293">WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-293">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="ff83a-294">Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-294">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="ff83a-295">Request-Reply ve tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff83a-295">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ff83a-296">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff83a-296">Binding</span></span>

<span data-ttu-id="ff83a-297">WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-297">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="ff83a-298">WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-298">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ff83a-299">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-299">CreateSequence Exchange</span></span>

<span data-ttu-id="ff83a-300">WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi olan bir ileti iletir `Offer` ve `CreateSequenceResponse` http yanıtında ileti bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-300">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ff83a-301">WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` ILETIYI `Accept` http yanıtında bir öğe ile iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-301">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="ff83a-302">Tek yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="ff83a-302">One-way Message</span></span>

<span data-ttu-id="ff83a-303">Tek yönlü bir ileti değişimini başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına bir ileti alır `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-303">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="ff83a-304">, `SequenceAcknowledgement` İletilen iletiyi kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-304">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="ff83a-305">WCF Yanıtlayıcı, isteği bir onaylama, hata ya da boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-305">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="ff83a-306">İki yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="ff83a-306">Two Way Messages</span></span>

<span data-ttu-id="ff83a-307">İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-307">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="ff83a-308">Yanıt, `SequenceAcknowledgement` iletilen istek sırası iletisini bildiren bir ileti taşımalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-308">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="ff83a-309">WCF Yanıtlayıcı, isteği bir uygulama Yanıtla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-309">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="ff83a-310">Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.</span><span class="sxs-lookup"><span data-stu-id="ff83a-310">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="ff83a-311">Yanıtları yeniden deneme</span><span class="sxs-lookup"><span data-stu-id="ff83a-311">Retrying Replies</span></span>

<span data-ttu-id="ff83a-312">WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-312">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="ff83a-313">Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir `SequenceAcknowledgement` , uygulama yanıtı veya hata taşımadığında bir istek sırası iletisini yeniden denemeyi durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="ff83a-313">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="ff83a-314">WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP yanıtında yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="ff83a-314">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ff83a-315">CloseSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-315">CloseSequence Exchange</span></span>

<span data-ttu-id="ff83a-316">Tüm yanıt sırası iletilerini ve tüm tek yönlü istek sırası iletilerini aldıktan sonra, WCF Başlatıcısı `CloseSequence` istek sırası için BIR http isteği iletisi iletir ve `CloseSequenceResponse` http yanıtı üzerinde bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-316">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ff83a-317">İstek dizisinin kapatılması, yanıt sırasını örtük olarak kapatır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-317">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="ff83a-318">Bu, WCF başlatıcısının ileti üzerine yanıt sırasının son halini içerdiği `SequenceAcknowledgement` `CloseSequence` ve yanıt sırasının bir Exchange 'e sahip olmadığı anlamına gelir `CloseSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-318">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="ff83a-319">WCF Yanıtlayıcı tüm yanıtların kabul edilmesini sağlar ve `CloseSequenceResponse` ILETIYI http yanıtında iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-319">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ff83a-320">TerminateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-320">TerminateSequence Exchange</span></span>

<span data-ttu-id="ff83a-321">İleti alındıktan sonra `CloseSequenceResponse` , WCF Başlatıcısı `TerminateSequence` istek sırası IÇIN bir HTTP isteğine bir ileti ILETIR ve `TerminateSequenceResponse` http yanıtı üzerinde bekler.</span><span class="sxs-lookup"><span data-stu-id="ff83a-321">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ff83a-322">Exchange gibi `CloseSequence` , istek dizisinin sonlandırılması yanıt sırasını örtük olarak sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-322">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="ff83a-323">Bu, WCF başlatıcısının ileti üzerine yanıt sırasının son halini içerdiği `SequenceAcknowledgement` `TerminateSequence` ve yanıt sırasının bir Exchange 'e sahip olmadığı anlamına gelir `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-323">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="ff83a-324">WCF Yanıtlayıcı `TerminateSequenceResponse` ILETIYI http yanıtında iletir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-324">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="ff83a-325">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff83a-325">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ff83a-326">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff83a-326">Binding</span></span>

<span data-ttu-id="ff83a-327">WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanarak istek-yanıt iletisi değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-327">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ff83a-328">Bu ileti değişim deseninin, `Duplex, Addressable` Başlatıcı iletisi değişim düzeniyle sınırlı bir şekilde karışık olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff83a-328">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ff83a-329">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-329">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ff83a-330">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="ff83a-330">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ff83a-331">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="ff83a-331">CreateSequence Exchange</span></span>

<span data-ttu-id="ff83a-332">WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi ile bir ileti iletir `Offer` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-332">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ff83a-333">WCF Yanıtlayıcı, `CreateSequence` `Offer` öğesinin bir öğesi olmasını ve iletiyi bir öğe ile iletmesini sağlar `CreateSequenceResponse` `Accept` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-333">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="ff83a-334">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="ff83a-334">Request/Reply Correlation</span></span>

<span data-ttu-id="ff83a-335">Tüm bağıntılı istekler ve yanıtlar için aşağıdakiler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ff83a-335">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="ff83a-336">WCF, tüm uygulama istek iletilerinin bir `ReplyTo` uç nokta başvurusu ve bir almasını sağlar `MessageId` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-336">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="ff83a-337">WCF her uygulama isteği iletisi için Yerel uç nokta başvurusunu uygular `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-337">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="ff83a-338">Yerel uç nokta başvurusu, `CreateSequence` `ReplyTo` Başlatıcı için Ileti ve `CreateSequence` `To` yanıtlayanın iletisi olur.</span><span class="sxs-lookup"><span data-stu-id="ff83a-338">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="ff83a-339">WCF gelen istek iletilerinin bir `MessageId` ve bir almasını sağlar `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="ff83a-339">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="ff83a-340">WCF, `ReplyTo` tüm uygulama istek ILETILERININ URI 'sinin, daha önce tanımlanan yerel uç nokta başvurusuyla eşleştiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-340">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="ff83a-341">WCF, tüm yanıtların `RelatesTo` `To` `wsa` istek/yanıt bağıntı kurallarını izleyen doğru ve üst bilgileri kapsamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff83a-341">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
