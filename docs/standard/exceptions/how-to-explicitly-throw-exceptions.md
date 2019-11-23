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
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="b3d85-102">Özel durumları açıkça oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3d85-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="b3d85-103">C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) ifadesini kullanarak açık bir özel durum oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d85-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="b3d85-104">Ayrıca, `throw` ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d85-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="b3d85-105">Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="b3d85-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="b3d85-106">Aşağıdaki kod örneği, olası bir <xref:System.IO.FileNotFoundException>yakalamak için bir `try`/`catch` bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3d85-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="b3d85-107">`try` bloğunu takip eden, <xref:System.IO.FileNotFoundException> yakalayan ve veri dosyası bulunmazsa konsola bir ileti yazan bir `catch` bloğudur.</span><span class="sxs-lookup"><span data-stu-id="b3d85-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="b3d85-108">Sonraki ifade, yeni bir <xref:System.IO.FileNotFoundException> oluşturan ve özel duruma metin bilgileri ekleyen `throw` deyimidir.</span><span class="sxs-lookup"><span data-stu-id="b3d85-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="b3d85-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d85-109">See also</span></span>

- [<span data-ttu-id="b3d85-110">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="b3d85-110">Exceptions</span></span>](index.md)
