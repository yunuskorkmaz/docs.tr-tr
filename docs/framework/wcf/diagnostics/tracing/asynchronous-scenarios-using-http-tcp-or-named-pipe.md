---
description: 'Daha fazla bilgi edinin: HTTP, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar'
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 5e01866cd20d63796741a097a6d7d774ea45d3d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770956"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="8f4f3-103">HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar</span><span class="sxs-lookup"><span data-stu-id="8f4f3-103">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>

<span data-ttu-id="8f4f3-104">Bu konuda, HTTP, TCP veya adlandırılmış kanal kullanan çok iş parçacıklı istekler ile farklı zaman uyumsuz istek/yanıt senaryolarına yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-104">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="8f4f3-105">Hata olmadan zaman uyumsuz Istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="8f4f3-105">Asynchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="8f4f3-106">Bu bölümde, çok iş parçacıklı istemcilerle zaman uyumsuz istek/yanıt senaryosuna yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-106">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="8f4f3-107">Çağıran etkinlik, döndüğünde sonlanır `beginCall` ve `endCall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-107">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="8f4f3-108">Bir geri çağırma çağrılırsa geri arama döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-108">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="8f4f3-109">Çağrılan etkinlik, döndürüldüğünde `beginCall` , `endCall` döndüğünde veya geri çağırma, Bu etkinlikten çağrıldıysa döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-109">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="8f4f3-110">Geri çağırma olmadan zaman uyumsuz Istemci</span><span class="sxs-lookup"><span data-stu-id="8f4f3-110">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="8f4f3-111">Yayma, HTTP kullanarak her Iki tarafta da etkindir</span><span class="sxs-lookup"><span data-stu-id="8f4f3-111">Propagation is Enabled on Both Sides, using HTTP</span></span>  

 ![PropagateActivity her iki tarafta da true olarak ayarlandığında, geri arama olmadan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="8f4f3-113">Eğer `propagateActivity=true` , ProcessMessage hangi ProcessAction etkinliğinin aktarılacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-113">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="8f4f3-114">HTTP tabanlı senaryolar için, gönderilen ilk ileti üzerinde ReceiveBytes çağrılır ve isteğin ömrü için mevcut olur.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-114">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="8f4f3-115">Yayma, HTTP kullanarak her Iki tarafta da devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="8f4f3-115">Propagation is Disabled on Either Sides, using HTTP</span></span>  

 <span data-ttu-id="8f4f3-116">`propagateActivity=false`İki taraftan, ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-116">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="8f4f3-117">Bu nedenle, yeni KIMLIĞE sahip yeni bir geçici ProcessAction etkinliği çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-117">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="8f4f3-118">Zaman uyumsuz yanıt, ServiceModel kodundaki istekle eşleştiğinde, etkinlik KIMLIĞI Yerel içerikten alınabilir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-118">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="8f4f3-119">Gerçek ProcessAction etkinliği bu KIMLIKLE öğesine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-119">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![PropagateActivity her iki tarafta da false olarak ayarlandığında, geri çağırması olmayan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="8f4f3-121">HTTP tabanlı senaryolar için, gönderilen ilk ileti üzerinde ReceiveBytes çağrılır ve isteğin ömrü için mevcut olur.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-121">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="8f4f3-122">Bir Işlem eylemi etkinliği, çağıran veya çağrılan zaman uyumsuz bir istemcide oluşturulur `propagateActivity=false` ve yanıt iletisi bir eylem üst bilgisi içermez.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-122">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="8f4f3-123">Yayılma, TCP veya adlandırılmış kanal kullanılarak her Iki tarafta de etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="8f4f3-123">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  

 ![PropagateActivity her iki tarafta da true, ve adlandırılmış kanal/TCP olarak ayarlandığı zaman uyumsuz istemci geri çağırması yok.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="8f4f3-125">Named-Pipe veya TCP tabanlı bir senaryoda, istemci açıldığında ReceiveBytes çağrılır ve bağlantı ömrü boyunca mevcut olur.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-125">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="8f4f3-126">İlk resme benzer şekilde, `propagateActivity=true` ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-126">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="8f4f3-127">Yayma, TCP veya adlandırılmış kanal kullanılarak Iki tarafta da devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="8f4f3-127">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  

 <span data-ttu-id="8f4f3-128">Named-Pipe veya TCP tabanlı bir senaryoda, istemci açıldığında ReceiveBytes çağrılır ve bağlantı ömrü boyunca mevcut olur.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-128">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="8f4f3-129">İkinci görüntüye benzer şekilde, `propagateActivity=false` her iki tarafta de ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-129">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="8f4f3-130">Bu nedenle, yeni KIMLIĞE sahip yeni bir geçici ProcessAction etkinliği çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-130">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="8f4f3-131">Zaman uyumsuz yanıt, ServiceModel kodundaki istekle eşleştiğinde, etkinlik KIMLIĞI Yerel içerikten alınabilir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-131">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="8f4f3-132">Gerçek ProcessAction etkinliği bu KIMLIKLE öğesine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-132">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![PropagateActivity her iki tarafta ve adlandırılmış kanal/TCP 'de yanlış olarak ayarlandığı hiçbir geri arama olmadan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="8f4f3-134">Geri çağırma ile zaman uyumsuz istemci</span><span class="sxs-lookup"><span data-stu-id="8f4f3-134">Asynchronous client with Callback</span></span>  

 <span data-ttu-id="8f4f3-135">Bu senaryo, geri çağırma için ve `endCall` , ve bunların aktarımları içindeki/giden etkinliklere G ve A ' yı ekler.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-135">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="8f4f3-136">Bu bölüm yalnızca ile HTTP kullanımını gösterir `propagateActivity` = `true` .</span><span class="sxs-lookup"><span data-stu-id="8f4f3-136">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="8f4f3-137">Ancak, ek etkinlikler ve aktarımlar diğer durumlar için de geçerlidir (yani, `propagateActivity` = `false` TCP veya adlandırılmış kanal kullanarak).</span><span class="sxs-lookup"><span data-stu-id="8f4f3-137">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="8f4f3-138">Geri arama, istemci, sonuçların hazırlandığını bildirmek için Kullanıcı kodunu çağırdığında yeni bir etkinlik (G) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-138">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="8f4f3-139">Kullanıcı kodu daha sonra `endCall` geri çağırma içinde (Şekil 5 ' te gösterildiği gibi) veya geri çağırma dışında çağırır (Şekil 6).</span><span class="sxs-lookup"><span data-stu-id="8f4f3-139">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="8f4f3-140">Hangi kullanıcı etkinliğinin `endCall` çağrıldığı bilinmiyor, bu etkinlik etiketlidir `A’` .</span><span class="sxs-lookup"><span data-stu-id="8f4f3-140">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="8f4f3-141">' Bir ' ile aynı veya arasında farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-141">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Geri çağırma ile zaman uyumsuz bir istemciyi gösterir, geri çağırma sırasında endCall.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Geri çağırma, geri çağırma dışında zaman uyumsuz bir istemciyi gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="8f4f3-144">Geri çağırma ile zaman uyumsuz sunucu</span><span class="sxs-lookup"><span data-stu-id="8f4f3-144">Asynchronous Server with Callback</span></span>  

 ![Geri çağırma ile zaman uyumsuz bir sunucu gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="8f4f3-146">Kanal yığını istemciyi geri çağırır Ileti alma: Bu işleme yönelik izlemeler, ProcessRequest etkinliğinin kendisidir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-146">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="8f4f3-147">Zaman uyumsuz Istek/hatalarla yanıtla</span><span class="sxs-lookup"><span data-stu-id="8f4f3-147">Asynchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="8f4f3-148">Hata iletisi hataları sırasında alınır `endCall` .</span><span class="sxs-lookup"><span data-stu-id="8f4f3-148">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="8f4f3-149">Aksi takdirde, etkinlikler ve aktarımlar önceki senaryolara benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-149">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="8f4f3-150">Hatasız veya hata olmadan zaman uyumsuz One-Way</span><span class="sxs-lookup"><span data-stu-id="8f4f3-150">Asynchronous One-Way with or without Errors</span></span>  

 <span data-ttu-id="8f4f3-151">İstemciye yanıt veya hata döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="8f4f3-151">No response or fault is returned to the client.</span></span>
