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
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571804"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Catch bloğunda belirli özel durumların kullanma

Genel olarak, belirli bir özel durum türünü catch yerine temel kullanmak için uygulama programlama iyi `catch` deyimi.

Özel durum oluştuğunda yığını geçirilir ve her catch bloğu, işleme fırsatına verilir. Catch deyimleri sıralama önemlidir. Catch blokları belirli özel durumların genel özel durum yakalama bloğunu veya derleyici hata verecek önce hedeflenen yerleştirin. Uygun catch bloğu adı özel durumu catch bloğunda belirtilen özel durum türünü eşleşen tarafından belirlenir. Hiçbir özel catch bloğu varsa, özel durum varsa, genel catch bloğu tarafından yakalandı.

Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.InvalidCastException>. Adlı bir sınıf bir örnek oluşturur `Employee` ile tek bir özelliği, çalışan düzeyi (`Emlevel`). Yöntemi, bir `PromoteEmployee`, nesneyi alır ve çalışan düzeyini artırır. Bir <xref:System.InvalidCastException> oluşur, bir <xref:System.DateTime> örneği iletilir `PromoteEmployee` yöntemi.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel Durumlar](index.md)
