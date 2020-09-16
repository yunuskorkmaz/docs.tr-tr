---
ms.openlocfilehash: 85488de561a2298f2ff4009ec78b9a6e294053f3
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598183"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="1afeb-101">Thread. Abort artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="1afeb-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="1afeb-102"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1afeb-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="1afeb-103">.NET 5,0 veya sonraki bir sürümü hedefleyen projeler, bu yöntemler çağrılırsa derleme zamanı uyarılarıyla karşılaşacaktır.</span><span class="sxs-lookup"><span data-stu-id="1afeb-103">Projects that target .NET 5.0 or a later version will encounter compile-time warnings if these methods are called.</span></span> <span data-ttu-id="1afeb-104">Uyarıları bastırdığınızda, çalışma zamanında bir <xref:System.PlatformNotSupportedException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1afeb-104">If you suppress the warnings, a <xref:System.PlatformNotSupportedException> will be thrown at run time.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1afeb-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1afeb-105">Change description</span></span>

<span data-ttu-id="1afeb-106">Daha önce, ' <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a yapılan çağrılar derleme zamanı uyarıları üretmedi, ancak yöntem çalışma zamanında bir oluşturma işlemi gerçekleştiriyordu <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="1afeb-106">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="1afeb-107">.NET 5,0 ' den itibaren, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> artık uyarı olarak kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="1afeb-107">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="1afeb-108">Bu yöntemin çağrılması derleyici uyarısı oluşturur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="1afeb-108">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="1afeb-109">Yönteminin uygulanması değiştirilmez ve bir oluşturma işlemi devam eder <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="1afeb-109">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1afeb-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1afeb-110">Reason for change</span></span>

<span data-ttu-id="1afeb-111"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Her zaman <xref:System.PlatformNotSupportedException> , .NET Framework hariç tüm .NET uygulamalarında her zaman bir şekilde oluşturulan, <xref:System.ObsoleteAttribute> çağrıldığı yerlere dikkat çekmek için yönteme eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1afeb-111">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1afeb-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1afeb-112">Version introduced</span></span>

<span data-ttu-id="1afeb-113">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="1afeb-113">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1afeb-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1afeb-114">Recommended action</span></span>

- <span data-ttu-id="1afeb-115"><xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1afeb-115">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1afeb-116">Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="1afeb-116">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="1afeb-117">Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="1afeb-117">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="1afeb-118">Derleme zamanı uyarısını bastırmak için uyarı kodunu gizleyin `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="1afeb-118">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="1afeb-119">Uyarı kodu öğesine özeldir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ve bu kod, kodunuzun diğer kullanımdan kaldırma uyarılarını göstermez.</span><span class="sxs-lookup"><span data-stu-id="1afeb-119">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="1afeb-120">Ancak, uyarıları kaldırmak yerine ' a yapılan çağrıları kaldırmanızı öneririz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1afeb-120">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="1afeb-121">Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1afeb-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="1afeb-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="1afeb-122">Category</span></span>

- <span data-ttu-id="1afeb-123">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="1afeb-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1afeb-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1afeb-124">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
