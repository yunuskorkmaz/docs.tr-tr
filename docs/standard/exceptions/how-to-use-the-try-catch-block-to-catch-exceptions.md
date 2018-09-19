---
title: 'Nasıl yapılır: özel durumları yakalamak için Try-Catch bloğu kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45999081"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="ebd37-102">Özel durumları yakalamak için try/catch bloğu kullanma</span><span class="sxs-lookup"><span data-stu-id="ebd37-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="ebd37-103">Özel durum oluşturma olasılığı olan kod bölümlerini yerleştirileceği bir `try` özel durumları işleyen bloğu ve yerde kodu bir `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="ebd37-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="ebd37-104">`catch` Bloğudur bir dizi deyim anahtar sözcüğü ile başlayan `catch`ve ardından bir özel durum türünü ve bir eylem gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ebd37-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="ebd37-105">Aşağıdaki kod örneğinde bir `try` / `catch` olası bir özel durum yakalamak için blok.</span><span class="sxs-lookup"><span data-stu-id="ebd37-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="ebd37-106">`Main` Yöntemi içeren bir `try` ile engelleyecek bir <xref:System.IO.StreamReader> adlı bir veri dosyası açılır deyimi `data.txt` ve dosyanın bir dize yazar.</span><span class="sxs-lookup"><span data-stu-id="ebd37-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="ebd37-107">Aşağıdaki `try` bloğu bir `catch` oluşur herhangi bir özel durumu yakalar blok `try` blok.</span><span class="sxs-lookup"><span data-stu-id="ebd37-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="ebd37-108">Ortak dil çalışma zamanı bir catch bloğu tarafından yakalandı özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="ebd37-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="ebd37-109">Çalışma zamanının nasıl yapılandırdığına bağlı olarak hata ayıklama iletişim kutusu görüntülenirse, program yürütme durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görünür veya bir hata stderr biçiminde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="ebd37-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="ebd37-110">Hemen hemen her kod satırının bir özel durum, özellikle ortak dil çalışma zamanı tarafından kendisi gibi attığı özel durumları oluşabilir <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="ebd37-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="ebd37-111">Uygulamaların çoğu bu özel durumlar gerekmez, ancak, başkaları tarafından kullanılacak kitaplıkları yazarken bu olasılığını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebd37-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="ebd37-112">Öneriler ne zaman bir Try bloğu içinde kod için bkz: [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ebd37-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd37-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebd37-113">See also</span></span>

- [<span data-ttu-id="ebd37-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ebd37-114">Exceptions</span></span>](index.md)
