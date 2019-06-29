---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 218887f7d09e234d0d02dfa1df5c1d4e114ddc11
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422233"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="c023e-102">HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar</span><span class="sxs-lookup"><span data-stu-id="c023e-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="c023e-103">Bu konuda etkinlikler ve aktarımları farklı zaman uyumsuz istek/yanıt senaryoları için TCP ve HTTP kullanarak birden çok iş parçacıklı isteklerle açıklar veya adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="c023e-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="c023e-104">Zaman uyumsuz istek/yanıt hatasız</span><span class="sxs-lookup"><span data-stu-id="c023e-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="c023e-105">Bu bölümde, etkinlikleri ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c023e-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="c023e-106">Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="c023e-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="c023e-107">Bir geri çağırma çağrılırsa geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c023e-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="c023e-108">Çağrılan etkinliğin ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, veya geri döndüğünde, etkinlikten çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="c023e-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="c023e-109">Zaman uyumsuz istemci geri çağırma olmadan</span><span class="sxs-lookup"><span data-stu-id="c023e-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="c023e-110">Her iki HTTP kullanarak yüzüne yayma etkin</span><span class="sxs-lookup"><span data-stu-id="c023e-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 ![Zaman uyumsuz istemci için propagateActivity ayarlandığı hiçbir geri araması ile her iki tarafında true.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 <span data-ttu-id="c023e-112">Varsa `propagateActivity=true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c023e-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="c023e-113">HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.</span><span class="sxs-lookup"><span data-stu-id="c023e-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="c023e-114">Yayma ya da HTTP kullanarak yüzüne, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="c023e-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="c023e-115">Varsa `propagateActivity=false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="c023e-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="c023e-116">Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c023e-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="c023e-117">ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c023e-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="c023e-118">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="c023e-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Zaman uyumsuz istemci ile propagateActivity taraflardan üzerinde false olarak ayarlandığı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 <span data-ttu-id="c023e-120">HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.</span><span class="sxs-lookup"><span data-stu-id="c023e-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="c023e-121">Zaman uyumsuz bir istemcide bir işlem eylem etkinliği oluşturulur, `propagateActivity=false` çağıran ve çağrılan ve yanıt iletisi, bir eylem üst bilgisi içermez.</span><span class="sxs-lookup"><span data-stu-id="c023e-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="c023e-122">Yayma hem TCP veya adlandırılmış kanal kullanarak yüzüne etkin</span><span class="sxs-lookup"><span data-stu-id="c023e-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 ![Hiçbir geri çağırma propagateActivity her iki tarafında true ve adlandırılmış ayarlandığı zaman uyumsuz istemcisiyle kanal/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="c023e-124">İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c023e-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="c023e-125">İlk görüntüye benzer varsa `propagateActivity=true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c023e-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="c023e-126">Yayma ya da TCP veya adlandırılmış kanal kullanarak yüzüne, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="c023e-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="c023e-127">İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c023e-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="c023e-128">Benzer şekilde, ikinci görüntü, `propagateActivity=false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="c023e-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="c023e-129">Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c023e-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="c023e-130">ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c023e-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="c023e-131">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="c023e-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Zaman uyumsuz istemci ile burada propagateActivity iki tarafındaki false olarak ayarlayın ve kanal/TCP adlı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="c023e-133">Zaman uyumsuz geri çağırma istemcisiyle</span><span class="sxs-lookup"><span data-stu-id="c023e-133">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="c023e-134">Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları daraltma veya genişletme.</span><span class="sxs-lookup"><span data-stu-id="c023e-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="c023e-135">Bu bölüm, yalnızca HTTP kullanarak gösterir `propagateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="c023e-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="c023e-136">Ancak ek etkinlikler ve aktarımları da diğer durumlarda geçerlidir (yani `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).</span><span class="sxs-lookup"><span data-stu-id="c023e-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="c023e-137">İstemci sonuç hazır olduğunu bildiren, kullanıcı kodu çağırdığında, yeni bir etkinlik (G) geri çağırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c023e-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="c023e-138">Ardından kullanıcı kodu çağıran `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında (Şekil 6) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c023e-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="c023e-139">Hangi kullanıcı etkinliğini bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`.</span><span class="sxs-lookup"><span data-stu-id="c023e-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="c023e-140">Mümkünse, bir ' aynı veya farklı A. olabilir</span><span class="sxs-lookup"><span data-stu-id="c023e-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Zaman uyumsuz bir geri çağırma, geri çağırma içinde endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![Zaman uyumsuz bir geri çağırma, geri çağırma dışında endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="c023e-143">Zaman uyumsuz geri çağırma sunucusuyla</span><span class="sxs-lookup"><span data-stu-id="c023e-143">Asynchronous Server with Callback</span></span>  
 ![Zaman uyumsuz bir geri çağırma sunucusuyla gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 <span data-ttu-id="c023e-145">İstemci geri çağırır iletisi üzerinde kanal yığın: Bu işlem için izlemeler ProcessRequest etkinlik kendisini yayılan.</span><span class="sxs-lookup"><span data-stu-id="c023e-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="c023e-146">Hatalar ile zaman uyumsuz istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="c023e-146">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="c023e-147">Sırasında alınan hata iletisi hataları `endCall`.</span><span class="sxs-lookup"><span data-stu-id="c023e-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="c023e-148">Aksi takdirde, etkinlikleri ve aktarımları önceki senaryolara benzer.</span><span class="sxs-lookup"><span data-stu-id="c023e-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="c023e-149">Zaman uyumsuz olan veya olmayan hataları tek yönlü</span><span class="sxs-lookup"><span data-stu-id="c023e-149">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="c023e-150">İstemciye yanıt ya da hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c023e-150">No response or fault is returned to the client.</span></span>
