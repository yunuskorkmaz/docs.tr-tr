---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143451"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="316b0-102">Güvenilir Mesajlaşma Protokolü sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="316b0-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="316b0-103">Bu konu, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-güvenilir mesajlaşma Şubat 2005 (sürüm 1,0) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntılarını ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="316b0-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="316b0-104">WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-güvenilir mesajlaşma belirtimini izler.</span><span class="sxs-lookup"><span data-stu-id="316b0-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="316b0-105">WS-ReliableMessaging sürüm 1,0 protokolünün WinFX ile başlayarak uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="316b0-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="316b0-106">WS-güvenilir mesajlaşma Şubat 2005 protokolü, tarafından WCF 'de uygulanır <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="316b0-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="316b0-107">Kolaylık olması için, konusu aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="316b0-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="316b0-108">Başlatıcı: WS-güvenilir Ileti sırası oluşturmayı Başlatan istemci</span><span class="sxs-lookup"><span data-stu-id="316b0-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="316b0-109">Yanıtlayıcı: başlatıcısının isteklerini alan hizmet</span><span class="sxs-lookup"><span data-stu-id="316b0-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="316b0-110">Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="316b0-111">Ön ek</span><span class="sxs-lookup"><span data-stu-id="316b0-111">Prefix</span></span>|<span data-ttu-id="316b0-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="316b0-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="316b0-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="316b0-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="316b0-114">Netra</span><span class="sxs-lookup"><span data-stu-id="316b0-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="316b0-115">s</span><span class="sxs-lookup"><span data-stu-id="316b0-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="316b0-116">WSA</span><span class="sxs-lookup"><span data-stu-id="316b0-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="316b0-117">WSO</span><span class="sxs-lookup"><span data-stu-id="316b0-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="316b0-118">Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="316b0-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="316b0-119">Sıra kurulumu Iletileri</span><span class="sxs-lookup"><span data-stu-id="316b0-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="316b0-120">WCF `CreateSequence` , `CreateSequenceResponse` güvenilir bir ileti sırası oluşturmak için ve iletilerini uygular.</span><span class="sxs-lookup"><span data-stu-id="316b0-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="316b0-121">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="316b0-121">The following constraints apply:</span></span>

- <span data-ttu-id="316b0-122">B1101: WCF başlatıcısı, iletide isteğe bağlı süre sonu öğesini oluşturmaz `CreateSequence` veya `CreateSequence` ileti bir öğesi içerdiğinde, `Offer` öğesinde isteğe bağlı öğe olan durumlarda `Expires` `Offer` .</span><span class="sxs-lookup"><span data-stu-id="316b0-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="316b0-123">B1102: `CreateSequence` iletiye erişirken, WCF, varsa `Responder` her iki öğeyi de gönderir ve alır `Expires` , ancak değerlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="316b0-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="316b0-124">WS-güvenilir mesajlaşma, `Offer` bir oturum oluşturan iki dönüştürüce bağıntılı diziyi oluşturma mekanizmasını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="316b0-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="316b0-125">R1103: `CreateSequence` bir öğesi varsa `Offer` , güvenilir mesajlaşma Yanıtlayıcısı diziyi kabul etmeli ve `CreateSequenceResponse` bir `wsrm:Accept` öğesi içeren, iki ilişkili dönüştürme dizisi oluşturan veya isteği reddedecek şekilde yanıt vermelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="316b0-126">R1104: `SequenceAcknowledgement` ve convero sıralaması üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="316b0-127">R1105: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları, `CreateSequence` sekizli temelinde eşleşen adres değerlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="316b0-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="316b0-128">WCF Yanıtlayıcı, ve EPRs 'in URI kısmının `AcksTo` `ReplyTo` bir sıra oluşturmadan önce özdeş olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="316b0-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="316b0-129">R1106: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları `CreateSequence` aynı başvuru parametreleri kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="316b0-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="316b0-130">WCF zorunlu değildir, ancak/üzerindeki [başvuru parametreleri] öğesinin `AcksTo` aynı olduğunu varsayar `ReplyTo` `CreateSequence` ve `ReplyTo` bildirimlerin ve dönüştürüme sırası iletileri için uç nokta başvurusundan [başvuru parametreleri] kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="316b0-131">R1107: mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` `SequenceAcknowledgement` ve listesiyse dizileri üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="316b0-132">R1108: teklif mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, `[address]` `wsrm:AcksTo` öğesinin öğesinin bitiş noktası başvurusu alt öğesinin özelliği, öğesinin `wsrm:Accept` `CreateSequenceResponse` hedef URI 'si ile eşleşmelidir `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="316b0-133">R1109: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , başlatıcı tarafından gönderilen iletiler ve yanıtlayanın yanıt veren tarafından ileti bildirimleri aynı uç nokta başvurusuna gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="316b0-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="316b0-134">WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-güvenilir mesajlaşma kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="316b0-135">WCF WS-güvenilir Mesajlaşma uygulamasının tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="316b0-136">Üzerinde WS-güvenilir mesajlaşma `Offer` mekanizması `CreateSequence` / `CreateSequenceResponse` , iki bağıntılı dönüştürme dizisi ayarlamanıza olanak sağlar ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="316b0-137">WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe döndürüldüğünü sağlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="316b0-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="316b0-138">Bu Ayrıca, uygulama iletilerinde sıralı olarak oluşan bildirimlerin yedeklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="316b0-139">Bu nedenle, R1104, R1105 ve R1108 kısıtlamaları WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="316b0-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="316b0-140">`CreateSequence`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="316b0-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="316b0-141">`CreateSequenceResponse`İleti örneği.</span><span class="sxs-lookup"><span data-stu-id="316b0-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="316b0-142">Sequence</span><span class="sxs-lookup"><span data-stu-id="316b0-142">Sequence</span></span>

<span data-ttu-id="316b0-143">Diziler için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="316b0-144">B1201: WCF `xs:long` , en yüksek kapsamlı değer olan 9223372036854775807 ' den fazla olmayan sıra numarası üretir ve erişir.</span><span class="sxs-lookup"><span data-stu-id="316b0-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="316b0-145">B1202: WCF, eylem URI 'SI ile her zaman boş bir BOED son ileti üretir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="316b0-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="316b0-146">B1203: WCF `LastMessage` , eylem URI 'si olmadığı sürece bir öğe içeren bir dizi üst bilgisine sahip bir ileti alır ve gönderir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="316b0-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="316b0-147">Sıralı üst bilgi örneği.</span><span class="sxs-lookup"><span data-stu-id="316b0-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="316b0-148">AckRequested üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="316b0-148">AckRequested Header</span></span>

<span data-ttu-id="316b0-149">WCF `AckRequested` üstbilgiyi etkin tut mekanizması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="316b0-150">WCF isteğe bağlı `MessageNumber` öğe oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="316b0-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="316b0-151">Öğeyi içeren bir üst bilgiyle bir ileti aldıktan sonra `AckRequested` `MessageNumber` , WCF, `MessageNumber` Aşağıdaki örnekte gösterildiği gibi öğenin değerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="316b0-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="316b0-152">SequenceAcknowledgement üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="316b0-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="316b0-153">WCF, WS-güvenilir mesajlaşma 'da sunulan sıra bildirimleri için Piggy-Back mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="316b0-154">R1401: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `SequenceAcknowledgement` üst bilgi, istenen alıcıya iletilen herhangi bir uygulama iletisine dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="316b0-155">B1402: WCF herhangi bir sıra iletisi almadan önce bir onay üretmelidir (örneğin, bir iletiyi karşılamak için `AckRequested` ), WCF, `SequenceAcknowledgement` Aşağıdaki örnekte gösterildiği gibi 0-0 aralığını içeren bir üst bilgi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="316b0-156">B1403: WCF `SequenceAcknowledgement` bir öğesi içeren, `Nack` ancak öğeleri destekleyen üstbilgiler oluşturmaz `Nack` .</span><span class="sxs-lookup"><span data-stu-id="316b0-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="316b0-157">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="316b0-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="316b0-158">Aşağıda, WS-güvenilir mesajlaşma hatalarının WCF uygulaması için uygulanan kısıtlamaların bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="316b0-159">B1501: WCF `MessageNumberRollover` hata oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="316b0-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="316b0-160">B1502: WCF uç noktası `CreateSequenceRefused` , belirtimde açıklandığı gibi hatalar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="316b0-161">B1503: hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, `CreateSequenceRefused` `netrm:ConnectionLimitReached` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF ek bir hata alt kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="316b0-162">WS-Addressing hataları</span><span class="sxs-lookup"><span data-stu-id="316b0-162">WS-Addressing Faults</span></span>

<span data-ttu-id="316b0-163">WS-güvenilir mesajlaşma, WS-Addressing kullandığından, WCF WS güvenilir mesajlaşma uygulamaları WS-Addressing hataları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="316b0-164">Bu bölüm, WCF 'nin WS-güvenilir mesajlaşma katmanında açıkça oluşturduğu WS-Addressing hatalarını ele almaktadır:</span><span class="sxs-lookup"><span data-stu-id="316b0-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="316b0-165">B1601: WCF, aşağıdakilerden biri true olduğunda gereken hata Iletisi adresleme üstbilgisini üretir:</span><span class="sxs-lookup"><span data-stu-id="316b0-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="316b0-166">Bir iletide `Sequence` üst bilgi ve `Action` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="316b0-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="316b0-167">Bir `CreateSequence` iletide `MessageId` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="316b0-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="316b0-168">Bir `CreateSequence` iletide `ReplyTo` üst bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="316b0-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="316b0-169">B1602: WCF, bir `Sequence` üst bilgi eksik olan ve `Action` WS güvenilir mesajlaşma belirtiminde tanınmayan bir üstbilgiye sahip olan bir iletiye yanıt olarak desteklenmeyen hata eylemini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="316b0-170">B1603: WCF, hata uç noktasını, `CreateSequence` iletinin adres üst bilgilerini incelemeye göre sırayı işlemediğini göstermek Için kullanılamaz olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="316b0-171">Protokol oluşturma</span><span class="sxs-lookup"><span data-stu-id="316b0-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="316b0-172">WS-Addressing oluşturma</span><span class="sxs-lookup"><span data-stu-id="316b0-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="316b0-173">WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="316b0-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="316b0-174">WS-güvenilir mesajlaşma belirtiminde yalnızca WS-Addressing 2004/08 bahsetirken, WS-Addressing sürümü kullanılacak şekilde kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="316b0-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="316b0-175">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="316b0-176">R2101: hem WS-Addressing 2004/08 hem de WS-Addressing 1,0, WS-güvenilir mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="316b0-177">R2102: tek bir WS-Addressing sürümü, belirli bir WS-Addressing mesajlaşma sırası boyunca veya mekanizması kullanılarak bağıntılı bir convero dizileri çifti olarak kullanılmalıdır `wsrm:Offer` .</span><span class="sxs-lookup"><span data-stu-id="316b0-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="316b0-178">SOAP ile bileşim</span><span class="sxs-lookup"><span data-stu-id="316b0-178">Composition with SOAP</span></span>

<span data-ttu-id="316b0-179">WCF, hem SOAP 1,1 hem de WS-güvenilir mesajlaşma ile SOAP 1,2 kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="316b0-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="316b0-180">WS-Security ve WS-SecureConversation ile birleştirme</span><span class="sxs-lookup"><span data-stu-id="316b0-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="316b0-181">WCF, güvenli aktarım (HTTPS), WS-Security ile bileşim ve WS-Secure konuşmasıyla bileşim kullanılarak WS-güvenilir mesajlaşma dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="316b0-182">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="316b0-183">R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak, WS-güvenilir bir mesajlaşma sırasının bütünlüğünü korumak Için, WCF WS-Secure konuşmasının kullanılması gerektiğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="316b0-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="316b0-184">R2302: AWS-Secure görüşme oturumunun, WS-güvenilir mesajlaşma sırası kurulmadan önce kurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="316b0-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="316b0-185">R2303: WS-güvenilir mesajlaşma sırası ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, WS-Secure konuşma `SecurityContextToken` kullanılarak belirlenen, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="316b0-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="316b0-186">B2304: WS-güvenilir mesajlaşma sırası veya bir çift bağıntılı dönüştürme dizisi her zaman tek bir WS-SecureConversation oturumuna bağlanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="316b0-187">WCF kaynağı, `wsse:SecurityTokenReference` iletinin öğe genişletilebilirliği bölümünde öğesini oluşturur `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="316b0-188">R2305: WS-Secure konuşmasıyla birlikte kullanıldığında, bir `CreateSequence` ileti `wsse:SecurityTokenReference` öğesini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="316b0-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="316b0-189">WS-güvenilir mesajlaşma WS-Ilke onaylama</span><span class="sxs-lookup"><span data-stu-id="316b0-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="316b0-190">WCF `wsrm:RMAssertion` uç noktalar özelliklerini anlatmak IÇIN WS-güvenilir mesajlaşma WS-Policy onaylama işlemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="316b0-191">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="316b0-192">B3001: WCF `wsrm:RMAssertion` WS-Policy onay onayını `wsdl:binding` öğelere iliştirir.</span><span class="sxs-lookup"><span data-stu-id="316b0-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="316b0-193">WCF her iki Eki `wsdl:binding` ve `wsdl:port` öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="316b0-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="316b0-194">B3002: WCF, WS-güvenilir mesajlaşma onaylama 'nın aşağıdaki isteğe bağlı özelliklerini destekler ve WCF üzerinde denetim sağlar `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="316b0-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="316b0-195">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="316b0-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="316b0-196">Akış denetimi WS-güvenilir mesajlaşma uzantısı</span><span class="sxs-lookup"><span data-stu-id="316b0-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="316b0-197">WCF, sıralı ileti akışı üzerinde isteğe bağlı ek daha sıkı denetim sağlamak için WS-güvenilir mesajlaşma genişletilebilirliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="316b0-198">Akış denetimi <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği olarak ayarlanarak etkinleştirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="316b0-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="316b0-199">WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="316b0-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="316b0-200">B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF `netrm:BufferRemaining` öğenin genişletilebilirliği içindeki bir öğe oluşturur `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="316b0-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="316b0-201">B4002: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, `netrm:BufferRemaining` `SequenceAcknowledgement` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF, üst bilgide bir öğe bulunmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="316b0-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="316b0-202">B4003: WCF `netrm:BufferRemaining` , güvenilir mesajlaşma hedefinin arabelleğe abileceği yeni ileti sayısını göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="316b0-203">B4004: WCF güvenilir mesajlaşma hizmeti, güvenilir mesajlaşma hedefi uygulaması iletileri hızlı bir şekilde alamadığınızda aktarılan ileti sayısını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="316b0-204">Güvenilir Mesajlaşma hedefi iletileri arabelleğe alır ve öğenin değeri 0 ' a düşer.</span><span class="sxs-lookup"><span data-stu-id="316b0-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="316b0-205">B4005: WCF `netrm:BufferRemaining` , dahil 0 ve 4096 arasında tamsayı değerler üretir ve 0 214748364 ile arasında bir tamsayı değeri okur `xs:int` `maxInclusive` .</span><span class="sxs-lookup"><span data-stu-id="316b0-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="316b0-206">İleti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="316b0-206">Message Exchange Patterns</span></span>

<span data-ttu-id="316b0-207">Bu bölümde, farklı Ileti değişimi desenleri için WS-güvenilir mesajlaşma kullanıldığında WCF 'nin davranışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="316b0-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="316b0-208">Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="316b0-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="316b0-209">Adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasındaysa; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="316b0-210">Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="316b0-211">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="316b0-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="316b0-212">Bağlama</span><span class="sxs-lookup"><span data-stu-id="316b0-212">Binding</span></span>

<span data-ttu-id="316b0-213">WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="316b0-214">WCF, tüm iletileri RMS 'den RMD 'ye aktarmak için HTTP isteklerini ve RMD 'deki tüm iletileri RMS 'ye aktarmak için HTTP yanıtını kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="316b0-215">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-215">CreateSequence Exchange</span></span>

<span data-ttu-id="316b0-216">WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir.</span><span class="sxs-lookup"><span data-stu-id="316b0-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="316b0-217">WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="316b0-218">WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="316b0-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="316b0-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="316b0-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="316b0-220">WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri işler.</span><span class="sxs-lookup"><span data-stu-id="316b0-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="316b0-221">WCF Yanıtlayıcı her zaman hem sıra hem de ileti karşılığında tek başına bir onay üretir `AckRequested` .</span><span class="sxs-lookup"><span data-stu-id="316b0-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="316b0-222">TerminateSequence iletisi</span><span class="sxs-lookup"><span data-stu-id="316b0-222">TerminateSequence message</span></span>

<span data-ttu-id="316b0-223">WCF `TerminateSequence` tek yönlü bir işlem olarak davranır, yanı HTTP yanıtının boş bir gövdesi ve http 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="316b0-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="316b0-224">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="316b0-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="316b0-225">Bağlama</span><span class="sxs-lookup"><span data-stu-id="316b0-225">Binding</span></span>

<span data-ttu-id="316b0-226">WCF, gelen ve giden http kanalı üzerinden tek bir sıra kullanan tek yönlü bir ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="316b0-227">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="316b0-228">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="316b0-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="316b0-229">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-229">CreateSequence Exchange</span></span>

<span data-ttu-id="316b0-230">WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir.</span><span class="sxs-lookup"><span data-stu-id="316b0-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="316b0-231">WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="316b0-232">WCF Yanıtlayıcı, `CreateSequenceResponse` iletiyi `ReplyTo` uç nokta başvurusuyla BAHSEDILEN bir http isteği üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="316b0-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="316b0-233">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="316b0-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="316b0-234">Bağlama</span><span class="sxs-lookup"><span data-stu-id="316b0-234">Binding</span></span>

<span data-ttu-id="316b0-235">WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz iki yönlü bir ileti değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="316b0-236">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="316b0-237">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="316b0-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="316b0-238">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-238">CreateSequence Exchange</span></span>

<span data-ttu-id="316b0-239">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="316b0-240">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="316b0-241">WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="316b0-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="316b0-242">Sıra ömrü</span><span class="sxs-lookup"><span data-stu-id="316b0-242">Sequence Lifetime</span></span>

<span data-ttu-id="316b0-243">WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="316b0-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="316b0-244">Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler.</span><span class="sxs-lookup"><span data-stu-id="316b0-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="316b0-245">Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.</span><span class="sxs-lookup"><span data-stu-id="316b0-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="316b0-246">WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="316b0-247">Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="316b0-248">İstek-yanıt, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="316b0-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="316b0-249">Bağlama</span><span class="sxs-lookup"><span data-stu-id="316b0-249">Binding</span></span>

<span data-ttu-id="316b0-250">WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="316b0-251">WCF, istek dizisinin iletilerini aktarmak için HTTP isteklerini kullanır ve yanıt dizisinin iletilerini aktarmak için HTTP yanıtlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="316b0-252">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-252">CreateSequence Exchange</span></span>

<span data-ttu-id="316b0-253">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="316b0-254">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="316b0-255">WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .</span><span class="sxs-lookup"><span data-stu-id="316b0-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="316b0-256">Tek yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="316b0-256">One-way Message</span></span>

<span data-ttu-id="316b0-257">Tek yönlü ileti değişim protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına bir `SequenceAcknowledgement` ileti alır.</span><span class="sxs-lookup"><span data-stu-id="316b0-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="316b0-258">, `SequenceAcknowledgement` İletilen iletiyi kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="316b0-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="316b0-259">WCF Yanıtlayıcı, isteği bir onaylama, hata veya boş bir gövde ve HTTP 202 durum kodu olan bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="316b0-260">İki yönlü Ileti</span><span class="sxs-lookup"><span data-stu-id="316b0-260">Two Way Messages</span></span>

<span data-ttu-id="316b0-261">İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="316b0-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="316b0-262">Yanıt, `SequenceAcknowledgement` iletilen istek sırası iletisini bildiren bir ileti taşımalıdır.</span><span class="sxs-lookup"><span data-stu-id="316b0-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="316b0-263">WCF Yanıtlayıcı, isteği bir uygulama yanıtıyla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="316b0-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="316b0-264">Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.</span><span class="sxs-lookup"><span data-stu-id="316b0-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="316b0-265">Yanıtları yeniden deneme</span><span class="sxs-lookup"><span data-stu-id="316b0-265">Retrying Replies</span></span>

<span data-ttu-id="316b0-266">WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="316b0-267">Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir onay, kullanıcı iletisi veya hata taşımadığında bir istek sırası iletisinin yeniden denenmediğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="316b0-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="316b0-268">WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP isteği bacağı yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="316b0-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="316b0-269">LastMessage değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-269">LastMessage Exchange</span></span>

<span data-ttu-id="316b0-270">WCF başlatıcısı, HTTP istek baındaki boş bir BOED son ileti oluşturur ve iletir.</span><span class="sxs-lookup"><span data-stu-id="316b0-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="316b0-271">WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="316b0-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="316b0-272">WCF Yanıtlayıcı, istek dizisinin boş-Bodied son iletisi ile yanıt sırasının boş olduğunu ve son iletisini yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="316b0-273">WCF Yanıtlayıcı, eylem URI 'sinin olmadığı son bir iletiyi alırsa `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF son iletiyle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="316b0-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="316b0-274">İki yönlü ileti değişimi Protokolü söz konusu olduğunda, son ileti uygulama iletisini taşır; tek yönlü ileti Değişim Protokolü söz konusu olduğunda, son ileti boş olur.</span><span class="sxs-lookup"><span data-stu-id="316b0-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="316b0-275">WCF Yanıtlayıcı, yanıt sırasının boş-Bodied son iletisi için bir bildirim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="316b0-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="316b0-276">TerminateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="316b0-277">Tüm istekler geçerli bir yanıt aldığında, WCF başlatıcısı, istek dizisinin `TerminateSequence` ILETISINI http istek bacağı ' da oluşturur ve iletir.</span><span class="sxs-lookup"><span data-stu-id="316b0-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="316b0-278">WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="316b0-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="316b0-279">WCF Yanıtlayıcı, istek dizisinin `TerminateSequence` iletisine yanıt sırası iletisi ile yanıt verir `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="316b0-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="316b0-280">Normal bir kapalı dizisinde, her iki `TerminateSequence` ileti de tam bir Aralık taşır `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="316b0-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="316b0-281">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="316b0-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="316b0-282">Bağlama</span><span class="sxs-lookup"><span data-stu-id="316b0-282">Binding</span></span>

<span data-ttu-id="316b0-283">WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan bir istek-yanıt iletisi değişim modelini sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="316b0-284">WCF, tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="316b0-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="316b0-285">Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="316b0-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="316b0-286">CreateSequence değişimi</span><span class="sxs-lookup"><span data-stu-id="316b0-286">CreateSequence Exchange</span></span>

<span data-ttu-id="316b0-287">WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="316b0-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="316b0-288">WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="316b0-289">WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="316b0-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="316b0-290">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="316b0-290">Request/Reply Correlation</span></span>

<span data-ttu-id="316b0-291">WCF başlatıcısı, tüm uygulama istek iletilerinin bir `MessageId` ve bir `ReplyTo` uç nokta başvurusu olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="316b0-292">WCF başlatıcısı, `CreateSequence` `ReplyTo` her uygulama isteği iletisinde iletinin bitiş noktası başvurusunu uygular.</span><span class="sxs-lookup"><span data-stu-id="316b0-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="316b0-293">WCF Yanıtlayıcı, gelen istek iletilerinin bir `MessageId` ve bir olmasını gerektirir `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="316b0-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="316b0-294">WCF Yanıtlayıcı, uç nokta başvurusunun hem hem de `CreateSequence` tüm uygulama istek ILETILERININ URI 'sinin aynı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="316b0-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
