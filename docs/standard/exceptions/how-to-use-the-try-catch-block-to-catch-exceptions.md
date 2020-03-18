---
title: 'Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma'
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708472"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="f5885-102">Özel durumları yakalamak için try/catch bloğu nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f5885-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="f5885-103">Bir `try` blokta özel durum yükseltebilecek veya atabilecek kod deyimlerini yerleştirin ve özel durum `catch` veya özel `try` durumları işlemek için kullanılan deyimleri bloğun altındaki bir veya daha fazla bloka yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f5885-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="f5885-104">Her `catch` blok özel durum türünü içerir ve bu özel durum türünü işlemek için gereken ek deyimler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f5885-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="f5885-105">Aşağıdaki örnekte, <xref:System.IO.StreamReader> *data.txt* adlı bir dosya açılır ve dosyadan bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="f5885-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="f5885-106">Kod üç özel durumdan herhangi birini atabileceğinden, `try` bir blota yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5885-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="f5885-107">Üç `catch` blok özel durumları yakalar ve sonuçları konsola göstererek bunları işler.</span><span class="sxs-lookup"><span data-stu-id="f5885-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="f5885-108">Ortak Dil Çalışma Süresi (CLR), bloklar `catch` tarafından işlenmemiş özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="f5885-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="f5885-109">CLR tarafından bir özel durum yakalanırsa, CLR yapılandırmanıza bağlı olarak aşağıdaki sonuçlardan biri oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="f5885-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="f5885-110">Hata **Ayıklama** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5885-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="f5885-111">Program yürütmeyi durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5885-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="f5885-112">Standart [hata çıktı akışına](xref:System.Console.Error)bir hata yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f5885-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="f5885-113">Çoğu kod bir özel durum atabilir <xref:System.OutOfMemoryException>ve clr kendisi tarafından herhangi bir zamanda atılabilir gibi bazı özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="f5885-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="f5885-114">Bu özel durumlarla başa çıkmak için uygulamalar aranmazken, kitaplıkyazarken başkaları tarafından kullanılma olasılığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f5885-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="f5885-115">Bir `try` blokta kod ayarlamanın ne zaman ayarlanacaklarına ilişkin öneriler [için, Özel Durumlar için En İyi Uygulamalar'a](best-practices-for-exceptions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f5885-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5885-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5885-116">See also</span></span>

- [<span data-ttu-id="f5885-117">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f5885-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="f5885-118">.NET'teki G/Ç hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="f5885-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
