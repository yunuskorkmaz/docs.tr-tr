---
title: "Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ebc59035140ff0464cd959129fdf48a4e9a269f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="75637-102">Catch bloğunda belirli özel durumların kullanma</span><span class="sxs-lookup"><span data-stu-id="75637-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="75637-103">Genel olarak, belirli bir özel durum türünü catch yerine temel kullanmak için uygulama programlama iyi `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="75637-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="75637-104">Özel durum oluştuğunda yığını geçirilir ve her catch bloğu, işleme fırsatına verilir.</span><span class="sxs-lookup"><span data-stu-id="75637-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="75637-105">Catch deyimleri sıralama önemlidir.</span><span class="sxs-lookup"><span data-stu-id="75637-105">The order of catch statements is important.</span></span> <span data-ttu-id="75637-106">Catch blokları belirli özel durumların genel özel durum yakalama bloğunu veya derleyici hata verecek önce hedeflenen yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="75637-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="75637-107">Uygun catch bloğu adı özel durumu catch bloğunda belirtilen özel durum türünü eşleşen tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="75637-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="75637-108">Hiçbir özel catch bloğu varsa, özel durum varsa, genel catch bloğu tarafından yakalandı.</span><span class="sxs-lookup"><span data-stu-id="75637-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="75637-109">Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="75637-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="75637-110">Adlı bir sınıf bir örnek oluşturur `Employee` ile tek bir özelliği, çalışan düzeyi (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="75637-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="75637-111">Yöntemi, bir `PromoteEmployee`, nesneyi alır ve çalışan düzeyini artırır.</span><span class="sxs-lookup"><span data-stu-id="75637-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="75637-112">Bir <xref:System.InvalidCastException> oluşur, bir <xref:System.DateTime> örneği iletilir `PromoteEmployee` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75637-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="75637-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75637-113">See Also</span></span>  
[<span data-ttu-id="75637-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="75637-114">Exceptions</span></span>](index.md)
