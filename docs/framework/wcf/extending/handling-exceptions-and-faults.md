---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: bca77b575be65513f9a792352e14e3f9bd7b4904
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185622"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="17394-102">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="17394-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="17394-103">Özel durumlar, hizmet veya istemci uygulaması içindeki hataları yerel olarak iletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17394-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="17394-104">Hatalar, diğer taraftan, sunucudan istemciye veya tam tersi gibi hizmet sınırları içinde hataları iletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17394-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="17394-105">Aktarım kanalları hatalara ek olarak, aktarım düzeyi hatalarını iletmek için genellikle aktarıma özgü mekanizmalar kullanır.</span><span class="sxs-lookup"><span data-stu-id="17394-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="17394-106">Örneğin, HTTP aktarım, varolmayan bir uç nokta URL'sini iletmek için 404 gibi durum kodları kullanır (hata yı geri göndermek için bitiş noktası yoktur).</span><span class="sxs-lookup"><span data-stu-id="17394-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="17394-107">Bu belge, özel kanal yazarlarına rehberlik sağlayan üç bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="17394-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="17394-108">İlk bölümde, özel durumların ne zaman ve nasıl tanımlanılı piştileli ve atılaması konusunda rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="17394-109">İkinci bölümde, hata oluşturma ve tüketme konusunda kılavuzluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="17394-110">Üçüncü bölümde, çalışan uygulamalarda sorun gidermede özel kanalınızın kullanıcısına yardımcı olmak için izleme bilgilerinin nasıl sağlandığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17394-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="17394-111">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="17394-111">Exceptions</span></span>  
 <span data-ttu-id="17394-112">Bir özel durum atarken akılda tutulması gereken iki şey vardır: Öncelikle kullanıcıların özel duruma uygun şekilde tepki verebilen doğru kod yazmalarına olanak tanıyan bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="17394-113">İkinci olarak, kullanıcının neyin yanlış gittiğini, hata etkisini ve nasıl düzeltilebildiğini anlaması için yeterli bilgi sağlaması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="17394-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="17394-114">Aşağıdaki bölümler, Windows Communication Foundation (WCF) kanalları için özel durum türleri ve iletileri hakkında rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="17394-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="17394-115">Özel Durumlar için Tasarım Yönergeleri belgesinde .NET'teki özel durumlar hakkında genel kılavuz da vardır.</span><span class="sxs-lookup"><span data-stu-id="17394-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="17394-116">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="17394-116">Exception Types</span></span>  
 <span data-ttu-id="17394-117">Kanallar tarafından atılan tüm özel durumlar, bir <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>veya <xref:System.ServiceModel.CommunicationException>türetilen bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="17394-118">(Örneğin, <xref:System.ObjectDisposedException> yalnızca arama kodunun kanalı kötüye verdiğini belirtmek için de verilebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="17394-119">Bir kanal doğru kullanılırsa, yalnızca verilen özel durumları atmalıdır.) WCF, kanallardan <xref:System.ServiceModel.CommunicationException> türeyen ve kanallar tarafından kullanılmak üzere tasarlanmış yedi özel durum türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="17394-120">Sistemin diğer <xref:System.ServiceModel.CommunicationException>bölümleri tarafından kullanılmak üzere tasarlanmış başka türemiş özel durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="17394-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="17394-121">Bu özel durum türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="17394-121">These exception types are:</span></span>  
  
|<span data-ttu-id="17394-122">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="17394-122">Exception Type</span></span>|<span data-ttu-id="17394-123">Anlamı</span><span class="sxs-lookup"><span data-stu-id="17394-123">Meaning</span></span>|<span data-ttu-id="17394-124">İç Özel Durum İçeriği</span><span class="sxs-lookup"><span data-stu-id="17394-124">Inner Exception Content</span></span>|<span data-ttu-id="17394-125">Kurtarma Stratejisi</span><span class="sxs-lookup"><span data-stu-id="17394-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="17394-126">Dinleme için belirtilen bitiş noktası adresi zaten kullanımdadır.</span><span class="sxs-lookup"><span data-stu-id="17394-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="17394-127">Varsa, bu özel durum neden aktarım hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="17394-128">Örneğin.</span><span class="sxs-lookup"><span data-stu-id="17394-128">For example.</span></span> <span data-ttu-id="17394-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>veya <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="17394-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="17394-130">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="17394-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="17394-131">İşlem, dinleme için belirtilen uç nokta adresine erişim edeğildir.</span><span class="sxs-lookup"><span data-stu-id="17394-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="17394-132">Varsa, bu özel durum neden aktarım hatası hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="17394-133">Örneğin, <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>veya .</span><span class="sxs-lookup"><span data-stu-id="17394-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="17394-134">Farklı kimlik bilgileri ile deneyin.</span><span class="sxs-lookup"><span data-stu-id="17394-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="17394-135"><xref:System.ServiceModel.ICommunicationObject> Kullanılan hata lı durumdadır (daha fazla bilgi için [bkz.](understanding-state-changes.md)</span><span class="sxs-lookup"><span data-stu-id="17394-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="17394-136">Birden çok bekleyen çağrısı olan bir nesne Hatalı duruma geçtiğinde, yalnızca bir arama hatayla ilgili bir özel durum <xref:System.ServiceModel.CommunicationObjectFaultedException>atar ve geri kalan çağrılar da .</span><span class="sxs-lookup"><span data-stu-id="17394-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="17394-137">Bir uygulama bazı özel durumu gözden kbaktığından ve büyük olasılıkla özgün özel durumu yakalayan iş parçacığı dışında bir iş parçacığı üzerinde zaten hatalı bir nesne kullanmaya çalıştığından, bu özel durum genellikle atılır.</span><span class="sxs-lookup"><span data-stu-id="17394-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="17394-138">Varsa iç özel durum hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="17394-139">Yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17394-139">Create a new object.</span></span> <span data-ttu-id="17394-140">İlk etapta <xref:System.ServiceModel.ICommunicationObject> hataya neyin neden olduğuna bağlı olarak, kurtarmak için gereken başka işler olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17394-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="17394-141"><xref:System.ServiceModel.ICommunicationObject> Kullanılan iptal edildi (daha fazla bilgi için [bkz.](understanding-state-changes.md)</span><span class="sxs-lookup"><span data-stu-id="17394-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="17394-142">Benzer <xref:System.ServiceModel.CommunicationObjectFaultedException>, onun özel durum <xref:System.ServiceModel.ICommunicationObject.Abort%2A> uygulama nesne, büyük olasılıkla başka bir iş parçacığı çağırdı gösterir ve nesne artık bu nedenle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17394-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="17394-143">Varsa iç özel durum hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="17394-144">Yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17394-144">Create a new object.</span></span> <span data-ttu-id="17394-145">İlk etapta iptal <xref:System.ServiceModel.ICommunicationObject> in neden ne bağlı olarak, kurtarmak için gerekli başka bir iş olabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17394-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="17394-146">Hedef uzak bitiş noktası dinlemiyor.</span><span class="sxs-lookup"><span data-stu-id="17394-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="17394-147">Bu, bitiş noktası adresinin herhangi bir bölümünün yanlış, çözülemez veya bitiş noktasının aşağı olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="17394-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="17394-148">Örnekler arasında DNS hatası, Queue Manager kullanılamıyor ve hizmet inçalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="17394-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="17394-149">İç özel durum, genellikle temel aktarımdan ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="17394-150">Farklı bir adres deneyin.</span><span class="sxs-lookup"><span data-stu-id="17394-150">Try a different address.</span></span> <span data-ttu-id="17394-151">Alternatif olarak, gönderen bir süre bekleyebilir ve hizmetin düşmesi durumunda yeniden deneyebilir</span><span class="sxs-lookup"><span data-stu-id="17394-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="17394-152">Bitiş noktası ilkesinde açıklandığı gibi iletişim protokolleri uç noktalar arasında eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="17394-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="17394-153">Örneğin, çerçeveleme içerik türü uyuşmazlığı veya maksimum ileti boyutu aşıldı.</span><span class="sxs-lookup"><span data-stu-id="17394-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="17394-154">Varsa, belirli bir iletişim kuralı hatası hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="17394-155">Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedeni MaxReceivedMessageSize'ı aştığında iç özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="17394-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="17394-156">Kurtarma: Gönderenin ve alınan protokol ayarlarının eşleştirilmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="17394-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="17394-157">Bunu yapmanın bir yolu, hizmet bitiş noktasının meta verilerini (ilkesi) yeniden içe aktarma ve kanalı yeniden oluşturmak için oluşturulan bağlamayı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="17394-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="17394-158">Uzak bitiş noktası dinliyor, ancak iletileri işlemeye hazır değil.</span><span class="sxs-lookup"><span data-stu-id="17394-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="17394-159">Varsa, iç Özel Durum SOAP hatası veya taşıma düzeyinde hata ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="17394-160">Kurtarma: Bekleyin ve daha sonra işlemi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="17394-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="17394-161">İşlem zaman açısından tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="17394-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="17394-162">Zaman açığı hakkında ayrıntılı bilgi verebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-162">May provide details about the timeout.</span></span>|<span data-ttu-id="17394-163">Bekleyin ve işlemi daha sonra yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="17394-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="17394-164">Yalnızca bu tür varolan özel durum türlerinin tümünden farklı belirli bir kurtarma stratejisine karşılık geliyorsa yeni bir özel durum türü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="17394-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="17394-165">Yeni bir özel durum türü tanımlarsanız, <xref:System.ServiceModel.CommunicationException> türetilmiş sınıflarından veya bunlardan birini türemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="17394-166">Özel Durum Mesajları</span><span class="sxs-lookup"><span data-stu-id="17394-166">Exception Messages</span></span>  
 <span data-ttu-id="17394-167">Özel durum iletileri, kullanıcının sorunu anlamasına ve çözmesine yardımcı olacak yeterli bilgi sağlaması gerektiğinden, programı değil, kullanıcıyı hedeflenebiliyor.</span><span class="sxs-lookup"><span data-stu-id="17394-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="17394-168">İyi bir özel durum iletisinin üç temel bölümü şunlardır:</span><span class="sxs-lookup"><span data-stu-id="17394-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="17394-169">Olan şeyleri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="17394-169">What happened.</span></span> <span data-ttu-id="17394-170">Kullanıcının deneyimiyle ilgili terimleri kullanarak sorunun net bir açıklamasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="17394-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="17394-171">Örneğin, kötü bir özel durum iletisi "Geçersiz yapılandırma bölümü" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="17394-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="17394-172">Bu, kullanıcıyı hangi yapılandırma bölümünün yanlış olduğunu ve neden yanlış olduğunu merak etmeye bırakır.</span><span class="sxs-lookup"><span data-stu-id="17394-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="17394-173">Geliştirilmiş bir ileti "Geçersiz yapılandırma \<bölümü özel> bağlama" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="17394-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="17394-174">Daha da iyi bir mesaj olacaktır "Bağlama zaten myTransport adlı bir taşıma var, çünkü myBinding adlı bağlama myTransport adlı taşıma ekleyemezsiniz".</span><span class="sxs-lookup"><span data-stu-id="17394-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="17394-175">Bu, kullanıcının uygulamanın yapılandırma dosyasında kolayca tanımlayabileceği terimleri ve adları kullanan çok özel bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="17394-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="17394-176">Ancak, hala birkaç önemli bileşenleri eksik.</span><span class="sxs-lookup"><span data-stu-id="17394-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="17394-177">Hatanın önemi.</span><span class="sxs-lookup"><span data-stu-id="17394-177">The significance of the error.</span></span> <span data-ttu-id="17394-178">İleti hatanın ne anlama geldiğini açıkça belirtmediği sürece, kullanıcı büyük olasılıkla bunun önemli bir hata mı yoksa yoksayoksayılabilir mi diye merak edebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="17394-179">Genel olarak, iletiler hatanın anlamı veya önemi ile yol açmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="17394-180">Önceki örneği iyileştirmek için, ileti "ServiceHost bir yapılandırma hatası nedeniyle Aç'a ulaşamadı: bağlama zaten myTransport adlı bir aktarım olduğundan myBinding adlı bağlama myTransport adlı aktarım ekleyemezsiniz".</span><span class="sxs-lookup"><span data-stu-id="17394-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="17394-181">Kullanıcının sorunu nasıl düzeltmesi gerektiği.</span><span class="sxs-lookup"><span data-stu-id="17394-181">How the user should correct the problem.</span></span> <span data-ttu-id="17394-182">İletinin en önemli bölümü, kullanıcının sorunu düzeltmesi için yardımcı olmaktır.</span><span class="sxs-lookup"><span data-stu-id="17394-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="17394-183">İleti, sorunu gidermek için neyi denetlemesi veya düzeltilmeye ilişkin bazı kılavuzlar veya ipuçları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="17394-184">Örneğin, "ServiceHost bir yapılandırma hatası nedeniyle Aç'a ulaşamadı: Bağlama zaten myTransport adlı bir aktarım olduğundan myBinding adlı bağlama myTransport adlı aktarım ekleyemez.</span><span class="sxs-lookup"><span data-stu-id="17394-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="17394-185">Lütfen bağlamada sadece bir nakil olduğundan emin olun" dedi.</span><span class="sxs-lookup"><span data-stu-id="17394-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="17394-186">İletişim Hataları</span><span class="sxs-lookup"><span data-stu-id="17394-186">Communicating Faults</span></span>  
 <span data-ttu-id="17394-187">SOAP 1.1 ve SOAP 1.2 her ikisi de hatalar için belirli bir yapı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="17394-188">İki belirtim arasında bazı farklar vardır, ancak genel olarak, İleti ve MessageFault türleri hata oluşturmak ve tüketmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17394-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="17394-189">![Özel durumları ve hataları işleme](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultKarşılaştırmac")</span><span class="sxs-lookup"><span data-stu-id="17394-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="17394-190">SOAP 1.2 Arıza (sol) ve SOAP 1.1 Arıza (sağ).</span><span class="sxs-lookup"><span data-stu-id="17394-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="17394-191">SOAP 1.1'de yalnızca Fay öğesinin ad alanı nın nitelikli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17394-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="17394-192">SOAP, hata iletisini yalnızca bir hata öğesi (adı olan `<env:Fault>`bir öğe) `<env:Body>`içeren bir ileti olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="17394-193">Hata elemanının içeriği şekil 1'de gösterildiği gibi SOAP 1.1 ile SOAP 1.2 arasında biraz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="17394-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="17394-194">Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıf bu farklılıkları tek bir nesne modeline normalleştirir:</span><span class="sxs-lookup"><span data-stu-id="17394-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-195">Özellik `Code` `env:Code` (veya `faultCode` SOAP 1.1'de) karşılık gelir ve hatanın türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="17394-196">SOAP 1.2 için `faultCode` izin verilen beş değer (örneğin, Gönderen ve `Subcode` Alıcı) tanımlar ve herhangi bir alt kod değeri içerebilen bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="17394-197">(İzin verilebilen arıza kodları listesi ve anlamları için [SOAP 1.2 belirtimine](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) bakın.) SOAP 1.1'in biraz farklı bir mekanizması `faultCode` vardır: Tamamen yenilerini tanımlayarak veya nokta notasını kullanarak daha spesifik `faultCodes`, örneğin Client.Authentication' ı kullanarak genişletilebilecek dört değeri (örneğin, İstemci ve Sunucu) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-197">(See the [SOAP 1.2 specification](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="17394-198">MessageFault'ı program hataları için kullandığınızda, FaultCode.Name ve FaultCode.Namespace, SOAP 1.2 `env:Code` veya SOAP 1.1'in `faultCode`adı ve ad alanına eşler.</span><span class="sxs-lookup"><span data-stu-id="17394-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="17394-199">Soap 1.2 `env:Subcode` için FaultCode.SubCode haritaları ve SOAP 1.1 için null.</span><span class="sxs-lookup"><span data-stu-id="17394-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="17394-200">Bir hatayı programlı bir şekilde ayırt etmek ilginçse, yeni hata alt kodları (veya SOAP 1.1 kullanıyorsanız yeni hata kodları) oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="17394-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="17394-201">Bu, yeni bir özel durum türü oluşturmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="17394-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="17394-202">SOAP 1.1 hata kodları ile nokta gösterimini kullanmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="17394-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="17394-203">[(WS-I Temel Profili](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) de hata kodu nokta gösterimi kullanımını engeller.)</span><span class="sxs-lookup"><span data-stu-id="17394-203">(The [WS-I Basic Profile](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) also discourages the use of the fault code dot notation.)</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-204">Özellik, `Reason` bir özel durum `faultString` iletisine benzer hata durumunun insan tarafından okunabilir bir açıklamasına (veya SOAP 1.1'de) karşılık gelir. `env:Reason`</span><span class="sxs-lookup"><span data-stu-id="17394-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="17394-205">Sınıf `FaultReason` (ve `env:Reason/faultString`SOAP) küreselleşme yararına birden fazla çeviri olması için yerleşik destek vardır.</span><span class="sxs-lookup"><span data-stu-id="17394-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-206">Hata detay ı `GetDetail` \<içeriği, T> ve `GetReaderAtDetailContents`() dahil olmak üzere çeşitli yöntemler kullanılarak MessageFault'da açıklanır.</span><span class="sxs-lookup"><span data-stu-id="17394-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="17394-207">Hata ayrıntısı, hata yla ilgili ek ayrıntı taşımak için opak bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="17394-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="17394-208">Bu, hatayla birlikte taşımak istediğiniz bazı rasgele yapılandırılmış ayrıntı varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="17394-209">Hata Oluşturma</span><span class="sxs-lookup"><span data-stu-id="17394-209">Generating Faults</span></span>  
 <span data-ttu-id="17394-210">Bu bölümde, bir kanalda veya kanal tarafından oluşturulan bir ileti özelliğinde algılanan bir hata durumuna yanıt olarak hata oluşturma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="17394-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="17394-211">Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak bir hata geri göndermektir.</span><span class="sxs-lookup"><span data-stu-id="17394-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="17394-212">Bir hata oluştururken, özel kanal hatayı doğrudan göndermemeli, bunun yerine, bir özel durum oluşturmalı ve yukarıdaki katmanın bu özel durumu bir hataya dönüştürüp dönüştürmemeye ve nasıl gönderilemeyeceğine karar vermesine izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="17394-213">Bu dönüşüme yardımcı olmak için `FaultConverter` kanal, özel kanal tarafından atılan özel durumu uygun hataya dönüştürebilecek bir uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="17394-214">`FaultConverter`olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="17394-214">`FaultConverter` is defined as:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-215">Özel hatalar oluşturan her kanal, `FaultConverter` bir çağrıdan ''a' `GetProperty<FaultConverter>`yı uygulamalı ve döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="17394-216">Özel `OnTryCreateFaultMessage` uygulama, özel durumu bir hataya dönüştürmeli veya `FaultConverter`iç kanalın.</span><span class="sxs-lookup"><span data-stu-id="17394-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="17394-217">Kanal bir aktarım ise, özel durumu dönüştürmesi veya kodlayıcının `FaultConverter` `FaultConverter` veya WCF'de sağlanan varsayılan değere dönüştürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="17394-218">Varsayılan, `FaultConverter` WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="17394-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="17394-219">Burada bir `OnTryCreateFaultMessage` örnek uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="17394-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-220">Bu desenin bir sonucu, hata gerektiren hata koşulları için katmanlar arasında atılan özel durumlar doğru hata oluşturmak için ilgili hata oluşturucu için yeterli bilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="17394-221">Özel bir kanal yazarı olarak, bu tür özel durumlar zaten yoksa, farklı hata koşullarına karşılık gelen özel durum türleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17394-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="17394-222">Kanal katmanlarında geçiş yapan özel durumlar, opak hata verileri yerine hata koşulunu iletmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17394-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="17394-223">Hata Kategorileri</span><span class="sxs-lookup"><span data-stu-id="17394-223">Fault Categories</span></span>  
 <span data-ttu-id="17394-224">Genellikle üç hata kategorisi vardır:</span><span class="sxs-lookup"><span data-stu-id="17394-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="17394-225">Tüm yığın boyunca yaygın olan hatalar.</span><span class="sxs-lookup"><span data-stu-id="17394-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="17394-226">Bu hatalar kanal yığınındaki herhangi bir katmanda karşılaşılan olabilir, örneğin GeçersizKardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="17394-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="17394-227">Yığında belirli bir katmanın üzerinde herhangi bir yerde karşılaşılabilen hatalar, örneğin akışlı bir hareketle veya güvenlik rolleriyle ilgili bazı hatalar.</span><span class="sxs-lookup"><span data-stu-id="17394-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="17394-228">Yığındaki tek bir katmana yönlendirilen hatalar, örneğin WS-RM sıra numarası hataları gibi hatalar.</span><span class="sxs-lookup"><span data-stu-id="17394-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="17394-229">Kategori 1.</span><span class="sxs-lookup"><span data-stu-id="17394-229">Category 1.</span></span> <span data-ttu-id="17394-230">Hatalar genellikle WS-Adresleme ve SOAP hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="17394-231">WCF `FaultConverter` tarafından sağlanan taban sınıf, WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür, böylece bu özel durumların dönüştürülmesini kendiniz yapmak zorunda kalmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="17394-232">Kategori 2.</span><span class="sxs-lookup"><span data-stu-id="17394-232">Category 2.</span></span> <span data-ttu-id="17394-233">Hatalar, bir katman iletiye bu katmanla ilgili ileti bilgilerini tamamen tüketmeyen bir özellik eklediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="17394-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="17394-234">Daha yüksek bir katman ileti özelliğinden ileti bilgilerini daha fazla işlemesini istediğinde hatalar daha sonra algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="17394-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="17394-235">Bu tür kanallar, `GetProperty` daha yüksek katmanın doğru hatayı geri göndermesini sağlamak için daha önce belirtilenleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="17394-236">Bunun bir örneği TransactionMessageProperty'dir.</span><span class="sxs-lookup"><span data-stu-id="17394-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="17394-237">Bu özellik, üstbilgideki tüm verileri tam olarak doğrulamadan iletiye eklenir (bunu yapmak, dağıtılmış işlem koordinatörüyle (DTC) iletişim kurmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="17394-238">Kategori 3.</span><span class="sxs-lookup"><span data-stu-id="17394-238">Category 3.</span></span> <span data-ttu-id="17394-239">Hatalar yalnızca işlemcide tek bir katman tarafından oluşturulur ve gönderilir.</span><span class="sxs-lookup"><span data-stu-id="17394-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="17394-240">Bu nedenle tüm özel durumlar katman içinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="17394-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="17394-241">Kanallar arasında tutarlılığı artırmak ve bakımı kolaylaştırmak için, özel kanalınız dahili hatalar için bile hata iletileri oluşturmak için önceden belirtilen deseni kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="17394-242">Alınan Hataları yorumlama</span><span class="sxs-lookup"><span data-stu-id="17394-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="17394-243">Bu bölümde, bir hata iletisi alırken uygun özel durum oluşturmak için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="17394-244">Yığındaki her katmanda bir iletiyi işlemek için karar ağacı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="17394-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="17394-245">Katman iletiyi geçersiz kabul ederse, katman 'geçersiz ileti' işlemini yapmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="17394-246">Bu tür işlemler katmana özgüdür, ancak iletiyi bırakmayı, izlemeyi veya hataya dönüştürülen bir özel durum atmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="17394-247">Örnekler arasında güvenliğin düzgün güvenli olmayan bir ileti alması veya RM'nin hatalı sıra numarası olan bir ileti alması verilebilir.</span><span class="sxs-lookup"><span data-stu-id="17394-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="17394-248">Aksi takdirde, ileti katmana özel olarak uygulanan bir hata iletisiyse ve ileti katmanın etkileşimi dışında anlamlı değilse, katman hata koşulunu işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="17394-249">Bunun bir örneği, RM kanalının üzerindeki katmanlar için anlamsız olan ve RM kanalının hatalı olması ve bekleyen işlemlerden atılması anlamına gelen bir RM Dizisi Reddedilen hatadır.</span><span class="sxs-lookup"><span data-stu-id="17394-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="17394-250">Aksi takdirde, ileti İstek() veya Receive() adresinden döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="17394-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="17394-251">Bu, katmanın hatayı tanıdığı durumları içerir, ancak hata yalnızca bir isteğin başarısız olduğunu gösterir ve kanalı niçin hatalı olduğu ve bekleyen işlemlerden atıldığı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="17394-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="17394-252">Böyle bir durumda kullanılabilirliği artırmak için, `GetProperty<FaultConverter>` katman `FaultConverter` uygulamalı ve geçersiz kılma tarafından bir `OnTryCreateException`özel duruma hata dönüştürebilir türemiş bir sınıf döndürün.</span><span class="sxs-lookup"><span data-stu-id="17394-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="17394-253">Aşağıdaki nesne modeli iletileri özel durumlara dönüştürmeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="17394-253">The following object model supports converting messages to exceptions:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-254">Bir kanal katmanı, hata iletilerinin özel durumlara dönüştürülmesini desteklemek için uygulayabilir. `GetProperty<FaultConverter>`</span><span class="sxs-lookup"><span data-stu-id="17394-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="17394-255">Bunu yapmak için `OnTryCreateException` hata iletisini geçersiz kılın ve denetleyin.</span><span class="sxs-lookup"><span data-stu-id="17394-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="17394-256">Tanındıysa, dönüştürmeyi yapın, aksi takdirde iç kanaldan dönüştürmesini isteyin.</span><span class="sxs-lookup"><span data-stu-id="17394-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="17394-257">Aktarım kanalları varsayılan `FaultConverter.GetDefaultFaultConverter` SOAP/WS Adresleme FaultConverter almak için temsilci gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="17394-258">Tipik bir uygulama şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="17394-258">A typical implementation looks like this:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="17394-259">Farklı kurtarma senaryoları olan belirli hata koşulları için, `ProtocolException`türetilmiş bir sınıf tanımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="17394-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="17394-260">MustUnderstand İşleme</span><span class="sxs-lookup"><span data-stu-id="17394-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="17394-261">SOAP, gerekli bir üstbilginin alıcı tarafından anlaşılmadığını bildirmek için genel bir hata tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17394-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="17394-262">Bu hata `mustUnderstand` hata olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="17394-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="17394-263">WCF'de özel kanallar `mustUnderstand` hiçbir zaman hata oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="17394-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="17394-264">Bunun yerine, WCF iletişim yığınının üst kısmında bulunan WCF Dispatcher, MustUnderstand=true olarak işaretlenmiş tüm üstbilginin temel yığın tarafından anlaşıldığını denetler.</span><span class="sxs-lookup"><span data-stu-id="17394-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="17394-265">Herhangi bir anlaşılamadı, `mustUnderstand` bir hata bu noktada oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="17394-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="17394-266">(Kullanıcı bu `mustUnderstand` işlemi kapatmayı seçebilir ve uygulamanın tüm ileti üstbilgilerini almasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="17394-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="17394-267">Bu durumda uygulama işleme nin `mustUnderstand` uygulanmasından sorumludur.) Oluşturulan hata, MustUnderstand=true olan ve anlaşılamayan tüm üstbilginin adlarını içeren bir NotUnderstood üstbilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="17394-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="17394-268">Protokol kanalınız MustUnderstand=true ile özel bir üstbilgi gönderir ve bir `mustUnderstand` hata alırsa, bu hatanın gönderdiği üstbilgiden kaynaklanıp kaynaklanmadığını belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="17394-269">`MessageFault` Sınıfta bunun için yararlı olan iki üye vardır:</span><span class="sxs-lookup"><span data-stu-id="17394-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="17394-270">`IsMustUnderstandFault`hata `true` bir `mustUnderstand` hata ise döndürür.</span><span class="sxs-lookup"><span data-stu-id="17394-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="17394-271">`WasHeaderNotUnderstood`belirtilen `true` ad ve ad alanına sahip üstbilgi hataya NotUnderstood üstbilgi olarak dahil edilirse döndürür.</span><span class="sxs-lookup"><span data-stu-id="17394-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="17394-272">Aksi takdirde, `false`döner.</span><span class="sxs-lookup"><span data-stu-id="17394-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="17394-273">Bir kanal MustUnderstand = true olarak işaretlenmiş bir üstbilgi yayarsa, bu katma da `mustUnderstand` Özel Durum Oluşturma API deseni uygulamalı ve bu üstbilginin neden olduğu hataları daha önce açıklandığı gibi daha kullanışlı bir özel durum dönüştürmeli.</span><span class="sxs-lookup"><span data-stu-id="17394-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="17394-274">İzleme</span><span class="sxs-lookup"><span data-stu-id="17394-274">Tracing</span></span>  
 <span data-ttu-id="17394-275">.NET Framework, üretim uygulamalarını veya yalnızca hata ayıklayıcı eklemenin ve kod üzerinden adım atmanın mümkün olmadığı aralıklı sorunların tanılanmasına yardımcı olmak için program yürütmesini izlemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="17394-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="17394-276">Bu mekanizmanın temel bileşenleri <xref:System.Diagnostics?displayProperty=nameWithType> ad alanındadır ve aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="17394-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="17394-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, hangi iz bilgi nin kaynağı <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>yazılması, hangi somut dinleyiciler için soyut bir taban sınıf <xref:System.Diagnostics.TraceSource> olan bu bilgi takip almak ve bir dinleyici özgü hedefe çıktı.</span><span class="sxs-lookup"><span data-stu-id="17394-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="17394-278">Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> bir XML dosyasına izleme bilgileri çıktıları.</span><span class="sxs-lookup"><span data-stu-id="17394-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="17394-279">Son <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>olarak, uygulama kullanıcı izleme verbosity kontrol sağlar ve genellikle yapılandırmada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="17394-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="17394-280">Temel bileşenlere ek olarak, WCF izlerini görüntülemek ve aramak için [Service Trace Viewer Aracı'nı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17394-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="17394-281">Araç, WCF tarafından oluşturulan ve kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener>yazılan izleme dosyaları için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="17394-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="17394-282">Aşağıdaki şekil, izleme ile ilgili çeşitli bileşenleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="17394-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="17394-283">![Özel durumları ve hataları işleme](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="17394-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="17394-284">Özel Kanaldan İzleme</span><span class="sxs-lookup"><span data-stu-id="17394-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="17394-285">Özel kanallar, çalışan uygulamaya hata ayıklama eklemenin mümkün olmadığında sorunları tanılamada yardımcı olmak için izleme iletileri yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="17394-286">Bu iki üst düzey görev içerir: <xref:System.Diagnostics.TraceSource> A'yı anında bulma ve izleme yazmak için yöntemlerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="17394-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="17394-287">Bir <xref:System.Diagnostics.TraceSource>, belirttiğiniz dize, o kaynağın adı olur.</span><span class="sxs-lookup"><span data-stu-id="17394-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="17394-288">Bu ad, izleme kaynağını yapılandırmak (etkinleştirme/devre dışı bırakma/ayarlama düzeyi) için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17394-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="17394-289">Ayrıca izleme çıktısının kendisinde de görünür.</span><span class="sxs-lookup"><span data-stu-id="17394-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="17394-290">Özel kanallar, izleme çıktısını okuyucuların izleme bilgilerinin nereden geldiğini anlamalarına yardımcı olmak için benzersiz bir kaynak adı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="17394-291">İzleme kaynağının adı olarak bilgileri yazan derlemenin adını kullanmak yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="17394-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="17394-292">Örneğin, WCF System.ServiceModel assemblyinden yazılan bilgiler için izleme kaynağı olarak System.ServiceModel kullanır.</span><span class="sxs-lookup"><span data-stu-id="17394-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="17394-293">Bir izleme kaynağına sahip olduktan <xref:System.Diagnostics.TraceSource.TraceData%2A> <xref:System.Diagnostics.TraceSource.TraceEvent%2A>sonra, <xref:System.Diagnostics.TraceSource.TraceInformation%2A> izleme dinleyicilerine izleme girişleri yazmak için onun , veya yöntemleri çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="17394-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="17394-294">Yazdığınız her izleme girişi için, olay türünü <xref:System.Diagnostics.TraceEventType>'de tanımlanan olay türlerinden biri olarak sınıflandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="17394-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="17394-295">Bu sınıflandırma ve yapılandırmadaki izleme düzeyi ayarı, izleme girişinin dinleyiciye çıktı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="17394-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="17394-296">Örneğin, yapılandırmada izleme düzeyini, `Warning` `Warning`girişlerin yazılmasına `Error` izin verir ve izleme yi engeller, ancak Bilgi ve `Critical` Verbose girişlerini engeller.</span><span class="sxs-lookup"><span data-stu-id="17394-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="17394-297">Aşağıda, izleme kaynağının anlık olarak yazılması ve Bilgi düzeyinde bir girişin yazılmasına bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="17394-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="17394-298">Çıktı okuyucularının çıktının nereden geldiğini anlamasına yardımcı olmak için özel kanalınıza özgü bir izleme kaynağı adı belirtmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="17394-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="17394-299">İz Görüntüleyici ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="17394-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="17394-300">Kanalınız tarafından oluşturulan izleme ler, izleme dinleyicisi olarak kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Service Trace Viewer Tool [(SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tarafından okunabilir bir biçimde çıkarılabilir.</span><span class="sxs-lookup"><span data-stu-id="17394-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="17394-301">Bu, kanal geliştiricisi olarak yapmanız gereken bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="17394-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="17394-302">Bunun yerine, bu izleme dinleyicisini uygulamanın yapılandırma dosyasında yapılandırması gereken uygulama kullanıcısı (veya uygulamayı sorun gideren kişidir).</span><span class="sxs-lookup"><span data-stu-id="17394-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="17394-303">Örneğin, aşağıdaki yapılandırma çıktıları hem <xref:System.ServiceModel?displayProperty=nameWithType> de `Microsoft.Samples.Udp` adlı `TraceEventsFile.e2e`dosyaya aşağıdaki bilgileri izleme:</span><span class="sxs-lookup"><span data-stu-id="17394-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="17394-304">Yapılandırılmış Verilerin İzlemi</span><span class="sxs-lookup"><span data-stu-id="17394-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="17394-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>izleme <xref:System.Diagnostics.TraceSource.TraceData%2A> girişine dahil edilecek bir veya daha fazla nesneyi alan bir yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="17394-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="17394-306">Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntem her nesneye çağrılır ve elde edilen dize izleme girişinin bir parçası olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="17394-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="17394-307">Çıktı <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> izlemelerini kullanırken, veri <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> nesnesi olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>bir 'e geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17394-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="17394-308">Elde edilen izleme girişi, <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>xml tarafından sağlanan içerir.</span><span class="sxs-lookup"><span data-stu-id="17394-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17394-309">Aşağıda, XML uygulama verilerine sahip bir örnek giriş verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="17394-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="17394-310">WCF iz görüntüleyici, daha önce `TraceRecord` gösterilen öğenin şemasını anlar ve alt öğelerinden verileri ayıklar ve bir tabular biçiminde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="17394-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="17394-311">Kanalınız, Yapılandırılmış uygulama verilerini takip ederken Svctraceviewer.exe kullanıcılarının verileri okumasına yardımcı olmak için bu şemayı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17394-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
