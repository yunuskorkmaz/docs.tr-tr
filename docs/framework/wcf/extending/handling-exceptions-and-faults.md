---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 6c56f1e4709953a78ffc5616444b5a40db9eb0f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963904"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="73063-102">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="73063-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="73063-103">Özel durumlar, hizmette veya istemci uygulamasında yerel olarak hatalara iletişim kurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73063-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="73063-104">Diğer yandan hatalar, sunucudan istemciye gibi veya tam tersi gibi hizmet sınırları genelinde hataları iletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73063-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="73063-105">Hatalara ek olarak, aktarım kanalları genellikle aktarım düzeyi hataları iletmek için aktarıma özgü mekanizmalar kullanır.</span><span class="sxs-lookup"><span data-stu-id="73063-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="73063-106">Örneğin, HTTP taşıması mevcut olmayan bir uç nokta URL 'SI ile iletişim kurmak için 404 gibi durum kodlarını kullanır (bir hata geri gönderilmesi için uç nokta yoktur).</span><span class="sxs-lookup"><span data-stu-id="73063-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="73063-107">Bu belge, özel kanal yazarlarına rehberlik sağlayan üç bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="73063-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="73063-108">İlk bölüm, özel durumların ne zaman ve nasıl tanımlanacağını ve throw hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="73063-109">İkinci bölüm, hataları oluşturma ve kullanma konusunda rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="73063-110">Üçüncü bölümde, çalışan uygulamalarda sorun gidermek için özel kanalınızın kullanıcısına yardımcı olmak üzere izleme bilgilerinin nasıl sağlanacağını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73063-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="73063-111">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="73063-111">Exceptions</span></span>  
 <span data-ttu-id="73063-112">Özel durum oluştururken aklınızda bulundurmanız gereken iki şey vardır: İlk olarak, kullanıcıların özel duruma uygun şekilde tepki veren doğru kodu yazmasına izin veren bir tür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="73063-113">İkincisi, kullanıcının neyin yanlış gittiğini, hatanın etkisini ve nasıl düzeltileceğini anlayabilmesi için yeterli bilgi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="73063-114">Aşağıdaki bölümler, Windows Communication Foundation (WCF) kanalları için özel durum türleri ve iletileri hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="73063-115">Özel durumlar için tasarım yönergelerinden .NET 'teki özel durumların etrafında de genel rehberlik vardır.</span><span class="sxs-lookup"><span data-stu-id="73063-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="73063-116">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="73063-116">Exception Types</span></span>  
 <span data-ttu-id="73063-117">Kanallar tarafından oluşturulan tüm özel durumlar <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>ya da öğesinden <xref:System.ServiceModel.CommunicationException>türetilmiş bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="73063-118">(Gibi özel durumlar <xref:System.ObjectDisposedException> da oluşturulabilir, ancak yalnızca çağıran kodun kanalı kötüye yanlış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="73063-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="73063-119">Bir kanal doğru şekilde kullanılırsa yalnızca verilen özel durumları oluşturması gerekir.) WCF, ' den <xref:System.ServiceModel.CommunicationException> türetilen ve kanallar tarafından kullanılmak üzere tasarlanan yedi özel durum türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="73063-120">Sistemin diğer bölümleri <xref:System.ServiceModel.CommunicationException>tarafından kullanılmak üzere tasarlanan, diğer türetilmiş özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="73063-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="73063-121">Bu özel durum türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="73063-121">These exception types are:</span></span>  
  
|<span data-ttu-id="73063-122">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="73063-122">Exception Type</span></span>|<span data-ttu-id="73063-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73063-123">Meaning</span></span>|<span data-ttu-id="73063-124">İç özel durum Içeriği</span><span class="sxs-lookup"><span data-stu-id="73063-124">Inner Exception Content</span></span>|<span data-ttu-id="73063-125">Kurtarma stratejisi</span><span class="sxs-lookup"><span data-stu-id="73063-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="73063-126">Dinleme için belirtilen uç nokta adresi zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="73063-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="73063-127">Varsa, bu özel duruma neden olan taşıma hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="73063-128">Örneğin.</span><span class="sxs-lookup"><span data-stu-id="73063-128">For example.</span></span> <span data-ttu-id="73063-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, veya <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="73063-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="73063-130">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="73063-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="73063-131">İşlem, dinleme için belirtilen uç nokta adresine erişime izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="73063-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="73063-132">Varsa, bu özel duruma neden olan taşıma hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="73063-133">Örneğin, <xref:System.IO.PipeException>veya <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="73063-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="73063-134">Farklı kimlik bilgileriyle deneyin.</span><span class="sxs-lookup"><span data-stu-id="73063-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="73063-135">Kullanılmakta olan durum hatalı durumda (daha fazla bilgi için bkz. [durum değişikliklerini anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject></span><span class="sxs-lookup"><span data-stu-id="73063-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="73063-136">Birden çok bekleyen çağıran bir nesne hatalı duruma geçerse, yalnızca bir çağrı hatayla ilgili bir özel durum oluşturduğunda ve çağrıların geri kalanı bir <xref:System.ServiceModel.CommunicationObjectFaultedException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73063-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="73063-137">Bu özel durum tipik olarak oluşur çünkü bir uygulama bazı özel durumları daha fazla inceler ve muhtemelen hatalı bir nesneyi kullanmaya çalışır, büyük olasılıkla özgün özel durumu yakaladı dışında bir iş parçacığında.</span><span class="sxs-lookup"><span data-stu-id="73063-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="73063-138">Varsa, iç özel durumla ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="73063-139">Yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73063-139">Create a new object.</span></span> <span data-ttu-id="73063-140">İlk yerde hatanın ne <xref:System.ServiceModel.ICommunicationObject> olduğuna bağlı olarak, kurtarmak için gereken başka bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="73063-141">Kullanılmakta olan işlem durduruldu (daha fazla bilgi için bkz. [durum değişikliklerini anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject></span><span class="sxs-lookup"><span data-stu-id="73063-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="73063-142">Benzer şekilde <xref:System.ServiceModel.CommunicationObjectFaultedException>, özel durumu uygulamanın nesne üzerinde çağırdığını <xref:System.ServiceModel.ICommunicationObject.Abort%2A> , belki de başka bir iş parçacığından olduğunu ve nesnenin artık bu nedenle kullanılamaz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="73063-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="73063-143">Varsa, iç özel durumla ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="73063-144">Yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73063-144">Create a new object.</span></span> <span data-ttu-id="73063-145">İlk yerde iptal edilmeye neden <xref:System.ServiceModel.ICommunicationObject> olduğuna bağlı olarak, kurtarmak için gereken başka bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="73063-146">Hedef uzak uç nokta dinlemiyor.</span><span class="sxs-lookup"><span data-stu-id="73063-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="73063-147">Bu, uç nokta adresinin herhangi bir kısmının yanlış, irçözümlenebilen veya bitiş noktasının çalışmıyor olmasından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="73063-148">DNS hatası, kuyruk yöneticisi kullanılamıyor ve hizmet çalışmıyor örneklerde yer verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73063-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="73063-149">İç özel durum, genellikle temel aktarımdan ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="73063-150">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="73063-150">Try a different address.</span></span> <span data-ttu-id="73063-151">Alternatif olarak, gönderici bir süre bekleyebilir ve hizmetin kapatılmış olması durumunda tekrar deneyebilir</span><span class="sxs-lookup"><span data-stu-id="73063-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="73063-152">Uç noktanın ilkesinde açıklanan iletişim protokolleri, uç noktalar arasında eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="73063-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="73063-153">Örneğin, çerçeveleme içerik türü uyumsuzluğu veya en fazla ileti boyutu aşıldı.</span><span class="sxs-lookup"><span data-stu-id="73063-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="73063-154">Varsa, belirli protokol hatası hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="73063-155">Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedeni MaxReceivedMessageSize değerini aşarak iç özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="73063-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="73063-156">Kurtarma Gönderenin ve alınan protokol ayarlarının eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="73063-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="73063-157">Bunu yapmanın bir yolu, hizmet uç noktasının meta verilerini (ilke) yeniden içeri aktarmanız ve oluşturulan bağlamayı kullanarak kanalı yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73063-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="73063-158">Uzak uç nokta dinliyor ancak iletileri işlemeye hazır değil.</span><span class="sxs-lookup"><span data-stu-id="73063-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="73063-159">Varsa, iç özel durum SOAP hata veya aktarım düzeyi hata ayrıntılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="73063-160">Kurtarma Bekleyip işlemi daha sonra yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="73063-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="73063-161">İşlem, zaman aşımı süresi içinde tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="73063-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="73063-162">Zaman aşımı hakkındaki ayrıntıları verebilir.</span><span class="sxs-lookup"><span data-stu-id="73063-162">May provide details about the timeout.</span></span>|<span data-ttu-id="73063-163">Bekleyip işlemi daha sonra yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="73063-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="73063-164">Yalnızca bu tür, mevcut özel durum türlerinden farklı olan belirli bir kurtarma stratejisine karşılık geliyorsa yeni bir özel durum türü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="73063-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="73063-165">Yeni bir özel durum türü tanımlarsanız, onun türetilmiş sınıflarından <xref:System.ServiceModel.CommunicationException> veya birinden türemelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="73063-166">Özel durum Iletileri</span><span class="sxs-lookup"><span data-stu-id="73063-166">Exception Messages</span></span>  
 <span data-ttu-id="73063-167">Özel durum iletileri, kullanıcının sorunu anlamalarına ve çözmesine yardımcı olmak için yeterli bilgi sağlamaları için programı değil kullanıcıya hedeflenirler.</span><span class="sxs-lookup"><span data-stu-id="73063-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="73063-168">İyi bir özel durum iletisinin üç temel bölümü şunlardır:</span><span class="sxs-lookup"><span data-stu-id="73063-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="73063-169">Ne oldu.</span><span class="sxs-lookup"><span data-stu-id="73063-169">What happened.</span></span> <span data-ttu-id="73063-170">Kullanıcının deneyimiyle ilgili terimleri kullanarak sorun hakkında net bir açıklama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="73063-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="73063-171">Örneğin, hatalı bir özel durum iletisi "geçersiz yapılandırma bölümü" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="73063-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="73063-172">Bu, kullanıcının hangi yapılandırma bölümünün yanlış olduğunu ve neden yanlış olduğunu merak eden kullanıcı olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="73063-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="73063-173">İyileştirilmiş bir ileti "geçersiz yapılandırma bölümü \<CustomBinding >" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="73063-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="73063-174">Daha da iyi bir ileti "myTransport adlı bağlamaya myBinding adlı bağlamaya eklenemiyor, çünkü bağlama zaten myTransport adlı bir aktarıma sahip" olur.</span><span class="sxs-lookup"><span data-stu-id="73063-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="73063-175">Bu, kullanıcının uygulama yapılandırma dosyasında kolayca tanımlayabilmesi için hüküm ve adları kullanan çok özel bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="73063-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="73063-176">Ancak, hala birkaç anahtar bileşen eksik.</span><span class="sxs-lookup"><span data-stu-id="73063-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="73063-177">Hatanın önemi.</span><span class="sxs-lookup"><span data-stu-id="73063-177">The significance of the error.</span></span> <span data-ttu-id="73063-178">İleti, hatanın ne anlama geldiğini açıkça belirtmedikçe, Kullanıcı önemli bir hata olup olmadığını veya yoksayılıp yoksayılmadığını merak ediyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="73063-179">Genel olarak, iletiler hatanın anlamı veya önemi ile sonuçlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="73063-180">Önceki örneği geliştirmek için, "bir yapılandırma hatası nedeniyle" ServiceHost açılamadı: MyTransport adlı bağlamaya myBinding adlı bağlama eklenemiyor çünkü bağlamanın zaten myTransport adlı bir taşıması var.</span><span class="sxs-lookup"><span data-stu-id="73063-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="73063-181">Kullanıcının sorunu nasıl düzeltebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-181">How the user should correct the problem.</span></span> <span data-ttu-id="73063-182">İletinin en önemli bölümü, kullanıcının sorunu gidermesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="73063-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="73063-183">İleti, sorunu gidermek için nelerin denetlenmesi veya düzeltilmesi hakkında bazı kılavuz veya ipuçları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="73063-184">Örneğin, "bir yapılandırma hatası nedeniyle ServiceHost açılamadı: MyTransport adlı bağlamaya myBinding adlı bağlama eklenemiyor çünkü bağlamanın zaten myTransport adlı bir taşıması var.</span><span class="sxs-lookup"><span data-stu-id="73063-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="73063-185">Lütfen bağlamada yalnızca bir aktarım olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="73063-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="73063-186">Hataları iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="73063-186">Communicating Faults</span></span>  
 <span data-ttu-id="73063-187">SOAP 1,1 ve SOAP 1,2 hatalar için belirli bir yapı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73063-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="73063-188">İki belirtim arasında bazı farklılıklar vardır ancak genel olarak, hata oluşturmak ve kullanmak için Ileti ve MessageFault türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73063-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="73063-189">![Özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="73063-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="73063-190">SOAP 1,2 hatası (sol) ve SOAP 1,1 hatası (sağ).</span><span class="sxs-lookup"><span data-stu-id="73063-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="73063-191">SOAP 1,1 ' de yalnızca hata öğesinin ad alanı nitelikli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="73063-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="73063-192">SOAP bir hata iletisini yalnızca bir hata öğesi (adı `<env:Fault>`olan bir öğe) `<env:Body>`alt öğesi olan bir ileti olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73063-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="73063-193">Hata öğesinin içeriği, Şekil 1 ' de gösterildiği gibi SOAP 1,1 ve SOAP 1,2 arasında biraz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="73063-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="73063-194">Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıfı bu farklılıkları bir nesne modeliyle normalleştirir:</span><span class="sxs-lookup"><span data-stu-id="73063-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
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
  
 <span data-ttu-id="73063-195">Özelliği ( veya`faultCode` SOAP 1,1 ' de) öğesine karşılık gelir ve hatanın türünü tanımlar. `env:Code` `Code`</span><span class="sxs-lookup"><span data-stu-id="73063-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="73063-196">SOAP 1,2, için `faultCode` izin verilen beş değeri tanımlar (örneğin, gönderen ve alıcı) ve herhangi bir alt kod değeri içerebilen bir `Subcode` öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73063-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="73063-197">(İzin verilen hata kodlarının listesi ve anlamları için [SOAP 1,2 belirtimine](https://go.microsoft.com/fwlink/?LinkId=95176) bakın.) SOAP 1,1 biraz farklı bir mekanizmaya sahiptir: Tamamen yeni olanlar `faultCode` tanımlayarak ya da daha belirgin `faultCodes`bir şekilde (örneğin, Client. Authentication gibi) oluşturmak için nokta gösterimini kullanarak genişletilebilen dört değeri (örneğin, istemci ve sunucu) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73063-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="73063-198">Program hatalarına MessageFault kullandığınızda, FaultCode.Name ve FaultCode. Namespace, soap 1,2 `env:Code` veya soap 1,1 `faultCode`ad ve ad alanı ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="73063-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="73063-199">FaultCode. alt kodu soap 1,2 `env:Subcode` için eşlenir ve SOAP 1,1 için boştur.</span><span class="sxs-lookup"><span data-stu-id="73063-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="73063-200">Bir hatayı programlama yoluyla ayırt etmek için ilginç olması halinde yeni hata alt kodları (veya SOAP 1,1 kullanıyorsanız yeni hata kodları) oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="73063-201">Bu, yeni bir özel durum türü oluşturulmasına benzer.</span><span class="sxs-lookup"><span data-stu-id="73063-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="73063-202">SOAP 1,1 hata kodlarıyla nokta gösterimini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="73063-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="73063-203">( [WS-ı temel profili](https://go.microsoft.com/fwlink/?LinkId=95177) Ayrıca hata kodu nokta gösteriminin kullanımını etkilenmeden.)</span><span class="sxs-lookup"><span data-stu-id="73063-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
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
  
 <span data-ttu-id="73063-204">Özelliği, `env:Reason` bir özel durumun iletisine benzer `faultString` şekilde hata koşulunun okunabilir bir açıklamasını (veya soap 1,1 ' de) karşılık gelir. `Reason`</span><span class="sxs-lookup"><span data-stu-id="73063-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="73063-205">Sınıfında `FaultReason` (ve SOAP `env:Reason/faultString`), Genelleştirme açısından birden çok çevirisi olması için yerleşik destek vardır.</span><span class="sxs-lookup"><span data-stu-id="73063-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
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
  
 <span data-ttu-id="73063-206">Hata ayrıntısı içerikleri, `GetDetail` \<T > ve `GetReaderAtDetailContents`() gibi çeşitli yöntemler kullanılarak MessageFault üzerinde kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="73063-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="73063-207">Hata ayrıntısı, hata hakkında ek ayrıntı taşıyan donuk bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="73063-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="73063-208">Bu, hata ile taşımak istediğiniz rastgele yapılandırılmış bazı ayrıntılar varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="73063-209">Hatalar üretiliyor</span><span class="sxs-lookup"><span data-stu-id="73063-209">Generating Faults</span></span>  
 <span data-ttu-id="73063-210">Bu bölümde, bir kanalda veya kanal tarafından oluşturulan bir ileti özelliğinde algılanan bir hata koşuluna yanıt olarak hata oluşturma işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73063-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="73063-211">Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak hata geri gönderiyor.</span><span class="sxs-lookup"><span data-stu-id="73063-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="73063-212">Bir hata oluştururken, özel kanal hatayı doğrudan göndermemelidir, bunun yerine bir özel durum oluşturması ve katmanın bu özel durumu bir hataya dönüştürüp dönüştürmeyeceğine karar vermesini ve bunun nasıl gönderileceğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="73063-213">Bu dönüştürmeye yardımcı olması için kanal, özel kanal tarafından oluşturulan `FaultConverter` özel durumu uygun hataya dönüştürebileceğiniz bir uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="73063-214">`FaultConverter`şöyle tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="73063-214">`FaultConverter` is defined as:</span></span>  
  
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
  
 <span data-ttu-id="73063-215">Özel hatalar üreten her kanal, öğesini uygulamalıdır `FaultConverter` ve bir `GetProperty<FaultConverter>`çağrısından döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="73063-216">Özel `OnTryCreateFaultMessage` uygulama, özel durumu iç `FaultConverter`kanalın bir hata ya da temsilcisine dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="73063-217">Kanal bir aktarımalıyorsa, özel durumu veya temsilciyi WCF 'de belirtilen varsayılan `FaultConverter` `FaultConverter` ya da bir şekilde dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="73063-218">Varsayılan değer `FaultConverter` , ws-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="73063-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="73063-219">Örnek `OnTryCreateFaultMessage` bir uygulama aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73063-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
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
  
 <span data-ttu-id="73063-220">Bu düzenin bir aksaklığındaki hata koşulları için katmanlar arasında oluşturulan özel durumların, ilgili hata oluşturucusunun doğru hatayı oluşturması için yeterli bilgi içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="73063-221">Özel bir kanal yazarı olarak, bu özel durumlar zaten mevcut değilse farklı hata koşullarına karşılık gelen özel durum türleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73063-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="73063-222">Kanal katmanlarındaki özel durumların, donuk hata verileri yerine hata koşulunu iletmeli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="73063-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="73063-223">Hata kategorileri</span><span class="sxs-lookup"><span data-stu-id="73063-223">Fault Categories</span></span>  
 <span data-ttu-id="73063-224">Genellikle üç hata kategorisi vardır:</span><span class="sxs-lookup"><span data-stu-id="73063-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="73063-225">Tüm yığının tamamında kapsamlı olan hatalar.</span><span class="sxs-lookup"><span data-stu-id="73063-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="73063-226">Bu hatalara kanal yığınındaki herhangi bir katmanda rastlandı, örneğin ınvalidcardınalityaddressingexception.</span><span class="sxs-lookup"><span data-stu-id="73063-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="73063-227">Yığındaki belirli bir katmanın üzerinde herhangi bir yerde, örneğin, bir akışlı işleme veya güvenlik rollerine ilişkin bazı hatalar ile karşılaşabileceği hatalar.</span><span class="sxs-lookup"><span data-stu-id="73063-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="73063-228">Yığındaki tek bir katmana yönlendirilmiş hatalar, örneğin WS-RM sıra numarası hataları gibi hatalar.</span><span class="sxs-lookup"><span data-stu-id="73063-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="73063-229">Kategori 1.</span><span class="sxs-lookup"><span data-stu-id="73063-229">Category 1.</span></span> <span data-ttu-id="73063-230">Hatalar genellikle WS-Addressing ve SOAP hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="73063-231">WCF tarafından `FaultConverter` sunulan temel sınıf, ws-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür, bu nedenle bu özel durumların dönüştürülmesini işlemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="73063-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="73063-232">Kategori 2.</span><span class="sxs-lookup"><span data-stu-id="73063-232">Category 2.</span></span> <span data-ttu-id="73063-233">Bir katman, iletiye o katmana ait ileti bilgisini tamamen tüketmeyen bir özellik eklediğinde hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="73063-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="73063-234">Daha sonra, daha yüksek bir katman ileti özelliğinin ileti bilgisini daha fazla işlemesini istediğinde hatalar algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="73063-235">Bu tür kanallar, daha `GetProperty` önce belirtilen daha yüksek katmanın doğru hatayı geri göndermesini sağlamak için belirtilen ' i uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="73063-236">Bu, TransactionMessageProperty örneğidir.</span><span class="sxs-lookup"><span data-stu-id="73063-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="73063-237">Bu özellik, üstbilgideki tüm verilerin tam olarak doğrulanması gerekmeden iletiye eklenir (Bunun yapılması dağıtılmış işlem Düzenleyicisi 'ne (DTC) başvurmayı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="73063-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="73063-238">Kategori 3.</span><span class="sxs-lookup"><span data-stu-id="73063-238">Category 3.</span></span> <span data-ttu-id="73063-239">Hatalar yalnızca işlemcideki tek bir katman tarafından oluşturulup gönderilir.</span><span class="sxs-lookup"><span data-stu-id="73063-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="73063-240">Bu nedenle, tüm özel durumlar katmanın içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="73063-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="73063-241">Kanallar arasındaki tutarlılığı artırmak ve bakım kolaylığı sağlamak için, özel kanalınız iç hatalar için bile hata iletileri oluşturmak üzere önceden belirtilen kalıbı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="73063-242">Alınan hataları yorumlama</span><span class="sxs-lookup"><span data-stu-id="73063-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="73063-243">Bu bölüm, bir hata iletisi alırken uygun özel durumu oluşturmaya yönelik rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="73063-244">Yığındaki her katmanda bir iletiyi işlemeye yönelik karar ağacı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="73063-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="73063-245">Katman iletinin geçersiz olduğunu düşünür, katmanın ' geçersiz ileti ' işlemesini yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="73063-246">Bu tür bir işlem katmana özeldir, ancak iletiyi bırakmayı, izlemeyi veya bir hataya dönüştürülecek bir özel durum üretilmesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73063-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="73063-247">Örnek olarak güvenli bir şekilde güvenliği sağlanmış olmayan bir iletiyi alma, veya RM 'nin hatalı sıra numarası içeren bir ileti almasına yönelik güvenlik örnekleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="73063-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="73063-248">Aksi takdirde, ileti özellikle katmana uygulanan bir hata iletiyorsa ve ileti katmanın etkileşimi dışında anlamlı değilse, katmanın hata koşulunu işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="73063-249">Bunun bir örneği, RM kanalının üzerindeki katmanlara anlamlı olan ve RM kanalının hata veren ve bekleyen işlemlerden oluşturulamaması gereken bir RM sırası reddedildi hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="73063-250">Aksi takdirde, ileti Istekten () veya Receive () döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="73063-251">Bu, katmanın hatayı tanıdığı durumları içerir, ancak hata yalnızca bir isteğin başarısız olduğunu gösterir ve kanalın hatalı olduğunu göstermez ve bekleyen işlemlerden hata vermez.</span><span class="sxs-lookup"><span data-stu-id="73063-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="73063-252">Bu tür bir durumda kullanılabilirliği artırmak için, katman geçersiz kılarak `GetProperty<FaultConverter>` `OnTryCreateException`hatayı bir özel duruma `FaultConverter` dönüştürebilen türetilmiş bir sınıf uygulamalıdır ve döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="73063-253">Aşağıdaki nesne modeli, iletilerin özel durumlara dönüştürülmesini destekler:</span><span class="sxs-lookup"><span data-stu-id="73063-253">The following object model supports converting messages to exceptions:</span></span>  
  
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
  
 <span data-ttu-id="73063-254">Bir kanal katmanı, `GetProperty<FaultConverter>` hata iletilerinin özel durumlara dönüştürülmesini desteklemek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="73063-255">Bunu yapmak için hata iletisini `OnTryCreateException` geçersiz kılın ve inceleyin.</span><span class="sxs-lookup"><span data-stu-id="73063-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="73063-256">Tanınırsa, dönüştürmeyi yapın, aksi takdirde iç kanaldan dönüştürmeyi isteyin.</span><span class="sxs-lookup"><span data-stu-id="73063-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="73063-257">Aktarım kanalları, varsayılan soap `FaultConverter.GetDefaultFaultConverter` /ws-Addressing FaultConverter 'ı almak için ' a temsilci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="73063-258">Tipik bir uygulama şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="73063-258">A typical implementation looks like this:</span></span>  
  
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
  
 <span data-ttu-id="73063-259">Ayrı kurtarma senaryolarına sahip belirli hata koşulları için, türetilmiş bir sınıfını `ProtocolException`tanımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="73063-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="73063-260">MustUnderstand Işleme</span><span class="sxs-lookup"><span data-stu-id="73063-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="73063-261">SOAP, gerekli bir üstbilginin alıcı tarafından anlaşılmadığından, sinyal için genel bir hata tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73063-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="73063-262">Bu hata, `mustUnderstand` hata olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="73063-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="73063-263">WCF 'de özel kanallar hiçbir şekilde hata `mustUnderstand` oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="73063-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="73063-264">Bunun yerine, WCF iletişim yığınının en üstünde bulunan WCF dağıtıcısı, MustUnderstand = true olarak işaretlenen tüm üstbilgilerin temeldeki yığın tarafından anlaşılmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="73063-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="73063-265">Herhangi bir anlaşıldığında, bu noktada `mustUnderstand` bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73063-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="73063-266">(Kullanıcı bu `mustUnderstand` işlemeyi kapatmayı seçebilir ve uygulamanın tüm ileti üstbilgilerini almasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="73063-267">Bu durumda, uygulamanın işlemeyi gerçekleştirmekten `mustUnderstand` sorumludur.) Oluşturulan hata, MustUnderstand = true olan tüm üst bilgilerin adlarını içeren bir NotUnderstood üst bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="73063-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="73063-268">Protokol kanallarınız MustUnderstand = true ile özel bir üst bilgi gönderirse ve bir `mustUnderstand` hata alırsa, bu hatanın gönderdiği üst bilgi olup olmadığını anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="73063-269">`MessageFault` Sınıfta bu için yararlı olan iki üye vardır:</span><span class="sxs-lookup"><span data-stu-id="73063-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
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
  
 <span data-ttu-id="73063-270">`IsMustUnderstandFault`hatanın `true` bir`mustUnderstand` hata olup olmadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="73063-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="73063-271">`WasHeaderNotUnderstood`Belirtilen `true` ad ve ad alanına sahip üstbilgi hataya NotUnderstood üstbilgisi olarak dahil edilip edilmediğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="73063-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="73063-272">Aksi takdirde, döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="73063-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="73063-273">Bir kanal MustUnderstand = true olarak işaretlenmiş bir üst bilgi yayıyorsa, bu katman özel durum oluşturma API 'si modelini de uygulamalıdır ve bu üstbilginin neden `mustUnderstand` olduğu hataları daha önce açıklandığı gibi daha kullanışlı bir özel duruma dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="73063-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="73063-274">İzleme</span><span class="sxs-lookup"><span data-stu-id="73063-274">Tracing</span></span>  
 <span data-ttu-id="73063-275">.NET Framework, program yürütmesini izlemeye yardımcı olmak için bir mekanizma sağlar ve yalnızca bir hata ayıklayıcı iliştirmek ve kodda adım adım ilerlemek mümkün olmadığı durumlarda, üretim uygulamalarını tanılamaya veya aralıklı sorunları ortaya çıkarmanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="73063-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="73063-276">Bu mekanizmanın çekirdek bileşenleri <xref:System.Diagnostics?displayProperty=nameWithType> ad alanında bulunur ve şunlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="73063-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="73063-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>yazılacak <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>izleme bilgilerinin kaynağı olan, ' <xref:System.Diagnostics.TraceSource> den izlenecek bilgileri alan somut dinleyiciler için soyut bir temel sınıf olan ve dinleyiciye özgü hedefe çıkış yapan bir Özet taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="73063-278">Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> izleme bilgilerini bir XML dosyasına verir.</span><span class="sxs-lookup"><span data-stu-id="73063-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="73063-279"><xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>Son olarak, uygulama kullanıcısının izleme ayrıntı düzeyini denetlemesini ve genellikle yapılandırmada belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="73063-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="73063-280">Çekirdek bileşenlerine ek olarak, WCF izlemelerini görüntülemek ve aramak için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73063-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="73063-281">Araç, WCF tarafından oluşturulan ve kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener>yazılan izleme dosyaları için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="73063-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="73063-282">Aşağıdaki şekilde, izlemeyle ilgili çeşitli bileşenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73063-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="73063-283">![Özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="73063-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="73063-284">Özel bir kanaldan izleme</span><span class="sxs-lookup"><span data-stu-id="73063-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="73063-285">Özel kanallar, çalışan uygulamaya bir hata ayıklayıcı eklemek mümkün olmadığında sorunları tanılamaya yardımcı olmak için izleme iletilerini yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="73063-286">Bu iki üst düzey görevi içerir: İzleme yazmak <xref:System.Diagnostics.TraceSource> için bir ve yöntemlerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="73063-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="73063-287">Bir <xref:System.Diagnostics.TraceSource>örneğini örnekledikten sonra belirttiğiniz dize, kaynağın adı olur.</span><span class="sxs-lookup"><span data-stu-id="73063-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="73063-288">Bu ad, izleme kaynağını yapılandırmak için kullanılır (etkinleştirme/devre dışı bırakma/ayarlama izleme düzeyi).</span><span class="sxs-lookup"><span data-stu-id="73063-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="73063-289">Ayrıca, izleme çıktısı içinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="73063-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="73063-290">Özel kanallar, izleme çıktısının okuyucuların izleme bilgilerinin nereden geldiğini anlamasına yardımcı olmak için benzersiz bir kaynak adı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73063-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="73063-291">İzleme kaynağının adı olarak bilgileri yazan derlemenin adının kullanılması yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="73063-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="73063-292">Örneğin, WCF System. ServiceModel derlemesinden yazılan bilgiler için izleme kaynağı olarak System. ServiceModel kullanır.</span><span class="sxs-lookup"><span data-stu-id="73063-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="73063-293">Bir izleme kaynağına sahip olduktan sonra, izleme girdilerini izleme <xref:System.Diagnostics.TraceSource.TraceData%2A>dinleyicilerine yazmak <xref:System.Diagnostics.TraceSource.TraceInformation%2A> için, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>veya yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="73063-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="73063-294">Yazdığınız her izleme girişi için, olay türünü içinde <xref:System.Diagnostics.TraceEventType>tanımlanan olay türlerinden biri olarak sınıflandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="73063-295">Yapılandırma içindeki bu sınıflandırma ve izleme düzeyi ayarı, izleme girişinin dinleyiciye çıkış olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73063-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="73063-296">Örneğin, `Warning` yapılandırmada izleme düzeyini izin `Warning`verecek şekilde ayarlama ve `Critical` girdileri izlemek `Error` , ancak bilgileri ve ayrıntılı girdileri engeller.</span><span class="sxs-lookup"><span data-stu-id="73063-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="73063-297">Aşağıda, bir izleme kaynağı örneğini oluşturma ve bilgi düzeyinde bir girişi yazma örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="73063-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="73063-298">İzleme çıkış okuyucularınızın çıktının nereden geldiğini anlamalarına yardımcı olmak için özel kanalınıza özgü bir izleme kaynağı adı belirtmeniz kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="73063-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="73063-299">Izleme görüntüleyiciyle tümleştirme</span><span class="sxs-lookup"><span data-stu-id="73063-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="73063-300">Kanalınızın oluşturduğu izlemeler, izleme dinleyicisi olarak kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> [hizmet izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) tarafından okunabilen bir biçimde çıktı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73063-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="73063-301">Bu, kanal geliştiricisi olarak yapmanız gereken bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="73063-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="73063-302">Bunun yerine, uygulamanın yapılandırma dosyasında bu izleme dinleyicisini yapılandırması gereken uygulama kullanıcısı (veya uygulamanın sorun giderme ile ilgili kişi).</span><span class="sxs-lookup"><span data-stu-id="73063-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="73063-303">Örneğin, aşağıdaki yapılandırma hem <xref:System.ServiceModel?displayProperty=nameWithType> ve `Microsoft.Samples.Udp` içindeki izleme bilgilerini adlı `TraceEventsFile.e2e`dosyaya çıktı:</span><span class="sxs-lookup"><span data-stu-id="73063-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="73063-304">Yapılandırılmış verileri izleme</span><span class="sxs-lookup"><span data-stu-id="73063-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="73063-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, izleme <xref:System.Diagnostics.TraceSource.TraceData%2A> girişine dahil edilecek bir veya daha fazla nesne alan bir yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73063-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="73063-306">Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi her bir nesnede çağrılır ve sonuçta elde edilen dize, izleme girişinin bir parçası olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="73063-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="73063-307">Çıktı izlemeleri <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> için kullanırken, veri nesnesi <xref:System.Diagnostics.TraceSource.TraceData%2A>olarak bir <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73063-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="73063-308">Elde edilen izleme girişi, <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>tarafından sağlanan xml 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="73063-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73063-309">XML uygulama verileri içeren örnek bir giriş aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="73063-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="73063-310">WCF izleme Görüntüleyicisi, daha önce gösterilen `TraceRecord` öğenin şemasını anlamıştır ve verileri alt öğelerinden ayıklar ve tablosal biçiminde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73063-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="73063-311">Kanalınızın, SvcTraceViewer. exe kullanıcılarına verileri okumasına yardımcı olmak için yapılandırılmış uygulama verilerini izlerken bu şemayı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73063-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
