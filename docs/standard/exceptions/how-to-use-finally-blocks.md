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
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708838"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="5faf5-102">Son blokları nasıl kullanılır</span><span class="sxs-lookup"><span data-stu-id="5faf5-102">How to use finally blocks</span></span>

<span data-ttu-id="5faf5-103">Bir özel durum oluştuğunda, yürütme durur ve denetim uygun özel durum işleyicisine verilir.</span><span class="sxs-lookup"><span data-stu-id="5faf5-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="5faf5-104">Bu genellikle yürütülmesini beklediğiniz kod satırlarının atlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5faf5-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="5faf5-105">Bir dosyayı kapatma gibi bazı kaynak temizleme, bir özel durum atılsa bile yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5faf5-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="5faf5-106">Bunu yapmak için bir `finally` blok kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5faf5-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="5faf5-107">Bir `finally` özel durum atılıp atılmadığına bakılmaksızın, bir blok her zaman yürütür.</span><span class="sxs-lookup"><span data-stu-id="5faf5-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="5faf5-108">Aşağıdaki kod örneği `try` / `catch` bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="5faf5-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="5faf5-109">Yöntem `Main` iki dizi oluşturur ve birini diğerine kopyalamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5faf5-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="5faf5-110">Eylem bir oluşturur <xref:System.ArgumentOutOfRangeException> ve hata konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="5faf5-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="5faf5-111">Blok, `finally` kopyalama eyleminin sonucuna bakılmaksızın yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5faf5-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="5faf5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5faf5-112">See also</span></span>

- [<span data-ttu-id="5faf5-113">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5faf5-113">Exceptions</span></span>](index.md)
