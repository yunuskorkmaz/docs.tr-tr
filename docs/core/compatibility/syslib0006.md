---
title: SYSLIB0006 uyarısı
description: Derleme zamanı uyarı SYSLIB0006 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 45d2d8ec6ad99996f8b8f46d0c2e0ac2e02cf450
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333358"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="ba61b-103">SYSLIB0006: Thread. Abort desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ba61b-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="ba61b-104">Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ba61b-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="ba61b-105">Bu API 'lerin kullanımı, `SYSLIB0006` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba61b-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="ba61b-106">Geçici çözüm</span><span class="sxs-lookup"><span data-stu-id="ba61b-106">Workaround</span></span>

<span data-ttu-id="ba61b-107"><xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ba61b-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba61b-108">Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="ba61b-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ba61b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba61b-109">See also</span></span>

- [<span data-ttu-id="ba61b-110">Thread. Abort kullanımdan kalktı ve değişiklik</span><span class="sxs-lookup"><span data-stu-id="ba61b-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="ba61b-111">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="ba61b-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
