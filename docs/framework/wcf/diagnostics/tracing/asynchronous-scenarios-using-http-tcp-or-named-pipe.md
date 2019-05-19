---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 48957ec0abd1b4b0623f9b613fcd94912a38845b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881664"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="cd4d6-102">HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar</span><span class="sxs-lookup"><span data-stu-id="cd4d6-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="cd4d6-103">Bu konuda etkinlikler ve aktarımları farklı zaman uyumsuz istek/yanıt senaryoları için TCP ve HTTP kullanarak birden çok iş parçacıklı isteklerle açıklar veya adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="cd4d6-104">Zaman uyumsuz istek/yanıt hatasız</span><span class="sxs-lookup"><span data-stu-id="cd4d6-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="cd4d6-105">Bu bölümde, etkinlikleri ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="cd4d6-106">Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="cd4d6-107">Bir geri çağırma çağrılırsa geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="cd4d6-108">Çağrılan etkinliğin ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, veya geri döndüğünde, etkinlikten çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="cd4d6-109">Zaman uyumsuz istemci geri çağırma olmadan</span><span class="sxs-lookup"><span data-stu-id="cd4d6-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="cd4d6-110">Her iki HTTP kullanarak yüzüne yayma etkin</span><span class="sxs-lookup"><span data-stu-id="cd4d6-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 ![Zaman uyumsuz istemci için propagateActivity ayarlandığı hiçbir geri araması ile her iki tarafında true.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 <span data-ttu-id="cd4d6-112">Varsa `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-112">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="cd4d6-113">HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="cd4d6-114">Yayma ya da HTTP kullanarak yüzüne, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="cd4d6-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="cd4d6-115">Varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-115">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="cd4d6-116">Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="cd4d6-117">ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="cd4d6-118">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="cd4d6-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Zaman uyumsuz istemci ile propagateActivity taraflardan üzerinde false olarak ayarlandığı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 <span data-ttu-id="cd4d6-120">HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="cd4d6-121">Zaman uyumsuz bir istemcide bir işlem eylem etkinliği oluşturulur, `propagateActivity` = `false` çağıran ve çağrılan ve yanıt iletisi, bir eylem üst bilgisi içermez.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-121">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="cd4d6-122">Yayma hem TCP veya adlandırılmış kanal kullanarak yüzüne etkin</span><span class="sxs-lookup"><span data-stu-id="cd4d6-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 ![Hiçbir geri çağırma propagateActivity her iki tarafında true ve adlandırılmış ayarlandığı zaman uyumsuz istemcisiyle kanal/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="cd4d6-124">İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="cd4d6-125">İlk görüntüye benzer varsa `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-125">Similar to the first image, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="cd4d6-126">Yayma ya da TCP veya adlandırılmış kanal kullanarak yüzüne, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="cd4d6-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="cd4d6-127">İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="cd4d6-128">Benzer şekilde, ikinci görüntü, `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-128">Similar to the second image, if `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="cd4d6-129">Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="cd4d6-130">ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="cd4d6-131">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="cd4d6-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Zaman uyumsuz istemci ile burada propagateActivity iki tarafındaki false olarak ayarlayın ve kanal/TCP adlı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="cd4d6-133">Zaman uyumsuz geri çağırma istemcisiyle</span><span class="sxs-lookup"><span data-stu-id="cd4d6-133">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="cd4d6-134">Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları daraltma veya genişletme.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="cd4d6-135">Bu bölüm, yalnızca HTTP kullanarak gösterir `propragateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-135">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="cd4d6-136">Ancak ek etkinlikler ve aktarımları da diğer durumlarda geçerlidir (yani `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).</span><span class="sxs-lookup"><span data-stu-id="cd4d6-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="cd4d6-137">İstemci sonuç hazır olduğunu bildiren, kullanıcı kodu çağırdığında, yeni bir etkinlik (G) geri çağırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="cd4d6-138">Ardından kullanıcı kodu çağıran `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında (Şekil 6) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="cd4d6-139">Hangi kullanıcı etkinliğini bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="cd4d6-140">Mümkünse, bir ' aynı veya farklı A. olabilir</span><span class="sxs-lookup"><span data-stu-id="cd4d6-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Zaman uyumsuz bir geri çağırma, geri çağırma içinde endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![Zaman uyumsuz bir geri çağırma, geri çağırma dışında endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="cd4d6-143">Zaman uyumsuz geri çağırma sunucusuyla</span><span class="sxs-lookup"><span data-stu-id="cd4d6-143">Asynchronous Server with Callback</span></span>  
 ![Zaman uyumsuz bir geri çağırma sunucusuyla gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 <span data-ttu-id="cd4d6-145">İstemci geri çağırır iletisi üzerinde kanal yığın: Bu işlem için izlemeler ProcessRequest etkinlik kendisini yayılan.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="cd4d6-146">Hatalar ile zaman uyumsuz istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="cd4d6-146">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="cd4d6-147">Sırasında alınan hata iletisi hataları `endCall`.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="cd4d6-148">Aksi takdirde, etkinlikleri ve aktarımları önceki senaryolara benzer.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="cd4d6-149">Zaman uyumsuz olan veya olmayan hataları tek yönlü</span><span class="sxs-lookup"><span data-stu-id="cd4d6-149">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="cd4d6-150">İstemciye yanıt ya da hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cd4d6-150">No response or fault is returned to the client.</span></span>
