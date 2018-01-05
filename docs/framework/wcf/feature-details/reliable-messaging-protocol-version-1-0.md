---
title: "Güvenilir Mesajlaşma Protokolü sürüm 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a32c16067446459817e9943c2d729a67373a0333
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="53de7-102">Güvenilir Mesajlaşma Protokolü sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="53de7-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="53de7-103">Bu konuda ele alınmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WS güvenilir Mesajlaşma uygulama ayrıntılarını Şubat 2005 (sürüm 1.0) protokolünü kullanarak HTTP aktarımı birlikte çalışma için gerekli.</span><span class="sxs-lookup"><span data-stu-id="53de7-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-104">WS güvenilir Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler.</span><span class="sxs-lookup"><span data-stu-id="53de7-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="53de7-105">WS-ReliableMessaging 1.0 sürümü protokolü ile başlayan uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53de7-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="53de7-106">WS-güvenilir Protokolü uygulandığına Mesajlaşma Şubat 2005 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tarafından <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="53de7-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="53de7-107">Kolaylık olması için konunun aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="53de7-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="53de7-108">Başlatıcı: WS güvenilir ileti sırası oluşturması başlatan istemci</span><span class="sxs-lookup"><span data-stu-id="53de7-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="53de7-109">Yanıtlayıcı: başlatanın isteği alan hizmeti</span><span class="sxs-lookup"><span data-stu-id="53de7-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="53de7-110">Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="53de7-111">önek</span><span class="sxs-lookup"><span data-stu-id="53de7-111">Prefix</span></span>|<span data-ttu-id="53de7-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="53de7-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="53de7-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="53de7-113">wsrm</span></span>|<span data-ttu-id="53de7-114">http://schemas.xmlsoap.org/ws/2005/02/RM</span><span class="sxs-lookup"><span data-stu-id="53de7-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="53de7-115">netrm</span><span class="sxs-lookup"><span data-stu-id="53de7-115">netrm</span></span>|<span data-ttu-id="53de7-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="53de7-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="53de7-117">s</span><span class="sxs-lookup"><span data-stu-id="53de7-117">s</span></span>|<span data-ttu-id="53de7-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="53de7-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="53de7-119">wsa</span><span class="sxs-lookup"><span data-stu-id="53de7-119">wsa</span></span>|<span data-ttu-id="53de7-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="53de7-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="53de7-121">wsse</span><span class="sxs-lookup"><span data-stu-id="53de7-121">wsse</span></span>|<span data-ttu-id="53de7-122">http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="53de7-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="53de7-123">İleti</span><span class="sxs-lookup"><span data-stu-id="53de7-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="53de7-124">Sıra kurma iletileri</span><span class="sxs-lookup"><span data-stu-id="53de7-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-125">uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir ileti sırası kurmak için iletileri.</span><span class="sxs-lookup"><span data-stu-id="53de7-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="53de7-126">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="53de7-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="53de7-127">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı isteğe bağlı Expires öğesinde oluşturmaz `CreateSequence` ileti veya durumda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53de7-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="53de7-128">B1102: erişirken `CreateSequence` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` alıp gönderen her ikisi de `Expires` var ancak değerlerine kullanmaz öğeleri.</span><span class="sxs-lookup"><span data-stu-id="53de7-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="53de7-129">WS güvenilir Mesajlaşma tanıtır `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="53de7-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="53de7-130">R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da sırası kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` öğesi, iki bağıntılı oluşturan gruplarıdır dizileri veya Reddet`CreateSequence` isteği.</span><span class="sxs-lookup"><span data-stu-id="53de7-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="53de7-131">R1104: `SequenceAcknowledgement` ve ters sıra üzerinde akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="53de7-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="53de7-132">R1105: `AcksTo` ve `ReplyTo` endpoint başvuran `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53de7-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="53de7-133">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="53de7-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="53de7-134">R1106: `AcksTo` ve `ReplyTo` Endpoint başvurularında `CreateSequence` aynı başvurusu parametre kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53de7-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-135">zorunlu değildir ancak varsayar o [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.</span><span class="sxs-lookup"><span data-stu-id="53de7-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="53de7-136">R1107: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` ve üzerinde ters sıraları akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="53de7-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="53de7-137">R1108: iki gruplarıdır zaman serileri teklif mekanizması kullanılarak oluşturulan `[address]` özelliği `wsrm:AcksTo` bitiş noktası başvurusu alt öğesi olan `wsrm:Accept` öğesinin `CreateSequenceResponse` hedef URI byte-wise eşleşmelidir, `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="53de7-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="53de7-138">R1109: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletileri için onayları tarafından gönderilen iletilerin gönderileceği aynı uç nokta referansı.</span><span class="sxs-lookup"><span data-stu-id="53de7-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-139">WS güvenilir Mesajlaşma Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-140">'s uygulamasını WS güvenilir Mesajlaşma sağlar güvenilir oturum tek yönlü, istek-yanıt ve tam çift yönlü desenleri Mesajlaşma.</span><span class="sxs-lookup"><span data-stu-id="53de7-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="53de7-141">WS güvenilir Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı ters sıraları oluşturmanıza olanak sağlar ve tüm uç noktaları iletisi için uygun bir oturum Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="53de7-142">Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik garanti sağlayan uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere bu tür bir oturum için aynı tarafa yönelik iletilerin aynı hedefte ulaşan emin olmak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="53de7-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="53de7-143">Bu ardışık-yedeklemelerini dizisi onayları uygulama iletilerinde de sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="53de7-144">R1104, R1105 ve R1108 kısıtlamaları uygulamak bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53de7-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="53de7-145">Örnek olarak bir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-145">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="53de7-146">Örnek olarak bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="53de7-147">Sırası</span><span class="sxs-lookup"><span data-stu-id="53de7-147">Sequence</span></span>  
 <span data-ttu-id="53de7-148">Dizilerine uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="53de7-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="53de7-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve daha yüksek sıra numaraları erişir `xs:long`'s en büyük içermeli değer, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="53de7-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="53de7-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman bir boş bodied son iletisiyle http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage eylem URI'si oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53de7-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="53de7-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] alır ve içeren sırası üstbilgi içeren bir ileti teslim bir `LastMessage` öğesi eylem URI'si http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage değil sürece.</span><span class="sxs-lookup"><span data-stu-id="53de7-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="53de7-152">Bir sıra üstbilgisi örneği.</span><span class="sxs-lookup"><span data-stu-id="53de7-152">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="53de7-153">AckRequested üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="53de7-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-154">kullanan `AckRequested` tutma mekanizması olarak üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-155">İsteğe bağlı oluşturmaz `MessageNumber` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53de7-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="53de7-156">İçeren bir ileti alır almaz bir `AckRequested` üstbilgisinin içeren `MessageNumber` öğesi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yoksayar `MessageNumber` aşağıdaki örnekte gösterildiği gibi öğenin değeri.</span><span class="sxs-lookup"><span data-stu-id="53de7-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="53de7-157">SequenceAcknowledgement üstbilgisi</span><span class="sxs-lookup"><span data-stu-id="53de7-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-158">WS güvenilir Mesajlaşma içinde sağlanan dizisi bildirimleri için ardışık mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="53de7-159">R1401: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi.</span><span class="sxs-lookup"><span data-stu-id="53de7-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="53de7-160">B1402: Zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dizisi iletileri alma önce onay oluşturmanız gerekir (örneğin karşılamak için bir `AckRequested` ileti), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur bir `SequenceAcknowledgement` aralık 0-0, aşağıda gösterildiği gibi içeriyor üstbilgisi örnek.</span><span class="sxs-lookup"><span data-stu-id="53de7-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="53de7-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri bir `Nack` öğesi ancak destekler `Nack` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="53de7-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="53de7-162">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="53de7-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="53de7-163">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama hatalarının WS güvenilir Mesajlaşma:</span><span class="sxs-lookup"><span data-stu-id="53de7-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="53de7-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `MessageNumberRollover` hataları.</span><span class="sxs-lookup"><span data-stu-id="53de7-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="53de7-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası oluşturabilir `CreateSequenceRefused` hataları belirtiminde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="53de7-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="53de7-166">B1503:when hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ek bir oluşturur `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="53de7-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="53de7-167">WS-adresleme hataları</span><span class="sxs-lookup"><span data-stu-id="53de7-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="53de7-168">WS güvenilir Mesajlaşma WS adresleme kullandığından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenilir Mesajlaşma uygulaması WS adresleme hataları görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="53de7-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="53de7-169">Bu bölümde kapsar WS adresleme hataları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] açıkça WS güvenilir Mesajlaşma katmanında oluşturur:</span><span class="sxs-lookup"><span data-stu-id="53de7-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="53de7-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] şunlardan biri doğru olduğunda hata ileti başlığı adresleme gereken oluşturur:</span><span class="sxs-lookup"><span data-stu-id="53de7-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="53de7-171">Bir ileti eksik bir `Sequence` başlığı ve bir `Action` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="53de7-172">A `CreateSequence` ileti eksik bir `MessageId` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="53de7-173">A `CreateSequence` ileti eksik bir `ReplyTo` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="53de7-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] eksik mesaja eylemi desteklenmiyor hataya oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS güvenilir Mesajlaşma belirtiminde değil üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="53de7-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta incelenmesi temel sıralı işlemez belirtmek için uç nokta kullanılamaz hatası oluşturur `CreateSequence` ileti üstbilgilerini adresleme.</span><span class="sxs-lookup"><span data-stu-id="53de7-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="53de7-176">İletişim kuralı oluşturma</span><span class="sxs-lookup"><span data-stu-id="53de7-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="53de7-177">WS-adresleme ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="53de7-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-178">WS-adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="53de7-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="53de7-179">While WS güvenilir Mesajlaşma belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü.</span><span class="sxs-lookup"><span data-stu-id="53de7-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="53de7-180">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="53de7-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="53de7-181">R2101: hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53de7-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="53de7-182">R2102:A tek sürümü WS adresleme için kullanılan, belirli bir WS güvenilir Mesajlaşma dizi veya ters sıraları kullanarak bağıntılı çifti boyunca `wsrm:Offer` mekanizması.</span><span class="sxs-lookup"><span data-stu-id="53de7-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="53de7-183">SOAP ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="53de7-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-184">SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile destekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="53de7-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="53de7-185">WS güvenliği ve WS-SecureConversation ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="53de7-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-186">güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS güvenilir Mesajlaşma dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="53de7-187">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="53de7-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="53de7-188">R2301: WS güvenilir Mesajlaşma dizisi bütünlüğü yanı sıra bütünlüğünü ve tek bir ileti gizliliğini korumak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenli konuşma kullanılmalıdır gerektirir.</span><span class="sxs-lookup"><span data-stu-id="53de7-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="53de7-189">R2302:AWS-güvenli konuşma oturum WS güvenilir Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53de7-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="53de7-190">R2303: WS güvenilir Mesajlaşma ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="53de7-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="53de7-191">B2304:ws-güvenilir Mesajlaşma dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.</span><span class="sxs-lookup"><span data-stu-id="53de7-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="53de7-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kaynağı oluşturur `wsse:SecurityTokenReference` öğesi genişletilebilirlik bölümünü öğesinde `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="53de7-193">WS-güvenli konuşma oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53de7-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="53de7-194">WS güvenilir Mesajlaşma WS-Policy onaylama</span><span class="sxs-lookup"><span data-stu-id="53de7-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-195">WS güvenilir Mesajlaşma WS-Policy onaylama kullanan `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="53de7-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="53de7-196">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="53de7-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="53de7-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iliştirir `wsrm:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="53de7-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-198">Her iki ekleri destekler `wsdl:binding` ve `wsdl:port` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="53de7-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="53de7-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenilir Mesajlaşma onaylama aşağıdaki isteğe bağlı özellikleri destekler ve bunları üzerinde denetim sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="53de7-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="53de7-200">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53de7-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="53de7-201">Akış Denetim WS güvenilir Mesajlaşma uzantısı</span><span class="sxs-lookup"><span data-stu-id="53de7-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-202">WS güvenilir Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="53de7-203">Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``bool` özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="53de7-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="53de7-204">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="53de7-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="53de7-205">B4001: Güvenilir Mesajlaşma akışı denetlemek etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturan bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="53de7-206">B4002: Güvenilir Mesajlaşma akışı denetlemek etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="53de7-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="53de7-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan `netrm:BufferRemaining` kaç tane yeni güvenilir Mesajlaşma hedef iletileri göstermek için arabellek.</span><span class="sxs-lookup"><span data-stu-id="53de7-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="53de7-208">B4004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma hizmeti güvenilir Mesajlaşma hedef uygulama iletileri hızla alamadığı zaman gönderilen ileti sayısını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="53de7-209">Hedef arabellek güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="53de7-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="53de7-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.</span><span class="sxs-lookup"><span data-stu-id="53de7-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="53de7-211">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="53de7-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="53de7-212">Bu bölümde açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s davranış WS güvenilir Mesajlaşma farklı ileti Exchange desenler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53de7-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="53de7-213">Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="53de7-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="53de7-214">Olmayan adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasında olan; Yanıtlayıcı iletileri yalnızca HTTP yanıtları başlatıcıya sunabilir.</span><span class="sxs-lookup"><span data-stu-id="53de7-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="53de7-215">Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="53de7-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="53de7-216">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="53de7-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="53de7-217">Bağlama</span><span class="sxs-lookup"><span data-stu-id="53de7-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-218">bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-219">HTTP isteklerini RMD alınan tüm iletileri RMS'ye aktarmak için tüm iletiler RMS'den RMD ve HTTP yanıtı iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="53de7-220">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="53de7-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="53de7-222">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok.</span><span class="sxs-lookup"><span data-stu-id="53de7-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="53de7-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="53de7-224">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="53de7-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="53de7-225">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="53de7-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="53de7-226">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı oluşturur her zaman tek başına bir bildirim yanıt hem sıralı olarak ve `AckRequested` iletileri.</span><span class="sxs-lookup"><span data-stu-id="53de7-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="53de7-227">TerminateSequence iletisi</span><span class="sxs-lookup"><span data-stu-id="53de7-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-228">işler `TerminateSequence` tek yönlü bir işlem olarak HTTP yanıtı anlamına gelen bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="53de7-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="53de7-229">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="53de7-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="53de7-230">Bağlama</span><span class="sxs-lookup"><span data-stu-id="53de7-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-231">bir dizisi üzerinde bir gelen ve giden bir Http kanalı kullanılarak bir tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-232">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="53de7-233">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="53de7-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="53de7-234">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-235">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok.</span><span class="sxs-lookup"><span data-stu-id="53de7-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="53de7-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok.</span><span class="sxs-lookup"><span data-stu-id="53de7-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="53de7-237">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="53de7-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="53de7-238">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="53de7-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="53de7-239">Bağlama</span><span class="sxs-lookup"><span data-stu-id="53de7-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-240">bir gelen ve giden bir HTTP kanalı iki sıraları kullanarak bir iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-241">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="53de7-242">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="53de7-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="53de7-243">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-244">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="53de7-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="53de7-245">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="53de7-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-246">gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="53de7-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="53de7-247">Sıra yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="53de7-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-248">iki sıraları tam çift yönlü bir oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="53de7-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="53de7-249">Bir dizi hataları bir arıza oluşturma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları alınmasını uzak uç nokta bekler.</span><span class="sxs-lookup"><span data-stu-id="53de7-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="53de7-250">Bir dizi hataları bir arıza okuma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları hataları.</span><span class="sxs-lookup"><span data-stu-id="53de7-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-251">Giden sırası kapatın ve gelen sırası iletileri işlemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53de7-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="53de7-252">Buna karşılık, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelen sırası kapatma işlemek ve onun giden sırasını iletileri göndermeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="53de7-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="53de7-253">İstek-yanıt, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="53de7-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="53de7-254">Bağlama</span><span class="sxs-lookup"><span data-stu-id="53de7-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-255">üzerinde bir HTTP kanalı iki kullanarak bir tek yönlü ve istek-yanıt ileti değişim deseni dizilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-256">HTTP isteklerini istek sırasının iletileri iletmek için ve yanıt sırasının tüm iletileri iletmek için HTTP yanıtlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="53de7-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="53de7-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="53de7-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="53de7-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="53de7-260">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="53de7-261">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="53de7-261">One-way Message</span></span>  
 <span data-ttu-id="53de7-262">Tek yönlü ileti değişimi Protokolü başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="53de7-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="53de7-263">`SequenceAcknowledgement` Aktarılan ileti kabul gerekir.</span><span class="sxs-lookup"><span data-stu-id="53de7-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="53de7-264">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı isteğine bir bildirim, bir hata ya da yanıtın bir boş gövde ve HTTP 202 durum kodu ile yanıtla.</span><span class="sxs-lookup"><span data-stu-id="53de7-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="53de7-265">İki şekilde iletileri</span><span class="sxs-lookup"><span data-stu-id="53de7-265">Two Way Messages</span></span>  
 <span data-ttu-id="53de7-266">İki yönlü ileti değişimi Protokolü başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="53de7-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="53de7-267">Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.</span><span class="sxs-lookup"><span data-stu-id="53de7-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="53de7-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı isteğine bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt yanıtla.</span><span class="sxs-lookup"><span data-stu-id="53de7-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="53de7-269">Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="53de7-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="53de7-270">Yanıt yeniden deneniyor</span><span class="sxs-lookup"><span data-stu-id="53de7-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-271">HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="53de7-272">Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı değil durdurmak istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor, ancak bunun yerine ne zaman HTTP yanıtı taşıyan bir bildirim, kullanıcı iletisi ya da hata.</span><span class="sxs-lookup"><span data-stu-id="53de7-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="53de7-273">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıt bağıntılı isteğin HTTP isteği leg üzerinde yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="53de7-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="53de7-274">LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="53de7-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturur ve HTTP isteği leg üzerinde boş bodied son ileti iletir.</span><span class="sxs-lookup"><span data-stu-id="53de7-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-276">bir yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="53de7-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="53de7-277">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için istek sırasının boş bodied son iletisiyle yanıt sırasının boş bodied son ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="53de7-278">Varsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı alır, eylem URI'si değil http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, son bir ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] son iletiye verilen yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="53de7-279">Bir iki yönlü ileti exchange protokol söz konusu olduğunda, son uygulama ileti taşır; bir tek yönlü ileti exchange protokol söz konusu olduğunda, son ileti boştur.</span><span class="sxs-lookup"><span data-stu-id="53de7-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="53de7-280">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıt sırasının boş bodied son ileti için onay gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="53de7-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="53de7-281">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-282">Tüm isteklerin geçerli bir yanıt alındığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturur ve bu isteği sırasının iletir `TerminateSequence` HTTP isteği leg iletisi.</span><span class="sxs-lookup"><span data-stu-id="53de7-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-283">bir yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="53de7-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="53de7-284">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtları istek sırası için 's `TerminateSequence` yanıt sırasının iletisiyle `TerminateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="53de7-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="53de7-285">Normal kapatma dizisindeki her ikisi de `TerminateSequence` iletilerini taşıyan tam kapsamlı bir `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="53de7-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="53de7-286">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="53de7-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="53de7-287">Bağlama</span><span class="sxs-lookup"><span data-stu-id="53de7-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-288">iki sıraları üzerinden bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="53de7-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-289">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="53de7-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="53de7-290">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="53de7-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="53de7-291">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="53de7-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="53de7-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle.</span><span class="sxs-lookup"><span data-stu-id="53de7-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="53de7-293">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir.</span><span class="sxs-lookup"><span data-stu-id="53de7-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="53de7-294">gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="53de7-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="53de7-295">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="53de7-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="53de7-296">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı sağlar tüm uygulama istek iletileri ayı bir `MessageId` ve `ReplyTo` bitiş noktası başvurusu.</span><span class="sxs-lookup"><span data-stu-id="53de7-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="53de7-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı geçerlidir `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisi üzerinde uç noktası başvuru.</span><span class="sxs-lookup"><span data-stu-id="53de7-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="53de7-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayan gerektiriyorsa, gelen istek iletileri ayı bir `MessageId` ve `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="53de7-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="53de7-299">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar, her iki uç nokta referansının URI `CreateSequence` ve tüm uygulama istek iletilerini aynıdır.</span><span class="sxs-lookup"><span data-stu-id="53de7-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
