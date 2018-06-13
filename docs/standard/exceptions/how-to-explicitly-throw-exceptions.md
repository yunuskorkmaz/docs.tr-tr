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
ms.openlocfilehash: 4eeb70c10d71a7c96136039342bcdcc7bc8ece20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570358"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="ce1dd-102">Nasıl açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce1dd-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="ce1dd-103">Kullanarak bir özel durum açıkça atabilirsiniz `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="ce1dd-104">Kullanarak yeniden yakalanan bir özel durum da atabilirsiniz `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="ce1dd-105">Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden atılmış bir özel durum bilgileri eklemek için uygulama kodlama iyi olur.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="ce1dd-106">Aşağıdaki kod örneğinde bir `try` / `catch` olası catch bloğu <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="ce1dd-107">Aşağıdaki `try` bloğu bir `catch` yakalar blok <xref:System.IO.FileNotFoundException> ve veri dosyası bulunamazsa, bir ileti konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="ce1dd-108">Sonraki deyim `throw` yeni bir oluşturur deyimi <xref:System.IO.FileNotFoundException> ve metin bilgileri özel durumu ekler.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="ce1dd-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce1dd-109">See Also</span></span>  
[<span data-ttu-id="ce1dd-110">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ce1dd-110">Exceptions</span></span>](index.md)
