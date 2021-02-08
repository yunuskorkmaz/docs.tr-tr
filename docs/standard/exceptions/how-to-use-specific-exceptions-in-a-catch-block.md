---
description: 'Hakkında daha fazla bilgi edinin: bir catch bloğunda belirli özel durumları kullanma'
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
ms.openlocfilehash: 5eb2a753af05c10b722cc7e41b5bb13f45fdef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775870"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="49089-103">Bir catch bloğunda belirli özel durumları kullanma</span><span class="sxs-lookup"><span data-stu-id="49089-103">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="49089-104">Genel olarak, temel bir deyimin kullanılması yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır `catch` .</span><span class="sxs-lookup"><span data-stu-id="49089-104">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="49089-105">Bir özel durum oluştuğunda, yığın geçirilir ve her bir catch bloğunun onu işleme fırsatı verilir.</span><span class="sxs-lookup"><span data-stu-id="49089-105">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="49089-106">Catch deyimlerinin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="49089-106">The order of catch statements is important.</span></span> <span data-ttu-id="49089-107">Genel bir özel durum yakalama bloğundan önce belirli özel durumlara hedeflenmiş catch blokları koyun veya derleyici bir hata verebilir.</span><span class="sxs-lookup"><span data-stu-id="49089-107">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="49089-108">Uygun catch bloğu, özel durumun türü, catch bloğunda belirtilen özel durumun adı ile eşleştirilirken belirlenir.</span><span class="sxs-lookup"><span data-stu-id="49089-108">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="49089-109">Belirli bir catch bloğu yoksa, özel durum, varsa genel bir catch bloğu tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="49089-109">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="49089-110">Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="49089-110">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="49089-111">Örnek `Employee` , tek bir özellik, çalışan düzeyi () ile çağrılan bir sınıf oluşturur `Emlevel` .</span><span class="sxs-lookup"><span data-stu-id="49089-111">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="49089-112">Bir yöntemi, `PromoteEmployee` bir nesnesi alır ve çalışan düzeyini artırır.</span><span class="sxs-lookup"><span data-stu-id="49089-112">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="49089-113"><xref:System.InvalidCastException> <xref:System.DateTime> Yöntemine bir örnek geçirildiğinde gerçekleşir `PromoteEmployee` .</span><span class="sxs-lookup"><span data-stu-id="49089-113">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="49089-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49089-114">See also</span></span>

- [<span data-ttu-id="49089-115">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="49089-115">Exceptions</span></span>](index.md)
