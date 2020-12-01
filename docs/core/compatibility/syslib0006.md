---
title: SYSLIB0006 uyarısı
description: Derleme zamanı uyarı SYSLIB0006 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: a5ab4fe4576bd336cb7de0a91b889fa48ac5650a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437460"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="0fba7-103">SYSLIB0006: Thread. Abort desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="0fba7-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="0fba7-104">Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0fba7-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0fba7-105">Bu API 'lerin kullanımı, `SYSLIB0006` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fba7-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="0fba7-106">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="0fba7-106">Workarounds</span></span>

<span data-ttu-id="0fba7-107"><xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0fba7-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0fba7-108">Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="0fba7-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="0fba7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fba7-109">See also</span></span>

- [<span data-ttu-id="0fba7-110">Thread.Abort kullanımdan kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0fba7-110">Thread.Abort is obsolete</span></span>](core-libraries/5.0/thread-abort-obsolete.md)
- [<span data-ttu-id="0fba7-111">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="0fba7-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
