---
title: 'Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 6f0956c6418d894a5768463861151f86a1948850
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708587"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Bir catch bloğunda belirli özel durumları kullanma

Genel olarak, temel bir `catch` bildiri kullanmak yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır.

Bir özel durum oluştuğunda, yığın geçirilir ve her bir catch bloğunun onu işleme fırsatı verilir. Catch deyimlerinin sırası önemlidir. Genel bir özel durum yakalama bloğundan önce belirli özel durumlara hedeflenmiş catch blokları koyun veya derleyici bir hata verebilir. Uygun catch bloğu, özel durumun türü, catch bloğunda belirtilen özel durumun adı ile eşleştirilirken belirlenir. Belirli bir catch bloğu yoksa, özel durum, varsa genel bir catch bloğu tarafından yakalanır.

Aşağıdaki kod örneği bir <xref:System.InvalidCastException>yakalamak için bir `try`/`catch` bloğu kullanır. Örnek, `Employee` adlı bir sınıf oluşturur, çalışan düzeyi (`Emlevel`). Bir yöntem, `PromoteEmployee`, bir nesnesi alır ve çalışan düzeyini artırır. Bir <xref:System.InvalidCastException>, `PromoteEmployee` yöntemine <xref:System.DateTime> bir örnek geçirildiğinde gerçekleşir.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
