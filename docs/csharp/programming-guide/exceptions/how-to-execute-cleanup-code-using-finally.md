---
title: 'Nasıl yapılır: Finally Anahtar Sözcüğünü Kullanarak Temizleme Kodu Yürütme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 948281af45d04714ed6fc308b60341e87abeb830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331714"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="ad6b8-102">Nasıl yapılır: Finally Anahtar Sözcüğünü Kullanarak Temizleme Kodu Yürütme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ad6b8-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="ad6b8-103">Amacı bir `finally` açıklamadır bir özel durum olsa bile nesneleri, dış kaynaklara bulunduran genellikle gerekli temizlenmesi hemen gerçekleşmesini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="ad6b8-104">Bu tür temizleme bir örneği çağırma <xref:System.IO.Stream.Close%2A> üzerinde bir <xref:System.IO.FileStream> nesnesi gibi ortak dil çalışma zamanı tarafından toplanacak beklemek yerine hemen kullandıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="ad6b8-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ad6b8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad6b8-105">Example</span></span>  
 <span data-ttu-id="ad6b8-106">Önceki koda açmak için bir `try-catch-finally` deyimi, kodu temizleme ayrılmış çalışma koddan gibi.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 <span data-ttu-id="ad6b8-107">Özel bir durum içinde herhangi bir zamanda olabileceği için `try` önce engelle `OpenWrite()` çağrısı, veya `OpenWrite()` çağrı kendisini başarısız, biz kapatmak denediğinizde dosyanın açık olduğunu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="ad6b8-108">`finally` Bloğu ekler emin olmak için bir onay <xref:System.IO.FileStream> nesnesi değil `null` çağırmadan önce <xref:System.IO.Stream.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="ad6b8-109">Olmadan `null` denetleyin, `finally` blok throw kendi <xref:System.NullReferenceException>, ancak özel durumları atma `finally` mümkünse blokları kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="ad6b8-110">Bir veritabanı bağlantısı başka bir iyi kapalı için adaydır bir `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="ad6b8-111">Bir veritabanı sunucusu için izin verilen bağlantı sayısının bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olan en kısa sürede kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="ad6b8-112">Bağlantınızı kapatmadan önce bir özel durum, bu başka bir örneği ise kullanarak burada `finally` blok atık toplama için bekleyen daha iyi.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6b8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad6b8-113">See Also</span></span>  
 [<span data-ttu-id="ad6b8-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ad6b8-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ad6b8-115">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ad6b8-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="ad6b8-116">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ad6b8-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="ad6b8-117">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="ad6b8-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
 [<span data-ttu-id="ad6b8-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="ad6b8-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="ad6b8-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="ad6b8-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="ad6b8-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="ad6b8-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
