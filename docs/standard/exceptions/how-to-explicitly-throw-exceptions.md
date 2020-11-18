---
title: 'Nasıl yapılır: Açıkça Özel Durumlar Oluşturma'
description: C# throw ifadesini veya Visual Basic throw ifadesini kullanarak .NET 'te açık bir özel durum oluşturmayı öğrenin.
ms.date: 03/30/2017
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
ms.openlocfilehash: 37ba5f952d621ff2e209a3bac375b62894c944a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828055"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Özel durumları açıkça oluşturma

C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic deyiminizi kullanarak açıkça bir özel durum oluşturabilirsiniz [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Ayrıca, ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz `throw` . Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.

Aşağıdaki kod örneği, `try` / `catch` olası bir yakalamak için bir blok kullanır <xref:System.IO.FileNotFoundException> . Bloğu takip `try` `catch` eden bir blok, <xref:System.IO.FileNotFoundException> veri dosyası bulunmazsa, öğesini yakalar ve konsola bir ileti yazar. Sonraki ifade, `throw` Yeni bir oluşturan <xref:System.IO.FileNotFoundException> ve özel duruma metin bilgileri ekleyen deyimdir.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
