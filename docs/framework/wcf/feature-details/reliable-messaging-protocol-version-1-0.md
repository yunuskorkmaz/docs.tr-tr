---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 02a0815f62999c27507ed5e1610f090e944c135a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55073219"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="f3e6f-102">Güvenilir Mesajlaşma Protokolü sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="f3e6f-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="f3e6f-103">WS-Reliable Mesajlaşma için bu konuda Windows Communication Foundation (WCF) uygulama ayrıntılarını kapsayan Şubat 2005 (sürüm 1.0) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="f3e6f-104">WCF WS-Reliable Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="f3e6f-105">İle başlayarak WS-ReliableMessaging sürüm 1.0 protokolü uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3e6f-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="f3e6f-106">WS-Reliable Protokolü WCF uygulandığına Mesajlaşma Şubat 2005 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="f3e6f-107">Kolaylık olması için konunun aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="f3e6f-108">Başlatıcı: WS güvenilir ileti sırası oluşturma başlatan istemci</span><span class="sxs-lookup"><span data-stu-id="f3e6f-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="f3e6f-109">Yanıtlayıcı: başlatanın isteği aldığı hizmeti</span><span class="sxs-lookup"><span data-stu-id="f3e6f-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="f3e6f-110">Bu belge, aşağıdaki tabloda ad alanlarını ve önekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="f3e6f-111">Ön eki</span><span class="sxs-lookup"><span data-stu-id="f3e6f-111">Prefix</span></span>|<span data-ttu-id="f3e6f-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="f3e6f-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="f3e6f-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="f3e6f-114">netrm</span><span class="sxs-lookup"><span data-stu-id="f3e6f-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="f3e6f-115">s</span><span class="sxs-lookup"><span data-stu-id="f3e6f-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="f3e6f-116">wsa</span><span class="sxs-lookup"><span data-stu-id="f3e6f-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="f3e6f-117">wsse</span><span class="sxs-lookup"><span data-stu-id="f3e6f-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="f3e6f-118">İleti</span><span class="sxs-lookup"><span data-stu-id="f3e6f-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="f3e6f-119">Dizisi kurma iletileri</span><span class="sxs-lookup"><span data-stu-id="f3e6f-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="f3e6f-120">WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` iletileri güvenilir ileti dizisi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="f3e6f-121">Aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-121">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f3e6f-122">B1101: WCF Başlatıcı isteğe bağlı süre sonu öğesinde oluşturmaz `CreateSequence` ileti veya durumlarda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="f3e6f-123">B1102: Erişirken `CreateSequence` iletisi, WCF`Responder` gönderir ve her ikisi de alır `Expires` öğeler var ancak bunların değerlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="f3e6f-124">WS-Reliable Mesajlaşma tanıtır `Offer` iki oturum form bağıntılı dizileri gruplarıdır kurmak için bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="f3e6f-125">R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da dizisi kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` iki bağıntılı oluşturan öğesini gruplarıdır dizileri veya Reddet`CreateSequence`istek.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="f3e6f-126">R1104: `SequenceAcknowledgement` ve ters sırası akan uygulama iletileri için gönderilmelidir `ReplyTo` uç nokta başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="f3e6f-127">R1105: `AcksTo` ve `ReplyTo` uç nokta başvurularının `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="f3e6f-128">WCF Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="f3e6f-129">R1106: `AcksTo` ve `ReplyTo` uç nokta başvuruları `CreateSequence` başvuru parametrelerinin aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="f3e6f-130">WCF mecbur kılmaz ancak varsayar, [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="f3e6f-131">R1107: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` listesiyse dizileri üzerinde akan uygulama iletileri gönderilen, için ve `ReplyTo` uç nokta başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="f3e6f-132">R1108: İki ters dizileri teklif mekanizması kullanılarak oluşturulduğunda `[address]` özelliği `wsrm:AcksTo` uç nokta başvurusu alt öğesi `wsrm:Accept` öğesinin `CreateSequenceResponse` hedefiniURIbyte-wiseeşleşmelidir`CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="f3e6f-133">R1109: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletilere katkıda bulunanlar tarafından gönderilen iletiler için aynı uç nokta başvurusu gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="f3e6f-134">WS-Reliable Mesajlaşma WCF Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="f3e6f-135">WCF'ın WS-Reliable Mesajlaşma uygulaması sağlayan güvenilir oturum için tek yönlü, istek-yanıt ve tam çift yönlü Mesajlaşma desenleri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="f3e6f-136">WS-Reliable Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı listesiyse dizileri oluşturmanıza olanak sağlar ve tüm uç noktalar iletisi için uygun bir oturumu Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="f3e6f-137">WCF oturum tutarlılığı için uçtan uca koruma dahil olmak üzere oturum için güvenlik garantisi sunduğundan, aynı hedefe yönelik aynı tarafa iletilerinin geliş emin olmak pratik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="f3e6f-138">Bu uygulama iletilerinde ardışık-yedekleme, sıralı onayları da sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="f3e6f-139">Bu nedenle, kısıtlamaları R1104 R1105 ve R1108 WCF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="f3e6f-140">Örneği bir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-140">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="f3e6f-141">Örneği bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="f3e6f-142">Dizisi</span><span class="sxs-lookup"><span data-stu-id="f3e6f-142">Sequence</span></span>  
 <span data-ttu-id="f3e6f-143">Dizilerine uygulama kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-143">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="f3e6f-144">B1201:WCF oluşturur ve erişimleri numaraları daha yüksek sıralı `xs:long`'s maksimum kapsamlı değeri, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="f3e6f-145">B1202:WCF her zaman bir boş gövdeli son iletisi ' % s'eylemi URI'si ile oluşturur, `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>  
  
-   <span data-ttu-id="f3e6f-146">B1203: WCF alır ve sunan bir ileti içeren bir dizisi üst bilgisiyle bir `LastMessage` öğesi ' % s'eylemi URI'si değil sürece `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>  
  
 <span data-ttu-id="f3e6f-147">Bir örnek dizisi üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-147">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="f3e6f-148">AckRequested üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="f3e6f-148">AckRequested Header</span></span>  
 <span data-ttu-id="f3e6f-149">WCF kullanan `AckRequested` tutma mekanizması olarak başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="f3e6f-150">WCF isteğe bağlı oluşturmaz `MessageNumber` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="f3e6f-151">Bir mesajı almak bağlı bir `AckRequested` içeren üstbilgi `MessageNumber` WCF öğesini yoksayar `MessageNumber` öğenin değeri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="f3e6f-152">SequenceAcknowledgement üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="f3e6f-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="f3e6f-153">WCF WS-Reliable Mesajlaşma sağlanan sıralı onayları için ardışık mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="f3e6f-154">R1401: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` üst bilgisi için hedeflenen alıcı aktarılan herhangi bir uygulama iletisi içinde eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="f3e6f-155">B1402: Ne zaman WCF gerekir Oluşturma sırası iletileri alma önce bir bildirim (örneğin, karşılamak için bir `AckRequested` ileti), WCF oluşturur bir `SequenceAcknowledgement` aralığı 0-0, aşağıdaki örnekte gösterildiği gibi içeren üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="f3e6f-156">B1403: WCF oluşturmaz `SequenceAcknowledgement` içeren üst bilgiler bir `Nack` öğesi ancak destekler `Nack` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="f3e6f-157">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="f3e6f-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="f3e6f-158">WS-Reliable Mesajlaşma hataları WCF uygulaması için geçerli olan sınırlamalar listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="f3e6f-159">B1501: WCF oluşturmaz `MessageNumberRollover` hataları.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="f3e6f-160">B1502:WCF uç noktası oluşturabilir `CreateSequenceRefused` Belirtimi'nde açıklanan hataları.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="f3e6f-161">B1503:when hizmet uç noktası, bağlantı sınırına ulaştığında ve yeni bağlantı işlenemiyor, ek bir WCF oluşturur `CreateSequenceRefused` alt kod, hata `netrm:ConnectionLimitReached`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="f3e6f-162">WS-Addressing hataları</span><span class="sxs-lookup"><span data-stu-id="f3e6f-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="f3e6f-163">WS-Reliable Mesajlaşma WS-Addressing kullandığından WCF WS-Reliable Mesajlaşma uygulaması WS-Addressing hatalarının oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="f3e6f-164">Bu bölüm, WCF WS-Reliable Mesajlaşma katmanında açıkça oluşturur WS-Addressing hataları kapsar:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="f3e6f-165">Aşağıdakilerden biri doğruysa B1601:WCF ileti adresleme üstbilgi gereken hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="f3e6f-166">Bir ileti eksik bir `Sequence` başlığı ve bir `Action` başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="f3e6f-167">A `CreateSequence` ileti eksik bir `MessageId` başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="f3e6f-168">A `CreateSequence` ileti eksik bir `ReplyTo` başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="f3e6f-169">B1602:WCF eksik olduğunu belirten bir ileti girilecek yanıt eylemi desteklenmiyor hatası oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS-Reliable Mesajlaşma belirtiminde değil başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="f3e6f-170">Uç nokta incelenmesi göre sırası işlemez belirtmek için kullanılabilir uç nokta hatası B1603:WCF oluşturur `CreateSequence` ileti üstbilgileri adresleme.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="f3e6f-171">İletişim kuralı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3e6f-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="f3e6f-172">WS-Addressing ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3e6f-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="f3e6f-173">WCF WS-Addressing iki sürümlerini destekler: WS-Addressing 2004/08 WS-ADDR ve W3C WS-Addressing 1.0 önerileri [WS-ADDR-CORE] ve [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="f3e6f-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="f3e6f-174">While WS-Reliable Mesajlaşma belirtimi bahsetmeleri yalnızca WS-Addressing 2004/08, onu kısıtlamaz kullanılacak WS-Addressing sürümü.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="f3e6f-175">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-175">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f3e6f-176">R2101: hem WS-Addressing 2004/08 ve WS-Addressing 1.0 WS-Reliable Mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="f3e6f-177">R2102:A tek sürüm, WS-Addressing kullanılan, WS-Reliable Mesajlaşma belirli bir dizi veya bir çift ters dizileri kullanılarak bağıntılı boyunca `wsrm:Offer` mekanizması.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="f3e6f-178">SOAP ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3e6f-178">Composition with SOAP</span></span>  
 <span data-ttu-id="f3e6f-179">WCF SOAP 1.1 ve SOAP 1.2 WS-Reliable Mesajlaşma ile destekler.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="f3e6f-180">WS-güvenlik ve WS-SecureConversation ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3e6f-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="f3e6f-181">WCF ile WS-Secure Conversation güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve oluşturma'yı kullanarak dizileri WS-Reliable Mesajlaşma için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="f3e6f-182">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-182">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f3e6f-183">R2301: bütünlüğü yanı sıra bir WS-Reliable Mesajlaşma dizisi bütünlüğünü ve tek tek iletilerin gizliliğini korumak için WS-Secure Conversation kullanılmalıdır WCF gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="f3e6f-184">R2302:AWS-Secure Conversation oturumu WS-Reliable Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="f3e6f-185">R2303: WS-Reliable Mesajlaşma dizisi ömrü oturumunun ömrü, WS-Secure Conversation aşarsa `SecurityContextToken` kullanarak WS-Secure Conversation gerekir yenilenmiş karşılık gelen WS-Secure konuşma yenileme bağlama kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="f3e6f-186">B2304:ws-güvenilir Mesajlaşma dizisi veya bir çift bağlantılı listesiyse dizileri tek bir WS-SecureConversation oturumuna bağlı her zaman.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="f3e6f-187">WCF kaynağının oluşturduğu `wsse:SecurityTokenReference` öğesi öğe genişletilebilirlik bölümünde `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="f3e6f-188">WS-Secure Conversation ile oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="f3e6f-189">WS-Reliable Mesajlaşma WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="f3e6f-190">WCF kullanan WS-Reliable Mesajlaşma WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özelliklerini tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="f3e6f-191">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-191">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f3e6f-192">B3001: WCF ekler `wsrm:RMAssertion` WS-Policy onaylama için `wsdl:binding` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="f3e6f-193">WCF destekleyen iki ek `wsdl:binding` ve `wsdl:port` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="f3e6f-194">B3002: WCF WS-Reliable Mesajlaşma onaylama aşağıdaki isteğe bağlı özelliklerini destekler ve bunlar üzerindeki denetimi WCF sağlar`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="f3e6f-195">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="f3e6f-196">WS-Reliable Mesajlaşma akışı kontrol uzantısı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="f3e6f-197">WCF WS-Reliable Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="f3e6f-198">Akış denetimi etkin ayarlayarak <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f3e6f-199">WCF için uygulanan kısıtlamaları listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-199">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f3e6f-200">B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="f3e6f-201">B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi başlığı.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="f3e6f-202">B4003: WCF kullanan `netrm:BufferRemaining` kaç yeni güvenilir Mesajlaşma hedef iletileri göstermek için ara belleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="f3e6f-203">B4004: WCF güvenilir Mesajlaşma hizmeti hedef uygulama güvenilir Mesajlaşma iletileri hızlı bir şekilde zaman gönderilen ileti sayısını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="f3e6f-204">Hedef arabelleği güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="f3e6f-205">B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile kapsamlı 4096 arasında ve 0 arasında tamsayı değerlerini okur ve `xs:int`'s `maxInclusive` 214748364 kapsamlı değeri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="f3e6f-206">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="f3e6f-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="f3e6f-207">Bu bölümde, WS-Reliable Mesajlaşma için farklı ileti Exchange desenleri kullanıldığında WCF'ın davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="f3e6f-208">Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="f3e6f-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="f3e6f-209">Adreslenebilir olmayan Başlatıcı: Başlatıcı güvenlik duvarı ardında kaldığı; Yanıtlayıcı, yalnızca HTTP yanıtları için Başlatıcı iletileri teslim edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="f3e6f-210">Başlatıcı adreslenebilir: Başlatıcı hem Yanıtlayıcı HTTP isteklerini gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantı kurulur.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="f3e6f-211">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f3e6f-212">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-212">Binding</span></span>  
 <span data-ttu-id="f3e6f-213">WCF bir HTTP kanalı üzerinden bir dizisi kullanırken bir yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="f3e6f-214">WCF HTTP isteklerini RMD gelen tüm iletileri RMS'ye aktarmaya tüm ileti RMS RMD ve HTTP yanıtı aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f3e6f-215">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-216">WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f3e6f-217">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce herhangi bir teklif vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f3e6f-218">WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="f3e6f-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f3e6f-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="f3e6f-220">WCF Başlatıcı yanıtlama bir onayları tüm iletileri işleyen `CreateSequence` iletisi ve hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="f3e6f-221">WCF Yanıtlayıcı her zaman yanıt hem dizisi olarak tek başına bir bildirim oluşturur ve `AckRequested` iletileri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="f3e6f-222">TerminateSequence iletisi</span><span class="sxs-lookup"><span data-stu-id="f3e6f-222">TerminateSequence message</span></span>  
 <span data-ttu-id="f3e6f-223">WCF işler `TerminateSequence` , tek yönlü bir işlem olarak HTTP yanıtını bir boş gövdesi ve 202 HTTP durum kodu sahiptir yani.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="f3e6f-224">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f3e6f-225">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-225">Binding</span></span>  
 <span data-ttu-id="f3e6f-226">WCF bir dizi üzerinde bir gelen ve giden bir Http kanalı kullanan tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="f3e6f-227">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f3e6f-228">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f3e6f-229">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-230">WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f3e6f-231">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce herhangi bir teklif vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f3e6f-232">WCF Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="f3e6f-233">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f3e6f-234">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-234">Binding</span></span>  
 <span data-ttu-id="f3e6f-235">WCF iki diziyi bir gelen ve giden bir HTTP kanalı kullanarak iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f3e6f-236">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f3e6f-237">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f3e6f-238">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-239">WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f3e6f-240">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f3e6f-241">WCF gönderir `CreateSequenceResponse` yönelik HTTP isteği için `CreateSequence`'s `ReplyTo` uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="f3e6f-242">Dizisi ömrü</span><span class="sxs-lookup"><span data-stu-id="f3e6f-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="f3e6f-243">WCF iki sıranın tam çift yönlü bir oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="f3e6f-244">Bir sıralı hataları bir hata oluşturma sırasında uzak uç noktanın hem dizileri hata WCF bekliyor.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="f3e6f-245">Bir sıralı hataları bir hataya okuma sırasında WCF hem dizileri hataları.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="f3e6f-246">WCF giden kendi dizisi kapatın ve gelen kendi sıra üzerinde iletileri işleme devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="f3e6f-247">Buna karşılık, WCF gelen dizisi kapatma işlemi ve bu giden kendi sıra üzerinde iletileri göndermeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="f3e6f-248">İstek-yanıt, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f3e6f-249">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-249">Binding</span></span>  
 <span data-ttu-id="f3e6f-250">WCF tek yönlü sağlar ve istek-yanıt ileti değişim deseni iki kullanarak tek HTTP kanalı serileri.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="f3e6f-251">WCF HTTP isteklerini isteği sırasının ileti aktarmaya ve HTTP yanıtlarını yanıt sırasının ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f3e6f-252">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-253">WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f3e6f-254">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f3e6f-255">WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="f3e6f-256">Tek yönlü mesaj</span><span class="sxs-lookup"><span data-stu-id="f3e6f-256">One-way Message</span></span>  
 <span data-ttu-id="f3e6f-257">WCF Başlatıcı bir tek yönlü mesaj değişimi Protokolü başarıyla tamamlamak için bir istek sırası iletisi HTTP isteğini iletir ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="f3e6f-258">`SequenceAcknowledgement` Aktarılan iletiyi kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="f3e6f-259">WCF Yanıtlayıcı bir bildirim, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="f3e6f-260">İki şekilde iletileri</span><span class="sxs-lookup"><span data-stu-id="f3e6f-260">Two Way Messages</span></span>  
 <span data-ttu-id="f3e6f-261">İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteğini bir istek sırası iletisi aktarır ve HTTP yanıtını yanıt sırası iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="f3e6f-262">Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi sıkan aktarılan.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="f3e6f-263">WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="f3e6f-264">Tek yönlü iletileri varlığını ve uygulama yanıt zamanlaması nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası ile hiçbir bağıntısı vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="f3e6f-265">Yanıt yeniden deneniyor</span><span class="sxs-lookup"><span data-stu-id="f3e6f-265">Retrying Replies</span></span>  
 <span data-ttu-id="f3e6f-266">WCF için iki yönlü ileti exchange Protokolü bağıntısı HTTP isteği-yanıt bağıntısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="f3e6f-267">Bu nedenle, WCF Başlatıcı bir istek sırası iletisi istek sırası iletisi onaylandığında, ancak yerine HTTP yanıtını bir bildirim, kullanıcı iletisi veya hata getirirken yeniden deneniyor durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="f3e6f-268">WCF Yanıtlayıcı yanıt, yanıt bağıntılı isteğin HTTP isteği oluşturan üzerinde yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="f3e6f-269">LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="f3e6f-270">WCF Başlatıcı oluşturur ve bir HTTP isteği oluşturan üzerinde boş bodied son ileti iletir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="f3e6f-271">WCF bir yanıt gerektirir, ancak gerçek bir yanıt iletisi yok sayar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f3e6f-272">WCF Yanıtlayıcı isteği sırasının boş gövdeli son iletiye yanıt sırasının boş gövdeli son ileti ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="f3e6f-273">WCF Yanıtlayıcı, ' % s'eylemi URI'si değil bir son ileti alırsa `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, son bir ileti ile WCF yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="f3e6f-274">İki yönlü ileti değişimi Protokolü söz konusu olduğunda, uygulama iletisi son iletiyi taşır; tek yönlü mesaj değişimi Protokolü söz konusu olduğunda, son iletinin boştur.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="f3e6f-275">WCF Yanıtlayıcı yanıt sırasının boş gövdeli son iletisi için bir onay gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f3e6f-276">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-277">Tüm istekler geçerli bir yanıt alındığında, bu WCF Başlatıcı oluşturur ve istek sırasının iletir `TerminateSequence` HTTP isteği oluşturan iletisi.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="f3e6f-278">WCF bir yanıt gerektirir, ancak gerçek bir yanıt iletisi yok sayar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f3e6f-279">WCF Yanıtlayıcı isteği sırasının için yanıtlar `TerminateSequence` iletisiyle yanıt sırasının `TerminateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="f3e6f-280">Normal kapatma dizideki her ikisi de `TerminateSequence` iletilerini taşıyan çeşitli `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="f3e6f-281">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f3e6f-282">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f3e6f-282">Binding</span></span>  
 <span data-ttu-id="f3e6f-283">WCF iki diziyi üzerinde bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f3e6f-284">WCF HTTP isteklerini tüm ileti aktarmaya kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f3e6f-285">Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f3e6f-286">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f3e6f-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f3e6f-287">WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f3e6f-288">WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f3e6f-289">WCF gönderir `CreateSequenceResponse` yönelik HTTP isteği için `CreateSequence`'s `ReplyTo` uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="f3e6f-290">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="f3e6f-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="f3e6f-291">Tüm uygulama istek iletileri ayı WCF Başlatıcı sağlar bir `MessageId` ve `ReplyTo` uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="f3e6f-292">WCF Başlatıcı geçerli `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisinde uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="f3e6f-293">WCF Yanıtlayıcı, gelen istek iletisi ayı gerektiren bir `MessageId` ve `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="f3e6f-294">Her iki uç nokta referansının URI sağlar WCF Yanıtlayıcı `CreateSequence` ve tüm uygulama istek iletilerinin aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e6f-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
