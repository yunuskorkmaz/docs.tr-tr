---
title: 'Nasıl yapılır: Açıkça Özel Durumlar Oluşturma'
description: C# throw ifadesini veya Visual Basic throw ifadesini kullanarak .NET 'te açık bir özel durum oluşturmayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662790"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Özel durumları açıkça oluşturma

C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic deyiminizi kullanarak açıkça bir özel durum oluşturabilirsiniz [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Ayrıca, ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz `throw` . Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.

Aşağıdaki kod örneği, `try` / `catch` olası bir yakalamak için bir blok kullanır <xref:System.IO.FileNotFoundException> . Bloğu takip `try` `catch` eden bir blok, <xref:System.IO.FileNotFoundException> veri dosyası bulunmazsa, öğesini yakalar ve konsola bir ileti yazar. Sonraki ifade, `throw` Yeni bir oluşturan <xref:System.IO.FileNotFoundException> ve özel duruma metin bilgileri ekleyen deyimdir.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
