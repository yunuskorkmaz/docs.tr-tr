---
title: 'Nasıl yapılır: Finally Bloklarını Kullanma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 8bc36ce9a755762bb5159a27f9ef5699b2992f0e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828042"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="f7aa9-102">Finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="f7aa9-102">How to use finally blocks</span></span>

<span data-ttu-id="f7aa9-103">Bir özel durum oluştuğunda, yürütme duraklar ve denetim uygun özel durum işleyicisine verilir.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="f7aa9-104">Bu genellikle, yürütülmesi beklenen kod satırlarının atlanacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="f7aa9-105">Bir dosya kapatma gibi bazı kaynak temizleme işlemleri, özel durum oluşturulması durumunda bile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="f7aa9-106">Bunu yapmak için bir `finally` bloğu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="f7aa9-107">Bir `finally` blok, bir özel durumun oluşturulup oluşturulmayacağını ne olursa olsun her zaman yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="f7aa9-108">Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="f7aa9-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="f7aa9-109">`Main`Yöntemi iki dizi oluşturur ve diğerini kopyalamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="f7aa9-110">Eylem bir oluşturur <xref:System.ArgumentOutOfRangeException> ve hata konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="f7aa9-111">`finally`Blok, kopyalama eyleminin sonucu ne olursa olsun yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="f7aa9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7aa9-112">See also</span></span>

- [<span data-ttu-id="f7aa9-113">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f7aa9-113">Exceptions</span></span>](index.md)
