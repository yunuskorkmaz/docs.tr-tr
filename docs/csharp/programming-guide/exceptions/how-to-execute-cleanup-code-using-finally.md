---
title: Son C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705281"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="afaaa-102">Son kullanılan temizleme kodunu yürütme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="afaaa-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="afaaa-103">Bir `finally` ifadesinin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="afaaa-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="afaaa-104">Bu tür bir temizlik örneği, nesnenin ortak dil çalışma zamanı tarafından atık olarak toplanmasını beklemek yerine, bir <xref:System.IO.FileStream> hemen sonrasında <xref:System.IO.Stream.Close%2A>, aşağıdaki gibi çağırıyor:</span><span class="sxs-lookup"><span data-stu-id="afaaa-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="afaaa-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="afaaa-105">Example</span></span>  
 <span data-ttu-id="afaaa-106">Önceki kodu bir `try-catch-finally` ifadesine dönüştürmek için, temizleme kodu aşağıdaki gibi çalışma kodundan ayrılır.</span><span class="sxs-lookup"><span data-stu-id="afaaa-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="afaaa-107">`OpenWrite()` çağrısından önce `try` bloğunda herhangi bir zamanda bir özel durum gerçekleşebildiğinden veya `OpenWrite()` çağrısı başarısız olursa, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="afaaa-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="afaaa-108">`finally` bloğu, <xref:System.IO.Stream.Close%2A> yöntemini çağırmadan önce <xref:System.IO.FileStream> nesnesinin `null` olmadığından emin olmak için bir denetim ekler.</span><span class="sxs-lookup"><span data-stu-id="afaaa-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="afaaa-109">`null` denetimi olmadan `finally` bloğu kendi <xref:System.NullReferenceException>oluşturabilir, ancak mümkünse `finally` bloklardaki özel durumların oluşturulması kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afaaa-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="afaaa-110">Veritabanı bağlantısı, `finally` bloğunda kapanmakta olan başka bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="afaaa-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="afaaa-111">Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="afaaa-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="afaaa-112">Bağlantınızı kapatabilmeniz için önce bir özel durum oluşturulursa, bu, `finally` bloğunun kullanımı çöp toplama işleminin daha iyi olduğu bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="afaaa-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afaaa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afaaa-113">See also</span></span>

- [<span data-ttu-id="afaaa-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="afaaa-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="afaaa-115">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="afaaa-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="afaaa-116">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="afaaa-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="afaaa-117">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="afaaa-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="afaaa-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="afaaa-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="afaaa-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="afaaa-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="afaaa-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="afaaa-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
