---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 494a0665f5bad2c7da3998cf77ced79314ca2f36
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="31d95-102">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="31d95-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="31d95-103">Özel durumlar, yerel hizmet veya istemci uygulaması içindeki hataları iletişim kurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="31d95-104">Hataları, diğer yandan hataları hizmet sınırları boyunca gibi istemci (veya tersi) sunucusundan iletişim kurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="31d95-105">Hataları yanı sıra, taşıma kanalları çoğunlukla aktarım özgü mekanizmaları aktarım düzeyi hataları iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="31d95-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="31d95-106">Örneğin, HTTP taşıma (bir arıza geri gönderilecek bitiş noktası yoktur) bir var olmayan uç nokta URL'si iletişim kurmak için durum kodları 404 gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="31d95-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="31d95-107">Özel kanal yazarları için kılavuzluk üç bölüm, bu belgede oluşur.</span><span class="sxs-lookup"><span data-stu-id="31d95-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="31d95-108">İlk bölümde, ne zaman ve nasıl tanımlamak ve özel durumlar oluşturma yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="31d95-109">İkinci bölümde oluşturma ve hatalarını tüketen etrafında yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="31d95-110">Üçüncü bölüm özel kanal kullanıcı çalışan uygulamalarda sorun gidermede yardımcı olmak için izleme bilgilerini sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="31d95-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="31d95-111">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="31d95-111">Exceptions</span></span>  
 <span data-ttu-id="31d95-112">Bir özel durum atma zaman göz önünde bulundurmanız gereken iki nokta vardır: önce kullanıcıların özel durumu uygun şekilde tepki gösterebilmesi doğru kod yazmanıza olanak veren bir türde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="31d95-113">İkinci olarak, nelerin yanlış gittiğini anlamak için kullanıcıyı, hata etkisi ve nasıl düzeltileceği için yeterli bilgi sağlamak vardır.</span><span class="sxs-lookup"><span data-stu-id="31d95-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="31d95-114">Aşağıdaki bölümlerde, özel durum türleri ve Windows Communication Foundation (WCF) kanalları iletileri geçici rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="31d95-115">Özel durumlar belge için tasarım yönergeleri .NET özel durumları genel yönergeler bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="31d95-116">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="31d95-116">Exception Types</span></span>  
 <span data-ttu-id="31d95-117">Kanalları tarafından oluşturulan tüm özel durumları ya da olmalıdır bir <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, veya türetilmiş bir tür <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="31d95-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="31d95-118">(Özel durumlar gibi <xref:System.ObjectDisposedException> de, ancak yalnızca çağıran kodu kanal kötüye kullanımını göstermek için durum oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="31d95-119">Bir kanal doğru kullandıysanız, yalnızca belirli özel durumlar oluşturma gerekir.) Öğesinden türetilen yedi özel durum türü WCF sunar <xref:System.ServiceModel.CommunicationException> ve kanalları tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31d95-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="31d95-120">Diğer vardır <xref:System.ServiceModel.CommunicationException>-sisteminin diğer bölümleriyle tarafından kullanılmak üzere tasarlanmış özel durumlar türetilmiş.</span><span class="sxs-lookup"><span data-stu-id="31d95-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="31d95-121">Bu özel durum türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31d95-121">These exception types are:</span></span>  
  
|<span data-ttu-id="31d95-122">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="31d95-122">Exception Type</span></span>|<span data-ttu-id="31d95-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31d95-123">Meaning</span></span>|<span data-ttu-id="31d95-124">İç özel duruma içeriği</span><span class="sxs-lookup"><span data-stu-id="31d95-124">Inner Exception Content</span></span>|<span data-ttu-id="31d95-125">Kurtarma stratejisi</span><span class="sxs-lookup"><span data-stu-id="31d95-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="31d95-126">Dinlemek için belirtilen uç nokta adresi zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="31d95-127">Varsa, bu özel durumun nedeni aktarım hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="31d95-128">Örneğin.</span><span class="sxs-lookup"><span data-stu-id="31d95-128">For example.</span></span> <span data-ttu-id="31d95-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, veya <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="31d95-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="31d95-130">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="31d95-131">İşlem dinlemek için belirtilen uç nokta adresi erişmesine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="31d95-132">Varsa, bu özel durumun nedeni aktarım hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="31d95-133">Örneğin, <xref:System.IO.PipeException>, veya <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="31d95-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="31d95-134">Farklı kimlik bilgileriyle deneyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="31d95-135"><xref:System.ServiceModel.ICommunicationObject> Kullanılmakta olan Faulted durumunda (daha fazla bilgi için bkz: [anlama durum değişiklikleri](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="31d95-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="31d95-136">Bir nesne, birden çok Faulted durumunda çağrıları geçişleri bekleyen yalnızca bir çağrı hatası ve çağrıları throw geri kalanı ile ilgili bir özel durum atar Not bir <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="31d95-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="31d95-137">Çünkü uygulamanın bazı özel durum gözden ve zaten hatalı bir nesne, büyük olasılıkla orijinal özel durumu yakalandı farklı bir iş parçacığında kullanmayı dener ve bu durum genellikle atılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="31d95-138">Varsa, iç özel duruma hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="31d95-139">Yeni nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="31d95-139">Create a new object.</span></span> <span data-ttu-id="31d95-140">Neyin neden bağlı olarak unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta arıza için kurtarmak için gereken diğer iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="31d95-141"><xref:System.ServiceModel.ICommunicationObject> Kullanılan durduruldu (daha fazla bilgi için bkz: [anlama durum değişiklikleri](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="31d95-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="31d95-142">Benzer şekilde <xref:System.ServiceModel.CommunicationObjectFaultedException>, kendi özel durumu uygulama olarak adlandırılan gösterir <xref:System.ServiceModel.ICommunicationObject.Abort%2A> nesnesi, büyük olasılıkla başka bir iş parçacığı üzerinde ve nesne artık bu nedenle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="31d95-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="31d95-143">Varsa, iç özel duruma hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="31d95-144">Yeni nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="31d95-144">Create a new object.</span></span> <span data-ttu-id="31d95-145">Neyin neden bağlı olarak unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta iptal etmek için diğer iş kurtarmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="31d95-146">Hedef uzak uç noktada dinleme değil.</span><span class="sxs-lookup"><span data-stu-id="31d95-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="31d95-147">Bu herhangi bir parçası olan yanlış, irresolvable uç noktası adresi ya da aşağı olan uç nokta neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="31d95-148">Örnekler DNS hatası, sıra Yöneticisi kullanılabilir değil ve hizmet çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="31d95-149">İç özel duruma ayrıntılarının, genellikle temel aktarımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="31d95-150">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-150">Try a different address.</span></span> <span data-ttu-id="31d95-151">Alternatif olarak, gönderici bir süre bekleyin ve durumda aşağı hizmeti, yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="31d95-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="31d95-152">İletişim protokolleri uç noktanın İlkesi tarafından açıklanan uç noktaları arasında eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="31d95-153">Örneğin, içerik türü uyuşmazlığı veya maksimum ileti boyutu aşıldı çerçeveleme.</span><span class="sxs-lookup"><span data-stu-id="31d95-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="31d95-154">Varsa, belirli bir protokol hata hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="31d95-155">Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedenini MaxReceivedMessageSize aşıldığında iç istisnadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="31d95-156">Kurtarma: gönderen ve alınan Protokolü ayarlarla eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="31d95-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="31d95-157">Bunu yapmanın bir yolu, hizmet uç noktanın meta veriler (ilke) yeniden içeri aktarın ve kanal yeniden oluşturmak için oluşturulan bağlama kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="31d95-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="31d95-158">Uzak uç noktada dinleme ancak iletileri işlemek hazır değil.</span><span class="sxs-lookup"><span data-stu-id="31d95-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="31d95-159">Varsa, iç özel duruma bir SOAP hatası veya aktarım düzeyinde hata ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="31d95-160">Kurtarma: Bekleyin ve daha sonra işlemi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="31d95-161">İşlem zaman aşımı süresi içinde tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="31d95-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="31d95-162">Zaman aşımı ayrıntılarını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-162">May provide details about the timeout.</span></span>|<span data-ttu-id="31d95-163">Bekleyin ve daha sonra işlemi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="31d95-164">Yalnızca bu belirli bir kurtarma stratejisi tüm var olan özel durum türleri farklı karşılık gelen türü varsa yeni bir özel durum türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="31d95-165">Yeni bir özel durum türü tanımlarsanız öğesinden türetilmelidir <xref:System.ServiceModel.CommunicationException> veya türetilmiş sınıflarından biri.</span><span class="sxs-lookup"><span data-stu-id="31d95-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="31d95-166">Özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="31d95-166">Exception Messages</span></span>  
 <span data-ttu-id="31d95-167">Özel durum iletilerini kullanıcının hedeflenen kullanıcı anlamanıza ve sorunu çözmenize yardımcı olması için yeterli bilgi vermelidir böylece programın değil.</span><span class="sxs-lookup"><span data-stu-id="31d95-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="31d95-168">İyi özel durum iletisi üç temel bölümleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31d95-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="31d95-169">Ne oldu.</span><span class="sxs-lookup"><span data-stu-id="31d95-169">What happened.</span></span> <span data-ttu-id="31d95-170">Kullanıcı deneyimi ile ilgili koşulları'nı kullanarak sorunun anlaşılır bir açıklama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="31d95-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="31d95-171">Örneğin, hatalı özel durum iletisi "Geçersiz yapılandırma bölümünde" olur.</span><span class="sxs-lookup"><span data-stu-id="31d95-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="31d95-172">Bu, kullanıcının hangi yapılandırma bölümü hatalı ve neden yanlış olduğunu merak ediyor bırakır.</span><span class="sxs-lookup"><span data-stu-id="31d95-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="31d95-173">Geliştirilmiş iletisine olacaktır "Geçersiz yapılandırma bölümü \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="31d95-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="31d95-174">Daha iyi bir ileti olacaktır "myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten".</span><span class="sxs-lookup"><span data-stu-id="31d95-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="31d95-175">Bu, uygulamanın yapılandırma dosyasında hüküm ve kullanıcı kolayca tanıyacak adlarını kullanarak, belirli bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="31d95-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="31d95-176">Ancak, eksik hala birkaç anahtar bileşenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="31d95-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="31d95-177">Hata önemi.</span><span class="sxs-lookup"><span data-stu-id="31d95-177">The significance of the error.</span></span> <span data-ttu-id="31d95-178">İleti açıkça hata anlamı belirtilmedikçe, kullanıcı önemli bir hata olup olmadığını veya yoksayılabilir varsa merak ediyor olasıdır.</span><span class="sxs-lookup"><span data-stu-id="31d95-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="31d95-179">Genel olarak, iletileri anlamı ya da hata önemini neden.</span><span class="sxs-lookup"><span data-stu-id="31d95-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="31d95-180">Önceki örnekte geliştirmek için ileti olabilir "ServiceHost açık bir yapılandırma hatası nedeniyle başarısız oldu: myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten".</span><span class="sxs-lookup"><span data-stu-id="31d95-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="31d95-181">Nasıl kullanıcı sorunu düzeltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-181">How the user should correct the problem.</span></span> <span data-ttu-id="31d95-182">İleti en önemli bir parçası kullanıcı düzeltme sorun yardımcı oluyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="31d95-183">İletinin bazı yönergeler veya denetleyin veya sorunu çözmek düzeltme gerekenler hakkında ipuçları içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="31d95-184">Örneğin, "ServiceHost açık bir yapılandırma hatası nedeniyle başarısız oldu: myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten.</span><span class="sxs-lookup"><span data-stu-id="31d95-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="31d95-185">Lütfen yalnızca bir aktarım bağlama sağlayın".</span><span class="sxs-lookup"><span data-stu-id="31d95-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="31d95-186">İletişim hataları</span><span class="sxs-lookup"><span data-stu-id="31d95-186">Communicating Faults</span></span>  
 <span data-ttu-id="31d95-187">SOAP 1.1 ve SOAP 1.2 hataları için belirli bir yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="31d95-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="31d95-188">İki özellikleri arasında bazı farklar vardır, ancak genel olarak, ileti ve MessageFault türleri oluşturmak ve hataları kullanmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="31d95-189">![Özel durumlar ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1 1AndSOAP1 2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="31d95-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="31d95-190">SOAP 1.2 arıza (sol) ve (sağdaki) bir SOAP 1.1 hatası.</span><span class="sxs-lookup"><span data-stu-id="31d95-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="31d95-191">SOAP 1.1 tam ad alanı yalnızca hataya öğesi olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="31d95-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="31d95-192">SOAP yalnızca bir hata öğesi içeren bir ileti bir hata iletisi tanımlar (adı olan bir öğeyi `<env:Fault>`) bir alt öğesi olarak `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="31d95-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="31d95-193">Hataya öğenin içeriğini, biraz Şekil 1 ' gösterildiği gibi SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="31d95-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="31d95-194">Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıfı normalleştirir bir nesne modeline Bu farklılıklar:</span><span class="sxs-lookup"><span data-stu-id="31d95-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 <span data-ttu-id="31d95-195">`Code` Özelliğine karşılık gelen `env:Code` (veya `faultCode` SOAP 1.1 içinde) ve hataya türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="31d95-196">SOAP 1.2 tanımlar için beş izin verilen değerler `faultCode` (örneğin, gönderici ve alıcı) ve tanımlayan bir `Subcode` herhangi bir alt değer içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="31d95-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="31d95-197">(Bkz [SOAP 1.2 belirtimi](http://go.microsoft.com/fwlink/?LinkId=95176) izin verilen hata kodları ve anlamları listesi için.) SOAP 1.1 biraz farklı mekanizması vardır: dört tanımlar `faultCode` tamamen yenilerini tanımlayarak ya da daha fazla belirli oluşturulacağı noktalı gösterim kullanılarak genişletilmiş değerleri (örneğin, istemci ve sunucu) `faultCodes`, örneğin, Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="31d95-197">(See the [SOAP 1.2 specification](http://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="31d95-198">Ne zaman FaultCode.Name program hataları MessageFault kullanın ve FaultCode.Namespace eşler adı ve SOAP 1.2 ad alanı `env:Code` veya SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="31d95-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="31d95-199">FaultCode.SubCode eşlendiği `env:Subcode` SOAP 1.2 ve SOAP 1.1 için null.</span><span class="sxs-lookup"><span data-stu-id="31d95-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="31d95-200">Yeni hata kodlarını (veya SOAP 1.1 kullanıyorsanız yeni hata kodları) oluşturmalısınız program aracılığıyla bir arıza ayırt etmek ilginç ise.</span><span class="sxs-lookup"><span data-stu-id="31d95-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="31d95-201">Bu, yeni bir özel durum türü oluşturmak için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="31d95-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="31d95-202">SOAP 1.1 hata kodlarıyla noktalı gösterim kullanılarak kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="31d95-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="31d95-203">( [WS-ı temel profil](http://go.microsoft.com/fwlink/?LinkId=95177) hata kodu noktalı gösterim kullanımını da zorlaştırır.)</span><span class="sxs-lookup"><span data-stu-id="31d95-203">(The [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 <span data-ttu-id="31d95-204">`Reason` Özelliğine karşılık gelen `env:Reason` (veya `faultString` SOAP 1.1 içinde) özel durum iletisi benzer hata koşulu okunabilir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="31d95-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="31d95-205">`FaultReason` Sınıfı (ve SOAP `env:Reason/faultString`) birden çok çevirisinde Genelleştirme gerçekleştirebiliriz sahip olmak için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="31d95-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 <span data-ttu-id="31d95-206">Hata ayrıntı içeriği de dahil olmak üzere çeşitli yöntemlerle MessageFault üzerinde gösterilen `GetDetail` \<T > ve `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="31d95-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="31d95-207">Hata ayrıntı, hata hakkında ek ayrıntılar taşınma donuk bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="31d95-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="31d95-208">Bu hata ile gerçekleştirmek istediğiniz bazı rastgele yapılandırılmış ayrıntı ise yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="31d95-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="31d95-209">Oluşturma hataları</span><span class="sxs-lookup"><span data-stu-id="31d95-209">Generating Faults</span></span>  
 <span data-ttu-id="31d95-210">Bu bölümde bir kanal veya kanal tarafından oluşturulan bir ileti özelliği algılanan bir hata koşulu yanıtta bir arıza oluşturma işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="31d95-211">Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak bir hata geri gönderiyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="31d95-212">Bir arıza oluşturulurken özel kanal hataya doğrudan göndermemelisiniz, bunun yerine, bir özel durum ve üzerindeki başka bir özel durum bir hata dönüştürülüp dönüştürülmeyeceğini ve göndermek nasıl karar katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="31d95-213">Bu dönüştürme yardımcı olmak için kanal sağlamalıdır bir `FaultConverter` uygulamasında, uygun hataya özel kanal tarafından oluşturulan özel durum dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31d95-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="31d95-214">`FaultConverter` olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="31d95-214">`FaultConverter` is defined as:</span></span>  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 <span data-ttu-id="31d95-215">Özel hatalar oluşturan her bir kanala uygulamalıdır `FaultConverter` ve çağrısından döndürün `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="31d95-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="31d95-216">Özel `OnTryCreateFaultMessage` uygulama için bir hata özel durum Dönüştür veya temsilci iç kanalın için `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="31d95-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="31d95-217">Kanal aktarım ise özel durum Dönüştür veya temsilci kodlayıcıya 's `FaultConverter` veya varsayılan `FaultConverter` WCF'de sağlanan.</span><span class="sxs-lookup"><span data-stu-id="31d95-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="31d95-218">Varsayılan `FaultConverter` WS adresleme ve SOAP tarafından belirtilen hata iletileri için karşılık gelen hataları dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="31d95-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="31d95-219">İşte bir örnek `OnTryCreateFaultMessage` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="31d95-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="31d95-220">Hataları gerektiren hata koşulları için Katmanlar arasında oluşturulan özel durumları doğru hataya oluşturmak karşılık gelen arıza Oluşturucu için yeterli bilgi içermelidir olduğu bu desenin bir çıkarımında bulunulur.</span><span class="sxs-lookup"><span data-stu-id="31d95-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="31d95-221">Özel kanal yazar olarak, bu tür özel durumlar zaten yoksa, farklı hata koşulları için karşılık gelen özel durum türleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="31d95-222">Kanal katmanlarının çapraz geçiş yapan özel durumlar donuk arıza verilerini yerine hata koşulu iletişim unutmayın.</span><span class="sxs-lookup"><span data-stu-id="31d95-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="31d95-223">Hata kategorisi</span><span class="sxs-lookup"><span data-stu-id="31d95-223">Fault Categories</span></span>  
 <span data-ttu-id="31d95-224">Genellikle hatalarının üç kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="31d95-224">There are generally three categories of faults:</span></span>  
  
1.  <span data-ttu-id="31d95-225">Tüm yığın yaygın hataları.</span><span class="sxs-lookup"><span data-stu-id="31d95-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="31d95-226">Bu hataları kanal yığınında, örneğin InvalidCardinalityAddressingException herhangi katmanında karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="31d95-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2.  <span data-ttu-id="31d95-227">Olabilecek hataları herhangi bir yere yığınında belirli bir katmanının akışlı bir işlem veya güvenlik rollerini ait örneğin bazı hatalarla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="31d95-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3.  <span data-ttu-id="31d95-228">Yığındaki tek bir katmanında yönlendirilmiş hataları, örneğin hataları WS-RM sıra numarası hataları gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="31d95-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="31d95-229">Kategori 1.</span><span class="sxs-lookup"><span data-stu-id="31d95-229">Category 1.</span></span> <span data-ttu-id="31d95-230">Genellikle WS adresleme ve SOAP hataları hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="31d95-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="31d95-231">Temel `FaultConverter` bu özel durumlar dönüştürmeyi gerekmez şekilde WCF tarafından hata iletileri için karşılık gelen dönüştürür hataları WS adresleme ve SOAP tarafından kendiniz belirtilen sağlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31d95-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="31d95-232">Kategori 2.</span><span class="sxs-lookup"><span data-stu-id="31d95-232">Category 2.</span></span> <span data-ttu-id="31d95-233">Bir katman tamamen katmana ilgilidir ileti bilgilerini tüketen değil ileti bir özellik ekler hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="31d95-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="31d95-234">Daha yüksek bir katman daha fazla bilgi iletisi işleyemedi ileti özelliği sorduğunda hataları daha sonra algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="31d95-235">Bu tür kanalları uygulamalıdır `GetProperty` daha önce doğru hataya geri göndermek daha yüksek katman etkinleştirmek için belirtilen.</span><span class="sxs-lookup"><span data-stu-id="31d95-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="31d95-236">Bu TransactionMessageProperty örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31d95-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="31d95-237">Bu özellik tamamen (Dağıtılmış İşlem Düzenleyicisi (DTC) başvurarak gerektirebilir Bunun yapılması. üstbilgisindeki tüm verilere doğrulamadan iletiye eklenir</span><span class="sxs-lookup"><span data-stu-id="31d95-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="31d95-238">Kategori 3.</span><span class="sxs-lookup"><span data-stu-id="31d95-238">Category 3.</span></span> <span data-ttu-id="31d95-239">Hataları yalnızca oluşturulur ve tek bir işlemcinin katmanda tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="31d95-240">Bu nedenle tüm özel durumları katman içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="31d95-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="31d95-241">Kanallar ve kolaylığı bakım arasında tutarlılığı artırmak için özel kanal bile iç hataları için hata iletileri oluşturmak için daha önce belirtilen desenle kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="31d95-242">Alınan hataları yorumlama</span><span class="sxs-lookup"><span data-stu-id="31d95-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="31d95-243">Bu bölümde, bir hata iletisi alırken uygun özel durum oluşturmak için yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="31d95-244">Yığındaki her katmanında bir ileti işleme için karar ağacı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="31d95-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1.  <span data-ttu-id="31d95-245">Geçersiz olduğu için ileti katmanı göz önünde bulundurur varsa Katman 'geçersiz bir ileti' işlemesi yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="31d95-246">Bu tür işleme katmana özgü ancak izleme, iletinin bırakarak dahil olabilir veya bir özel durum atma bir hataya dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="31d95-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="31d95-247">Güvenlik düzgün korunmuyorsa bir mesaj alarak veya hatalı sıra numarasına sahip bir ileti alma RM örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2.  <span data-ttu-id="31d95-248">Aksi takdirde, ileti özellikle katmana uygulanır bir hata iletisi ve ileti katman etkileşim dışında anlamlı değil, katman hata koşulu işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="31d95-249">Bu RM kanal yukarıda katmanlara anlamsız ve RM kanal hatalı ve gelen bekleyen işlemler atma gelir bir RM sırası reddedildi hatası örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31d95-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3.  <span data-ttu-id="31d95-250">Aksi takdirde, ileti Request() veya Receive() döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="31d95-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="31d95-251">Bu, burada hataya katman tanır, ancak hata yalnızca bir istek başarısız oldu ve kanal hatalı ve gelen bekleyen işlemler atma göstermez gösterir durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="31d95-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="31d95-252">Böyle bir durumda kullanılabilirliğini artırmak için katman uygulamalıdır `GetProperty<FaultConverter>` ve dönüş bir `FaultConverter` türetilen hataya bir özel durum için geçersiz kılarak dönüştürebilirsiniz sınıfı `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="31d95-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="31d95-253">Aşağıdaki nesne modeli, özel durumları dönüştürme iletileri destekler:</span><span class="sxs-lookup"><span data-stu-id="31d95-253">The following object model supports converting messages to exceptions:</span></span>  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 <span data-ttu-id="31d95-254">Kanal katmanını uygulayabilirsiniz `GetProperty<FaultConverter>` özel durumları dönüştürme hata iletileri desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="31d95-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="31d95-255">Bunu yapmak için geçersiz kılma `OnTryCreateException` ve hata iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="31d95-256">Kabul dönüştürme yapılamıyor, aksi takdirde dönüştürülebilmesi için iç kanal isteyin.</span><span class="sxs-lookup"><span data-stu-id="31d95-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="31d95-257">Taşıma kanalları için temsilci seçme `FaultConverter.GetDefaultFaultConverter` SOAP/WS-adresleme FaultConverter varsayılan alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="31d95-258">Tipik bir uygulama şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="31d95-258">A typical implementation looks like this:</span></span>  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="31d95-259">Farklı kurtarma senaryoları gereken belirli hata koşulları için türetilmiş bir sınıf tanımlama göz önünde bulundurun `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="31d95-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="31d95-260">MustUnderstand işleme</span><span class="sxs-lookup"><span data-stu-id="31d95-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="31d95-261">SOAP gereken bir üstbilgi alıcı tarafından anlaşılmadı sinyal genel bir hata tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31d95-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="31d95-262">Bu hata olarak bilinen `mustUnderstand` hata.</span><span class="sxs-lookup"><span data-stu-id="31d95-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="31d95-263">WCF'de, hiçbir zaman özel kanallar oluşturmak `mustUnderstand` hataları.</span><span class="sxs-lookup"><span data-stu-id="31d95-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="31d95-264">Bunun yerine, WCF iletişimi yığının üst kısmında bulunur, WCF dağıtıcısı, bakar MustUndestand işaretlenen tüm üstbilgileri = true temel yığını tarafından anlaşılan.</span><span class="sxs-lookup"><span data-stu-id="31d95-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="31d95-265">Herhangi bir anlaşılmayan, bir `mustUnderstand` arıza bu noktada oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="31d95-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="31d95-266">(Kullanıcı bunu kapatmak seçebilir `mustUnderstand` işleme ve tüm ileti üstbilgilerini almak uygulamaya sahip.</span><span class="sxs-lookup"><span data-stu-id="31d95-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="31d95-267">Uygulama in that Case gerçekleştirmek için sorumlu olduğu `mustUnderstand` işleme.) Oluşturulan hata MustUnderstand ile tüm üstbilgileri adlarını içeren bir NotUnderstood üstbilgisi içerir = değil anladım true.</span><span class="sxs-lookup"><span data-stu-id="31d95-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="31d95-268">Protokol kanal MustUnderstand sahip özel bir üstbilgi gönderirse = true ve alan bir `mustUnderstand` arıza, gerekir, şekil bu hataya, gönderilen üstbilgisi son olup.</span><span class="sxs-lookup"><span data-stu-id="31d95-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="31d95-269">İki üye vardır `MessageFault` bunun için yararlı sınıfı:</span><span class="sxs-lookup"><span data-stu-id="31d95-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="31d95-270">`IsMustUnderstandFault` döndürür `true` arıza olması durumunda bir `mustUnderstand` hatası.</span><span class="sxs-lookup"><span data-stu-id="31d95-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="31d95-271">`WasHeaderNotUnderstood` döndürür `true` üstbilgisi belirtilen ad ve ad alanı ile NotUnderstood üstbilgisi olarak hataya dahil değilse.</span><span class="sxs-lookup"><span data-stu-id="31d95-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="31d95-272">Aksi takdirde, döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="31d95-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="31d95-273">Bir kanal MustUnderstand olarak işaretlenmiş bir üstbilgi yayar katman özel durum oluşturma API'si düzeni de uygulamanız gerekir ve dönüştürmeniz gerekir. ardından, = true `mustUnderstand` bu başlığı için daha önce açıklandığı gibi daha kullanışlı bir özel nedeni hataları.</span><span class="sxs-lookup"><span data-stu-id="31d95-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="31d95-274">İzleme</span><span class="sxs-lookup"><span data-stu-id="31d95-274">Tracing</span></span>  
 <span data-ttu-id="31d95-275">.NET Framework tanılama üretim uygulamaları yardımcı olmak için bir yol olarak izleme program yürütme için bir mekanizma sağlar veya bir hata ayıklayıcı ve kod aracılığıyla adım burada yalnızca mümkün değildir zaman zaman ortaya çıkan sorunları iliştirin.</span><span class="sxs-lookup"><span data-stu-id="31d95-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="31d95-276">Bu mekanizma çekirdek bileşenlerini bulunan <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı ve oluşur:</span><span class="sxs-lookup"><span data-stu-id="31d95-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
-   <span data-ttu-id="31d95-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, yazılması için izleme bilgilerin kaynağına ait olduğu <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, gelen izlenecek bilgileri almanızı somut dinleyiciler için Özet temel sınıf olan <xref:System.Diagnostics.TraceSource> ve bir dinleyici özgü hedefine çıktı.</span><span class="sxs-lookup"><span data-stu-id="31d95-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="31d95-278">Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> çıkışları izleme bilgileri bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="31d95-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="31d95-279">Son olarak, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, izleme ayrıntı denetim uygulama kullanıcının izin verir ve genellikle yapılandırmasında belirtilen.</span><span class="sxs-lookup"><span data-stu-id="31d95-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
-   <span data-ttu-id="31d95-280">Temel bileşenlerine ek olarak, kullandığınız [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) görüntülemek ve WCF aramak için izler.</span><span class="sxs-lookup"><span data-stu-id="31d95-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="31d95-281">Aracı, WCF tarafından oluşturulan ve kullanılarak yazılan özellikle izleme dosyaları için tasarlanmıştır <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="31d95-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="31d95-282">Aşağıdaki şekilde çeşitli bileşenler izleme katılan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31d95-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="31d95-283">![Özel durumlar ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="31d95-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="31d95-284">Bir özel kanaldan izleme</span><span class="sxs-lookup"><span data-stu-id="31d95-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="31d95-285">Özel kanal çalışan uygulama bir hata ayıklayıcısı eklemeniz mümkün değilse, sorunları tanılamalarına yardımcı olmak için izleme iletilerini çıkışı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="31d95-286">Bu iki üst düzey görevler içerir: örnekleme bir <xref:System.Diagnostics.TraceSource> ve izlemelerini yazmak için kendi yöntemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="31d95-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="31d95-287">Başlatılırken bir <xref:System.Diagnostics.TraceSource>, belirttiğiniz dize kaynak adı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="31d95-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="31d95-288">Bu ad, izleme kaynağı (etkinleştir/devre dışı bırak/kümesi izleme düzeyini) yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="31d95-289">Ayrıca, kendi çıktı izlemede görünür.</span><span class="sxs-lookup"><span data-stu-id="31d95-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="31d95-290">Özel kanal izleme bilgilerini nereden geldiğini anlamak okuyucular izleme çıktısını yardımcı olmak için bir benzersiz kaynak adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="31d95-291">İzleme kaynağı adı olarak bilgilerinin yazma derlemenin adını kullanarak yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="31d95-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="31d95-292">Örneğin, WCF System.ServiceModel derlemesinden yazılan bilgi için izleme kaynağı olarak System.ServiceModel kullanır.</span><span class="sxs-lookup"><span data-stu-id="31d95-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="31d95-293">İzleme kaynağı oluşturduktan sonra arama kendi <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, veya <xref:System.Diagnostics.TraceSource.TraceInformation%2A> izleme dinleyicileri izleme girişler yazmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="31d95-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="31d95-294">Her izleme giriş için yazma, tanımlanan olay türleri biri olarak olay türünü sınıflandırmak için ihtiyacınız <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="31d95-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="31d95-295">Bu sınıflandırma ve izleme düzeyi ayarı yapılandırmasında izleme girişi dinleyicisi çıkış olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="31d95-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="31d95-296">Örneğin, yapılandırma için izleme düzeyi ayarını `Warning` sağlayan `Warning`, `Error` ve `Critical` yazılacak girişleri ancak blokları bilgiler ve ayrıntılı girişleri izleme.</span><span class="sxs-lookup"><span data-stu-id="31d95-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="31d95-297">İzleme kaynağı başlatmasını ve bilgi düzeyindeki bir giriş çıkışı yazma örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="31d95-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="31d95-298">İzleme çıktısı okuyucular çıkış nereden geldiğini anlamak amacıyla, özel kanal için benzersiz olan bir izleme kaynak adı belirtmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="31d95-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="31d95-299">İzleme Görüntüleyicisi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="31d95-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="31d95-300">Kanal tarafından oluşturulan izlemeleri, çıktı tarafından okunabilir bir biçimde olabilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> İzleme dinleyicisi olarak.</span><span class="sxs-lookup"><span data-stu-id="31d95-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="31d95-301">Bu zorunlu değildir, kanal geliştiricisi olarak, yapmanız gereken.</span><span class="sxs-lookup"><span data-stu-id="31d95-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="31d95-302">Bunun yerine, uygulama kullanıcısı (veya uygulama sorunlarını giderme kişi) olduğundan, bu İzleme dinleyicisi uygulamanın yapılandırma dosyasındaki yapılandırma gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="31d95-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="31d95-303">Örneğin, aşağıdaki yapılandırma hem izleme bilgilerini çıkarır <xref:System.ServiceModel?displayProperty=nameWithType> ve `Microsoft.Samples.Udp` adlı dosyaya `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="31d95-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="31d95-304">İzleme yapılandırılmış verileri</span><span class="sxs-lookup"><span data-stu-id="31d95-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="31d95-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> sahip bir <xref:System.Diagnostics.TraceSource.TraceData%2A> bir veya daha fazla nesne alan yöntemi olan izleme girişi dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="31d95-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="31d95-306">Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi, her nesne üzerinde çağrılır ve sonuç dizesini izleme girişi bir parçası olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="31d95-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="31d95-307">Kullanırken <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> izlemeleri çıktısını almak için geçirebilirsiniz bir <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> veri nesnesi olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="31d95-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="31d95-308">Sonuçta elde edilen izleme girişi tarafından sağlanan XML içeren <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31d95-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31d95-309">Bir örnek girdi XML uygulama verilerle şöyledir:</span><span class="sxs-lookup"><span data-stu-id="31d95-309">Here is an example entry with XML application data:</span></span>  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 <span data-ttu-id="31d95-310">WCF izleme görüntüleyicisini şeması anlar `TraceRecord` daha önce gösterilen öğesi ve kendi alt öğelerini verileri ayıklar ve tablo biçiminde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="31d95-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="31d95-311">Kanalınızı Bu şemayı yapılandırılmış uygulama verilerini izlerken veri okuma Svctraceviewer.exe kullanıcıların yardımcı olmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d95-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
