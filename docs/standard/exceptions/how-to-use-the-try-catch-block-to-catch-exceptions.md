---
title: "Nasıl yapılır: özel durumları yakalamak için Try-Catch bloğu kullanın"
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
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 192f762872b112ea261d22251175db6867229437
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="73948-102">Özel durumları yakalamak için try/catch bloğu kullanma</span><span class="sxs-lookup"><span data-stu-id="73948-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="73948-103">Özel durumlar oluşturma kodun bölümlerini yerleştirin bir `try` özel durumları işleme bloğu ve Yerleştir kod bir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="73948-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="73948-104">`catch` Bloğu bir dizi anahtar sözcüğüyle başlayan deyimi `catch`, bir özel durum türünü ve bir eylem yapılması ardından.</span><span class="sxs-lookup"><span data-stu-id="73948-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="73948-105">Aşağıdaki kod örneğinde bir `try` / `catch` olası Özel catch bloğu.</span><span class="sxs-lookup"><span data-stu-id="73948-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="73948-106">`Main` Yöntemini içeren bir `try` ile engelleme bir <xref:System.IO.StreamReader> veri dosyasını açar deyimi adlı `data.txt` ve dosyasından bir dize yazar.</span><span class="sxs-lookup"><span data-stu-id="73948-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="73948-107">Aşağıdaki `try` bloğu bir `catch` oluşur özel durumları yakalar blok `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="73948-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="73948-108">Ortak dil çalışma zamanı catch bloğu tarafından yakalandı özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="73948-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="73948-109">Çalışma zamanı nasıl yapılandırıldığına bağlı olarak hata ayıklama iletişim kutusu görüntülenirse, programın yürütülmesi durdurulur ve özel durum bilgilerini içeren bir iletişim kutusu görünür veya STDERR'e bir hata yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="73948-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="73948-110">Neredeyse her kod satırının bir özel durum, özellikle ortak dil çalışma zamanı tarafından kendisine gibi oluşturulan özel durumlara neden olabilir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="73948-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="73948-111">Uygulamaların çoğu bu durumlarla başa gerekmez, ancak, başkaları tarafından kullanılacak kitaplıkları yazılırken bu olasılığını dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="73948-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="73948-112">Öneriler zaman ayarlamak bir Try bloğunda kod için bkz: [özel durumlar için en iyi uygulamaları](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="73948-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73948-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73948-113">See Also</span></span>  
[<span data-ttu-id="73948-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="73948-114">Exceptions</span></span>](index.md)
