---
title: 'Son değişiklik: Thread. Abort artık kullanılmıyor'
description: Iş parçacığı. Abort API 'Lerinin artık kullanılmayan çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 6d7dfce8fda393bfd88c9b4cf0c59d53942cee25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761385"
---
# <a name="threadabort-is-obsolete"></a><span data-ttu-id="0abe6-103">Thread. Abort artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="0abe6-103">Thread.Abort is obsolete</span></span>

<span data-ttu-id="0abe6-104"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0abe6-104">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="0abe6-105">.NET 5,0 veya sonraki bir sürümü hedefleyen projeler, bu yöntemler çağrılırsa derleme zamanı uyarısıyla karşılaşacaktır `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="0abe6-105">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

## <a name="change-description"></a><span data-ttu-id="0abe6-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0abe6-106">Change description</span></span>

<span data-ttu-id="0abe6-107">Daha önce, ' <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a yapılan çağrılar derleme zamanı uyarıları üretmedi, ancak yöntem çalışma zamanında bir oluşturma işlemi gerçekleştiriyordu <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="0abe6-107">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="0abe6-108">.NET 5,0 ' den itibaren, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> artık uyarı olarak kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0abe6-108">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="0abe6-109">Bu yöntemin çağrılması derleyici uyarısı oluşturur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="0abe6-109">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="0abe6-110">Yönteminin uygulanması değiştirilmez ve bir oluşturma işlemi devam eder <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="0abe6-110">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0abe6-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0abe6-111">Reason for change</span></span>

<span data-ttu-id="0abe6-112"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Her zaman <xref:System.PlatformNotSupportedException> , .NET Framework hariç tüm .NET uygulamalarında her zaman bir şekilde oluşturulan, <xref:System.ObsoleteAttribute> çağrıldığı yerlere dikkat çekmek için yönteme eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0abe6-112">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0abe6-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0abe6-113">Version introduced</span></span>

<span data-ttu-id="0abe6-114">5.0</span><span class="sxs-lookup"><span data-stu-id="0abe6-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0abe6-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0abe6-115">Recommended action</span></span>

- <span data-ttu-id="0abe6-116"><xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0abe6-116">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0abe6-117">Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="0abe6-117">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="0abe6-118">Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="0abe6-118">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="0abe6-119">Derleme zamanı uyarısını bastırmak için uyarı kodunu gizleyin `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="0abe6-119">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="0abe6-120">Uyarı kodu öğesine özeldir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ve bu kod, kodunuzun diğer kullanımdan kaldırma uyarılarını göstermez.</span><span class="sxs-lookup"><span data-stu-id="0abe6-120">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="0abe6-121">Ancak, uyarıları kaldırmak yerine ' a yapılan çağrıları kaldırmanızı öneririz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0abe6-121">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="0abe6-122">Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0abe6-122">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a><span data-ttu-id="0abe6-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0abe6-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
