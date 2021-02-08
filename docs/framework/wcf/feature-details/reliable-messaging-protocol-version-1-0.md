---
description: 'Daha fazla bilgi edinin: güvenilir mesajlaşma Protokolü sürüm 1,0'
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: dbd0184fd6ea9f92c96639d71088ac61bec20f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793603"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="f1d45-103">Güvenilir Mesajlaşma Protokolü sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="f1d45-103">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="f1d45-104">Bu konu, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-Reliable mesajlaşma Şubat 2005 (sürüm 1,0) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-104">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="f1d45-105">WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-Reliable mesajlaşma belirtimini izler.</span><span class="sxs-lookup"><span data-stu-id="f1d45-105">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="f1d45-106">WS-ReliableMessaging sürüm 1,0 protokolünün WinFX ile başlayarak uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f1d45-106">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="f1d45-107">WS-Reliable mesajlaşma Şubat 2005 protokolü, tarafından WCF 'de uygulanır <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="f1d45-107">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="f1d45-108">Kolaylık olması için, konusu aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="f1d45-108">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="f1d45-109">Başlatıcı: WS-Reliable Ileti sırası oluşturmayı Başlatan istemci</span><span class="sxs-lookup"><span data-stu-id="f1d45-109">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="f1d45-110">Yanıtlayıcı: başlatıcısının isteklerini alan hizmet</span><span class="sxs-lookup"><span data-stu-id="f1d45-110">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="f1d45-111">Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-111">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="f1d45-112">Ön ek</span><span class="sxs-lookup"><span data-stu-id="f1d45-112">Prefix</span></span>|<span data-ttu-id="f1d45-113">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f1d45-113">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="f1d45-114">WSRM</span><span class="sxs-lookup"><span data-stu-id="f1d45-114">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="f1d45-115">Netra</span><span class="sxs-lookup"><span data-stu-id="f1d45-115">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="f1d45-116">s</span><span class="sxs-lookup"><span data-stu-id="f1d45-116">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="f1d45-117">WSA</span><span class="sxs-lookup"><span data-stu-id="f1d45-117">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="f1d45-118">WSO</span><span class="sxs-lookup"><span data-stu-id="f1d45-118">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="f1d45-119">Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="f1d45-119">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="f1d45-120">Sıra kurulumu Iletileri</span><span class="sxs-lookup"><span data-stu-id="f1d45-120">Sequence Establishment Messages</span></span>

<span data-ttu-id="f1d45-121">WCF `CreateSequence` , `CreateSequenceResponse` güvenilir bir ileti sırası oluşturmak için ve iletilerini uygular.</span><span class="sxs-lookup"><span data-stu-id="f1d45-121">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="f1d45-122">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-122">The following constraints apply:</span></span>

- <span data-ttu-id="f1d45-123">B1101: WCF başlatıcısı, iletide isteğe bağlı süre sonu öğesini oluşturmaz `CreateSequence` veya `CreateSequence` ileti bir öğesi içerdiğinde, `Offer` öğesinde isteğe bağlı öğe olan durumlarda `Expires` `Offer` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-123">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="f1d45-124">B1102: `CreateSequence` iletiye erişirken, WCF, varsa `Responder` her iki öğeyi de gönderir ve alır `Expires` , ancak değerlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f1d45-124">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="f1d45-125">WS-Reliable mesajlaşma, `Offer` bir oturum oluşturan iki dönüştürüce bağıntılı diziyi oluşturma mekanizmasını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-125">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="f1d45-126">R1103: `CreateSequence` bir öğesi varsa `Offer` , güvenilir mesajlaşma Yanıtlayıcısı diziyi kabul etmeli ve `CreateSequenceResponse` bir `wsrm:Accept` öğesi içeren, iki ilişkili dönüştürme dizisi oluşturan veya isteği reddedecek şekilde yanıt vermelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-126">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="f1d45-127">R1104: `SequenceAcknowledgement` ve convero sıralaması üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-127">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="f1d45-128">R1105: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları, `CreateSequence` sekizli temelinde eşleşen adres değerlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-128">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="f1d45-129">WCF Yanıtlayıcı, ve EPRs 'in URI kısmının `AcksTo` `ReplyTo` bir sıra oluşturmadan önce özdeş olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="f1d45-129">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="f1d45-130">R1106: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları `CreateSequence` aynı başvuru parametreleri kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-130">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="f1d45-131">WCF zorunlu değildir, ancak/üzerindeki [başvuru parametreleri] öğesinin `AcksTo` aynı olduğunu varsayar `ReplyTo` `CreateSequence` ve `ReplyTo` bildirimlerin ve dönüştürüme sırası iletileri için uç nokta başvurusundan [başvuru parametreleri] kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-131">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="f1d45-132">R1107: mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` `SequenceAcknowledgement` ve listesiyse dizileri üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-132">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="f1d45-133">R1108: teklif mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, `[address]` `wsrm:AcksTo` öğesinin öğesinin bitiş noktası başvurusu alt öğesinin özelliği, öğesinin `wsrm:Accept` `CreateSequenceResponse` hedef URI 'si ile eşleşmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-133">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="f1d45-134">R1109: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , başlatıcı tarafından gönderilen iletiler ve yanıtlayanın yanıt veren tarafından ileti bildirimleri aynı uç nokta başvurusuna gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-134">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="f1d45-135">WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-Reliable mesajlaşma kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-135">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="f1d45-136">WCF WS-Reliable mesajlaşma kullanımı, tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-136">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="f1d45-137">Üzerinde WS-Reliable mesajlaşma `Offer` mekanizması `CreateSequence` / `CreateSequenceResponse` , iki bağıntılı dönüştürme dizisi ayarlamanıza olanak sağlar ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-137">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="f1d45-138">WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe döndürüldüğünü sağlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-138">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="f1d45-139">Bu Ayrıca, uygulama iletilerinde sıralı olarak oluşan bildirimlerin yedeklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-139">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="f1d45-140">Bu nedenle, R1104, R1105 ve R1108 kısıtlamaları WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-140">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="f1d45-141">`CreateSequence`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="f1d45-141">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="f1d45-142">`CreateSequenceResponse`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="f1d45-142">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="f1d45-143">Sequence</span><span class="sxs-lookup"><span data-stu-id="f1d45-143">Sequence</span></span>

<span data-ttu-id="f1d45-144">Diziler için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-144">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="f1d45-145">B1201: WCF `xs:long` , en yüksek kapsamlı değer olan 9223372036854775807 ' den fazla olmayan sıra numarası üretir ve erişir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-145">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="f1d45-146">B1202: WCF, eylem URI 'SI ile her zaman boş bir BOED son ileti üretir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-146">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="f1d45-147">B1203: WCF `LastMessage` , eylem URI 'si olmadığı sürece bir öğe içeren bir dizi üst bilgisine sahip bir ileti alır ve gönderir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-147">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="f1d45-148">Sıralı üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="f1d45-148">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="f1d45-149">AckRequested üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="f1d45-149">AckRequested Header</span></span>

<span data-ttu-id="f1d45-150">WCF `AckRequested` üstbilgiyi etkin tut mekanizması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-150">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="f1d45-151">WCF isteğe bağlı `MessageNumber` öğe oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f1d45-151">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="f1d45-152">Öğeyi içeren bir üst bilgiyle bir ileti aldıktan sonra `AckRequested` `MessageNumber` , WCF, `MessageNumber` Aşağıdaki örnekte gösterildiği gibi öğenin değerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-152">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="f1d45-153">SequenceAcknowledgement üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="f1d45-153">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="f1d45-154">WCF, WS-Reliable mesajlaşma 'da sunulan sıra bildirimleri için Piggy-Back mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-154">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="f1d45-155">R1401: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `SequenceAcknowledgement` üst bilgi, istenen alıcıya iletilen herhangi bir uygulama iletisine dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-155">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="f1d45-156">B1402: WCF herhangi bir sıra iletisi almadan önce bir onay üretmelidir (örneğin, bir iletiyi karşılamak için `AckRequested` ), WCF, `SequenceAcknowledgement` Aşağıdaki örnekte gösterildiği gibi 0-0 aralığını içeren bir üst bilgi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-156">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="f1d45-157">B1403: WCF `SequenceAcknowledgement` bir öğesi içeren, `Nack` ancak öğeleri destekleyen üstbilgiler oluşturmaz `Nack` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-157">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="f1d45-158">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="f1d45-158">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="f1d45-159">Aşağıda, WS-Reliable mesajlaşma hatalarının WCF uygulaması için uygulanan kısıtlamaların bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-159">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="f1d45-160">B1501: WCF `MessageNumberRollover` hata oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f1d45-160">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="f1d45-161">B1502: WCF uç noktası `CreateSequenceRefused` , belirtimde açıklandığı gibi hatalar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-161">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="f1d45-162">B1503: hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, `CreateSequenceRefused` `netrm:ConnectionLimitReached` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF ek bir hata alt kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-162">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="f1d45-163">WS-Addressing hataları</span><span class="sxs-lookup"><span data-stu-id="f1d45-163">WS-Addressing Faults</span></span>

<span data-ttu-id="f1d45-164">WS-Reliable mesajlaşma WS-Addressing kullandığından, WCF WS-Reliable mesajlaşma uygulama WS-Addressing hata oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-164">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="f1d45-165">Bu bölümde, WCF 'nin WS-Reliable mesajlaşma katmanında açıkça oluşturduğu WS-Addressing hataları ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f1d45-165">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="f1d45-166">B1601: WCF, aşağıdakilerden biri true olduğunda gereken hata Iletisi adresleme üstbilgisini üretir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-166">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="f1d45-167">Bir iletide `Sequence` üst bilgi ve `Action` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="f1d45-167">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="f1d45-168">Bir `CreateSequence` iletide `MessageId` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="f1d45-168">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="f1d45-169">Bir `CreateSequence` iletide `ReplyTo` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="f1d45-169">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="f1d45-170">B1602: WCF, bir `Sequence` üst bilgi eksik olan ve `Action` WS-Reliable mesajlaşma belirtiminde tanınan bir üst bilgisine sahip olan bir iletiye yanıt olarak desteklenmeyen hata eylemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-170">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="f1d45-171">B1603: WCF, hata uç noktasını, `CreateSequence` iletinin adres üst bilgilerini incelemeye göre sırayı işlemediğini göstermek Için kullanılamaz olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-171">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="f1d45-172">Protokol oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1d45-172">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="f1d45-173">WS-Addressing oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1d45-173">Composition with WS-Addressing</span></span>

<span data-ttu-id="f1d45-174">WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="f1d45-174">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="f1d45-175">WS-Reliable mesajlaşma belirtimi yalnızca WS-Addressing 2004/08 ' den bahsetirken, WS-Addressing sürümü kullanılmak üzere kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="f1d45-175">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="f1d45-176">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-176">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f1d45-177">R2101: WS-Addressing 2004/08 ve WS-Addressing 1,0, WS-Reliable mesajlaşma ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-177">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="f1d45-178">R2102: tek bir WS-Addressing bir sürümü, belirli bir WS-Reliable mesajlaşma sırası boyunca veya mekanizması kullanılarak bağıntılı bir convero dizileri çifti olarak kullanılmalıdır `wsrm:Offer` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-178">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="f1d45-179">SOAP ile bileşim</span><span class="sxs-lookup"><span data-stu-id="f1d45-179">Composition with SOAP</span></span>

<span data-ttu-id="f1d45-180">WCF, WS-Reliable mesajlaşma ile hem SOAP 1,1 hem de SOAP 1,2 kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="f1d45-180">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="f1d45-181">WS-Security ve WS-SecureConversation oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1d45-181">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="f1d45-182">WCF, güvenli aktarım (HTTPS), WS-güvenlik ile bileşim ve WS-Secure konuşmayla bileşim kullanarak WS-Reliable mesajlaşma dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-182">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="f1d45-183">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-183">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f1d45-184">R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak, WS-Reliable bir mesajlaşma sırasının bütünlüğünü korumak Için, WCF WS-Secure konuşmanın kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-184">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="f1d45-185">R2302: AWS-Secure konuşma oturumunun WS-Reliable mesajlaşma sırası kurulmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-185">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="f1d45-186">R2303: WS-Reliable mesajlaşma sırası ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, `SecurityContextToken` WS-Secure konuşması kullanılarak belirlenen, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-186">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="f1d45-187">B2304: WS-güvenilir mesajlaşma sırası veya bir çift bağıntılı dönüştürme dizisi her zaman tek bir WS-SecureConversation oturumuna bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-187">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="f1d45-188">WCF kaynağı, `wsse:SecurityTokenReference` iletinin öğe genişletilebilirliği bölümünde öğesini oluşturur `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-188">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="f1d45-189">R2305: WS-Secure konuşmasıyla birlikte oluşturulduğunda, bir `CreateSequence` ileti `wsse:SecurityTokenReference` öğesini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-189">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="f1d45-190">WS-Reliable mesajlaşma WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="f1d45-190">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="f1d45-191">WCF, `wsrm:RMAssertion` uç noktalar özelliklerini anlatmak için WS-Reliable mesajlaşma WS-Policy onayını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-191">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="f1d45-192">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-192">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f1d45-193">B3001: WCF `wsrm:RMAssertion` öğelere WS-Policy onay ekler `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-193">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="f1d45-194">WCF her iki Eki `wsdl:binding` ve `wsdl:port` öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f1d45-194">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="f1d45-195">B3002: WCF WS-Reliable mesajlaşma onaylaması 'nın aşağıdaki isteğe bağlı özelliklerini destekler ve WCF üzerinde denetim sağlar `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="f1d45-195">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="f1d45-196">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-196">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="f1d45-197">Akış denetimi WS-Reliable mesajlaşma uzantısı</span><span class="sxs-lookup"><span data-stu-id="f1d45-197">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="f1d45-198">WCF, sıralı ileti akışı üzerinde isteğe bağlı ek daha sıkı denetim sağlamak için WS-Reliable mesajlaşma genişletilebilirliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-198">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="f1d45-199">Akış denetimi <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği olarak ayarlanarak etkinleştirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-199">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f1d45-200">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1d45-200">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f1d45-201">B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF `netrm:BufferRemaining` öğenin genişletilebilirliği içindeki bir öğe oluşturur `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-201">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="f1d45-202">B4002: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, `netrm:BufferRemaining` `SequenceAcknowledgement` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF, üst bilgide bir öğe bulunmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f1d45-202">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="f1d45-203">B4003: WCF `netrm:BufferRemaining` , güvenilir mesajlaşma hedefinin arabelleğe abileceği yeni ileti sayısını göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-203">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="f1d45-204">B4004: WCF güvenilir mesajlaşma hizmeti, güvenilir mesajlaşma hedefi uygulaması iletileri hızlı bir şekilde alamadığınızda aktarılan ileti sayısını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-204">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="f1d45-205">Güvenilir Mesajlaşma hedefi iletileri arabelleğe alır ve öğenin değeri 0 ' a düşer.</span><span class="sxs-lookup"><span data-stu-id="f1d45-205">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="f1d45-206">B4005: WCF `netrm:BufferRemaining` , dahil 0 ve 4096 arasında tamsayı değerler üretir ve 0 214748364 ile arasında bir tamsayı değeri okur `xs:int` `maxInclusive` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-206">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="f1d45-207">İleti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="f1d45-207">Message Exchange Patterns</span></span>

<span data-ttu-id="f1d45-208">Bu bölümde, farklı Ileti değişimi desenleri için WS-Reliable mesajlaşma kullanıldığında WCF 'nin davranışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-208">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="f1d45-209">Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f1d45-209">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="f1d45-210">Adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasındaysa; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-210">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="f1d45-211">Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-211">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="f1d45-212">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f1d45-212">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f1d45-213">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1d45-213">Binding</span></span>

<span data-ttu-id="f1d45-214">WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-214">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="f1d45-215">WCF, tüm iletileri RMS 'den RMD 'ye aktarmak için HTTP isteklerini ve RMD 'deki tüm iletileri RMS 'ye aktarmak için HTTP yanıtını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-215">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f1d45-216">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-216">CreateSequence Exchange</span></span>

<span data-ttu-id="f1d45-217">WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-217">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f1d45-218">WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-218">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f1d45-219">WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-219">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="f1d45-220">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f1d45-220">SequenceAcknowledgement</span></span>

<span data-ttu-id="f1d45-221">WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri işler.</span><span class="sxs-lookup"><span data-stu-id="f1d45-221">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="f1d45-222">WCF Yanıtlayıcı her zaman hem sıra hem de ileti karşılığında tek başına bir onay üretir `AckRequested` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-222">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="f1d45-223">TerminateSequence iletisi</span><span class="sxs-lookup"><span data-stu-id="f1d45-223">TerminateSequence message</span></span>

<span data-ttu-id="f1d45-224">WCF `TerminateSequence` tek yönlü bir işlem olarak davranır, yanı HTTP yanıtının boş bir gövdesi ve http 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-224">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="f1d45-225">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f1d45-225">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f1d45-226">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1d45-226">Binding</span></span>

<span data-ttu-id="f1d45-227">WCF, gelen ve giden http kanalı üzerinden tek bir sıra kullanan tek yönlü bir ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-227">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="f1d45-228">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-228">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f1d45-229">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-229">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f1d45-230">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-230">CreateSequence Exchange</span></span>

<span data-ttu-id="f1d45-231">WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-231">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f1d45-232">WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-232">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f1d45-233">WCF Yanıtlayıcı, `CreateSequenceResponse` iletiyi `ReplyTo` uç nokta başvurusuyla BAHSEDILEN bir http isteği üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-233">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="f1d45-234">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f1d45-234">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f1d45-235">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1d45-235">Binding</span></span>

<span data-ttu-id="f1d45-236">WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz iki yönlü bir ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-236">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f1d45-237">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-237">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f1d45-238">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-238">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f1d45-239">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-239">CreateSequence Exchange</span></span>

<span data-ttu-id="f1d45-240">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-240">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f1d45-241">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-241">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f1d45-242">WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-242">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="f1d45-243">Sıra ömrü</span><span class="sxs-lookup"><span data-stu-id="f1d45-243">Sequence Lifetime</span></span>

<span data-ttu-id="f1d45-244">WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-244">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="f1d45-245">Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler.</span><span class="sxs-lookup"><span data-stu-id="f1d45-245">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="f1d45-246">Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-246">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="f1d45-247">WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-247">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="f1d45-248">Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-248">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="f1d45-249">İstek-yanıt, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f1d45-249">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f1d45-250">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1d45-250">Binding</span></span>

<span data-ttu-id="f1d45-251">WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-251">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="f1d45-252">WCF, istek dizisinin iletilerini aktarmak için HTTP isteklerini kullanır ve yanıt dizisinin iletilerini aktarmak için HTTP yanıtlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-252">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f1d45-253">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-253">CreateSequence Exchange</span></span>

<span data-ttu-id="f1d45-254">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-254">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f1d45-255">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-255">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f1d45-256">WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-256">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="f1d45-257">Tek yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="f1d45-257">One-way Message</span></span>

<span data-ttu-id="f1d45-258">Tek yönlü ileti değişim protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına bir `SequenceAcknowledgement` ileti alır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-258">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="f1d45-259">, `SequenceAcknowledgement` İletilen iletiyi kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-259">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="f1d45-260">WCF Yanıtlayıcı, isteği bir onaylama, hata veya boş bir gövde ve HTTP 202 durum kodu olan bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-260">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="f1d45-261">İki yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="f1d45-261">Two Way Messages</span></span>

<span data-ttu-id="f1d45-262">İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-262">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="f1d45-263">Yanıt, `SequenceAcknowledgement` iletilen istek sırası iletisini bildiren bir ileti taşımalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-263">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="f1d45-264">WCF Yanıtlayıcı, isteği bir uygulama yanıtıyla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-264">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="f1d45-265">Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.</span><span class="sxs-lookup"><span data-stu-id="f1d45-265">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="f1d45-266">Yanıtları yeniden deneme</span><span class="sxs-lookup"><span data-stu-id="f1d45-266">Retrying Replies</span></span>

<span data-ttu-id="f1d45-267">WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-267">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="f1d45-268">Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir onay, kullanıcı iletisi veya hata taşımadığında bir istek sırası iletisinin yeniden denenmediğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-268">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="f1d45-269">WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP isteği bacağı yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="f1d45-269">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="f1d45-270">LastMessage değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-270">LastMessage Exchange</span></span>

<span data-ttu-id="f1d45-271">WCF başlatıcısı, HTTP istek baındaki boş bir BOED son ileti oluşturur ve iletir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-271">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="f1d45-272">WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-272">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f1d45-273">WCF Yanıtlayıcı, istek dizisinin boş-Bodied son iletisi ile yanıt sırasının boş olduğunu ve son iletisini yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-273">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="f1d45-274">WCF Yanıtlayıcı, eylem URI 'sinin olmadığı son bir iletiyi alırsa `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF son iletiyle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-274">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="f1d45-275">İki yönlü ileti değişimi Protokolü söz konusu olduğunda, son ileti uygulama iletisini taşır; tek yönlü ileti Değişim Protokolü söz konusu olduğunda, son ileti boş olur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-275">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="f1d45-276">WCF Yanıtlayıcı, yanıt sırasının boş-Bodied son iletisi için bir bildirim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f1d45-276">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f1d45-277">TerminateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-277">TerminateSequence Exchange</span></span>

<span data-ttu-id="f1d45-278">Tüm istekler geçerli bir yanıt aldığında, WCF başlatıcısı, istek dizisinin `TerminateSequence` ILETISINI http istek bacağı ' da oluşturur ve iletir.</span><span class="sxs-lookup"><span data-stu-id="f1d45-278">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="f1d45-279">WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-279">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f1d45-280">WCF Yanıtlayıcı, istek dizisinin `TerminateSequence` iletisine yanıt sırası iletisi ile yanıt verir `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-280">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="f1d45-281">Normal bir kapalı dizisinde, her iki `TerminateSequence` ileti de tam bir Aralık taşır `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-281">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="f1d45-282">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f1d45-282">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f1d45-283">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1d45-283">Binding</span></span>

<span data-ttu-id="f1d45-284">WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan bir istek-yanıt iletisi değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-284">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f1d45-285">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-285">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f1d45-286">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="f1d45-286">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f1d45-287">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="f1d45-287">CreateSequence Exchange</span></span>

<span data-ttu-id="f1d45-288">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d45-288">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f1d45-289">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-289">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f1d45-290">WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-290">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="f1d45-291">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="f1d45-291">Request/Reply Correlation</span></span>

<span data-ttu-id="f1d45-292">WCF başlatıcısı, tüm uygulama istek iletilerinin bir `MessageId` ve bir `ReplyTo` uç nokta başvurusu olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-292">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="f1d45-293">WCF başlatıcısı, `CreateSequence` `ReplyTo` her uygulama isteği iletisinde iletinin bitiş noktası başvurusunu uygular.</span><span class="sxs-lookup"><span data-stu-id="f1d45-293">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="f1d45-294">WCF Yanıtlayıcı, gelen istek iletilerinin bir `MessageId` ve bir olmasını gerektirir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="f1d45-294">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="f1d45-295">WCF Yanıtlayıcı, uç nokta başvurusunun hem hem de `CreateSequence` tüm uygulama istek ILETILERININ URI 'sinin aynı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1d45-295">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
