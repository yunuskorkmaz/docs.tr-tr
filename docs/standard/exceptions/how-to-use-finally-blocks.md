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
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507238"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="eb7fc-102">Finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="eb7fc-102">How to use finally blocks</span></span>

<span data-ttu-id="eb7fc-103">Bir özel durum oluştuğunda yürütmeyi durdurur ve denetim uygun bir özel durum işleyicisine verilir.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="eb7fc-104">Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="eb7fc-105">Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="eb7fc-106">Bunu yapmak için kullanabileceğiniz bir `finally` blok.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="eb7fc-107">A `finally` her zaman bloğun, bir özel durum ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="eb7fc-108">Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="eb7fc-109">`Main` Yöntemi iki diziler oluşturur ve diğerine kopyalamak çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="eb7fc-110">Eylem üretir bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="eb7fc-111">`finally` Blok kopyalama eylem sonucunu bağımsız olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="eb7fc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7fc-112">See also</span></span>

- [<span data-ttu-id="eb7fc-113">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="eb7fc-113">Exceptions</span></span>](index.md)
