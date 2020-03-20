---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185781"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="baeb2-102">HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar</span><span class="sxs-lookup"><span data-stu-id="baeb2-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="baeb2-103">Bu konu, http, TCP veya adlandırılmış boru kullanarak çok iş parçacığı istekleri ile farklı eşzamanlı istek/yanıt senaryoları için etkinlikleri ve aktarımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="baeb2-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="baeb2-104">Hatasız Asynchronous İstek/Yanıtla</span><span class="sxs-lookup"><span data-stu-id="baeb2-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="baeb2-105">Bu bölümde, çok iş parçacığı istemcileri olan bir eşzamanlı istek/yanıt senaryosu için etkinlikler ve aktarımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="baeb2-106">Arayan etkinliği `beginCall` döndüğünde sonlandırır `endCall` ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="baeb2-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="baeb2-107">Geri arama denirse, geri arama geri döner.</span><span class="sxs-lookup"><span data-stu-id="baeb2-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="baeb2-108">Çağrılan `beginCall` etkinlik, geri döndüğünde, `endCall` döndüğünde veya bu etkinlikten çağrıldığında geri arama geri döndüğünde sona erer.</span><span class="sxs-lookup"><span data-stu-id="baeb2-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="baeb2-109">Geri Arama olmadan Asynchronous İstemci</span><span class="sxs-lookup"><span data-stu-id="baeb2-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="baeb2-110">Http kullanılarak Her İki Tarafta Da Yayılma Etkindir</span><span class="sxs-lookup"><span data-stu-id="baeb2-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 ![PropagateActivity her iki tarafta doğru ayarlanmış hiçbir geri arama ile asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="baeb2-112">Eğer `propagateActivity=true`, ProcessMessage hangi ProcessAction etkinliğine aktagerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="baeb2-113">HTTP tabanlı senaryolar için ReceiveBytes gönderilecek ilk iletiye çağrılır ve isteğin kullanım ömrü boyunca vardır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="baeb2-114">Yayılma, HTTP kullanılarak Her Iki Tarafta Devre Dışı Bırakılır</span><span class="sxs-lookup"><span data-stu-id="baeb2-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="baeb2-115">Her `propagateActivity=false` iki tarafta ise, ProcessMessage hangi ProcessAction etkinliğine aktanınacak olduğunu göstermez.</span><span class="sxs-lookup"><span data-stu-id="baeb2-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="baeb2-116">Bu nedenle, yeni bir kimlik içeren yeni bir geçici İşlem Eylemi etkinliği çağrılır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="baeb2-117">Eşzamanlı yanıt ServiceModel kodundaki istekle eşleştiğinde, Etkinlik Kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="baeb2-118">Gerçek İşlem Eylem etkinliği bu kimlikle aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![PropagateActivity her iki tarafta yanlış olarak ayarlanmış hiçbir geri arama ile asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="baeb2-120">HTTP tabanlı senaryolar için ReceiveBytes gönderilecek ilk iletiye çağrılır ve isteğin kullanım ömrü boyunca vardır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="baeb2-121">Bir İşlem Eylem etkinliği, arayan veya callee'de ve `propagateActivity=false` yanıt iletisi eylem üstbilgisini içermediği zaman, eşzamanlı bir istemcide oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baeb2-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="baeb2-122">TCP veya Adlandırılmış Boru Kullanılarak Her İki Tarafta Da Yayılma Etkindir</span><span class="sxs-lookup"><span data-stu-id="baeb2-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 ![PropagateActivity'in her iki tarafta da doğru olarak ayarlandığı ve boru/TCP olarak adlandırılan geri aramasız asynchronous istemcisi.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="baeb2-124">Adlandırılmış Boru veya TCP tabanlı bir senaryo için, istemci açıldığında ReceiveBytes çağrılır ve bağlantının ömrü boyunca var olur.</span><span class="sxs-lookup"><span data-stu-id="baeb2-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="baeb2-125">İlk görüntüye benzer `propagateActivity=true`şekilde, ProcessMessage hangi ProcessAction etkinliğine aktagerektiğini gösterirse.</span><span class="sxs-lookup"><span data-stu-id="baeb2-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="baeb2-126">Yayılma, TCP veya Adlandırılmış Boru kullanılarak Her İki Tarafta Devre Dışı Bırakılır</span><span class="sxs-lookup"><span data-stu-id="baeb2-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="baeb2-127">Adlandırılmış Boru veya TCP tabanlı bir senaryo için, istemci açıldığında ReceiveBytes çağrılır ve bağlantının ömrü boyunca var olur.</span><span class="sxs-lookup"><span data-stu-id="baeb2-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="baeb2-128">İkinci görüntüye benzer `propagateActivity=false` şekilde, her iki tarafta ysa, ProcessMessage hangi ProcessAction etkinliğine aktanınacak olduğunu göstermez.</span><span class="sxs-lookup"><span data-stu-id="baeb2-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="baeb2-129">Bu nedenle, yeni bir kimlik içeren yeni bir geçici İşlem Eylemi etkinliği çağrılır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="baeb2-130">Eşzamanlı yanıt ServiceModel kodundaki istekle eşleştiğinde, Etkinlik Kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="baeb2-131">Gerçek İşlem Eylem etkinliği bu kimlikle aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![PropagateActivity'in her iki tarafta da false olarak ayarlandığı ve pipe/TCP adlı geri araması olmayan asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="baeb2-133">Callback ile asynchronous istemcisi</span><span class="sxs-lookup"><span data-stu-id="baeb2-133">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="baeb2-134">Bu senaryo, geri arama ve , ve `endCall`bunların transferleri için G ve A', etkinlikleri ekler ve bunların içinde/dışında.</span><span class="sxs-lookup"><span data-stu-id="baeb2-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="baeb2-135">Bu bölümde sadece HTTP `propagateActivity` = `true`kullanarak gösterir .</span><span class="sxs-lookup"><span data-stu-id="baeb2-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="baeb2-136">Ancak, ek etkinlikler ve aktarımlar diğer durumlar `propagateActivity` = `false`için de geçerlidir (diğer durumlarda (diğer bir deyişle, TCP veya Named-Pipe kullanarak).</span><span class="sxs-lookup"><span data-stu-id="baeb2-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="baeb2-137">Geri arama, istemci sonuçların hazır olduğunu bildirmek için kullanıcı kodunu aradığında yeni bir etkinlik (G) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baeb2-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="baeb2-138">Kullanıcı kodu `endCall` daha sonra geri arama içinde (Şekil 5'te gösterildiği gibi) veya geri arama dışında (Şekil 6) çağırır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="baeb2-139">Hangi kullanıcı etkinliğinin `endCall` çağrıldığı bilinmedığından, bu etkinlik `A’`etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="baeb2-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="baeb2-140">A'nın A ile aynı veya A'dan farklı olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="baeb2-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Geri arama ile bir eşzamanlı istemci gösterir, geri arama da endcall.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Geri arama, geri arama dışında endcall ile bir eşzamanlı istemci gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="baeb2-143">Geri Arama lı Asynchronous Server</span><span class="sxs-lookup"><span data-stu-id="baeb2-143">Asynchronous Server with Callback</span></span>  
 ![Geri arama ile bir eşzamanlı sunucu gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="baeb2-145">Kanal yığını Ileti Alma'daki istemciyi geri çağırır: Bu işleme ait izler ProcessRequest etkinliğinin kendisine yayılır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="baeb2-146">Hatalarla Eşkron İstek/Yanıtla</span><span class="sxs-lookup"><span data-stu-id="baeb2-146">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="baeb2-147">Hata iletisi `endCall`hataları sırasında alınır.</span><span class="sxs-lookup"><span data-stu-id="baeb2-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="baeb2-148">Aksi takdirde, etkinlikler ve aktarımlar önceki senaryolara benzer.</span><span class="sxs-lookup"><span data-stu-id="baeb2-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="baeb2-149">Asynchronous One-Way veya Hatalar olmadan</span><span class="sxs-lookup"><span data-stu-id="baeb2-149">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="baeb2-150">İstemciye yanıt veya hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="baeb2-150">No response or fault is returned to the client.</span></span>
