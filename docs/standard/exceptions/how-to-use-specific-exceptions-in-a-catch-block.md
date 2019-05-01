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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970891"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Bir catch bloğunda belirli özel durumları kullanma

Genel olarak, iyi bir yerine belirli bir özel durum türünün catch temel kullanmak için programlama `catch` deyimi.

Bir özel durum oluştuğunda yığını geçirilir ve her bir catch bloğu, işleme fırsatı verilir. Catch deyimleri sırası önemlidir. Genel özel durum yakalama bloğu ya da derleyici hata gönderebilirsiniz önce belirli özel durumları için hedeflenen catch blokları yerleştirin. Uygun catch bloğu içindeki yakalama bloğunun belirtilen özel durumun adıyla özel durumun türü eşleşen tarafından belirlenir. Hiçbir belirli bir catch bloğu ise özel durum varsa, bir genel bir catch bloğu tarafından yakalandı.

Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.InvalidCastException>. Örnek adlı bir sınıf oluşturur `Employee` çalışan düzeyi tek bir özellik ile (`Emlevel`). Bir yöntemin `PromoteEmployee`, bir nesneyi alır ve çalışan düzeyini artırır. Bir <xref:System.InvalidCastException> gerçekleşir, bir <xref:System.DateTime> örneği geçirildiğinde `PromoteEmployee` yöntemi.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
