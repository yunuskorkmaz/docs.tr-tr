---
title: Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
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
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663703"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="b2afd-102">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="b2afd-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="b2afd-103">Fark edilebilir gecikmelere neden olabilecek bazı işlemlere sahip bir sınıf yazıyorsanız, Olay tabanlı Eşzamanlı [Desen Genel Bakış'ı](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)uygulayarak sınıfa eşzamanlı işlevsellik vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="b2afd-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="b2afd-104">Olay tabanlı Asynchronous Pattern, eşzamanlı özelliklere sahip bir sınıfı paketlemek için standartlaştırılmış bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2afd-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="b2afd-105">Gibi yardımcı sınıflarla <xref:System.ComponentModel.AsyncOperationManager>uygulanırsa, ASP.NET, Konsol uygulamaları ve Windows Forms uygulamaları da dahil olmak üzere herhangi bir uygulama modeli altında sınıfınız doğru şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="b2afd-106">Olay tabanlı Asynchronous Deseni'ni uygulayan bir örnek için [bkz.](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="b2afd-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="b2afd-107">Basit asynchronous işlemleri için <xref:System.ComponentModel.BackgroundWorker> bileşeni uygun bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2afd-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="b2afd-108">Hakkında <xref:System.ComponentModel.BackgroundWorker>daha fazla bilgi için [bkz: Arka Planda Bir İşlem çalıştırın.](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)</span><span class="sxs-lookup"><span data-stu-id="b2afd-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="b2afd-109">Aşağıdaki listede, bu konuda tartışılan Olay tabanlı Eşzamanlı Desen'in özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="b2afd-110">Olay Tabanlı Asynchronous Modelini Uygulama Fırsatları</span><span class="sxs-lookup"><span data-stu-id="b2afd-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="b2afd-111">Adsız Yöntemler adlandırma</span><span class="sxs-lookup"><span data-stu-id="b2afd-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="b2afd-112">İsteğe Bağlı Destek İptali</span><span class="sxs-lookup"><span data-stu-id="b2afd-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="b2afd-113">İsteğe Bağlı Olarak IsBusy Özelliğini Destekleyin</span><span class="sxs-lookup"><span data-stu-id="b2afd-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="b2afd-114">İsteğe Bağlı Olarak İlerleme Raporlaması için Destek Sağlayın</span><span class="sxs-lookup"><span data-stu-id="b2afd-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="b2afd-115">İsteğe Bağlı Olarak Artan Sonuçları Döndürmek Için Destek Sağlayın</span><span class="sxs-lookup"><span data-stu-id="b2afd-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="b2afd-116">Yöntemlerde Çıkış ve Ref Parametrelerinin İşlemi</span><span class="sxs-lookup"><span data-stu-id="b2afd-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="b2afd-117">Olay Tabanlı Asynchronous Modelini Uygulama Fırsatları</span><span class="sxs-lookup"><span data-stu-id="b2afd-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="b2afd-118">Aşağıdaki halde Event tabanlı Eşzamanlı Desen'i uygulamayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="b2afd-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="b2afd-119">Sınıfınızın istemcileri gerekmez <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> ve nesneleri eşzamanlı işlemler için kullanılabilir, yani <xref:System.Threading.WaitHandle.WaitAll%2A> yoklama ve veya <xref:System.Threading.WaitHandle.WaitAny%2A> istemci tarafından inşa edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="b2afd-120">Eşzamanlı işlemlerin tanıdık olay/temsilci modeliyle istemci tarafından yönetilmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b2afd-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="b2afd-121">Herhangi bir işlem eşzamanlı bir uygulama için bir adaydır, ancak uzun gecikmelere maruz kalmak için beklediğiniz olanlar dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="b2afd-122">Özellikle uygun olan, müşterilerin bir metodu aradığı ve tamamlandığında bilgilendirildiği ve başka bir müdahale gerektirmeden bilgilendirildiği işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="b2afd-123">Ayrıca, sürekli çalışan, düzenli olarak ilerleme, artımlı sonuçlar veya durum değişiklikleri istemcileri bildiren işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="b2afd-124">Olay tabanlı Eşzamanlı Deseni'ni ne zaman destekleyeceğine karar verme hakkında daha fazla bilgi için olay tabanlı Eşzamanlı [Deseni'nin ne zaman uygulanacağına karar](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)verme konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="b2afd-125">Adsız Yöntemler adlandırma</span><span class="sxs-lookup"><span data-stu-id="b2afd-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="b2afd-126">Asynchronous muadili sağlamak istediğiniz her senkron yöntem *MethodName* için:</span><span class="sxs-lookup"><span data-stu-id="b2afd-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="b2afd-127">Bir _MethodName_**Async** yöntemi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b2afd-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="b2afd-128">`void` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2afd-128">Returns `void`.</span></span>

- <span data-ttu-id="b2afd-129">*MethodName* yöntemiyle aynı parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="b2afd-130">Birden çok çağrı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b2afd-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="b2afd-131">İsteğe bağlı olarak, MethodName**Async**ile aynı olan, ancak nesne değeri olan `userState`ek bir parametre adı verilen bir _MethodName_ _MethodName_**Async** aşırı yükünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="b2afd-132">Yönteminizin birden çok eşzamanlı çağrılarını yönetmeye hazırsanız bunu yapın, `userState` bu durumda değer yöntemin çağrılarını ayırt etmek için tüm olay işleyicilerine geri teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="b2afd-133">Ayrıca, bunu yalnızca daha sonra alma için kullanıcı durumunu depolamak için bir yer olarak yapmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2afd-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="b2afd-134">Her ayrı _MethodName_**Async** yöntemi imzası için:</span><span class="sxs-lookup"><span data-stu-id="b2afd-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="b2afd-135">Yöntemle aynı sınıfta aşağıdaki olayı tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b2afd-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="b2afd-136">Aşağıdaki temsilciyi <xref:System.ComponentModel.AsyncCompletedEventArgs>tanımlayın ve .</span><span class="sxs-lookup"><span data-stu-id="b2afd-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="b2afd-137">Bunlar büyük olasılıkla sınıfın kendisi dışında, ancak aynı ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="b2afd-138">_MethodName_**CompletedEventArgs** sınıfının, alanlar veri bağlamayı önlediği için, üyelerini alan olarak değil, salt okunur özellikler olarak ortaya çıkardığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2afd-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="b2afd-139">Sonuç üretmeyen <xref:System.ComponentModel.AsyncCompletedEventArgs>yöntemler için türetilmiş sınıfları tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="b2afd-140">Sadece kendi bir <xref:System.ComponentModel.AsyncCompletedEventArgs> örneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="b2afd-141">Temsilci ve <xref:System.ComponentModel.AsyncCompletedEventArgs> türleri yeniden kullanmak mümkün ve uygun olduğunda son derece kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="b2afd-142">Bu durumda, belirli bir temsilci ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlı olmayacaktır, çünkü adlandırma yöntem adı ile tutarlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="b2afd-143">İsteğe Bağlı Destek İptali</span><span class="sxs-lookup"><span data-stu-id="b2afd-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="b2afd-144">Sınıfınız eşzamanlı işlemleri iptal etmeyi destekleyecekse, iptal işlemi aşağıda açıklandığı gibi istemciye açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="b2afd-145">İptal desteğinizi tanımlamadan önce ulaşılması gereken iki karar noktası olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="b2afd-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="b2afd-146">Sınıfınızın, gelecekte beklenen eklemeler de dahil olmak üzere, iptali destekleyen tek bir eşzamanlı işlemi var mı?</span><span class="sxs-lookup"><span data-stu-id="b2afd-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="b2afd-147">İptali destekleyen eşzamanlı işlemler birden çok bekleyen işlemi destekleyebilir mi?</span><span class="sxs-lookup"><span data-stu-id="b2afd-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="b2afd-148">Diğer bir deyişle, _MethodName_**Async** yöntemi bir parametre alır ve herhangi bir `userState` bitirmek için beklemeden önce birden çok çağrıizin verir?</span><span class="sxs-lookup"><span data-stu-id="b2afd-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="b2afd-149">İptal yönteminiziçin imzanın ne olması gerektiğini belirlemek için aşağıdaki tablodaki bu iki sorunun yanıtlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="b2afd-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2afd-150">Visual Basic</span></span>

||<span data-ttu-id="b2afd-151">Birden Fazla Eşzamanlı Operasyon Desteklendi</span><span class="sxs-lookup"><span data-stu-id="b2afd-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="b2afd-152">Aynı Anda Yalnızca Bir İşlem</span><span class="sxs-lookup"><span data-stu-id="b2afd-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="b2afd-153">Tüm sınıfta bir Async İşlemi</span><span class="sxs-lookup"><span data-stu-id="b2afd-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="b2afd-154">Sınıfta Birden Çok Async İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b2afd-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="b2afd-155">C\#</span><span class="sxs-lookup"><span data-stu-id="b2afd-155">C\#</span></span>

||<span data-ttu-id="b2afd-156">Birden Fazla Eşzamanlı Operasyon Desteklendi</span><span class="sxs-lookup"><span data-stu-id="b2afd-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="b2afd-157">Aynı Anda Yalnızca Bir İşlem</span><span class="sxs-lookup"><span data-stu-id="b2afd-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="b2afd-158">Tüm sınıfta bir Async İşlemi</span><span class="sxs-lookup"><span data-stu-id="b2afd-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="b2afd-159">Sınıfta Birden Çok Async İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b2afd-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="b2afd-160">`CancelAsync(object userState)` Yöntemi tanımlarsanız, istemciler, yalnızca tek bir eşzamanlı yöntemin tüm çağrıları arasında değil, nesne üzerinde çağrılan tüm eşzamanlı yöntemler arasında ayırt yeteneğine sahip yapmak için durum değerlerini seçerken dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="b2afd-161">Tek async-operation sürümü _MethodName_**AsyncCancel** adlandırma kararı daha kolay Visual Studio's IntelliSense gibi bir tasarım ortamında yöntemi keşfetmek mümkün dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="b2afd-162">Bu, ilgili üyeleri gruplar ve onları eşzamanlı işlevsellikle ilgisi olmayan diğer üyelerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="b2afd-163">Sonraki sürümlerde ek eşzamanlı işlemler ekleyebileceğini bekliyorsanız, tanımlamak `CancelAsync`daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="b2afd-164">Aynı sınıfta yukarıdaki tablodan birden fazla yöntem tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="b2afd-165">Bu mantıklı olmayacaktır, ya da yöntemlerin çoğalması ile sınıf arayüzü darmadağın olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="b2afd-166">Bu yöntemler genellikle hemen geri döner ve işlem gerçekten iptal edebilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="b2afd-167">_MethodName_**Completed** olayının olay işleyicisinde, _MethodName_**CompletedEventArgs** nesnesi, istemcilerin iptalin gerçekleşip gerçekleşmediğini belirlemek için kullanabileceği bir `Cancelled` alan içerir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="b2afd-168">[Olay tabanlı Asynchronous Desen Uygulamak için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan iptal semantik uymak.</span><span class="sxs-lookup"><span data-stu-id="b2afd-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="b2afd-169">İsteğe Bağlı Olarak IsBusy Özelliğini Destekleyin</span><span class="sxs-lookup"><span data-stu-id="b2afd-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="b2afd-170">Sınıfınız birden çok eşzamanlı çağrıyı desteklemiyorsa, `IsBusy` bir özelliği açığa çıkarmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b2afd-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="b2afd-171">Bu, geliştiricilerin _MethodName_**Async** yönteminden bir özel durum yakalamadan bir _MethodName_**Async** yönteminin çalışıp çalışmadığını belirlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="b2afd-172">Olay tabanlı `IsBusy` [Asynchronous Desen Uygulamak için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan semantik tarafından abide.</span><span class="sxs-lookup"><span data-stu-id="b2afd-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="b2afd-173">İsteğe Bağlı Olarak İlerleme Raporlaması için Destek Sağlayın</span><span class="sxs-lookup"><span data-stu-id="b2afd-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="b2afd-174">Eşzamanlı bir işlemin çalışması sırasında ilerlemeyi bildirmesi sık sık istenir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="b2afd-175">Olay tabanlı Asynchronous Pattern bunu yapmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2afd-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="b2afd-176">İsteğe bağlı olarak, eşzamanlı işlem tarafından yükseltilecek ve uygun iş parçacığıüzerinde çağrılacak bir olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="b2afd-177">Nesne, <xref:System.ComponentModel.ProgressChangedEventArgs> 0 ile 100 arasında olması beklenen bir veyasede değerli ilerleme göstergesi taşır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="b2afd-178">Bu olayı aşağıdaki gibi adlandırın:</span><span class="sxs-lookup"><span data-stu-id="b2afd-178">Name this event as follows:</span></span>

  - <span data-ttu-id="b2afd-179">`ProgressChanged`sınıfın birden çok eşzamanlı işlemi varsa (veya gelecekteki sürümlerde birden çok eşzamanlı işlem içerecek şekilde büyümesi bekleniyorsa);</span><span class="sxs-lookup"><span data-stu-id="b2afd-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="b2afd-180">_MethodName_ProgressSınıfın tek bir eşzamanlı işlemi varsa**değiştirildi.**</span><span class="sxs-lookup"><span data-stu-id="b2afd-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="b2afd-181">Bu adlandırma seçimi, İsteğe Bağlı Destek İptali bölümünde açıklandığı gibi, iptal yöntemi için yapılan larla paraleldir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="b2afd-182">Bu olay temsilci <xref:System.ComponentModel.ProgressChangedEventHandler> imzasını <xref:System.ComponentModel.ProgressChangedEventArgs> ve sınıfı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="b2afd-183">Alternatif olarak, daha fazla etki alanına özgü ilerleme göstergesi sağlanabilirse (örneğin, bir indirme işlemi için bayt okuma <xref:System.ComponentModel.ProgressChangedEventArgs>ve toplam bayt), türetilmiş bir sınıf tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b2afd-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="b2afd-184">Desteklediği eşzamanlı yöntem `ProgressChanged` sayısına bakılmaksızın, sınıf için yalnızca bir veya _MethodName_**ProgressChanged** olayı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="b2afd-185">İstemcilerin, `userState` birden çok eşzamanlı işlemdeki ilerleme güncelleştirmelerini ayırt etmek için _MethodName_**Async** yöntemlerine geçirilen nesneyi kullanması beklenir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="b2afd-186">Birden çok operasyonun ilerlemeyi desteklediği ve her birinin ilerleme için farklı bir gösterge döndürdettiği durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="b2afd-187">Bu durumda, tek `ProgressChanged` bir olay uygun değildir ve birden `ProgressChanged` çok olayı desteklemeyi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2afd-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="b2afd-188">Bu durumda, her _MethodName_**Async** yöntemi için _MethodName_**ProgressChanged'in** bir adlandırma deseni kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="b2afd-189">İlerleme raporlama semantik tarafından olay [tabanlı Asynchronous Desen uygulanması için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan uymak.</span><span class="sxs-lookup"><span data-stu-id="b2afd-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="b2afd-190">İsteğe Bağlı Olarak Artan Sonuçları Döndürmek Için Destek Sağlayın</span><span class="sxs-lookup"><span data-stu-id="b2afd-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="b2afd-191">Bazen bir eşzamanlı işlem tamamlanmadan önce artımlı sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="b2afd-192">Bu senaryoyu desteklemek için kullanılabilecek birkaç seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="b2afd-193">Bazı örnekler izleyin.</span><span class="sxs-lookup"><span data-stu-id="b2afd-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="b2afd-194">Tek İşlemli Sınıf</span><span class="sxs-lookup"><span data-stu-id="b2afd-194">Single-operation Class</span></span>

<span data-ttu-id="b2afd-195">Sınıfınız yalnızca tek bir eşzamanlı işlemi destekliyorsa ve bu işlem artımlı sonuçlar döndürebiliyorsa, o zaman:</span><span class="sxs-lookup"><span data-stu-id="b2afd-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="b2afd-196">Türü artımlı sonuç verilerini taşımak için genişletin ve bu genişletilmiş verilerle bir _MethodName_**ProgressChanged** olayını tanımlayın. <xref:System.ComponentModel.ProgressChangedEventArgs></span><span class="sxs-lookup"><span data-stu-id="b2afd-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="b2afd-197">Rapor etmek için artımlı bir sonuç olduğunda bu _MethodName_**ProgressChanged** olayını yükseltin.</span><span class="sxs-lookup"><span data-stu-id="b2afd-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="b2afd-198">Bu çözüm, _MethodName_**ProgressChanged** olayının yaptığı gibi "tüm işlemler"de artımlı sonuçlar döndürmek için aynı olayla ilgili bir sorun olmadığından, tek eşli çalışma sınıfı için özel olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="b2afd-199">Homojen Artımlı Sonuçlarla Çoklu İşlem Sınıfı</span><span class="sxs-lookup"><span data-stu-id="b2afd-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="b2afd-200">Bu durumda, sınıfınız her biri artımlı sonuçlar döndürebilen birden çok eşzamanlı yöntemi destekler ve bu artımlı sonuçların tümü aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b2afd-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="b2afd-201">Aynı <xref:System.EventArgs> yapı tüm artımlı sonuçlar için çalışacağından, tek işlemli sınıflar için yukarıda açıklanan modeli izleyin.</span><span class="sxs-lookup"><span data-stu-id="b2afd-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="b2afd-202">Birden `ProgressChanged` çok eşzamanlı yöntem için geçerli olduğundan, _Bir YöntemAdı_**İlerlemeDeğiştirildi** olayı yerine bir olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="b2afd-203">Heterojen Artımlı Sonuçlarla Çoklu İşlem Sınıfı</span><span class="sxs-lookup"><span data-stu-id="b2afd-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="b2afd-204">Sınıfınız, her biri farklı türde veri döndüren birden çok eşzamanlı yöntemi destekliyorsa, şunları</span><span class="sxs-lookup"><span data-stu-id="b2afd-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="b2afd-205">Artımlı sonuç raporlamanızı ilerleme raporlamanızdan ayırın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="b2afd-206">Bu yöntemin artımlı sonuç <xref:System.EventArgs> verilerini işlemek için her bir eşzamanlı yöntem için uygun olan ayrı bir _MethodName_**ProgressChanged** olayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="b2afd-207">[Olay tabanlı Asynchronous Deseni'ni Uygulamak için En İyi Uygulamalar'da](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklandığı gibi, bu olay işleyicisini uygun iş parçacığına çağırın.</span><span class="sxs-lookup"><span data-stu-id="b2afd-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="b2afd-208">Yöntemlerde Çıkış ve Ref Parametrelerinin İşlemi</span><span class="sxs-lookup"><span data-stu-id="b2afd-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="b2afd-209">Genel olarak `out` .NET Çerçevesi'nde kullanımı ve `ref` kullanımı önerilse de, mevcut olduklarında uyulması gereken kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b2afd-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="b2afd-210">Senkron bir yöntem verilen *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="b2afd-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="b2afd-211">`out`*MethodName* parametreleri _MethodName_**Async'in**bir parçası olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2afd-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="b2afd-212">Bunun yerine, _MethodName'deki_parametre eşdeğeri ile aynı ada sahip *MethodName* MethodName**CompletedEventArgs'ın** bir parçası olmalıdırlar (daha uygun bir ad yoksa).</span><span class="sxs-lookup"><span data-stu-id="b2afd-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="b2afd-213">`ref`*MethodName* parametreleri _MethodName_**Async'in**bir parçası olarak ve _MethodName'deki_parametre eşdeğeri ile *MethodName* aynı ada sahip MethodName**CompletedEventArgs'ın** bir parçası olarak görünmelidir (daha uygun bir ad yoksa).</span><span class="sxs-lookup"><span data-stu-id="b2afd-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="b2afd-214">Örneğin, verilen:</span><span class="sxs-lookup"><span data-stu-id="b2afd-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="b2afd-215">Asynchronous yönteminiz <xref:System.ComponentModel.AsyncCompletedEventArgs> ve sınıfı şu na benzerdi:</span><span class="sxs-lookup"><span data-stu-id="b2afd-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b2afd-216">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2afd-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="b2afd-217">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="b2afd-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="b2afd-218">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b2afd-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="b2afd-219">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="b2afd-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="b2afd-220">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="b2afd-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="b2afd-221">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2afd-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="b2afd-222">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="b2afd-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
