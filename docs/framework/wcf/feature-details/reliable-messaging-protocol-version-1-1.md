---
title: "Güvenilir Mesajlaşma Protokolü sürüm 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98fe8ac04b7ac811802466cf63c58ea4cebd791e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="d3779-102">Güvenilir Mesajlaşma Protokolü sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="d3779-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="d3779-103">Bu konuda ele alınmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WS-ReliableMessaging uygulama ayrıntılarını Şubat 2007 (sürüm 1.1) Protokolü HTTP aktarımı kullanarak birlikte çalışabilirlik için gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3779-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-104">Bu konuda açıklanan açıklamalar ve kısıtlamaları WS-ReliableMessaging izler.</span><span class="sxs-lookup"><span data-stu-id="d3779-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="d3779-105">WS-ReliableMessaging sürüm 1.1 protokolünü başlayarak uygulandığını unutmayın [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3779-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="d3779-106">WS-Protokolü uygulandığına ReliableMessaging Şubat 2007 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tarafından <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d3779-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="d3779-107">Kolaylık olması için konunun aşağıdaki rolleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="d3779-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="d3779-108">Başlatıcı: WS güvenilir ileti sırası oluşturması başlatır istemci.</span><span class="sxs-lookup"><span data-stu-id="d3779-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="d3779-109">Yanıtlayıcı: başlatanın ister hizmeti.</span><span class="sxs-lookup"><span data-stu-id="d3779-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="d3779-110">Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="d3779-111">önek</span><span class="sxs-lookup"><span data-stu-id="d3779-111">Prefix</span></span>|<span data-ttu-id="d3779-112">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d3779-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="d3779-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="d3779-113">wsrm</span></span>|<span data-ttu-id="d3779-114">http://docs.oasis-Open.org/ws-Rx/WSRM/200702</span><span class="sxs-lookup"><span data-stu-id="d3779-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="d3779-115">netrm</span><span class="sxs-lookup"><span data-stu-id="d3779-115">netrm</span></span>|<span data-ttu-id="d3779-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="d3779-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="d3779-117">s</span><span class="sxs-lookup"><span data-stu-id="d3779-117">s</span></span>|<span data-ttu-id="d3779-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="d3779-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="d3779-119">wsa</span><span class="sxs-lookup"><span data-stu-id="d3779-119">wsa</span></span>|<span data-ttu-id="d3779-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="d3779-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="d3779-121">wsse</span><span class="sxs-lookup"><span data-stu-id="d3779-121">wsse</span></span>|<span data-ttu-id="d3779-122">http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="d3779-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="d3779-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="d3779-123">wsrmp</span></span>|<span data-ttu-id="d3779-124">http://docs.oasis-Open.org/ws-Rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="d3779-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="d3779-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="d3779-125">netrmp</span></span>|<span data-ttu-id="d3779-126">http://schemas.microsoft.com/ws-Rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="d3779-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="d3779-127">WSP</span><span class="sxs-lookup"><span data-stu-id="d3779-127">wsp</span></span>|<span data-ttu-id="d3779-128">(WS-Policy 1.2 veya WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="d3779-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="d3779-129">İleti</span><span class="sxs-lookup"><span data-stu-id="d3779-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="d3779-130">Sıra oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-131">uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir Mesajlaşma kurmak için iletilerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="d3779-132">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="d3779-133">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aynı uç noktası başvuru olarak kullanan `CreateSequence` iletinin `ReplyTo`, `AcksTo` ve `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="d3779-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="d3779-134">R1102: `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuran `CreateSequence` ileti octet-wise eşleşecek şekilde aynı dize Beyanları adresi değerlerle olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3779-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="d3779-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı doğrular URI kısmı `AcksTo`, `ReplyTo` ve `Endpoint` uç nokta başvuruları özdeş bir dizisini oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="d3779-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="d3779-136">R1103: `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuran `CreateSequence` ileti aynı başvurusu parametre kümesine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3779-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-137">zorunlu değildir, ancak varsayar parametrelerinin başvuru `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuruyor `CreateSequence` özdeş ve kullandığı başvuru parametrelerinden `ReplyTo` için uç nokta başvurusu Katkıda Bulunanlar ve ters sıra iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="d3779-138">B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı isteğe bağlı oluşturmaz `Expires` veya `Offer/Expires` öğesinde `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="d3779-139">B1105: erişirken `CreateSequence` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı kullanan `Expires` değeri `CreateSequence` öğesi olarak `Expires` değeri `CreateSequenceResponse` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="d3779-140">Aksi takdirde, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı okur ve yoksayar `Expires` ve `Offer/Expires` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d3779-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="d3779-141">B1106: erişirken `CreateSequenceResponse` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı okur isteğe bağlı `Expires` değer ancak bunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="d3779-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="d3779-142">B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı hem Yanıtlayıcı her zaman oluşturmak isteğe bağlı `IncompleteSequenceBehavior` öğesinde `CreateSequence/Offer` ve `CreateSequenceResponse` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d3779-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="d3779-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca kullanır `DiscardFollowingFirstGap` ve `NoDiscard` değerler `IncompleteSequenceBehavior` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="d3779-144">WS-ReliableMessaging yararlanan `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="d3779-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="d3779-145">B1109: Varsa `CreateSequence` içeren bir `Offer` öğesi, bir yolu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı ile yanıt tarafından sunulan dizisi reddeder bir `CreateSequenceResponse` olmadan bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="d3779-146">B1110: güvenilir Mesajlaşma Yanıtlayıcı sunulan dizisi reddederse [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı hataları yeni kurulan dizisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="d3779-147">B1111: Varsa `CreateSequence` içermeyen bir `Offer` öğesi, çift yönlü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı ile yanıt tarafından sunulan dizisi reddeder bir `CreateSequenceRefused` hata.</span><span class="sxs-lookup"><span data-stu-id="d3779-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="d3779-148">R1112: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `[address]` özelliği `CreateSequenceResponse/Accept/AcksTo` bitiş noktası başvurusu hedef URI eşleşmelidir, `CreateSequence` ileti baytı.</span><span class="sxs-lookup"><span data-stu-id="d3779-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="d3779-149">R1113: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, Yanıtlayıcı başlatıcıdan akan hem sıraları tüm iletileri gönderileceği aynı uç nokta referansı.</span><span class="sxs-lookup"><span data-stu-id="d3779-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-150">WS-ReliableMessaging Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="d3779-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging uygulamasını sağlar güvenilir oturum açmak için tek yönlü, istek-yanıt ve tam çift yönlü desenleri Mesajlaşma.</span><span class="sxs-lookup"><span data-stu-id="d3779-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="d3779-152">WS-ReliableMessaging `Offer` mekanizmasını `CreateSequence` ve `CreateSequenceResponse` iki bağıntılı ters dizilerinin ve tüm uç noktaları iletisi için uygun bir oturum protokol sağlar kurun sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3779-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="d3779-153">Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik garanti sağlayan uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere bu tür bir oturum için aynı taraf için yönelik iletilerin aynı hedefe ulaşmasını sağlamak pratik.</span><span class="sxs-lookup"><span data-stu-id="d3779-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="d3779-154">Bu, "ardışık-yedekleme" dizisi bildirimleri, uygulama iletileri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3779-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="d3779-155">R1102, R1112 ve R1113 kısıtlamaları uygulamak bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3779-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="d3779-156">Örnek olarak bir `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-156">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="d3779-157">Örnek olarak bir `CreateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="d3779-158">Bir dizi kapatma</span><span class="sxs-lookup"><span data-stu-id="d3779-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-159">kullanan `CloseSequence` ve `CloseSequenceResponse` güvenilir Mesajlaşma kaynak tarafından başlatılan bir kapatma iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="d3779-160">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Güvenilir Mesajlaşma hedef kapatma başlatmak değil ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma kaynak güvenilir Mesajlaşma hedef başlatılan bir kapatma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d3779-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="d3779-161">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="d3779-162">B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma kaynağı her zaman gönderir bir `CloseSequence` sırası kapatmaya ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="d3779-163">B1202: Güvenilir Mesajlaşma kaynak sırası iletilerinin tam aralığının göndermeden önce onay bekler `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="d3779-164">B1203: Güvenilir Mesajlaşma kaynağı her zaman isteğe bağlı içerir `LastMsgNumber` öğesi dizisi iletileri içermediği sürece.</span><span class="sxs-lookup"><span data-stu-id="d3779-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="d3779-165">R1204: Güvenilir Mesajlaşma hedef kapatma göndererek gerçekleştirmemelidir bir `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="d3779-166">B1205: temel alarak bir `CloseSequence` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma kaynak sırası eksik olarak değerlendirir ve bir hata gönderir.</span><span class="sxs-lookup"><span data-stu-id="d3779-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="d3779-167">Örnek olarak bir `CloseSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-167">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="d3779-168">Sıra sonlandırma</span><span class="sxs-lookup"><span data-stu-id="d3779-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-169">öncelikle kullanır `TerminateSequence/TerminateSequenceResponse` tamamladıktan sonra el sıkışma `CloseSequence/CloseSequenceResponse` el sıkışma.</span><span class="sxs-lookup"><span data-stu-id="d3779-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="d3779-170">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Güvenilir Mesajlaşma hedef sonlandırma başlatmak değil ve güvenilir Mesajlaşma kaynağı güvenilir Mesajlaşma hedef tarafından başlatılan bir sonlandırma desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="d3779-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="d3779-171">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="d3779-172">B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] başlatıcı yalnızca gönderir `TerminateSequence` başarıyla tamamlandıktan sonra ileti `CloseSequence/CloseSequenceResponse` el sıkışma.</span><span class="sxs-lookup"><span data-stu-id="d3779-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="d3779-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doğrular `LastMsgNumber` öğesi tutarlı olduğundan tüm `CloseSequence` ve `TerminateSequence` belirli bir dizi iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="d3779-174">Bunun anlamı `LastMsgNumber` ya da tüm mevcut `CloseSequence` ve `TerminateSequence` iletileri ya da mevcut ve tüm aynı `CloseSequence` ve `TerminateSequence` iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="d3779-175">B1303: alırken bir `TerminateSequence` sonra ileti `CloseSequence/CloseSequenceResponse` el sıkışması, güvenilir Mesajlaşma hedef yanıt ile bir `TerminateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="d3779-176">Güvenilir Mesajlaşma kaynak göndermeden önce son bildirim olduğundan `TerminateSequence` ileti, güvenilir Mesajlaşma hedef bilir olmadan emin olabilirsiniz dizisi sona ereceğini ve kaynakları hemen geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="d3779-177">B1304: alırken bir `TerminateSequence` öncesinde ileti `CloseSequence/CloseSequenceResponse` el sıkışması, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma hedef yanıt ile bir `TerminateSequenceResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="d3779-178">Güvenilir Mesajlaşma hedef sırada hiçbir tutarsızlıklar olduğunu belirlerse, güvenilir Mesajlaşma hedef önce istemcinin alma olanağı sağlamak için kaynakları, geri kazanma bir uygulama hedef belirtilen süresi bekler Son bildirim.</span><span class="sxs-lookup"><span data-stu-id="d3779-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="d3779-179">Aksi durumda, güvenilir Mesajlaşma hedef kaynaklar hemen geri kazanır ve uygulama hedef sırası yükselterek şüpheli ile biten gösterir `Faulted` olay.</span><span class="sxs-lookup"><span data-stu-id="d3779-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="d3779-180">Örnek olarak bir `TerminateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-180">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="d3779-181">Diziler</span><span class="sxs-lookup"><span data-stu-id="d3779-181">Sequences</span></span>  
 <span data-ttu-id="d3779-182">Dizilerine uygulama kısıtlamaları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="d3779-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="d3779-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve daha yüksek sıra numaraları erişir `xs:long`'s en büyük içermeli değer, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="d3779-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="d3779-184">Örnek olarak bir `Sequence` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="d3779-185">Bildirim isteği</span><span class="sxs-lookup"><span data-stu-id="d3779-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-186">kullanan `AckRequested` tutma mekanizması olarak üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="d3779-187">Örnek olarak bir `AckRequested` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="d3779-188">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="d3779-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-189">WS güvenilir Mesajlaşma içinde sağlanan dizisi bildirimleri için bir "ardışık" mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="d3779-190">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="d3779-191">R1601: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="d3779-192">Uzak uç noktada bir paketle gönderilen erişebilir `SequenceAcknowledgement` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="d3779-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri `Nack` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d3779-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-194">Her doğrular `Nack` öğesi bir sıra numarası içeriyor, ancak Aksi halde yoksayar `Nack` öğe ve değer.</span><span class="sxs-lookup"><span data-stu-id="d3779-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="d3779-195">Örnek olarak bir `SequenceAcknowledgement` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="d3779-196">WS-ReliableMessaging hataları</span><span class="sxs-lookup"><span data-stu-id="d3779-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="d3779-197">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging hataları uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d3779-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="d3779-198">Aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="d3779-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `MessageNumberRollover` hataları.</span><span class="sxs-lookup"><span data-stu-id="d3779-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="d3779-200">B1702: Üzerinden SOAP hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor 1.2 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iç içe bir oluşturur `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d3779-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="d3779-201">WS-adresleme hataları</span><span class="sxs-lookup"><span data-stu-id="d3779-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="d3779-202">WS-ReliableMessaging WS adresleme kullandığından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging uygulaması oluşturma ve hatalarını WS adresleme iletme.</span><span class="sxs-lookup"><span data-stu-id="d3779-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="d3779-203">Bu bölümde kapsar WS adresleme hataları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] açıkça oluşturur ve WS-ReliableMessaging katmanında aktarır:</span><span class="sxs-lookup"><span data-stu-id="d3779-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="d3779-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve iletir `Message Addressing Header Required` şunlardan biri doğru olduğunda hata:</span><span class="sxs-lookup"><span data-stu-id="d3779-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="d3779-205">A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `MessageId` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="d3779-206">A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `ReplyTo` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="d3779-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, veya `TerminateSequenceResponse` ileti eksik bir `RelatesTo` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="d3779-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve iletir `Endpoint Unavailable` , dinleme bitiş noktası olduğunu belirtmek için hata adresleme üstbilgilerinde incelenmesi temel sıralı işlem `CreateSequence` ileti.</span><span class="sxs-lookup"><span data-stu-id="d3779-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="d3779-209">İletişim kuralı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="d3779-210">WS-adresleme ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-211">WS-adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="d3779-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="d3779-212">While WS-ReliableMessaging belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü.</span><span class="sxs-lookup"><span data-stu-id="d3779-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="d3779-213">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d3779-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="d3779-214">R2101: Hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3779-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="d3779-215">R2102: Belirli bir WS-ReliableMessaging dizi veya ters sıraları kullanarak bağıntılı çifti boyunca WS adresleme tek sürümü kullanılmalıdır `Offer` mekanizması.</span><span class="sxs-lookup"><span data-stu-id="d3779-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="d3779-216">SOAP ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-217">SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="d3779-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="d3779-218">WS güvenliği ve WS-SecureConversation ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-219">güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS-ReliableMessaging dizileri için koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3779-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="d3779-220">WS-ReliableMessaging 1.1 protokolünü, WS-güvenlik 1.1 ve WS güvenli konuşma 1.3 Protokolü birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3779-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="d3779-221">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d3779-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="d3779-222">R2301: korumak için bir WS-ReliableMessaging bütünlüğünü sıra ayrıca tek bir ileti gizliliği ve bütünlük [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenli konuşma kullanılmalıdır gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d3779-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="d3779-223">R2302:AWS-güvenli konuşma oturum WS-ReliableMessaging sequence(s) kurmadan önce oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3779-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="d3779-224">R2303: WS-ReliableMessaging ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d3779-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="d3779-225">B2304:WS-ReliableMessaging dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.</span><span class="sxs-lookup"><span data-stu-id="d3779-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="d3779-226">R2305: WS güvenli konuşma oluşan zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı gerektirir `CreateSequence` ileti içeren `wsse:SecurityTokenReference` öğesi ve `wsrm:UsesSequenceSTR` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="d3779-227">Örnek olarak bir `UsesSequenceSTR` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="d3779-228">SSL/TLS oturumlarını ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-229">SSL/TLS oturumlarını ile oluşturma desteklemez:</span><span class="sxs-lookup"><span data-stu-id="d3779-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="d3779-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `wsrm:UsesSequenceSSL` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="d3779-231">R2402: Güvenilir Mesajlaşma Başlatıcı değil göndermelidir bir `CreateSequence` ile ileti bir `wsrm:UsesSequenceSSL` başlığına bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı.</span><span class="sxs-lookup"><span data-stu-id="d3779-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="d3779-232">WS-Policy ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3779-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-233">WS-Policy iki sürümlerini destekler: WS-Policy 1.2 ve WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="d3779-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="d3779-234">WS-ReliableMessaging WS-ilke onaylama</span><span class="sxs-lookup"><span data-stu-id="d3779-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-235">WS-ReliableMessaging WS-Policy onaylama kullanan `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="d3779-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="d3779-236">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d3779-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="d3779-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iliştirir `wsrmn:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d3779-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-238">Her iki ekleri destekler `wsdl:binding` ve `wsdl:port` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d3779-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="d3779-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hiçbir zaman oluşturur `wsp:Optional` etiketi.</span><span class="sxs-lookup"><span data-stu-id="d3779-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="d3779-240">B3003: erişirken `wsrmp:RMAssertion` WS-Policy onaylama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yoksayar `wsp:Optional` etiketi ve WS-RM ilkesi zorunlu olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d3779-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="d3779-241">R3004: Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SSL/TLS oturumlarıyla oluşturan değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] belirten ilkesini kabul etmiyorum `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="d3779-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="d3779-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman oluşturur `wsrmp:DeliveryAssurance` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="d3779-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman belirtir `wsrmp:ExactlyOnce` teslim güvence.</span><span class="sxs-lookup"><span data-stu-id="d3779-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="d3779-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve WS-ReliableMessaging onaylama aşağıdaki özelliklerini okur ve onları üzerinde denetim sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="d3779-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="d3779-245">Örnek olarak bir `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="d3779-245">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="d3779-246">Akış Denetim WS-ReliableMessaging uzantısı</span><span class="sxs-lookup"><span data-stu-id="d3779-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-247">WS-ReliableMessaging genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="d3779-248">Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``boolean` özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="d3779-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="d3779-249">Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d3779-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="d3779-250">B4001: Güvenilir Mesajlaşma akışı denetlemek etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="d3779-251">B4002: Bile güvenilir Mesajlaşma akış denetimi etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirmez bir `netrm:BufferRemaining` öğesinde `SequenceAcknowledgement` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d3779-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="d3779-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma hedef kullanan `netrm:BufferRemaining` kaç tane yeni ona iletileri göstermek için arabellek.</span><span class="sxs-lookup"><span data-stu-id="d3779-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="d3779-253">B4004:when güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma kaynağı değerini kullanır `netrm:BufferRemaining` kısıtlama ileti aktarımı için.</span><span class="sxs-lookup"><span data-stu-id="d3779-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="d3779-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.</span><span class="sxs-lookup"><span data-stu-id="d3779-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="d3779-255">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="d3779-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="d3779-256">Bu bölümde açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s davranış WS-ReliableMessaging farklı ileti Exchange desenler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3779-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="d3779-257">Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="d3779-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="d3779-258">Olmayan adreslenebilir Başlatıcı: Başlatıcı duvarıyla korunuyorsa; Yanıtlayıcı iletileri Başlatıcısı yalnızca HTTP yanıtlarını ulaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3779-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="d3779-259">Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="d3779-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="d3779-260">Tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="d3779-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="d3779-261">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d3779-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-262">bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3779-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-263">HTTP isteklerini yanıtlayan alınan tüm iletileri Başlatıcı iletmek için tüm iletiler başlatıcıdan Yanıtlayıcı ve HTTP yanıtları iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="d3779-264">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-265">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CreateSequence` hiçbir ileti `Offer` bir HTTP isteği öğede bekler `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="d3779-266">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` hiçbir ileti `Accept` HTTP yanıtı öğede.</span><span class="sxs-lookup"><span data-stu-id="d3779-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="d3779-267">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="d3779-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="d3779-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="d3779-269">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı her zaman tek başına bir bildirim tüm dizisi HTTP yanıtı üzerinde aktarır ve `AckRequested` iletileri.</span><span class="sxs-lookup"><span data-stu-id="d3779-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="d3779-270">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="d3779-271">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CloseSequence` bir HTTP isteği iletisi ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="d3779-272">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı iletir `CloseSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="d3779-273">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `TerminateSequence` bir HTTP isteği iletisi ve bekliyor `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="d3779-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="d3779-276">Tek yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="d3779-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="d3779-277">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d3779-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-278">bir dizi kullanarak bir tek yönlü ileti değişim deseni sağlar gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="d3779-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-279">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="d3779-280">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="d3779-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="d3779-281">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-282">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CreateSequence` hiçbir ileti `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="d3779-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="d3779-283">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` hiçbir ileti `Accept` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="d3779-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="d3779-284">Çift yönlü, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="d3779-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="d3779-285">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d3779-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-286">iki kullanarak tam olarak zaman uyumsuz, iki yönlü ileti değişim deseni üzerinde bir dizilerinin sağlar gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="d3779-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="d3779-287">Bu ileti değişim deseni ile karma `Request/Reply`, `Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni.</span><span class="sxs-lookup"><span data-stu-id="d3779-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-288">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="d3779-289">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="d3779-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="d3779-290">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-291">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="d3779-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="d3779-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="d3779-293">Sıra yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="d3779-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-294">iki sıraları bir tam çift yönlü oturum olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d3779-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="d3779-295">Bir dizi hataları bir arıza oluşturma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları alınmasını uzak uç nokta bekler.</span><span class="sxs-lookup"><span data-stu-id="d3779-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="d3779-296">Bir dizi hataları bir arıza okuma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları hataları.</span><span class="sxs-lookup"><span data-stu-id="d3779-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-297">Giden sırası kapatın ve gelen sırası iletileri işlemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3779-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="d3779-298">Buna karşılık, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelen sırası kapatma işlemek ve onun giden sırasını iletileri göndermeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="d3779-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="d3779-299">İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="d3779-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="d3779-300">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d3779-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-301">üzerinde bir HTTP kanalı iki kullanarak bir tek yönlü ve istek-yanıt ileti değişim deseni dizilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3779-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-302">HTTP isteklerini yanıtlayan alınan tüm iletileri Başlatıcı iletmek için tüm iletiler başlatıcıdan Yanıtlayıcı ve HTTP yanıtları iletmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="d3779-303">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-304">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` bir HTTP isteği öğede bekler `CreateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="d3779-305">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` HTTP yanıtı öğede.</span><span class="sxs-lookup"><span data-stu-id="d3779-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="d3779-306">Tek yönlü iletisi</span><span class="sxs-lookup"><span data-stu-id="d3779-306">One-way Message</span></span>  
 <span data-ttu-id="d3779-307">Tek yönlü ileti değişimi başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="d3779-308">`SequenceAcknowledgement` Aktarılan ileti kabul gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3779-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="d3779-309">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı onay, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt.</span><span class="sxs-lookup"><span data-stu-id="d3779-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="d3779-310">İki şekilde iletileri</span><span class="sxs-lookup"><span data-stu-id="d3779-310">Two Way Messages</span></span>  
 <span data-ttu-id="d3779-311">İki yönlü ileti değişimi Protokolü başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="d3779-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="d3779-312">Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.</span><span class="sxs-lookup"><span data-stu-id="d3779-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="d3779-313">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt.</span><span class="sxs-lookup"><span data-stu-id="d3779-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="d3779-314">Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d3779-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="d3779-315">Yanıt yeniden deneniyor</span><span class="sxs-lookup"><span data-stu-id="d3779-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-316">HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="d3779-317">Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı değil durdurmak istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor, ancak yerine HTTP yanıtı zaman taşıyan bir `SequenceAcknowledgement`, uygulama yanıt ya da hata.</span><span class="sxs-lookup"><span data-stu-id="d3779-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="d3779-318">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıt bağıntılı isteğin HTTP yanıtı üzerinde yanıtları yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="d3779-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="d3779-319">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="d3779-320">Tüm yanıt sırası iletilerinin ve tüm tek yönlü istek sırası iletileri için onayları aldıktan sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CloseSequence` iletisi için bir HTTP isteği istek sırasını ve bekliyor `CloseSequenceResponse` http yanıt.</span><span class="sxs-lookup"><span data-stu-id="d3779-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="d3779-321">İstek sırası örtük olarak kapatılmadan yanıt sırası kapatır.</span><span class="sxs-lookup"><span data-stu-id="d3779-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="d3779-322">Yani [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı içerir yanıt sırasının son `SequenceAcknowledgement` üzerinde `CloseSequence` ileti ve yanıt sırası yok bir `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="d3779-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="d3779-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar tüm yanıtları onaylanan ve iletir `CloseSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="d3779-324">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-325">Alındıktan sonra `CloseSequenceResponse` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `TerminateSequence` iletisi için bir HTTP isteği istek sırasını ve bekliyor `TerminateSequenceResponse` HTTP yanıtı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d3779-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="d3779-326">Gibi `CloseSequence` istek sırası örtük olarak sonlandırma exchange yanıt sırası sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d3779-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="d3779-327">Yani [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı içerir yanıt sırasının son `SequenceAcknowledgement` üzerinde `TerminateSequence` ileti ve yanıt sırası yok bir `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="d3779-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="d3779-328">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3779-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="d3779-329">İstek/yanıt, adreslenebilir Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="d3779-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="d3779-330">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d3779-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-331">iki kullanarak bir istek-yanıt ileti değişim deseni üzerinde bir dizilerinin sağlar gelen ve giden bir HTTP kanalı.</span><span class="sxs-lookup"><span data-stu-id="d3779-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="d3779-332">Bu ileti değişim deseni ile karma `Duplex, Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni.</span><span class="sxs-lookup"><span data-stu-id="d3779-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-333">tüm iletileri iletmek için HTTP isteklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3779-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="d3779-334">Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="d3779-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="d3779-335">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="d3779-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="d3779-336">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği.</span><span class="sxs-lookup"><span data-stu-id="d3779-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="d3779-337">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi sonra bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3779-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="d3779-338">İstek/yanıt bağıntısı</span><span class="sxs-lookup"><span data-stu-id="d3779-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="d3779-339">Aşağıdaki tüm bağıntılı istekleri ve yanıtları için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3779-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-340">tüm uygulama istek iletileri ayı sağlar bir `ReplyTo` bitiş noktası başvurusu ve `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="d3779-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-341">her uygulama isteği iletinin yerel uç nokta başvurusu geçerli `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="d3779-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="d3779-342">Yerel uç nokta başvuru `CreateSequence` iletinin `ReplyTo` başlatıcı ve `CreateSequence` iletinin `To` Yanıtlayıcı için.</span><span class="sxs-lookup"><span data-stu-id="d3779-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-343">Bu gelen istek iletileri ayı sağlar bir `MessageId` ve `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="d3779-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-344">sağlar `ReplyTo` daha önce tanımlanan tüm uygulama istek iletilerini uç nokta referansının URI'sini eşleşen yerel uç nokta başvuru.</span><span class="sxs-lookup"><span data-stu-id="d3779-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d3779-345">tüm yanıtlar doğru ayı sağlar `RelatesTo` ve `To` aşağıdaki üstbilgileri `wsa` bağıntı kuralları istek/yanıt.</span><span class="sxs-lookup"><span data-stu-id="d3779-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
