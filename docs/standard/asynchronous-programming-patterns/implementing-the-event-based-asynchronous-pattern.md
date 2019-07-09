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
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663703"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="9dfb6-102">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="9dfb6-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="9dfb6-103">Bir sınıf belirgin gecikmeler kaynaklanabilecek bazı işlemleri yazıyorsanız uygulayarak zaman uyumsuz işlevleri vererek göz önünde bulundurun [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="9dfb6-104">Olay tabanlı zaman uyumsuz desen, zaman uyumsuz özellikler sahip bir sınıf paketlemek için standartlaştırılmış bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="9dfb6-105">Yardımcı sınıfları ile uygulanması durumunda ister <xref:System.ComponentModel.AsyncOperationManager>, sınıfınıza ASP.NET dahil olmak üzere doğru şekilde tüm uygulama modeli altında çalışması konsol uygulamaları ve Windows Forms uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="9dfb6-106">Olay tabanlı zaman uyumsuz desen uygulayan bir örnek için bkz: [nasıl yapılır: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="9dfb6-107">Zaman uyumsuz işlemleri için basit, ilginizi çekebilecek <xref:System.ComponentModel.BackgroundWorker> uygun bileşeni.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="9dfb6-108">Hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker>, bkz: [nasıl yapılır: Arka planda işlem çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="9dfb6-109">Aşağıdaki listede, olay tabanlı zaman uyumsuz bu konuda tartışılan düzen özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="9dfb6-110">Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar</span><span class="sxs-lookup"><span data-stu-id="9dfb6-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="9dfb6-111">Zaman uyumsuz yöntemler Adlandırma</span><span class="sxs-lookup"><span data-stu-id="9dfb6-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="9dfb6-112">İsteğe bağlı olarak, iptal desteği</span><span class="sxs-lookup"><span data-stu-id="9dfb6-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="9dfb6-113">İsteğe bağlı olarak IsBusy özelliği desteği</span><span class="sxs-lookup"><span data-stu-id="9dfb6-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="9dfb6-114">İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="9dfb6-115">İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="9dfb6-116">Yöntemlerde Ref parametreleri ve çıkış işleme</span><span class="sxs-lookup"><span data-stu-id="9dfb6-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="9dfb6-117">Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar</span><span class="sxs-lookup"><span data-stu-id="9dfb6-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="9dfb6-118">Olay tabanlı zaman uyumsuz deseni uygulama göz önünde bulundurun olduğunda:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="9dfb6-119">Sınıfınızın istemciler gerekmez <xref:System.Threading.WaitHandle> ve <xref:System.IAsyncResult> anlamına gelir, yoklama zaman uyumsuz işlemler için kullanılabilir nesneleri ve <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> istemci tarafından oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="9dfb6-120">Tanıdık olay temsilci modeli ile istemci tarafından yönetilmek üzere zaman uyumsuz işlemler kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="9dfb6-121">Herhangi bir işlem zaman uyumsuz bir uygulama için bir aday olsa da bu uzun gecikmeleri uygulanmaya beklediğiniz düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="9dfb6-122">İstemciler bir yöntemi çağırabilir ve, tamamlanması gereken başka müdahale ile bildirilir operations özellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="9dfb6-123">Ayrıca, düzenli aralıklarla istemcileri ilerleme durumunu, artımlı sonuçları veya durum değişiklikleri bildiren sürekli olarak çalışan işlemleri uygundur.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="9dfb6-124">Olay tabanlı zaman uyumsuz deseni destekleyen ne zaman karar vermeyle ilgili daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz desen uygulamak için verirken](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="9dfb6-125">Zaman uyumsuz yöntemler Adlandırma</span><span class="sxs-lookup"><span data-stu-id="9dfb6-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="9dfb6-126">Her bir zaman uyumlu yöntemin *MethodName* zaman uyumsuz bir karşılığı sağlamak istediğiniz:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="9dfb6-127">Tanımlayan bir _MethodName_**zaman uyumsuz** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="9dfb6-128">Döndürür `void`.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-128">Returns `void`.</span></span>

- <span data-ttu-id="9dfb6-129">Aynı parametreleri alan *MethodName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="9dfb6-130">Birden çok çağrılarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="9dfb6-131">İsteğe bağlı olarak tanımlayan bir _MethodName_**zaman uyumsuz** aşırı yükleme, aynı _MethodName_**zaman uyumsuz**, ancak bir ek nesne değerli adlı parametreyi `userState`.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="9dfb6-132">Bu durumda birden çok eş zamanlı, yöntem çağrılarını yönetmek için hazır olmanız durumunda bunu `userState` değeri, yöntem çağrılarını ayırt etmek için geri tüm olay işleyicilerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="9dfb6-133">Bunu yapmak de tercih edebilirsiniz sonraki alma için kullanıcı durumunu depolamak için yalnızca bir yer olarak.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="9dfb6-134">Her ayrı için _MethodName_**zaman uyumsuz** yöntem imzası:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="9dfb6-135">Aşağıdaki olay yöntemi olarak aynı sınıftaki tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="9dfb6-136">Aşağıdaki temsilciyi tanımlamasına ve <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="9dfb6-137">Bunlar büyük olasılıkla sınıfın kendisi dışında ancak aynı ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="9dfb6-138">Emin _MethodName_**CompletedEventArgs** sınıfı gösterir üyelerine salt okunur özellikler ve alanları değil alanları veri bağlamayı Önle gibi.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="9dfb6-139">Tüm tanımlamazsanız <xref:System.ComponentModel.AsyncCompletedEventArgs>-türetilmiş sınıflar için sonuçlar üretmez yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="9dfb6-140">Yalnızca bir örneğini kullanması <xref:System.ComponentModel.AsyncCompletedEventArgs> kendisi.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="9dfb6-141">Bunun uygulanabilir ve temsilci yeniden kullanmak uygun edilebilir, ve <xref:System.ComponentModel.AsyncCompletedEventArgs> türleri.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="9dfb6-142">Bu durumda, adlandırma beri belirli bir temsilci yöntemi adıyla olarak tutarlı olmayacaktır ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlı olmaz.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="9dfb6-143">İsteğe bağlı olarak, iptal desteği</span><span class="sxs-lookup"><span data-stu-id="9dfb6-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="9dfb6-144">Zaman uyumsuz işlemleri iptal ediliyor sınıfınıza destekleyecekse, iptal aşağıda açıklandığı gibi istemciye açılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="9dfb6-145">İptal desteği tanımlamadan önce erişilmesi gereken iki karar noktaları olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="9dfb6-146">Gelecekteki beklenen eklemeler, dahil olmak üzere, kendi sınıfınızı iptali destekler yalnızca tek bir zaman uyumsuz işlem var mı?</span><span class="sxs-lookup"><span data-stu-id="9dfb6-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="9dfb6-147">İptal etme desteği birden fazla bekleyen işlemler zaman uyumsuz işlemleri yapabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="9dfb6-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="9dfb6-148">Diğer bir deyişle, mu _MethodName_**zaman uyumsuz** yöntemi Al bir `userState` parametresi ve herhangi tamamlanmasını beklemeden birden çok çağrılarına izin vermediğinden?</span><span class="sxs-lookup"><span data-stu-id="9dfb6-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="9dfb6-149">Bu iki soruların yanıtlarını aşağıdaki tabloda, iptal için imzası olması gerektiğini belirlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="9dfb6-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9dfb6-150">Visual Basic</span></span>

||<span data-ttu-id="9dfb6-151">Desteklenen birden çok eşzamanlı operasyonlar</span><span class="sxs-lookup"><span data-stu-id="9dfb6-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="9dfb6-152">Aynı anda yalnızca tek bir işlem</span><span class="sxs-lookup"><span data-stu-id="9dfb6-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="9dfb6-153">Sınıfın tamamı tek bir zaman uyumsuz işlemle</span><span class="sxs-lookup"><span data-stu-id="9dfb6-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="9dfb6-154">Sınıfta birden çok zaman uyumsuz işlemler</span><span class="sxs-lookup"><span data-stu-id="9dfb6-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="9dfb6-155">C\#</span><span class="sxs-lookup"><span data-stu-id="9dfb6-155">C\#</span></span>

||<span data-ttu-id="9dfb6-156">Desteklenen birden çok eşzamanlı operasyonlar</span><span class="sxs-lookup"><span data-stu-id="9dfb6-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="9dfb6-157">Aynı anda yalnızca tek bir işlem</span><span class="sxs-lookup"><span data-stu-id="9dfb6-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="9dfb6-158">Sınıfın tamamı tek bir zaman uyumsuz işlemle</span><span class="sxs-lookup"><span data-stu-id="9dfb6-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="9dfb6-159">Sınıfta birden çok zaman uyumsuz işlemler</span><span class="sxs-lookup"><span data-stu-id="9dfb6-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="9dfb6-160">Tanımlarsanız `CancelAsync(object userState)` yöntemi, istemcilerin bunları özellikli olan nesne üzerinde çağrılan tüm zaman uyumsuz yöntemler arasında ayrım yapmak için durum değerleri seçerken dikkatli ve yalnızca tek bir zaman uyumsuz yöntemin tüm çağrıları arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="9dfb6-161">Tek zaman uyumsuz işlem sürüm adı kararı _MethodName_**AsyncCancel** yöntemi Visual Studio IntelliSense gibi bir tasarım ortamında daha kolay bulmak için temel alır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="9dfb6-162">Bu, ilgili üyeleri grupları ve bunları zaman uyumsuz işlevleri ile ilgisi olan diğer üyelerinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="9dfb6-163">Olabileceğini ek bekliyorsanız zaman uyumsuz işlemler eklenir sonraki sürümlerinde, onu tanımlamak daha iyi `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="9dfb6-164">Yukarıdaki tabloda birden fazla yöntemleri aynı sınıfta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="9dfb6-165">Anlam ifade etmez veya sınıf arabirimi yöntemleri bir yaygınlaşmasının ile dağıtmayı.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="9dfb6-166">Bu yöntemler genellikle hemen döndürür ve işlem olabilir ya da gerçekte iptal.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="9dfb6-167">İçin olay işleyicisinde _MethodName_**tamamlandı** olay _MethodName_**CompletedEventArgs** nesne içeren bir `Cancelled` alanı istemciler iptal oluşup oluşmadığını belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="9dfb6-168">Tarafından açıklanan iptal semantiği uymayı [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="9dfb6-169">İsteğe bağlı olarak IsBusy özelliği desteği</span><span class="sxs-lookup"><span data-stu-id="9dfb6-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="9dfb6-170">Sınıfınız birden çok eş zamanlı çağrılarını desteklemiyor ise kullanıma sunmak isteyebilirsiniz bir `IsBusy` özelliği.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="9dfb6-171">Bu hizmet sayesinde geliştiriciler belirlemek için olup olmadığını bir _MethodName_**zaman uyumsuz** yöntemi, bir özel durum yakalama olmadan çalışıyor _MethodName_**zaman uyumsuz**  yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="9dfb6-172">Tarafından uymayı `IsBusy` semantiği açıklanan [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="9dfb6-173">İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="9dfb6-174">Bu, işlemi sırasında ilerlemeyi rapor için zaman uyumsuz bir işlem için sık istenen bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="9dfb6-175">Olay tabanlı zaman uyumsuz desen, bunu yapmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="9dfb6-176">İsteğe bağlı olarak zaman uyumsuz işlemi tarafından oluşturuldu ve uygun iş parçacığında çağrılan bir olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="9dfb6-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Nesne 0 ile 100 arasında olması beklenir bir tamsayı değerli İlerleme göstergesi taşır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="9dfb6-178">Bu olay şu şekilde adlandırın:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-178">Name this event as follows:</span></span>

  - <span data-ttu-id="9dfb6-179">`ProgressChanged` sınıfı birden çok zaman uyumsuz işlemleri vardır (veya gelecek sürümlerde birden çok zaman uyumsuz işlemler içerecek şekilde ulaşması için bekleniyor);</span><span class="sxs-lookup"><span data-stu-id="9dfb6-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="9dfb6-180">_MethodName_**ProgressChanged** sınıfın tek bir zaman uyumsuz işlem varsa.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="9dfb6-181">Bu adlandırma seçimi iptal yöntem için yapılan isteğe bağlı olarak destek iptal bölümünde açıklandığı gibi paraleldir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="9dfb6-182">Bu olay kullanması gereken <xref:System.ComponentModel.ProgressChangedEventHandler> temsilci imzası ve <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="9dfb6-183">Bir etki alanına özgü daha İlerleme göstergesi (için örnek, okunan bayt ve bir yükleme işlemi için toplam bayt) sağlanabilir, alternatif olarak, ardından, türetilmiş bir sınıf, tanımlamalıdır <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="9dfb6-184">Yalnızca bir tane olduğunu unutmayın `ProgressChanged` veya _MethodName_**ProgressChanged** destekliyorsa, zaman uyumsuz yöntemler sayısından bağımsız olarak, sınıf için olay.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="9dfb6-185">İstemciler, kullanılacak beklenir `userState` geçirilen nesne _MethodName_**zaman uyumsuz** birden fazla eşzamanlı işlem üzerinde devam eden güncelleştirmelerin arasında ayrım yapmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="9dfb6-186">Devam eden birden çok işlem desteği ve her ilerleme durumu için farklı bir göstergesini döndürür durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="9dfb6-187">Bu durumda, tek bir `ProgressChanged` olay uygun değilse ve birden fazla destekleyici düşünebilirsiniz `ProgressChanged` olayları.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="9dfb6-188">Bu durumda, bir adlandırma desenini kullanın _MethodName_**ProgressChanged** her _MethodName_**zaman uyumsuz** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="9dfb6-189">Açıklanan ilerleme durumunu bildirme semantiği tarafından uymayı [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="9dfb6-190">İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="9dfb6-191">Bazen zaman uyumsuz bir işlemi tamamlama önce artımlı sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="9dfb6-192">Bu senaryoyu desteklemek için kullanılan birkaç seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="9dfb6-193">Aşağıda bazı örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="9dfb6-194">Tek işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="9dfb6-194">Single-operation Class</span></span>

<span data-ttu-id="9dfb6-195">Sınıfınıza yalnızca tek bir zaman uyumsuz işlem destekler ve bu işlemin ardından artımlı sonuçları döndürmek için ise:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="9dfb6-196">Genişletme <xref:System.ComponentModel.ProgressChangedEventArgs> artımlı sonuç verilerini taşımak için yazın ve tanımlamak bir _MethodName_**ProgressChanged** bu veri genişletilmiş olay.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="9dfb6-197">Bu yükseltme _MethodName_**ProgressChanged** rapor için artımlı bir sonuç olduğunda olay.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="9dfb6-198">Aynı olay olarak "tüm işlemleri", artımlı sonuçları döndürmek için gerçekleşen herhangi bir sorun olduğundan bu çözüm, özellikle bir tek zaman uyumsuz işlemi sınıf için geçerlidir. _MethodName_**ProgressChanged**  olay yok.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="9dfb6-199">Artımlı homojen sonuçlarla birden çok işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="9dfb6-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="9dfb6-200">Bu durumda, sınıfınız birden çok zaman uyumsuz yöntem, artımlı sonuç döndürme özelliği destekler ve bu artımlı sonuçları tüm verilerin aynı türe sahip.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="9dfb6-201">Aynı olarak tek işlem sınıflar için yukarıda açıklanan modelini <xref:System.EventArgs> yapısı için tüm artımlı sonuçları çalışır.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="9dfb6-202">Tanımlayan bir `ProgressChanged` olay yerine bir _MethodName_**ProgressChanged** olduğundan, birden çok zaman uyumsuz yöntemler için geçerli olay.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="9dfb6-203">Heterojen artımlı sonuçlarla birden çok işlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="9dfb6-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="9dfb6-204">Birden çok zaman uyumsuz yöntemler sınıfınıza destekliyorsa, her farklı bir veri türü döndüren şunları yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="9dfb6-205">Raporlama, ilerleme durumunu raporlama artımlı sonuç ayırın.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="9dfb6-206">Ayrı bir tanımlama _MethodName_**ProgressChanged** olay uygun <xref:System.EventArgs> her zaman uyumsuz yöntemin bu yöntemin sonucu artımlı verileri işlemek.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="9dfb6-207">Bu olay işleyicisi uygun iş parçacığında içinde açıklanan şekilde çağırır [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="9dfb6-208">Yöntemlerde Ref parametreleri ve çıkış işleme</span><span class="sxs-lookup"><span data-stu-id="9dfb6-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="9dfb6-209">Ancak kullanımını `out` ve `ref` olduğundan, genel olarak, .NET Framework, burada önerilmez kurallarının mevcut olduğunda izleyin:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="9dfb6-210">Zaman uyumlu bir yöntem verilen *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="9dfb6-211">`out` parametreleri *MethodName* parçası olmamalıdır _MethodName_**zaman uyumsuz**.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="9dfb6-212">Bunun yerine, bir parçası olmalıdır _MethodName_**CompletedEventArgs** eşdeğer parametre olarak aynı ada sahip *MethodName* (olmadığı sürece daha uygun adı).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="9dfb6-213">`ref` parametreleri *MethodName* parçası olarak görünmesi gereken _MethodName_**zaman uyumsuz**ve bir parçası olarak _MethodName_  **CompletedEventArgs** eşdeğer parametre olarak aynı ada sahip *MethodName* (olmadığı sürece daha uygun bir ad).</span><span class="sxs-lookup"><span data-stu-id="9dfb6-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="9dfb6-214">Örneğin, verilen:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="9dfb6-215">Zaman uyumsuz yönteminizi ve kendi <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı şuna benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="9dfb6-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9dfb6-216">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dfb6-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="9dfb6-217">Nasıl yapılır: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama</span><span class="sxs-lookup"><span data-stu-id="9dfb6-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="9dfb6-218">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9dfb6-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="9dfb6-219">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="9dfb6-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="9dfb6-220">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="9dfb6-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="9dfb6-221">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9dfb6-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="9dfb6-222">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="9dfb6-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
