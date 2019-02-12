---
title: 'Nasıl yapılır: Özel durumları yakalamak için Try-Catch bloğu kullanma'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092754"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="9e489-102">Özel durumları yakalamak için try/catch bloğu kullanma</span><span class="sxs-lookup"><span data-stu-id="9e489-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="9e489-103">Yükseltme veya bir özel durum herhangi bir kod deyim koyun bir `try` blok ve özel durum ya da bir veya daha fazla özel durumları işlemek için kullanılan bir yerde ifadeleri `catch` aşağıdaki blokları `try` blok.</span><span class="sxs-lookup"><span data-stu-id="9e489-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="9e489-104">Her `catch` blok özel durum türü içerir ve bu özel durum türü işlemek için gereken ek ifadeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9e489-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="9e489-105">Aşağıdaki örnekte, bir <xref:System.IO.StreamReader> adlı bir dosya açılır *data.txt* ve dosyasından bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="9e489-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="9e489-106">Kod herhangi üç özel durum fırlatabilir beri yerleştirilir bir `try` blok.</span><span class="sxs-lookup"><span data-stu-id="9e489-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="9e489-107">Üç `catch` bloğu özel durumları yakalamak ve bunları konsola sonuçları görüntüleyerek işlemek.</span><span class="sxs-lookup"><span data-stu-id="9e489-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="9e489-108">Ortak dil çalışma zamanı (CLR) tarafından işlenmemiş özel durumları yakalayan `catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="9e489-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="9e489-109">Bir özel durum CLR tarafından yakalandı, aşağıdaki sonuçlardan birini CLR yapılandırmanıza bağlı olarak oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="9e489-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="9e489-110">A **hata ayıklama** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9e489-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="9e489-111">Program yürütme durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9e489-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="9e489-112">Bir hata yazdırır [standart hata çıkış akışına](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="9e489-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="9e489-113">Çoğu kod gibi bazı özel durumlar ve özel durum oluşturabilecek <xref:System.OutOfMemoryException>, CLR tarafından herhangi bir anda atılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e489-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="9e489-114">Uygulamalar, bu özel durumlar için gerekli değildir, ancak başkaları tarafından kullanılacak kitaplıkları yazarken olasılığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9e489-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="9e489-115">Kod ne zaman öneriler için bir `try` engellemek için bkz: [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="9e489-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e489-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e489-116">See also</span></span>

[<span data-ttu-id="9e489-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9e489-117">Exceptions</span></span>](index.md)  
[<span data-ttu-id="9e489-118">. NET'te g/ç hataları işleme</span><span class="sxs-lookup"><span data-stu-id="9e489-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
