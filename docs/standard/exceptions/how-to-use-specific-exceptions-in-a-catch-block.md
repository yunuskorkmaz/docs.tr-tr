---
title: 'Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202355"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="4fd4f-102">Bir catch bloğunda belirli özel durumları kullanma</span><span class="sxs-lookup"><span data-stu-id="4fd4f-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="4fd4f-103">Genel olarak, iyi bir yerine belirli bir özel durum türünün catch temel kullanmak için programlama `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="4fd4f-104">Bir özel durum oluştuğunda yığını geçirilir ve her bir catch bloğu, işleme fırsatı verilir.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="4fd4f-105">Catch deyimleri sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-105">The order of catch statements is important.</span></span> <span data-ttu-id="4fd4f-106">Genel özel durum yakalama bloğu ya da derleyici hata gönderebilirsiniz önce belirli özel durumları için hedeflenen catch blokları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="4fd4f-107">Uygun catch bloğu içindeki yakalama bloğunun belirtilen özel durumun adıyla özel durumun türü eşleşen tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="4fd4f-108">Hiçbir belirli bir catch bloğu ise özel durum varsa, bir genel bir catch bloğu tarafından yakalandı.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="4fd4f-109">Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="4fd4f-110">Örnek adlı bir sınıf oluşturur `Employee` çalışan düzeyi tek bir özellik ile (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="4fd4f-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="4fd4f-111">Bir yöntemin `PromoteEmployee`, bir nesneyi alır ve çalışan düzeyini artırır.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="4fd4f-112">Bir <xref:System.InvalidCastException> gerçekleşir, bir <xref:System.DateTime> örneği geçirildiğinde `PromoteEmployee` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="4fd4f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fd4f-113">See also</span></span>

- [<span data-ttu-id="4fd4f-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="4fd4f-114">Exceptions</span></span>](index.md)
