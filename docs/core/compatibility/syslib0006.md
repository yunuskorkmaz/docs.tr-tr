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
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006: Thread. Abort desteklenmiyor

Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'lerin kullanımı, `SYSLIB0006` derleme zamanında uyarı oluşturur.

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a>Geçici çözüm

<xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> . Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .

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

## <a name="see-also"></a>Ayrıca bkz.

- [Thread. Abort kullanımdan kalktı ve değişiklik](3.1-5.0.md#threadabort-is-obsolete)
- [Yönetilen İş Parçacıklarında İptal](../../standard/threading/cancellation-in-managed-threads.md)
