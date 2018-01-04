---
title: "Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ebc59035140ff0464cd959129fdf48a4e9a269f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
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
