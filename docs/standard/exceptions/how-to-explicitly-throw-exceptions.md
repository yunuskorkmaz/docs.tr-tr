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
ms.openlocfilehash: a1a8658999f08d295e76afc9df6ec8acd146abe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970904"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Nasıl açıkça özel durumlar oluşturma

Açıkça kullanarak bir özel durum oluşturabilecek `throw` deyimi. Ayrıca kullanarak yeniden yakalanan bir özel durumu oluşturabilecek `throw` deyimi. Kodlama yöntemi hata ayıklama sırasında daha fazla bilgi sağlamak için durum yeniden bir özel durum bilgileri eklemek için uygundur.

Aşağıdaki kod örneğinde bir `try` / `catch` olası bir catch bloğu <xref:System.IO.FileNotFoundException>. Aşağıdaki `try` bloğu bir `catch` yakalayan blok <xref:System.IO.FileNotFoundException> ve veri dosyası bulunamazsa iletiyi konsola yazar. Sonraki deyim `throw` yeni oluşturduğu deyimi <xref:System.IO.FileNotFoundException> ve özel durum için metin bilgi ekler.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
