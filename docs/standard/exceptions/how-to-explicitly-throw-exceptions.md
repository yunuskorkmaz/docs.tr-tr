---
title: 'Nasıl yapılır: Açıkça Özel Durumlar Oluşturma'
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
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708868"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Özel durumlar açıkça nasıl atılır?

C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) deyimini kullanarak açıkça bir özel durum atabilirsiniz. `throw` Ayrıca, deyimi kullanarak yakalanan bir özel durum da atabilirsiniz. Hata ayıklama yaparken daha fazla bilgi sağlamak için yeniden atılan bir özel durum için bilgi eklemek iyi bir kodlama uygulamasıdır.

Aşağıdaki kod örneği `try` / `catch` olası <xref:System.IO.FileNotFoundException>bir yakalamak için bir blok kullanır. Engellemeyi `try` takip `catch` eden, veri <xref:System.IO.FileNotFoundException> dosyasını bulmazsa konsola ileti yi yakalayan ve ileti yazan bir blok bulunur. Bir sonraki deyim, yeni `throw` <xref:System.IO.FileNotFoundException> bir ifade atan ve özel durum için metin bilgisi ekleyen ifadedir.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
