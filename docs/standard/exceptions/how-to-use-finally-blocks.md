---
title: "Nasıl yapılır: Finally Bloklarını Kullanma"
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
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="b5acd-102">Finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="b5acd-102">How to use finally blocks</span></span>

<span data-ttu-id="b5acd-103">Özel durum oluştuğunda yürütme durur ve denetim için uygun özel durum işleyici verilir.</span><span class="sxs-lookup"><span data-stu-id="b5acd-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="b5acd-104">Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5acd-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="b5acd-105">Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5acd-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="b5acd-106">Bunu yapmak için kullanabileceğiniz bir `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="b5acd-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="b5acd-107">A `finally` bloğu her zaman yürütür, bir özel durum ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="b5acd-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="b5acd-108">Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="b5acd-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="b5acd-109">`Main` Yöntemi dizilerinin oluşturur ve diğerine kopyalamak çalışır.</span><span class="sxs-lookup"><span data-stu-id="b5acd-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="b5acd-110">Eylem oluşturan bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="b5acd-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="b5acd-111">`finally` Blok kopyalama eylemin sonucunu bağımsız olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="b5acd-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="b5acd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5acd-112">See Also</span></span>  
[<span data-ttu-id="b5acd-113">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="b5acd-113">Exceptions</span></span>](index.md)   
