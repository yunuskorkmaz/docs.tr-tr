---
title: "Nasıl yapılır: Açıkça Özel Durumlar Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3fce332263dac3f9906d33fe3bd2590050b86f8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="769a2-102">Nasıl açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="769a2-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="769a2-103">Kullanarak bir özel durum açıkça atabilirsiniz `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="769a2-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="769a2-104">Kullanarak yeniden yakalanan bir özel durum da atabilirsiniz `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="769a2-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="769a2-105">Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden atılmış bir özel durum bilgileri eklemek için uygulama kodlama iyi olur.</span><span class="sxs-lookup"><span data-stu-id="769a2-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="769a2-106">Aşağıdaki kod örneğinde bir `try` / `catch` olası catch bloğu <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="769a2-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="769a2-107">Aşağıdaki `try` bloğu bir `catch` yakalar blok <xref:System.IO.FileNotFoundException> ve veri dosyası bulunamazsa, bir ileti konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="769a2-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="769a2-108">Sonraki deyim `throw` yeni bir oluşturur deyimi <xref:System.IO.FileNotFoundException> ve metin bilgileri özel durumu ekler.</span><span class="sxs-lookup"><span data-stu-id="769a2-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="769a2-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="769a2-109">See Also</span></span>  
[<span data-ttu-id="769a2-110">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="769a2-110">Exceptions</span></span>](index.md)
