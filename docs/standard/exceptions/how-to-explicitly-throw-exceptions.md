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
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="af6ba-103">Özel durumları açıkça oluşturma</span><span class="sxs-lookup"><span data-stu-id="af6ba-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="af6ba-104">C# [`throw`](../../csharp/language-reference/keywords/throw.md) veya Visual Basic deyiminizi kullanarak açıkça bir özel durum oluşturabilirsiniz [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="af6ba-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="af6ba-105">Ayrıca, ifadesini kullanarak bir kez yakalanamayan özel durum da oluşturabilirsiniz `throw` .</span><span class="sxs-lookup"><span data-stu-id="af6ba-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="af6ba-106">Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden oluşturulan bir özel duruma bilgi eklemek için iyi bir kodlama yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="af6ba-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="af6ba-107">Aşağıdaki kod örneği, `try` / `catch` olası bir yakalamak için bir blok kullanır <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="af6ba-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="af6ba-108">Bloğu takip `try` `catch` eden bir blok, <xref:System.IO.FileNotFoundException> veri dosyası bulunmazsa, öğesini yakalar ve konsola bir ileti yazar.</span><span class="sxs-lookup"><span data-stu-id="af6ba-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="af6ba-109">Sonraki ifade, `throw` Yeni bir oluşturan <xref:System.IO.FileNotFoundException> ve özel duruma metin bilgileri ekleyen deyimdir.</span><span class="sxs-lookup"><span data-stu-id="af6ba-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="af6ba-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af6ba-110">See also</span></span>

- [<span data-ttu-id="af6ba-111">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="af6ba-111">Exceptions</span></span>](index.md)
