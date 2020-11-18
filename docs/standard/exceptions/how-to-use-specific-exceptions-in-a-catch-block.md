---
title: 'Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: bf4813e950b034cb807abebfe016c1e34487d594
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828029"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Bir catch bloğunda belirli özel durumları kullanma

Genel olarak, temel bir deyimin kullanılması yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır `catch` .

Bir özel durum oluştuğunda, yığın geçirilir ve her bir catch bloğunun onu işleme fırsatı verilir. Catch deyimlerinin sırası önemlidir. Genel bir özel durum yakalama bloğundan önce belirli özel durumlara hedeflenmiş catch blokları koyun veya derleyici bir hata verebilir. Uygun catch bloğu, özel durumun türü, catch bloğunda belirtilen özel durumun adı ile eşleştirilirken belirlenir. Belirli bir catch bloğu yoksa, özel durum, varsa genel bir catch bloğu tarafından yakalanır.

Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.InvalidCastException> . Örnek `Employee` , tek bir özellik, çalışan düzeyi () ile çağrılan bir sınıf oluşturur `Emlevel` . Bir yöntemi, `PromoteEmployee` bir nesnesi alır ve çalışan düzeyini artırır. <xref:System.InvalidCastException> <xref:System.DateTime> Yöntemine bir örnek geçirildiğinde gerçekleşir `PromoteEmployee` .

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
