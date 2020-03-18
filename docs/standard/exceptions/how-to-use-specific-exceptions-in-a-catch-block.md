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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160163"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="0b41c-102">Yakalama bloğunda belirli özel durumlar nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="0b41c-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="0b41c-103">Genel olarak, temel `catch` bir deyim kullanmak yerine belirli bir özel durum türünü yakalamak iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b41c-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="0b41c-104">Bir özel durum oluştuğunda, yığın alını ve her catch bloğu işlemek için fırsat verilir.</span><span class="sxs-lookup"><span data-stu-id="0b41c-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="0b41c-105">Yakalama ifadelerinin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0b41c-105">The order of catch statements is important.</span></span> <span data-ttu-id="0b41c-106">Genel bir özel durum yakalama bloğu veya derleyici bir hata sorunu olabilir önce belirli özel durumlara hedeflenen catch blokları koyun.</span><span class="sxs-lookup"><span data-stu-id="0b41c-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="0b41c-107">Uygun catch bloğu, özel durum türü yle catch bloğunda belirtilen özel durum adıyla eşleştirilerek belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0b41c-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="0b41c-108">Belirli bir catch bloğu yoksa, özel durum varsa genel bir catch bloğu tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="0b41c-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="0b41c-109">Aşağıdaki kod örneği `try` / `catch` bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="0b41c-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="0b41c-110">Örnek, tek bir `Employee` özellik, çalışan düzeyi (`Emlevel`ile adlandırılan bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b41c-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="0b41c-111">Bir yöntem, `PromoteEmployee`bir nesne alır ve çalışan düzeyini yükselter.</span><span class="sxs-lookup"><span data-stu-id="0b41c-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="0b41c-112">Bir <xref:System.InvalidCastException> <xref:System.DateTime> örnek `PromoteEmployee` yönteme geçirildiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b41c-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0b41c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b41c-113">See also</span></span>

- [<span data-ttu-id="0b41c-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="0b41c-114">Exceptions</span></span>](index.md)
