---
title: 'Nasıl yapılır: Finally Bloklarını Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571527"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="811ee-102">Finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="811ee-102">How to use finally blocks</span></span>

<span data-ttu-id="811ee-103">Özel durum oluştuğunda yürütme durur ve denetim için uygun özel durum işleyici verilir.</span><span class="sxs-lookup"><span data-stu-id="811ee-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="811ee-104">Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="811ee-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="811ee-105">Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="811ee-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="811ee-106">Bunu yapmak için kullanabileceğiniz bir `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="811ee-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="811ee-107">A `finally` bloğu her zaman yürütür, bir özel durum ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="811ee-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="811ee-108">Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="811ee-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="811ee-109">`Main` Yöntemi dizilerinin oluşturur ve diğerine kopyalamak çalışır.</span><span class="sxs-lookup"><span data-stu-id="811ee-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="811ee-110">Eylem oluşturan bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="811ee-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="811ee-111">`finally` Blok kopyalama eylemin sonucunu bağımsız olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="811ee-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="811ee-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="811ee-112">See Also</span></span>  
[<span data-ttu-id="811ee-113">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="811ee-113">Exceptions</span></span>](index.md)   
