---
description: 'Hakkında daha fazla bilgi edinin: bir catch bloğunda belirli özel durumları kullanma'
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
ms.openlocfilehash: 5eb2a753af05c10b722cc7e41b5bb13f45fdef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775870"
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
