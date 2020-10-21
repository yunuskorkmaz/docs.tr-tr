---
ms.openlocfilehash: ee67b32b093ebd42f8ac685b34b12f2f6833be86
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332943"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="9b614-101">Thread. Abort artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="9b614-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="9b614-102"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9b614-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="9b614-103">.NET 5,0 veya sonraki bir sürümü hedefleyen projeler, bu yöntemler çağrılırsa derleme zamanı uyarısıyla karşılaşacaktır `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="9b614-103">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9b614-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9b614-104">Change description</span></span>

<span data-ttu-id="9b614-105">Daha önce, ' <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a yapılan çağrılar derleme zamanı uyarıları üretmedi, ancak yöntem çalışma zamanında bir oluşturma işlemi gerçekleştiriyordu <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9b614-105">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="9b614-106">.NET 5,0 ' den itibaren, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> artık uyarı olarak kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="9b614-106">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="9b614-107">Bu yöntemin çağrılması derleyici uyarısı oluşturur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="9b614-107">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="9b614-108">Yönteminin uygulanması değiştirilmez ve bir oluşturma işlemi devam eder <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9b614-108">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9b614-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9b614-109">Reason for change</span></span>

<span data-ttu-id="9b614-110"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Her zaman <xref:System.PlatformNotSupportedException> , .NET Framework hariç tüm .NET uygulamalarında her zaman bir şekilde oluşturulan, <xref:System.ObsoleteAttribute> çağrıldığı yerlere dikkat çekmek için yönteme eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9b614-110">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b614-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9b614-111">Version introduced</span></span>

<span data-ttu-id="9b614-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="9b614-112">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b614-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9b614-113">Recommended action</span></span>

- <span data-ttu-id="9b614-114"><xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9b614-114">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9b614-115">Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="9b614-115">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="9b614-116">Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="9b614-116">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="9b614-117">Derleme zamanı uyarısını bastırmak için uyarı kodunu gizleyin `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="9b614-117">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="9b614-118">Uyarı kodu öğesine özeldir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ve bu kod, kodunuzun diğer kullanımdan kaldırma uyarılarını göstermez.</span><span class="sxs-lookup"><span data-stu-id="9b614-118">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="9b614-119">Ancak, uyarıları kaldırmak yerine ' a yapılan çağrıları kaldırmanızı öneririz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9b614-119">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="9b614-120">Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b614-120">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="9b614-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="9b614-121">Category</span></span>

- <span data-ttu-id="9b614-122">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="9b614-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b614-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9b614-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
