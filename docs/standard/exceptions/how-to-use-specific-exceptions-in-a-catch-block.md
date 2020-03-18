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
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160163"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Yakalama bloğunda belirli özel durumlar nasıl kullanılır?

Genel olarak, temel `catch` bir deyim kullanmak yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır.

Bir özel durum oluştuğunda, yığın alını ve her catch bloğu işlemek için fırsat verilir. Yakalama ifadelerinin sırası önemlidir. Genel bir özel durum yakalama bloğu veya derleyici bir hata sorunu olabilir önce belirli özel durumlara hedeflenen catch blokları koyun. Uygun catch bloğu, özel durum türü yle catch bloğunda belirtilen özel durum adıyla eşleştirilerek belirlenir. Belirli bir catch bloğu yoksa, özel durum varsa genel bir catch bloğu tarafından yakalanır.

Aşağıdaki kod örneği `try` / `catch` bir <xref:System.InvalidCastException>. Örnek, tek bir `Employee` özellik, çalışan düzeyi (`Emlevel`ile adlandırılan bir sınıf oluşturur. Bir yöntem, `PromoteEmployee`bir nesne alır ve çalışan düzeyini yükselter. Bir <xref:System.InvalidCastException> <xref:System.DateTime> örnek `PromoteEmployee` yönteme geçirildiğinde oluşur.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
