---
title: 'Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma'
description: Özel durum tetiklemeli veya oluşturabilen deyimler içermesi için try bloğunu kullanın. Bir veya daha fazla catch bloklarında özel durumları işlemek için deyimler koyun.
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
ms.openlocfilehash: 60ed213ea777fe35873fd1e67555b7506e3ca587
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768917"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="f1444-104">Özel durumları yakalamak için try/catch bloğunu kullanma</span><span class="sxs-lookup"><span data-stu-id="f1444-104">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="f1444-105">Bir blok içinde özel durum oluşturabilen veya oluşturabilen herhangi bir kod deyimini yerleştirin `try` ve bir veya daha fazla blok altındaki bir veya daha fazla blok içindeki özel durumu veya özel durumları işlemek için kullanılan deyimleri yerleştirebilirsiniz `catch` `try` .</span><span class="sxs-lookup"><span data-stu-id="f1444-105">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="f1444-106">Her `catch` bir blok özel durum türünü içerir ve bu özel durum türünü işlemek için gereken ek deyimler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f1444-106">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="f1444-107">Aşağıdaki örnekte, <xref:System.IO.StreamReader> *data.txt* adlı bir dosya açılır ve dosyadan bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="f1444-107">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="f1444-108">Kod üç özel durum oluşturmasından dolayı bir blok içine yerleştirilir `try` .</span><span class="sxs-lookup"><span data-stu-id="f1444-108">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="f1444-109">Üç `catch` blok özel durumları yakalar ve sonuçları konsola görüntüleyerek işler.</span><span class="sxs-lookup"><span data-stu-id="f1444-109">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="f1444-110">Ortak dil çalışma zamanı (CLR), bloklar tarafından işlenmeyen özel durumları yakalar `catch` .</span><span class="sxs-lookup"><span data-stu-id="f1444-110">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="f1444-111">CLR tarafından bir özel durum yakalanmışsa, CLR yapılandırmanıza bağlı olarak aşağıdaki sonuçlardan biri ortaya çıkabilir:</span><span class="sxs-lookup"><span data-stu-id="f1444-111">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="f1444-112">**Hata ayıklama** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f1444-112">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="f1444-113">Program yürütmeyi durduruyor ve özel durum bilgileri içeren bir iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="f1444-113">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="f1444-114">Bir hata [Standart hata çıkış akışına](xref:System.Console.Error)yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="f1444-114">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="f1444-115">Çoğu kod bir özel durum oluşturabilir ve gibi bazı özel durumlar <xref:System.OutOfMemoryException> herhangi bir zamanda CLR tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f1444-115">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="f1444-116">Uygulamalar bu özel durumlarla uğraşmak zorunda olmasa da, diğer kullanıcılar tarafından kullanılacak kitaplıkları yazma olasılıklarının farkında olun.</span><span class="sxs-lookup"><span data-stu-id="f1444-116">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="f1444-117">Bir bloktaki kodun ne zaman ayarlanacağı hakkında öneriler için `try` bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f1444-117">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1444-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1444-118">See also</span></span>

- [<span data-ttu-id="f1444-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f1444-119">Exceptions</span></span>](index.md)
- [<span data-ttu-id="f1444-120">.NET 'te g/ç hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="f1444-120">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
