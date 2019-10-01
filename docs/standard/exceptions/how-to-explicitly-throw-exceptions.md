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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a71cefc0a6483dbbe6513a64d8111a07a2e5af42
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696735"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Özel durumları açıkça oluşturma

C# [@No__t-2](../../csharp/language-reference/keywords/throw.md) veya Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) ifadesini kullanarak açıkça bir özel durum oluşturabilirsiniz. @No__t-0 ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz. Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.

Aşağıdaki kod örneği, olası bir <xref:System.IO.FileNotFoundException> ' ü yakalamak için `try` @ no__t-1 @ no__t-2 bloğunu kullanır. @No__t-0 bloğundan sonra, <xref:System.IO.FileNotFoundException> ' i yakalayan ve veri dosyası bulunmazsa konsola bir ileti yazan bir `catch` bloğu vardır. Sonraki ifade, yeni bir <xref:System.IO.FileNotFoundException> oluşturan ve özel duruma metin bilgileri ekleyen `throw` deyimidir.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
