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
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160163"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="2645f-102">Bir catch bloğunda belirli özel durumları kullanma</span><span class="sxs-lookup"><span data-stu-id="2645f-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="2645f-103">Genel olarak, temel bir `catch` bildiri kullanmak yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2645f-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="2645f-104">Bir özel durum oluştuğunda, yığın geçirilir ve her bir catch bloğunun onu işleme fırsatı verilir.</span><span class="sxs-lookup"><span data-stu-id="2645f-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="2645f-105">Catch deyimlerinin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2645f-105">The order of catch statements is important.</span></span> <span data-ttu-id="2645f-106">Genel bir özel durum yakalama bloğundan önce belirli özel durumlara hedeflenmiş catch blokları koyun veya derleyici bir hata verebilir.</span><span class="sxs-lookup"><span data-stu-id="2645f-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="2645f-107">Uygun catch bloğu, özel durumun türü, catch bloğunda belirtilen özel durumun adı ile eşleştirilirken belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2645f-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="2645f-108">Belirli bir catch bloğu yoksa, özel durum, varsa genel bir catch bloğu tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="2645f-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="2645f-109">Aşağıdaki kod örneği bir <xref:System.InvalidCastException>yakalamak için bir `try`/`catch` bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2645f-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="2645f-110">Örnek, `Employee` adlı bir sınıf oluşturur, çalışan düzeyi (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="2645f-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="2645f-111">Bir yöntem, `PromoteEmployee`, bir nesnesi alır ve çalışan düzeyini artırır.</span><span class="sxs-lookup"><span data-stu-id="2645f-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="2645f-112">Bir <xref:System.InvalidCastException>, `PromoteEmployee` yöntemine <xref:System.DateTime> bir örnek geçirildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2645f-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2645f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2645f-113">See also</span></span>

- [<span data-ttu-id="2645f-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="2645f-114">Exceptions</span></span>](index.md)
