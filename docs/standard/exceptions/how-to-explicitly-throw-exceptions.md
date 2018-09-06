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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863232"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="da2ae-102">Nasıl açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="da2ae-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="da2ae-103">Açıkça kullanarak bir özel durum oluşturabilecek `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="da2ae-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="da2ae-104">Ayrıca kullanarak yeniden yakalanan bir özel durumu oluşturabilecek `throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="da2ae-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="da2ae-105">Kodlama yöntemi hata ayıklama sırasında daha fazla bilgi sağlamak için durum yeniden bir özel durum bilgileri eklemek için uygundur.</span><span class="sxs-lookup"><span data-stu-id="da2ae-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="da2ae-106">Aşağıdaki kod örneğinde bir `try` / `catch` olası bir catch bloğu <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="da2ae-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="da2ae-107">Aşağıdaki `try` bloğu bir `catch` yakalayan blok <xref:System.IO.FileNotFoundException> ve veri dosyası bulunamazsa iletiyi konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="da2ae-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="da2ae-108">Sonraki deyim `throw` yeni oluşturduğu deyimi <xref:System.IO.FileNotFoundException> ve özel durum için metin bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="da2ae-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="da2ae-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da2ae-109">See also</span></span>

- [<span data-ttu-id="da2ae-110">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="da2ae-110">Exceptions</span></span>](index.md)
