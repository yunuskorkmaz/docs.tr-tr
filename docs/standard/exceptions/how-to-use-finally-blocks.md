---
description: 'Daha fazla bilgi edinin: finally bloklarını kullanma'
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
ms.openlocfilehash: 0c296e5cba8e3f4f50005a6178886a116f6e7bac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629610"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="3d20b-103">Finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="3d20b-103">How to use finally blocks</span></span>

<span data-ttu-id="3d20b-104">Bir özel durum oluştuğunda, yürütme duraklar ve denetim uygun özel durum işleyicisine verilir.</span><span class="sxs-lookup"><span data-stu-id="3d20b-104">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="3d20b-105">Bu genellikle, yürütülmesi beklenen kod satırlarının atlanacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3d20b-105">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="3d20b-106">Bir dosya kapatma gibi bazı kaynak temizleme işlemleri, özel durum oluşturulması durumunda bile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d20b-106">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="3d20b-107">Bunu yapmak için bir `finally` bloğu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d20b-107">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="3d20b-108">Bir `finally` blok, bir özel durumun oluşturulup oluşturulmayacağını ne olursa olsun her zaman yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3d20b-108">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="3d20b-109">Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="3d20b-109">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="3d20b-110">`Main`Yöntemi iki dizi oluşturur ve diğerini kopyalamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="3d20b-110">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="3d20b-111">Eylem bir oluşturur <xref:System.ArgumentOutOfRangeException> ve hata konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="3d20b-111">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="3d20b-112">`finally`Blok, kopyalama eyleminin sonucu ne olursa olsun yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3d20b-112">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="3d20b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d20b-113">See also</span></span>

- [<span data-ttu-id="3d20b-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="3d20b-114">Exceptions</span></span>](index.md)
