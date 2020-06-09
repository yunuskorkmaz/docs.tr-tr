---
title: Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
description: .NET ' te olay tabanlı zaman uyumsuz model (EAP) uygulamayı nasıl uygulayacağınızı öğrenin. EAP, zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standart bir yoldur.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 9ffb2e2f426e2d2d97998a89a3e8d306de4f29ca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583667"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="33331-104">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="33331-104">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="33331-105">Fark edilebilir gecikme olabilecek bazı işlemlerle bir sınıf yazıyorsanız, [olay tabanlı zaman uyumsuz düzene genel bakış](event-based-asynchronous-pattern-overview.md)uygulayarak zaman uyumsuz işlevsellik vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="33331-105">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="33331-106">Olay tabanlı zaman uyumsuz model, zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standartlaştırılmış bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="33331-106">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="33331-107">Gibi yardımcı sınıflarla uygulanmışsa <xref:System.ComponentModel.AsyncOperationManager> , sınıfınız ASP.net, konsol uygulamaları ve Windows Forms uygulamalar dahil olmak üzere herhangi bir uygulama modelinde doğru şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="33331-107">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="33331-108">Olay tabanlı zaman uyumsuz model uygulayan bir örnek için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşen uygulama](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="33331-108">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="33331-109">Basit zaman uyumsuz işlemler için <xref:System.ComponentModel.BackgroundWorker> uygun bileşeni bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33331-109">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="33331-110">Hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> bkz. [nasıl yapılır: arka planda işlem çalıştırma](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="33331-110">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="33331-111">Aşağıdaki listede, bu konuda açıklanan olay tabanlı zaman uyumsuz düzenin özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33331-111">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="33331-112">Olay tabanlı zaman uyumsuz model uygulama olanakları</span><span class="sxs-lookup"><span data-stu-id="33331-112">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="33331-113">Zaman uyumsuz yöntemleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="33331-113">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="33331-114">İsteğe bağlı olarak Iptali destekler</span><span class="sxs-lookup"><span data-stu-id="33331-114">Optionally Support Cancellation</span></span>

- <span data-ttu-id="33331-115">İsteğe bağlı olarak IsBusy özelliğini destekler</span><span class="sxs-lookup"><span data-stu-id="33331-115">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="33331-116">İsteğe bağlı olarak Ilerleme raporlaması için destek sağlama</span><span class="sxs-lookup"><span data-stu-id="33331-116">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="33331-117">İsteğe bağlı olarak artımlı sonuçlar döndürme desteği sağlar</span><span class="sxs-lookup"><span data-stu-id="33331-117">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="33331-118">Metotlarda çıkış ve başvuru parametrelerini işleme</span><span class="sxs-lookup"><span data-stu-id="33331-118">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="33331-119">Olay tabanlı zaman uyumsuz model uygulama olanakları</span><span class="sxs-lookup"><span data-stu-id="33331-119">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="33331-120">Şu durumlarda olay tabanlı zaman uyumsuz model uygulamayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="33331-120">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="33331-121">Sınıfınızın istemcilerine <xref:System.Threading.WaitHandle> ve <xref:System.IAsyncResult> zaman uyumsuz işlemler için kullanılabilen nesnelere gerek yoktur, bu, yoklamanın ve <xref:System.Threading.WaitHandle.WaitAll%2A> veya istemcinin oluşturulması gereken anlamına gelir <xref:System.Threading.WaitHandle.WaitAny%2A> .</span><span class="sxs-lookup"><span data-stu-id="33331-121">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="33331-122">Zaman uyumsuz işlemlerin istemci tarafından tanıdık olay/temsilci modeliyle yönetilmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="33331-122">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="33331-123">Herhangi bir işlem, zaman uyumsuz bir uygulama için adaydır, ancak uzun gecikme sürelerine yol açmaya beklediğinizi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="33331-123">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="33331-124">Özellikle uygun olan istemciler, daha fazla müdahale gerekmeden, istemcilerin bir yöntemi çağırması ve tamamlanmasıyla ilgili bilgilendirilir işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="33331-124">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="33331-125">Ayrıca, sürekli olarak çalışan, ilerleme durumunu, artımlı sonuçları veya durum değişikliklerini düzenli olarak bildiren işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="33331-125">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="33331-126">Olay tabanlı zaman uyumsuz deseninin ne zaman desteklenmeyeceğine karar verme hakkında daha fazla bilgi için, bkz. [olay tabanlı zaman uyumsuz düzenin ne zaman uygulanacağını seçme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="33331-126">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="33331-127">Zaman uyumsuz yöntemleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="33331-127">Naming Asynchronous Methods</span></span>

<span data-ttu-id="33331-128">Zaman uyumsuz bir karşılığı sağlamak istediğiniz her zaman uyumlu yöntemin *MethodName* için:</span><span class="sxs-lookup"><span data-stu-id="33331-128">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="33331-129">Şunu içeren bir _MethodName_**zaman uyumsuz** yöntemi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="33331-129">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="33331-130">`void` döndürür.</span><span class="sxs-lookup"><span data-stu-id="33331-130">Returns `void`.</span></span>

- <span data-ttu-id="33331-131">*MethodName* yöntemiyle aynı parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="33331-131">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="33331-132">Birden çok çağırmaları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="33331-132">Accepts multiple invocations.</span></span>

<span data-ttu-id="33331-133">İsteğe bağlı olarak, _MethodName_**Async**ile özdeş, ancak başka bir nesne değerli parametresi adlı bir _MethodName_**zaman uyumsuz** aşırı yüklemesi tanımlayın `userState` .</span><span class="sxs-lookup"><span data-stu-id="33331-133">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="33331-134">Yönteminizin birden çok eş zamanlı çağırma yönetimini yönetmeye hazırlandıysanız bunu yapın. Bu durumda `userState` değer, yöntemin etkinleştirmeleri ayırt edilebilmesi için tüm olay işleyicilerine geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="33331-134">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="33331-135">Bunu, daha sonra alımı için Kullanıcı durumunu depolamak üzere bir yerde yapmayı da tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33331-135">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="33331-136">Her ayrı _MethodName_**zaman uyumsuz** Yöntem imzası için:</span><span class="sxs-lookup"><span data-stu-id="33331-136">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="33331-137">Aşağıdaki olayı, yöntemiyle aynı sınıfta tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="33331-137">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="33331-138">Aşağıdaki temsilciyi ve tanımlayın <xref:System.ComponentModel.AsyncCompletedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="33331-138">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="33331-139">Bunlar muhtemelen sınıfın kendisi dışında, ancak aynı ad alanında tanımlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="33331-139">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - <span data-ttu-id="33331-140">Alan veri bağlamayı engellediği için, _MethodName_**CompletedEventArgs** sınıfının üyelerini salt okuma özellikleri olarak gösterdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="33331-140">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="33331-141"><xref:System.ComponentModel.AsyncCompletedEventArgs>Sonuç üretmeyen yöntemler için herhangi bir türetilmiş sınıf tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="33331-141">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="33331-142">Yalnızca kendi örneğini kullanmanız yeterlidir <xref:System.ComponentModel.AsyncCompletedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="33331-142">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="33331-143">Uygun olduğunda, temsilci ve türleri yeniden kullanmak için uygun olduğunda kusursuz kabul edilebilir <xref:System.ComponentModel.AsyncCompletedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="33331-143">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="33331-144">Bu durumda, belirtilen bir temsilciden ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlanmayacaksa, adlandırma yöntem adı ile tutarlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="33331-144">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="33331-145">İsteğe bağlı olarak Iptali destekler</span><span class="sxs-lookup"><span data-stu-id="33331-145">Optionally Support Cancellation</span></span>

<span data-ttu-id="33331-146">Sınıfınız zaman uyumsuz işlemleri iptal etmeyi destekleyecektir, iptal etme işlemi istemciye aşağıda açıklandığı gibi gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="33331-146">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="33331-147">İptal desteğini tanımlamadan önce erişilmesi gereken iki karar noktası olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="33331-147">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="33331-148">Sınıfınızın daha sonra bu işleme eklemeleri de dahil olmak üzere, yalnızca iptali destekleyen bir zaman uyumsuz işlem var mı?</span><span class="sxs-lookup"><span data-stu-id="33331-148">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="33331-149">İptali destekleyen zaman uyumsuz işlemler birden çok bekleyen işlemi destekliyor mu?</span><span class="sxs-lookup"><span data-stu-id="33331-149">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="33331-150">Yani, _MethodName_**zaman uyumsuz** yöntemi bir `userState` parametre alır ve herhangi birinin bitmesini beklemeden birden çok yüklemeye izin veriyor mu?</span><span class="sxs-lookup"><span data-stu-id="33331-150">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="33331-151">İptal yönteminiz için imzanın ne olduğunu belirlemek için aşağıdaki tabloda bu iki soruya verilen yanıtları kullanın.</span><span class="sxs-lookup"><span data-stu-id="33331-151">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="33331-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33331-152">Visual Basic</span></span>

||<span data-ttu-id="33331-153">Birden çok eşzamanlı Işlem destekleniyor</span><span class="sxs-lookup"><span data-stu-id="33331-153">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="33331-154">Tek seferde yalnızca bir Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-154">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="33331-155">Sınıfın tamamında bir zaman uyumsuz Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-155">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="33331-156">Sınıfta birden çok zaman uyumsuz Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-156">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="33331-157">C\#</span><span class="sxs-lookup"><span data-stu-id="33331-157">C\#</span></span>

||<span data-ttu-id="33331-158">Birden çok eşzamanlı Işlem destekleniyor</span><span class="sxs-lookup"><span data-stu-id="33331-158">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="33331-159">Tek seferde yalnızca bir Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-159">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="33331-160">Sınıfın tamamında bir zaman uyumsuz Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-160">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="33331-161">Sınıfta birden çok zaman uyumsuz Işlem</span><span class="sxs-lookup"><span data-stu-id="33331-161">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="33331-162">`CancelAsync(object userState)`Yöntemini tanımlarsanız istemciler, tek bir zaman uyumsuz yöntemin yalnızca tüm etkinleştirmeleri arasında değil, nesne üzerinde çağrılan tüm zaman uyumsuz yöntemler arasında ayrım yapabilmeleri için durum değerlerini seçerken dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33331-162">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="33331-163">Tek zaman uyumsuz-işlem sürümü _MethodName_**asynccancel** olarak adlandırma kararı, yöntemi Visual Studio 'nun IntelliSense gibi bir tasarım ortamında daha kolay bir şekilde keşfetmenizi temel alır.</span><span class="sxs-lookup"><span data-stu-id="33331-163">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="33331-164">Bu, ilgili üyeleri gruplandırır ve bunları zaman uyumsuz işlevlerle hiçbir şey olmayan diğer üyelerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="33331-164">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="33331-165">Sonraki sürümlere eklenmiş ek zaman uyumsuz işlemler olabileceğini düşünüyorsanız, tanımlanması daha iyidir `CancelAsync` .</span><span class="sxs-lookup"><span data-stu-id="33331-165">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="33331-166">Aynı sınıfta yukarıdaki tabloda birden çok yöntem tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="33331-166">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="33331-167">Bu anlamlı olmayacak veya bir dizi yöntem ile sınıf arabirimini yığacak hale getirir.</span><span class="sxs-lookup"><span data-stu-id="33331-167">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="33331-168">Bu yöntemler genellikle hemen döndürülür ve işlem gerçekten iptal edebilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="33331-168">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="33331-169">_MethodName_**tamamlandı** olayının olay işleyicisinde, _MethodName_**CompletedEventArgs** nesnesi, `Cancelled` istemcilerin İptalin oluşup oluşmadığını belirlemede kullanabileceği bir alan içerir.</span><span class="sxs-lookup"><span data-stu-id="33331-169">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="33331-170">[Olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklanan iptal semantiğine göre ABIDE.</span><span class="sxs-lookup"><span data-stu-id="33331-170">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="33331-171">İsteğe bağlı olarak IsBusy özelliğini destekler</span><span class="sxs-lookup"><span data-stu-id="33331-171">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="33331-172">Sınıfınız birden çok eş zamanlı çağırma desteklemiyorsa, bir özellik kullanıma sunulmasını düşünün `IsBusy` .</span><span class="sxs-lookup"><span data-stu-id="33331-172">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="33331-173">Bu, bir _MethodName_zaman**uyumsuz** yönteminin _MethodName_**zaman** uyumsuz yönteminden bir özel durum yakalanmadan çalışıp çalışmadığını belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="33331-173">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="33331-174">`IsBusy` [Olay tabanlı zaman uyumsuz model uygulamak Için en iyi uygulamalar](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklanan semantiğe göre ABIDE.</span><span class="sxs-lookup"><span data-stu-id="33331-174">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="33331-175">İsteğe bağlı olarak Ilerleme raporlaması için destek sağlama</span><span class="sxs-lookup"><span data-stu-id="33331-175">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="33331-176">Zaman uyumsuz bir işlemin işlem sırasında ilerleme durumunu raporlamak için sık tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="33331-176">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="33331-177">Olay tabanlı zaman uyumsuz model bu işlemi gerçekleştirmek için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="33331-177">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="33331-178">İsteğe bağlı olarak, zaman uyumsuz işlem tarafından oluşturulacak ve uygun iş parçacığında çağrılan bir olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33331-178">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="33331-179"><xref:System.ComponentModel.ProgressChangedEventArgs>Nesne, 0 ile 100 arasında olması beklenen bir tamsayı değerli ilerleme göstergesi taşır.</span><span class="sxs-lookup"><span data-stu-id="33331-179">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="33331-180">Bu olayı aşağıdaki şekilde adlandırın:</span><span class="sxs-lookup"><span data-stu-id="33331-180">Name this event as follows:</span></span>

  - <span data-ttu-id="33331-181">`ProgressChanged`sınıfta birden çok zaman uyumsuz işlem varsa (veya gelecekteki sürümlerde birden çok zaman uyumsuz işlem içermesi için büyüme bekleniyorsa);</span><span class="sxs-lookup"><span data-stu-id="33331-181">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="33331-182">_MethodName_**ProgressChanged & lt** sınıfında tek bir zaman uyumsuz işlem varsa MethodName.</span><span class="sxs-lookup"><span data-stu-id="33331-182">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="33331-183">Bu adlandırma seçeneği, Isteğe bağlı destek Iptali bölümünde açıklandığı gibi, iptal yöntemi için oluşturulan paraleller.</span><span class="sxs-lookup"><span data-stu-id="33331-183">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="33331-184">Bu olay, <xref:System.ComponentModel.ProgressChangedEventHandler> temsilci imzasını ve <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33331-184">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="33331-185">Alternatif olarak, daha fazla alana özgü bir ilerleme göstergesi sağlandıysa (örneğin, okunan bayt sayısı ve bir indirme işlemi için toplam bayt), türetilmiş bir sınıfı tanımlamanız gerekir <xref:System.ComponentModel.ProgressChangedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="33331-185">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="33331-186">`ProgressChanged`Desteklediği zaman uyumsuz yöntemlerin sayısından bağımsız olarak, sınıfı için yalnızca bir veya _MethodName_**ProgressChanged & lt** olayı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="33331-186">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="33331-187">İstemcilerin, `userState` birden çok eşzamanlı işlemde ilerleme güncelleştirmelerini ayırt etmek Için _MethodName_**zaman uyumsuz** yöntemlerine geçirilen nesneyi kullanması beklenir.</span><span class="sxs-lookup"><span data-stu-id="33331-187">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="33331-188">Birden çok işlemin ilerleme durumunu desteklediği ve her biri ilerleme için farklı bir gösterge döndüren durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="33331-188">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="33331-189">Bu durumda, tek bir `ProgressChanged` olay uygun değildir ve birden çok olayı desteklemeyi düşünebilirsiniz `ProgressChanged` .</span><span class="sxs-lookup"><span data-stu-id="33331-189">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="33331-190">Bu durumda, her _MethodName_**zaman uyumsuz** yöntemi için _MethodName_**ProgressChanged & lt** 'in bir adlandırma modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="33331-190">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="33331-191">İlerleme durumuna göre ABIDE [olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="33331-191">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="33331-192">İsteğe bağlı olarak artımlı sonuçlar döndürme desteği sağlar</span><span class="sxs-lookup"><span data-stu-id="33331-192">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="33331-193">Bazen zaman uyumsuz bir işlem, tamamlanmadan önce artımlı sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="33331-193">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="33331-194">Bu senaryoyu desteklemek için kullanılabilecek birçok seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="33331-194">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="33331-195">Bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33331-195">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="33331-196">Tek işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="33331-196">Single-operation Class</span></span>

<span data-ttu-id="33331-197">Sınıfınız yalnızca tek bir zaman uyumsuz işlemi destekliyorsa ve bu işlem artımlı sonuçlar döndürebiliyor, sonra:</span><span class="sxs-lookup"><span data-stu-id="33331-197">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="33331-198"><xref:System.ComponentModel.ProgressChangedEventArgs>Türü artımlı sonuç verilerini taşımak için genişletin ve bu genişletilmiş verilerle bir _MethodName_**ProgressChanged & lt** olayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="33331-198">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="33331-199">Raporlamak için artımlı bir sonuç olduğunda bu _MethodName_**ProgressChanged & lt** olayını yükseltin.</span><span class="sxs-lookup"><span data-stu-id="33331-199">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="33331-200">Bu çözüm, özel olarak tek bir zaman uyumsuz-Operation sınıfına uygulanır çünkü "All Operations" üzerinde artımlı sonuçlar döndürmek için bir sorun yoktur, çünkü _MethodName_**ProgressChanged & lt** olayı.</span><span class="sxs-lookup"><span data-stu-id="33331-200">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="33331-201">Homojen artımlı sonuçları olan birden çok işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="33331-201">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="33331-202">Bu durumda, sınıfınız birden çok zaman uyumsuz yöntemi destekler, her biri artımlı sonuçları döndürmüştür ve bu artımlı sonuçların hepsi aynı türde verilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="33331-202">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="33331-203">Aynı <xref:System.EventArgs> yapı tüm artımlı sonuçlar için çalışacaktır, tek işlem sınıfları için yukarıda açıklanan modeli izleyin.</span><span class="sxs-lookup"><span data-stu-id="33331-203">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="33331-204">`ProgressChanged`Birden çok zaman uyumsuz yöntem için geçerli olduğundan _MethodName_**ProgressChanged & lt** olayı yerine bir olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="33331-204">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="33331-205">Heterojen artımlı sonuçlarla çoklu işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="33331-205">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="33331-206">Sınıfınız, her biri farklı türde veriler döndüren birden çok zaman uyumsuz yöntemi destekliyorsa şunları yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="33331-206">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="33331-207">Artımlı sonuç raporlarınızı ilerleme raporınızdan ayırın.</span><span class="sxs-lookup"><span data-stu-id="33331-207">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="33331-208">_MethodName_**ProgressChanged** <xref:System.EventArgs> Bu yöntemin artımlı sonuç verilerini işlemek için her zaman uyumsuz yöntem Için uygun olan ayrı bir MethodName ProgressChanged & lt olayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="33331-208">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="33331-209">[Olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklandığı gibi ilgili iş parçacığında bu olay işleyicisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="33331-209">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="33331-210">Metotlarda çıkış ve başvuru parametrelerini işleme</span><span class="sxs-lookup"><span data-stu-id="33331-210">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="33331-211">Ve ' nin kullanımı, genel olarak, .NET Framework önerilse de `out` `ref` , mevcut olduklarında izlenecek kurallar aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="33331-211">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="33331-212">Zaman uyumlu bir yöntem *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="33331-212">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="33331-213">`out`*MethodName* parametresi _MethodName_**Async**öğesinin bir parçası olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="33331-213">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="33331-214">Bunun yerine _, MethodName parametresinin bir parçası_olmaları *gerekir (daha* uygun bir ad olmadıkça) parametre eşdeğeri olarak aynı**ada sahip.**</span><span class="sxs-lookup"><span data-stu-id="33331-214">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="33331-215">`ref`*MethodName* parametresi, _MethodName_**zaman uyumsuz**değerinin bir parçası olarak ve *MethodName (daha* uygun bir ad olmadıkça) parametresi ile aynı ada sahip _MethodName_**CompletedEventArgs** öğesinin bir parçası olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="33331-215">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="33331-216">Örneğin, verilen:</span><span class="sxs-lookup"><span data-stu-id="33331-216">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="33331-217">Zaman uyumsuz yönteminiz ve <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="33331-217">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a><span data-ttu-id="33331-218">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33331-218">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="33331-219">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="33331-219">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="33331-220">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="33331-220">How to: Run an Operation in the Background</span></span>](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="33331-221">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="33331-221">How to: Implement a Form That Uses a Background Operation</span></span>](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="33331-222">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="33331-222">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="33331-223">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="33331-223">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="33331-224">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="33331-224">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
