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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708868"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Özel durumları açıkça oluşturma

C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) ifadesini kullanarak açık bir özel durum oluşturabilirsiniz. Ayrıca, `throw` ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz. Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.

Aşağıdaki kod örneği, olası bir <xref:System.IO.FileNotFoundException>yakalamak için bir `try`/`catch` bloğu kullanır. `try` bloğunu takip eden, <xref:System.IO.FileNotFoundException> yakalayan ve veri dosyası bulunmazsa konsola bir ileti yazan bir `catch` bloğudur. Sonraki ifade, yeni bir <xref:System.IO.FileNotFoundException> oluşturan ve özel duruma metin bilgileri ekleyen `throw` deyimidir.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
