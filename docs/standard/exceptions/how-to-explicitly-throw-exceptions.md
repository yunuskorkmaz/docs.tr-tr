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
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="2ca83-102">Özel durumlar açıkça nasıl atılır?</span><span class="sxs-lookup"><span data-stu-id="2ca83-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="2ca83-103">C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) deyimini kullanarak açıkça bir özel durum atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ca83-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="2ca83-104">`throw` Ayrıca, deyimi kullanarak yakalanan bir özel durum da atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ca83-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="2ca83-105">Hata ayıklama yaparken daha fazla bilgi sağlamak için yeniden atılan bir özel durum için bilgi eklemek iyi bir kodlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2ca83-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="2ca83-106">Aşağıdaki kod örneği `try` / `catch` olası <xref:System.IO.FileNotFoundException>bir yakalamak için bir blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ca83-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="2ca83-107">Engellemeyi `try` takip `catch` eden, veri <xref:System.IO.FileNotFoundException> dosyasını bulmazsa konsola ileti yi yakalayan ve ileti yazan bir blok bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ca83-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="2ca83-108">Bir sonraki deyim, yeni `throw` <xref:System.IO.FileNotFoundException> bir ifade atan ve özel durum için metin bilgisi ekleyen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2ca83-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="2ca83-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ca83-109">See also</span></span>

- [<span data-ttu-id="2ca83-110">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="2ca83-110">Exceptions</span></span>](index.md)
