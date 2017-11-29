---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c697069aad590013ff360eb6ee4cba39468b89d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="e14d8-102">HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar</span><span class="sxs-lookup"><span data-stu-id="e14d8-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="e14d8-103">Bu konuda veya adlandırılmış etkinlikleri ve aktarımlar farklı zaman uyumsuz istek/yanıt senaryoları için HTTP, TCP, kullanarak birden çok iş parçacıklı isteklerle açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="e14d8-104">Zaman uyumsuz istek/yanıt hatasız</span><span class="sxs-lookup"><span data-stu-id="e14d8-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="e14d8-105">Bu bölümde etkinlikler ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="e14d8-106">Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e14d8-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="e14d8-107">Bir geri çağırma çağrılıp çağrılmayacağını geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e14d8-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="e14d8-108">Çağrılan etkinlik ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, ya da geri döndüğünde bu etkinliğinden çağrıldı durumunda.</span><span class="sxs-lookup"><span data-stu-id="e14d8-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="e14d8-109">Zaman uyumsuz istemcisi olmadan geri çağırma</span><span class="sxs-lookup"><span data-stu-id="e14d8-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="e14d8-110">Her iki HTTP kullanarak tarafta yayma etkin</span><span class="sxs-lookup"><span data-stu-id="e14d8-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 <span data-ttu-id="e14d8-111">![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span><span class="sxs-lookup"><span data-stu-id="e14d8-111">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span></span>  
  
 <span data-ttu-id="e14d8-112">Şekil 1 '.</span><span class="sxs-lookup"><span data-stu-id="e14d8-112">Figure 1.</span></span> <span data-ttu-id="e14d8-113">Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `true` her iki tarafında, HTTP</span><span class="sxs-lookup"><span data-stu-id="e14d8-113">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, HTTP</span></span>  
  
 <span data-ttu-id="e14d8-114">Varsa `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="e14d8-114">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="e14d8-115">HTTP tabanlı senaryoları için ReceiveBytes göndermek için ilk ileti çağrılır ve istek ömrü boyunca bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-115">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="e14d8-116">Yayma ya da HTTP kullanarak tarafta, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="e14d8-116">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="e14d8-117">Varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="e14d8-117">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="e14d8-118">Bu nedenle, yeni bir kimliği ile yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-118">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="e14d8-119">ServiceModel kod istek için zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e14d8-119">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="e14d8-120">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="e14d8-120">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="e14d8-121">![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span><span class="sxs-lookup"><span data-stu-id="e14d8-121">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span></span>  
  
 <span data-ttu-id="e14d8-122">Şekil 2 '.</span><span class="sxs-lookup"><span data-stu-id="e14d8-122">Figure 2.</span></span> <span data-ttu-id="e14d8-123">Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `false` her iki tarafında, HTTP</span><span class="sxs-lookup"><span data-stu-id="e14d8-123">Asynchronous client, no callback, `propagateActivity`=`false` on either side, HTTP</span></span>  
  
 <span data-ttu-id="e14d8-124">HTTP tabanlı senaryoları için ReceiveBytes göndermek için ilk ileti çağrılır ve istek ömrü boyunca bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-124">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="e14d8-125">Bir işlem eylem etkinlik zaman uyumsuz bir istemcide oluşturulan zaman `propagateActivity` = `false` çağıran ve çağrılan ve yanıt iletisi bir eylem üstbilgisi içermez.</span><span class="sxs-lookup"><span data-stu-id="e14d8-125">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="e14d8-126">Yayma hem TCP veya adlandırılmış kanal kullanarak tarafta etkin</span><span class="sxs-lookup"><span data-stu-id="e14d8-126">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="e14d8-127">![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span><span class="sxs-lookup"><span data-stu-id="e14d8-127">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span></span>  
  
 <span data-ttu-id="e14d8-128">Şekil 3 '.</span><span class="sxs-lookup"><span data-stu-id="e14d8-128">Figure 3.</span></span> <span data-ttu-id="e14d8-129">Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `true` her iki tarafında Named-Pipe/TCP</span><span class="sxs-lookup"><span data-stu-id="e14d8-129">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, Named-Pipe/TCP</span></span>  
  
 <span data-ttu-id="e14d8-130">İstemci açılmış ve bağlantı ömrü için mevcut bir adlandırılmış kanal veya TCP tabanlı senaryo için ReceiveBytes çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-130">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="e14d8-131">Benzer ise 1, Şekil `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="e14d8-131">Similar to Figure 1, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="e14d8-132">Yayma ya da TCP veya adlandırılmış kanal kullanarak tarafta, devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="e14d8-132">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="e14d8-133">İstemci açılmış ve bağlantı ömrü için mevcut bir adlandırılmış kanal veya TCP tabanlı senaryo için ReceiveBytes çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-133">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="e14d8-134">Benzer şekilde Fig.2, varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez.</span><span class="sxs-lookup"><span data-stu-id="e14d8-134">Similar to Fig.2, If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="e14d8-135">Bu nedenle, yeni bir kimliği ile yeni bir geçici ProcessAction etkinlik çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e14d8-135">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="e14d8-136">ServiceModel kod istek için zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e14d8-136">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="e14d8-137">Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="e14d8-137">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="e14d8-138">![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış Kanallar](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span><span class="sxs-lookup"><span data-stu-id="e14d8-138">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span></span>  
  
 <span data-ttu-id="e14d8-139">Şekil 4 '.</span><span class="sxs-lookup"><span data-stu-id="e14d8-139">Figure 4.</span></span> <span data-ttu-id="e14d8-140">Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `false` her iki tarafında Named-Pipe/TCP</span><span class="sxs-lookup"><span data-stu-id="e14d8-140">Asynchronous client, no callback, `propagateActivity`=`false` on either side, Named-Pipe/TCP</span></span>  
  
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="e14d8-141">Zaman uyumsuz istemci geri araması ile</span><span class="sxs-lookup"><span data-stu-id="e14d8-141">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="e14d8-142">Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları giriş/çıkış.</span><span class="sxs-lookup"><span data-stu-id="e14d8-142">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="e14d8-143">Bu bölüm, yalnızca HTTP kullanarak gösterir `propragateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="e14d8-143">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="e14d8-144">Ancak, ek etkinlikler ve aktarımları de diğer örnekleri için geçerlidir (yani, `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).</span><span class="sxs-lookup"><span data-stu-id="e14d8-144">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="e14d8-145">İstemci sonuç hazır olduğunu bildirmek için kullanıcı kodu çağırdığında geri çağırma yeni bir etkinlik (G) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e14d8-145">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="e14d8-146">Kullanıcı kodu daha sonra çağırır `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında geri çağırma (Şekil 6).</span><span class="sxs-lookup"><span data-stu-id="e14d8-146">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="e14d8-147">Hangi kullanıcı etkinliği bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`.</span><span class="sxs-lookup"><span data-stu-id="e14d8-147">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="e14d8-148">Mümkünse A' özdeş veya A. farklı olabilir</span><span class="sxs-lookup"><span data-stu-id="e14d8-148">It is possible that A’ can be identical to or different from A.</span></span>  
  
 <span data-ttu-id="e14d8-149">![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span><span class="sxs-lookup"><span data-stu-id="e14d8-149">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span></span>  
  
 <span data-ttu-id="e14d8-150">Şekil 5.</span><span class="sxs-lookup"><span data-stu-id="e14d8-150">Figure 5.</span></span> <span data-ttu-id="e14d8-151">Zaman uyumsuz geri çağırma, istemciyle `endCall` içinde geri çağırma</span><span class="sxs-lookup"><span data-stu-id="e14d8-151">Asynchronous client with callback, `endCall` in Callback</span></span>  
  
 <span data-ttu-id="e14d8-152">![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span><span class="sxs-lookup"><span data-stu-id="e14d8-152">![Asynchronous Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span></span>  
  
 <span data-ttu-id="e14d8-153">Şekil 6.</span><span class="sxs-lookup"><span data-stu-id="e14d8-153">Figure 6.</span></span> <span data-ttu-id="e14d8-154">Zaman uyumsuz geri çağırma, istemciyle `endCall` geri çağırma dışında</span><span class="sxs-lookup"><span data-stu-id="e14d8-154">Asynchronous client with callback, `endCall` outside of Callback</span></span>  
  
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="e14d8-155">Zaman uyumsuz geri çağırma sunucusuyla</span><span class="sxs-lookup"><span data-stu-id="e14d8-155">Asynchronous Server with Callback</span></span>  
 <span data-ttu-id="e14d8-156">![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlı &#45; Kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span><span class="sxs-lookup"><span data-stu-id="e14d8-156">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named&#45;Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span></span>  
  
 <span data-ttu-id="e14d8-157">Şekil 7.</span><span class="sxs-lookup"><span data-stu-id="e14d8-157">Figure 7.</span></span> <span data-ttu-id="e14d8-158">Zaman uyumsuz sunucusuyla, geri çağırma</span><span class="sxs-lookup"><span data-stu-id="e14d8-158">Asynchronous server, with callback</span></span>  
  
 <span data-ttu-id="e14d8-159">İstemci geri çağrıları iletisi alıyorsunuz kanal yığın: Bu işlem için izlemeleri ProcessRequest etkinlik kendisini yayılan.</span><span class="sxs-lookup"><span data-stu-id="e14d8-159">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="e14d8-160">Zaman uyumsuz istek/yanıt hatalı</span><span class="sxs-lookup"><span data-stu-id="e14d8-160">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="e14d8-161">Sırasında alınan hata iletisi hataları `endCall`.</span><span class="sxs-lookup"><span data-stu-id="e14d8-161">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="e14d8-162">Aksi takdirde, etkinlikler ve aktarımları önceki senaryolara benzer.</span><span class="sxs-lookup"><span data-stu-id="e14d8-162">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="e14d8-163">Zaman uyumsuz olan veya olmayan hataları tek yönlü</span><span class="sxs-lookup"><span data-stu-id="e14d8-163">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="e14d8-164">İstemciye yanıt ya da hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e14d8-164">No response or fault is returned to the client.</span></span>
