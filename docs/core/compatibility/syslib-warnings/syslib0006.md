---
title: SYSLIB0006 uyarısı
description: Derleme zamanı uyarı SYSLIB0006 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: c1eecade9280ac37917bc24aa2973756c7f08d87
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596558"
---
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006: Thread. Abort desteklenmiyor

Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'lerin kullanımı, `SYSLIB0006` derleme zamanında uyarı oluşturur.

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Thread.Abort kullanımdan kaldırıldı](../core-libraries/5.0/thread-abort-obsolete.md)
- [Yönetilen İş Parçacıklarında İptal](../../../standard/threading/cancellation-in-managed-threads.md)
