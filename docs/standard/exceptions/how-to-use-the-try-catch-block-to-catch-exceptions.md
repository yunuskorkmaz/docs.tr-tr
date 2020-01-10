---
title: 'Nasıl yapılır: özel durumları yakalamak için try-catch bloğunu kullanma'
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708472"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="c08c0-102">Özel durumları yakalamak için try/catch bloğunu kullanma</span><span class="sxs-lookup"><span data-stu-id="c08c0-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="c08c0-103">`try` bloğunda bir özel durum oluşturabilen veya oluşturabilen herhangi bir kod deyimini yerleştirin ve `try` bloğunun altındaki bir veya daha fazla `catch` bloğunda özel durumu veya özel durumları işlemek için kullanılan deyimleri yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c08c0-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="c08c0-104">Her `catch` bloğu özel durum türünü içerir ve bu özel durum türünü işlemek için gereken ek deyimler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c08c0-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="c08c0-105">Aşağıdaki örnekte, bir <xref:System.IO.StreamReader> *Data. txt* adlı bir dosya açar ve dosyadan bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="c08c0-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="c08c0-106">Kod üç özel durum oluşturmasından dolayı, bu bir `try` bloğuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c08c0-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="c08c0-107">Üç `catch` blok, özel durumları yakalar ve sonuçları konsola görüntüleyerek işler.</span><span class="sxs-lookup"><span data-stu-id="c08c0-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="c08c0-108">Ortak dil çalışma zamanı (CLR), `catch` blokları tarafından işlenmeyen özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="c08c0-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="c08c0-109">CLR tarafından bir özel durum yakalanmışsa, CLR yapılandırmanıza bağlı olarak aşağıdaki sonuçlardan biri ortaya çıkabilir:</span><span class="sxs-lookup"><span data-stu-id="c08c0-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="c08c0-110">**Hata ayıklama** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c08c0-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="c08c0-111">Program yürütmeyi durduruyor ve özel durum bilgileri içeren bir iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="c08c0-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="c08c0-112">Bir hata [Standart hata çıkış akışına](xref:System.Console.Error)yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="c08c0-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="c08c0-113">Çoğu kod bir özel durum oluşturabilir ve <xref:System.OutOfMemoryException>gibi bazı özel durumlar herhangi bir zamanda CLR tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c08c0-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="c08c0-114">Uygulamalar bu özel durumlarla uğraşmak zorunda olmasa da, diğer kullanıcılar tarafından kullanılacak kitaplıkları yazma olasılıklarının farkında olun.</span><span class="sxs-lookup"><span data-stu-id="c08c0-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="c08c0-115">`try` bloğundaki kodun ne zaman ayarlanacağı hakkında öneriler için bkz. [özel durumlar Için En Iyi uygulamalar](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c08c0-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c08c0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c08c0-116">See also</span></span>

- [<span data-ttu-id="c08c0-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="c08c0-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="c08c0-118">.NET 'te g/ç hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="c08c0-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
