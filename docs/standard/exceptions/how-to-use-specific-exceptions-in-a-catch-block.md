---
title: 'Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: bf4813e950b034cb807abebfe016c1e34487d594
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828029"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="da09e-102">Bir catch bloğunda belirli özel durumları kullanma</span><span class="sxs-lookup"><span data-stu-id="da09e-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="da09e-103">Genel olarak, temel bir deyimin kullanılması yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır `catch` .</span><span class="sxs-lookup"><span data-stu-id="da09e-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="da09e-104">Bir özel durum oluştuğunda, yığın geçirilir ve her bir catch bloğunun onu işleme fırsatı verilir.</span><span class="sxs-lookup"><span data-stu-id="da09e-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="da09e-105">Catch deyimlerinin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="da09e-105">The order of catch statements is important.</span></span> <span data-ttu-id="da09e-106">Genel bir özel durum yakalama bloğundan önce belirli özel durumlara hedeflenmiş catch blokları koyun veya derleyici bir hata verebilir.</span><span class="sxs-lookup"><span data-stu-id="da09e-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="da09e-107">Uygun catch bloğu, özel durumun türü, catch bloğunda belirtilen özel durumun adı ile eşleştirilirken belirlenir.</span><span class="sxs-lookup"><span data-stu-id="da09e-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="da09e-108">Belirli bir catch bloğu yoksa, özel durum, varsa genel bir catch bloğu tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="da09e-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="da09e-109">Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="da09e-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="da09e-110">Örnek `Employee` , tek bir özellik, çalışan düzeyi () ile çağrılan bir sınıf oluşturur `Emlevel` .</span><span class="sxs-lookup"><span data-stu-id="da09e-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="da09e-111">Bir yöntemi, `PromoteEmployee` bir nesnesi alır ve çalışan düzeyini artırır.</span><span class="sxs-lookup"><span data-stu-id="da09e-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="da09e-112"><xref:System.InvalidCastException> <xref:System.DateTime> Yöntemine bir örnek geçirildiğinde gerçekleşir `PromoteEmployee` .</span><span class="sxs-lookup"><span data-stu-id="da09e-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="da09e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da09e-113">See also</span></span>

- [<span data-ttu-id="da09e-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="da09e-114">Exceptions</span></span>](index.md)
