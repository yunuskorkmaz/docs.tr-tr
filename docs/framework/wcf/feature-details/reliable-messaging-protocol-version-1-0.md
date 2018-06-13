---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497058"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="68f1a-102">Güvenilir Mesajlaşma Protokolü sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="68f1a-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="68f1a-103">Bu konu, WS güvenilir Mesajlaşma için Windows Communication Foundation (WCF) uygulama ayrıntılarını kapsar Şubat 2005 (sürüm 1.0) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli.</span><span class="sxs-lookup"><span data-stu-id="68f1a-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="68f1a-104">WCF WS güvenilir Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler.</span><span class="sxs-lookup"><span data-stu-id="68f1a-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="68f1a-105">WS-ReliableMessaging 1.0 sürümü protokolü ile başlayan uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68f1a-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="68f1a-106">WS-güvenilir Protokolü WCF tarafından uygulandığına Mesajlaşma Şubat 2005 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="68f1a-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="68f1a-107">Kolaylık olması için konunun aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="68f1a-108">Başlatıcı: WS güvenilir ileti sırası oluşturması başlatan istemci</span><span class="sxs-lookup"><span data-stu-id="68f1a-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="68f1a-109">Yanıtlayıcı: başlatanın isteği alan hizmeti</span><span class="sxs-lookup"><span data-stu-id="68f1a-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="68f1a-110">Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="68f1a-111">önek</span><span class="sxs-lookup"><span data-stu-id="68f1a-111">Prefix</span></span>|<span data-ttu-id="68f1a-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="68f1a-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="68f1a-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="68f1a-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="68f1a-114">netrm</span><span class="sxs-lookup"><span data-stu-id="68f1a-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="68f1a-115">s</span><span class="sxs-lookup"><span data-stu-id="68f1a-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="68f1a-116">wsa</span><span class="sxs-lookup"><span data-stu-id="68f1a-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="68f1a-117">wsse</span><span class="sxs-lookup"><span data-stu-id="68f1a-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="68f1a-118">İleti</span><span class="sxs-lookup"><span data-stu-id="68f1a-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="68f1a-119">Sıra kurma iletileri</span><span class="sxs-lookup"><span data-stu-id="68f1a-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="68f1a-120">WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir ileti sırası kurmak için iletileri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="68f1a-121">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="68f1a-121">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="68f1a-122">B1101: İsteğe bağlı Expires öğesinde WCF Başlatıcı oluşturmaz `CreateSequence` ileti veya durumda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="68f1a-123">B1102: erişirken `CreateSequence` iletisi, WCF`Responder` alıp gönderen her ikisi de `Expires` var ancak değerlerine kullanmaz öğeleri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="68f1a-124">WS güvenilir Mesajlaşma tanıtır `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="68f1a-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="68f1a-125">R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da sırası kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` öğesi, iki bağıntılı oluşturan gruplarıdır dizileri veya Reddet`CreateSequence` isteği.</span><span class="sxs-lookup"><span data-stu-id="68f1a-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="68f1a-126">R1104: `SequenceAcknowledgement` ve ters sıra üzerinde akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="68f1a-127">R1105: `AcksTo` ve `ReplyTo` endpoint başvuran `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="68f1a-128">WCF Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="68f1a-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="68f1a-129">R1106: `AcksTo` ve `ReplyTo` Endpoint başvurularında `CreateSequence` aynı başvurusu parametre kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="68f1a-130">WCF zorunlu değildir ancak varsayar o [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="68f1a-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="68f1a-131">R1107: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` ve üzerinde ters sıraları akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="68f1a-132">R1108: iki gruplarıdır zaman serileri teklif mekanizması kullanılarak oluşturulan `[address]` özelliği `wsrm:AcksTo` bitiş noktası başvurusu alt öğesi olan `wsrm:Accept` öğesinin `CreateSequenceResponse` hedef URI byte-wise eşleşmelidir, `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="68f1a-133">R1109: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletileri için onayları tarafından gönderilen iletilerin gönderileceği aynı uç nokta referansı.</span><span class="sxs-lookup"><span data-stu-id="68f1a-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="68f1a-134">WS güvenilir Mesajlaşma WCF Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="68f1a-135">WCF'ın WS güvenilir Mesajlaşma uygulamasını sağlar güvenilir oturum tek yönlü, istek-yanıt ve tam çift yönlü desenleri Mesajlaşma.</span><span class="sxs-lookup"><span data-stu-id="68f1a-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="68f1a-136">WS güvenilir Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı ters sıraları oluşturmanıza olanak sağlar ve tüm uç noktaları iletisi için uygun bir oturum Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="68f1a-137">WCF güvenlik garantisi uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere oturumunun sağladığından, aynı hedef konumda aynı tarafa hedeflenen iletilerinin geliş emin olmak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="68f1a-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="68f1a-138">Bu ardışık-yedeklemelerini dizisi onayları uygulama iletilerinde de sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="68f1a-139">Bu nedenle, kısıtlamaları R1104, R1105 ve R1108 WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="68f1a-140">Örnek olarak bir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-140">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="68f1a-141">Örnek olarak bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="68f1a-142">Sırası</span><span class="sxs-lookup"><span data-stu-id="68f1a-142">Sequence</span></span>  
 <span data-ttu-id="68f1a-143">Dizilerine uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-143">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="68f1a-144">B1201:WCF oluşturur ve erişimleri sıra numaraları daha yüksek `xs:long`'s en büyük içermeli değer, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="68f1a-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="68f1a-145">B1202:WCF her zaman bir boş bodied son iletisiyle eylem URI'sini oluşturur, http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="68f1a-145">B1202:WCF always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="68f1a-146">B1203: WCF alır ve içeren sırası üstbilgi içeren bir ileti teslim bir `LastMessage` öğesi eylem URI'si değil sürece http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="68f1a-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="68f1a-147">Bir sıra üstbilgisi örneği.</span><span class="sxs-lookup"><span data-stu-id="68f1a-147">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="68f1a-148">AckRequested üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="68f1a-148">AckRequested Header</span></span>  
 <span data-ttu-id="68f1a-149">WCF kullanan `AckRequested` tutma mekanizması olarak üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="68f1a-150">WCF isteğe bağlı oluşturmaz `MessageNumber` öğesi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="68f1a-151">İçeren bir ileti alır almaz bir `AckRequested` üstbilgisinin içeren `MessageNumber` öğesi, WCF yoksayar `MessageNumber` aşağıdaki örnekte gösterildiği gibi öğenin değeri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="68f1a-152">SequenceAcknowledgement üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="68f1a-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="68f1a-153">WCF WS güvenilir Mesajlaşma içinde sağlanan dizisi onayları ardışık mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="68f1a-154">R1401: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="68f1a-155">B1402: WCF dizisi iletileri alma önce bir bildirim oluşturduğunuzda gerekir (örneğin, karşılamak için bir `AckRequested` ileti), WCF oluşturur bir `SequenceAcknowledgement` aralığı 0-0, aşağıdaki örnekte gösterildiği gibi içeren üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="68f1a-156">B1403: WCF oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri bir `Nack` öğesi ancak destekler `Nack` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="68f1a-157">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="68f1a-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="68f1a-158">WS güvenilir Mesajlaşma hataları WCF uygulaması için uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="68f1a-159">B1501: WCF oluşturmayacak `MessageNumberRollover` hataları.</span><span class="sxs-lookup"><span data-stu-id="68f1a-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="68f1a-160">B1502:WCF uç noktası oluşturabilir `CreateSequenceRefused` hataları belirtiminde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="68f1a-161">B1503:when hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor, WCF ek bir `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="68f1a-162">WS-adresleme hataları</span><span class="sxs-lookup"><span data-stu-id="68f1a-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="68f1a-163">WS güvenilir Mesajlaşma WS adresleme kullandığından, WCF WS güvenilir Mesajlaşma uygulaması WS adresleme hatalar oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="68f1a-164">Bu bölüm, WCF açıkça WS güvenilir Mesajlaşma katmanında oluşturur WS adresleme hataları kapsar:</span><span class="sxs-lookup"><span data-stu-id="68f1a-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="68f1a-165">Aşağıdakilerden biri doğruysa B1601:WCF hata ileti başlığı adresleme gereken oluşturur:</span><span class="sxs-lookup"><span data-stu-id="68f1a-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="68f1a-166">Bir ileti eksik bir `Sequence` başlığı ve bir `Action` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="68f1a-167">A `CreateSequence` ileti eksik bir `MessageId` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="68f1a-168">A `CreateSequence` ileti eksik bir `ReplyTo` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="68f1a-169">B1602:WCF eksik mesaja eylemi desteklenmiyor hataya oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS güvenilir Mesajlaşma belirtiminde değil üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="68f1a-170">B1603:WCF uç nokta incelenmesi temel sıralı işlemez belirtmek için uç nokta kullanılamaz hatası oluşturur `CreateSequence` ileti üstbilgilerini adresleme.</span><span class="sxs-lookup"><span data-stu-id="68f1a-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="68f1a-171">İletişim kuralı oluşturma</span><span class="sxs-lookup"><span data-stu-id="68f1a-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="68f1a-172">WS-adresleme ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="68f1a-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="68f1a-173">WCF WS adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="68f1a-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="68f1a-174">While WS güvenilir Mesajlaşma belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü.</span><span class="sxs-lookup"><span data-stu-id="68f1a-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="68f1a-175">WCF için uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-175">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="68f1a-176">R2101: hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="68f1a-177">R2102:A tek sürümü WS adresleme için kullanılan, belirli bir WS güvenilir Mesajlaşma dizi veya ters sıraları kullanarak bağıntılı çifti boyunca `wsrm:Offer` mekanizması.</span><span class="sxs-lookup"><span data-stu-id="68f1a-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="68f1a-178">SOAP ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="68f1a-178">Composition with SOAP</span></span>  
 <span data-ttu-id="68f1a-179">WCF SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="68f1a-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="68f1a-180">WS güvenliği ve WS-SecureConversation ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="68f1a-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="68f1a-181">WCF güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS güvenilir Mesajlaşma dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="68f1a-182">WCF için uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-182">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="68f1a-183">R2301: WS güvenilir Mesajlaşma dizisi bütünlüğü yanı sıra bütünlüğünü ve tek bir ileti gizliliğini korumak için WS-güvenli konuşma kullanılmalıdır WCF gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="68f1a-184">R2302:AWS-güvenli konuşma oturum WS güvenilir Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="68f1a-185">R2303: WS güvenilir Mesajlaşma ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="68f1a-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="68f1a-186">B2304:ws-güvenilir Mesajlaşma dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.</span><span class="sxs-lookup"><span data-stu-id="68f1a-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="68f1a-187">WCF kaynağı oluşturur `wsse:SecurityTokenReference` öğesi genişletilebilirlik bölümünü öğesinde `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="68f1a-188">WS-güvenli konuşma oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="68f1a-189">WS güvenilir Mesajlaşma WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="68f1a-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="68f1a-190">WCF kullanan WS güvenilir Mesajlaşma WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="68f1a-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="68f1a-191">WCF için uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-191">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="68f1a-192">B3001: WCF iliştirir `wsrm:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="68f1a-193">WCF destekleyen iki ekleri `wsdl:binding` ve `wsdl:port` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="68f1a-194">B3002: WCF WS güvenilir Mesajlaşma onaylama aşağıdaki isteğe bağlı özellikleri destekler ve bunları denetim WCF sunar`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="68f1a-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="68f1a-195">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="68f1a-196">Akış Denetim WS güvenilir Mesajlaşma uzantısı</span><span class="sxs-lookup"><span data-stu-id="68f1a-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="68f1a-197">WCF WS güvenilir Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="68f1a-198">Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``bool` özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-198">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="68f1a-199">WCF için uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="68f1a-199">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="68f1a-200">B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturan bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="68f1a-201">B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="68f1a-202">B4003: WCF kullanan `netrm:BufferRemaining` kaç tane yeni güvenilir Mesajlaşma hedef iletileri göstermek için arabellek.</span><span class="sxs-lookup"><span data-stu-id="68f1a-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="68f1a-203">B4004: WCF güvenilir Mesajlaşma hizmeti güvenilir Mesajlaşma hedef uygulama iletileri hızla alamadığı zaman aktarılan iletilerin sayısını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="68f1a-204">Hedef arabellek güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="68f1a-205">B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="68f1a-206">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="68f1a-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="68f1a-207">WS güvenilir Mesajlaşma farklı ileti Exchange desenler için kullanıldığında, bu bölümde WCF'in davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="68f1a-208">Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="68f1a-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="68f1a-209">Olmayan adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasında olan; Yanıtlayıcı iletileri yalnızca HTTP yanıtları başlatıcıya sunabilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="68f1a-210">Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="68f1a-211">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="68f1a-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="68f1a-212">Bağlama</span><span class="sxs-lookup"><span data-stu-id="68f1a-212">Binding</span></span>  
 <span data-ttu-id="68f1a-213">WCF bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="68f1a-214">WCF HTTP isteklerini RMD alınan tüm iletileri RMS'ye aktarmak için tüm iletiler RMS'den RMD ve HTTP yanıtı iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="68f1a-215">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-216">WCF Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="68f1a-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="68f1a-217">WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok.</span><span class="sxs-lookup"><span data-stu-id="68f1a-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="68f1a-218">WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="68f1a-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="68f1a-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="68f1a-220">WCF Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="68f1a-221">WCF Yanıtlayıcı her zaman yanıt hem dizisi olarak tek başına bir bildirim oluşturur ve `AckRequested` iletileri.</span><span class="sxs-lookup"><span data-stu-id="68f1a-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="68f1a-222">TerminateSequence iletisi</span><span class="sxs-lookup"><span data-stu-id="68f1a-222">TerminateSequence message</span></span>  
 <span data-ttu-id="68f1a-223">WCF değerlendirir `TerminateSequence` tek yönlü bir işlem olarak HTTP yanıtı anlamına gelen bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="68f1a-224">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="68f1a-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="68f1a-225">Bağlama</span><span class="sxs-lookup"><span data-stu-id="68f1a-225">Binding</span></span>  
 <span data-ttu-id="68f1a-226">WCF bir dizisi üzerinde bir gelen ve giden bir Http kanalı kullanılarak bir tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="68f1a-227">WCF HTTP isteklerini tüm iletileri iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="68f1a-228">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="68f1a-229">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-230">WCF Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="68f1a-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="68f1a-231">WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok.</span><span class="sxs-lookup"><span data-stu-id="68f1a-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="68f1a-232">WCF Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="68f1a-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="68f1a-233">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="68f1a-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="68f1a-234">Bağlama</span><span class="sxs-lookup"><span data-stu-id="68f1a-234">Binding</span></span>  
 <span data-ttu-id="68f1a-235">WCF bir gelen ve giden bir HTTP kanalı iki sıraları kullanarak bir iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="68f1a-236">WCF HTTP isteklerini tüm iletileri iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="68f1a-237">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="68f1a-238">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-239">WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="68f1a-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="68f1a-240">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="68f1a-241">WCF gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="68f1a-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="68f1a-242">Sıra yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="68f1a-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="68f1a-243">WCF iki sıraları tam çift yönlü bir oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="68f1a-244">Bir dizi hataları bir arıza oluşturma sırasında WCF hem sıraları alınmasını uzak uç nokta bekler.</span><span class="sxs-lookup"><span data-stu-id="68f1a-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="68f1a-245">Bir dizi hataları bir arıza okuma sırasında WCF hem sıraları hataları.</span><span class="sxs-lookup"><span data-stu-id="68f1a-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="68f1a-246">WCF giden sırası kapatın ve gelen sırası iletileri işlemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="68f1a-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="68f1a-247">Buna karşılık, WCF gelen sırası kapatma işlemek ve kendi giden sırasını iletileri göndermeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="68f1a-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="68f1a-248">İstek-yanıt, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="68f1a-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="68f1a-249">Bağlama</span><span class="sxs-lookup"><span data-stu-id="68f1a-249">Binding</span></span>  
 <span data-ttu-id="68f1a-250">İstek-yanıt ileti değişim deseni iki kullanarak üzerinde bir HTTP kanalı dizilerinin ve WCF tek yönlü sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="68f1a-251">WCF HTTP isteklerini istek sırasının iletileri iletmek için ve HTTP yanıtlarını yanıt sırasının tüm iletileri iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="68f1a-252">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-253">WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="68f1a-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="68f1a-254">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="68f1a-255">WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="68f1a-256">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="68f1a-256">One-way Message</span></span>  
 <span data-ttu-id="68f1a-257">Tek yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="68f1a-258">`SequenceAcknowledgement` Aktarılan ileti kabul gerekir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="68f1a-259">WCF Yanıtlayıcı onay, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="68f1a-260">İki şekilde iletileri</span><span class="sxs-lookup"><span data-stu-id="68f1a-260">Two Way Messages</span></span>  
 <span data-ttu-id="68f1a-261">İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="68f1a-262">Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.</span><span class="sxs-lookup"><span data-stu-id="68f1a-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="68f1a-263">WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="68f1a-264">Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="68f1a-265">Yanıt yeniden deneniyor</span><span class="sxs-lookup"><span data-stu-id="68f1a-265">Retrying Replies</span></span>  
 <span data-ttu-id="68f1a-266">WCF HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="68f1a-267">Bu nedenle, WCF Başlatıcı istek sırası iletisi onaylandığında, ancak yerine HTTP yanıtı bir bildirim, kullanıcı iletisi veya hataya getirirken bir istek sırası iletisi yeniden deneniyor durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="68f1a-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="68f1a-268">WCF Yanıtlayıcı yanıt bağıntılı isteğin HTTP isteği leg üzerinde yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="68f1a-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="68f1a-269">LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="68f1a-270">WCF Başlatıcı oluşturur ve HTTP isteği leg üzerinde boş bodied son ileti iletir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="68f1a-271">WCF yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="68f1a-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="68f1a-272">İstek sırasının boş bodied son iletisiyle yanıt sırasının boş bodied son ileti WCF Yanıtlayıcı yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="68f1a-273">WCF Yanıtlayıcı içinde eylem URI'si değil son bir ileti alırsa http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF yanıtları son iletiyle.</span><span class="sxs-lookup"><span data-stu-id="68f1a-273">If the WCF Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF replies with a last message.</span></span> <span data-ttu-id="68f1a-274">Bir iki yönlü ileti exchange protokol söz konusu olduğunda, son uygulama ileti taşır; bir tek yönlü ileti exchange protokol söz konusu olduğunda, son ileti boştur.</span><span class="sxs-lookup"><span data-stu-id="68f1a-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="68f1a-275">WCF Yanıtlayıcı onay yanıtı sırasının boş bodied son ileti için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="68f1a-276">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-277">Tüm isteklerin geçerli bir yanıt teslim aldıktan sonra WCF Başlatıcı oluşturur ve istek sırasının iletir `TerminateSequence` HTTP isteği leg iletisi.</span><span class="sxs-lookup"><span data-stu-id="68f1a-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="68f1a-278">WCF yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="68f1a-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="68f1a-279">WCF Yanıtlayıcı yanıtları istek sırası için 's `TerminateSequence` yanıt sırasının iletisiyle `TerminateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="68f1a-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="68f1a-280">Normal kapatma dizisindeki her ikisi de `TerminateSequence` iletilerini taşıyan tam kapsamlı bir `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="68f1a-281">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="68f1a-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="68f1a-282">Bağlama</span><span class="sxs-lookup"><span data-stu-id="68f1a-282">Binding</span></span>  
 <span data-ttu-id="68f1a-283">WCF iki sıraları üzerinden bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1a-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="68f1a-284">WCF HTTP isteklerini tüm iletileri iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="68f1a-285">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="68f1a-286">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="68f1a-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="68f1a-287">WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="68f1a-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="68f1a-288">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68f1a-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="68f1a-289">WCF gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="68f1a-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="68f1a-290">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="68f1a-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="68f1a-291">Tüm uygulama istek iletileri ayı WCF Başlatıcı sağlar bir `MessageId` ve `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="68f1a-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="68f1a-292">WCF Başlatıcı geçerlidir `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisi üzerinde uç noktası başvuru.</span><span class="sxs-lookup"><span data-stu-id="68f1a-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="68f1a-293">Bu gelen istek iletileri ayı WCF Yanıtlayıcı gerektiren bir `MessageId` ve `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="68f1a-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="68f1a-294">Her iki uç nokta referansının URI sağlar WCF Yanıtlayıcı `CreateSequence` ve tüm uygulama istek iletilerini aynıdır.</span><span class="sxs-lookup"><span data-stu-id="68f1a-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
