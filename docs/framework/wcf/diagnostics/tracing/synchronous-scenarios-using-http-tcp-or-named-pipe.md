---
description: 'Hakkında daha fazla bilgi edinin: HTTP, TCP veya Named-Pipe kullanarak zaman uyumlu senaryolar'
title: HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: fd6605be99a9419de27f000b378720adf0ae1a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635421"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="1f028-103">HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar</span><span class="sxs-lookup"><span data-stu-id="1f028-103">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="1f028-104">Bu konuda, HTTP, TCP veya adlandırılmış kanal kullanarak, tek iş parçacıklı bir istemciyle farklı zaman uyumlu istek/yanıt senaryolarına yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f028-104">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="1f028-105">Çoklu iş parçacıklı istekler hakkında daha fazla bilgi için bkz. [http, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .</span><span class="sxs-lookup"><span data-stu-id="1f028-105">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="1f028-106">Hata olmadan zaman uyumlu Istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="1f028-106">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="1f028-107">Bu bölümde, tek iş parçacıklı istemciyle geçerli bir zaman uyumlu istek/yanıt senaryosuna yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f028-107">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="1f028-108">İstemci</span><span class="sxs-lookup"><span data-stu-id="1f028-108">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="1f028-109">Hizmet uç noktası ile Iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="1f028-109">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="1f028-110">İstemci oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="1f028-110">A client is constructed and opened.</span></span> <span data-ttu-id="1f028-111">Bu adımların her biri için, çevresel etkinlik (A) sırasıyla bir "yapı Istemcisi" (B) ve "açık Istemci" (C) etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1f028-111">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="1f028-112">Aktarılmakta olan her etkinlik için, bir aktarım geri alınana kadar, diğer bir deyişle, ServiceModel kodu yürütülene kadar çevresel etkinlik askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="1f028-112">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="1f028-113">Hizmet uç noktasına Istek yapılıyor</span><span class="sxs-lookup"><span data-stu-id="1f028-113">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="1f028-114">Çevresel etkinlik bir "ProcessAction" (D) etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1f028-114">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="1f028-115">Bu etkinlik dahilinde bir istek iletisi gönderilir ve bir yanıt iletisi alınır.</span><span class="sxs-lookup"><span data-stu-id="1f028-115">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="1f028-116">Denetim Kullanıcı koduna döndüğünde etkinlik sona erer.</span><span class="sxs-lookup"><span data-stu-id="1f028-116">The activity ends when control returns to user code.</span></span> <span data-ttu-id="1f028-117">Bu zaman uyumlu bir istek olduğundan, ortam etkinliği denetim tarafından dönüşene kadar askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="1f028-117">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="1f028-118">Hizmet uç noktası ile Iletişim kapatılıyor</span><span class="sxs-lookup"><span data-stu-id="1f028-118">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="1f028-119">İstemci kapatma etkinliği (I) çevresel etkinlikten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-119">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="1f028-120">Bu, New ve Open ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1f028-120">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="1f028-121">Sunucu</span><span class="sxs-lookup"><span data-stu-id="1f028-121">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="1f028-122">Hizmet ana bilgisayarı ayarlama</span><span class="sxs-lookup"><span data-stu-id="1f028-122">Setting up a Service Host</span></span>  

 <span data-ttu-id="1f028-123">ServiceHost 'un yeni ve açık Etkinlikleri (N ve O) çevresel etkinlikten (M) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-123">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="1f028-124">Her dinleyici için bir ServiceHost açılmadan bir dinleyici etkinliği (P) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-124">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="1f028-125">Dinleyici etkinliği verileri almak ve işlemek için bekler.</span><span class="sxs-lookup"><span data-stu-id="1f028-125">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="1f028-126">Hattaki verileri alma</span><span class="sxs-lookup"><span data-stu-id="1f028-126">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="1f028-127">Veriler kabloya ulaştığında, alınan verileri işlemek için zaten mevcut değilse (Q) bir "ReceiveBytes" etkinliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-127">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="1f028-128">Bu etkinlik bir bağlantı veya kuyruk içindeki birden çok ileti için yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f028-128">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="1f028-129">Bir SOAP eylem iletisi oluşturmak için yeterli veri varsa, ReceiveBytes etkinliği bir ProcessMessage etkinliği (R) başlatır.</span><span class="sxs-lookup"><span data-stu-id="1f028-129">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="1f028-130">Etkinlik R ' de ileti üstbilgileri işlenir ve ActivityId üst bilgisi doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="1f028-130">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="1f028-131">Bu üst bilgi varsa, etkinlik KIMLIĞI ProcessAction etkinliğine ayarlanır; Aksi takdirde, yeni bir KIMLIK oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-131">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="1f028-132">Çağrı işlendiğinde ProcessAction etkinlikleri oluşturulur ve ' a aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1f028-132">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="1f028-133">Bu etkinlik, Kullanıcı kodu (T) yürütülüyor ve uygunsa yanıt iletisini gönderme dahil olmak üzere, gelen iletiyle ilgili tüm işlemler tamamlandığında sona erer.</span><span class="sxs-lookup"><span data-stu-id="1f028-133">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="1f028-134">Hizmet konağını kapatma</span><span class="sxs-lookup"><span data-stu-id="1f028-134">Closing a Service Host</span></span>  

 <span data-ttu-id="1f028-135">ServiceHost 'un Close etkinliği (Z) çevresel etkinlikten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f028-135">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![Zaman uyumlu senaryoları gösteren diyagram: HTTP, TCP veya adlandırılmış kanallar.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="1f028-137">İçinde \<A: name> , `A` önceki metinde ve tablo 3 ' te etkinliği açıklayan bir kısayol simgedir.</span><span class="sxs-lookup"><span data-stu-id="1f028-137">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="1f028-138">`Name` etkinliğin kısaltılmış bir adıdır.</span><span class="sxs-lookup"><span data-stu-id="1f028-138">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="1f028-139">Eğer `propagateActivity` = `true` , hem istemci hem de hizmette işlem eylemi aynı etkinlik kimliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1f028-139">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="1f028-140">Zaman uyumlu Istek/hatalarla yanıtla</span><span class="sxs-lookup"><span data-stu-id="1f028-140">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="1f028-141">Önceki senaryoya ilişkin tek fark, bir SOAP hata iletisinin yanıt iletisi olarak döndürüldüğünden olur.</span><span class="sxs-lookup"><span data-stu-id="1f028-141">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="1f028-142">İse `propagateActivity` = `true` , istek iletisinin etkinlik kimliği SOAP hata iletisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="1f028-142">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="1f028-143">Hata olmadan zaman uyumlu One-Way</span><span class="sxs-lookup"><span data-stu-id="1f028-143">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="1f028-144">İlk senaryoya göre tek fark, sunucuya hiçbir ileti döndürülmüyor.</span><span class="sxs-lookup"><span data-stu-id="1f028-144">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="1f028-145">HTTP tabanlı protokoller için istemciye bir durum (geçerli veya hata) döndürülmeye devam edilir.</span><span class="sxs-lookup"><span data-stu-id="1f028-145">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="1f028-146">Bunun nedeni, HTTP 'nin WCF protokol yığınının parçası olan bir istek-yanıt semantiğinin bulunduğu tek protokoldür.</span><span class="sxs-lookup"><span data-stu-id="1f028-146">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="1f028-147">TCP işlemi WCF 'den gizlendiğinden, istemciye hiçbir onay gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="1f028-147">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="1f028-148">Hatalarla zaman uyumlu One-Way</span><span class="sxs-lookup"><span data-stu-id="1f028-148">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="1f028-149">İleti işlenirken bir hata oluşursa (Q veya daha fazla), istemciye hiçbir bildirim döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="1f028-149">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="1f028-150">Bu, "hata olmadan zaman uyumlu One-Way" senaryosu ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1f028-150">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="1f028-151">Bir hata iletisi almak istiyorsanız One-Way senaryosu kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1f028-151">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="1f028-152">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="1f028-152">Duplex</span></span>  

 <span data-ttu-id="1f028-153">Önceki senaryolarla aradaki fark, istemcinin zaman uyumsuz senaryolara benzer şekilde ReceiveBytes ve ProcessMessage etkinlikleri oluşturduğu bir hizmet olarak davranmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f028-153">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
