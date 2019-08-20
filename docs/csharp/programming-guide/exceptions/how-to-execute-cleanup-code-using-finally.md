---
title: 'Nasıl yapılır: Son C# programlama kılavuzunu kullanarak temizlik kodu yürütme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590252"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="ecd57-102">Nasıl yapılır: Son kullanılan temizleme kodunu yürütme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ecd57-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="ecd57-103">Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ecd57-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="ecd57-104">Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> nesnenin ortak <xref:System.IO.FileStream> dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:</span><span class="sxs-lookup"><span data-stu-id="ecd57-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="ecd57-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecd57-105">Example</span></span>  
 <span data-ttu-id="ecd57-106">Önceki kodu bir `try-catch-finally` ifadeye dönüştürmek için, temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ecd57-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="ecd57-107">Bir özel durum, `try` `OpenWrite()` çağrıdan önce blok içinde herhangi bir zamanda olabileceği veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="ecd57-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="ecd57-108">Blok, <xref:System.IO.Stream.Close%2A> yöntemi çağırmadan önce <xref:System.IO.FileStream> nesnenin olmadığından `null` emin olmak için bir denetim ekler. `finally`</span><span class="sxs-lookup"><span data-stu-id="ecd57-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="ecd57-109">Denetim olmadan, <xref:System.NullReferenceException>blok kendi kendine oluşturabilir, ancak mümkünse özel durumların `finally` atma işlemi mümkünse kaçınılmalıdır. `finally` `null`</span><span class="sxs-lookup"><span data-stu-id="ecd57-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="ecd57-110">Veritabanı bağlantısı, bir `finally` blokta kapanmakta olan başka bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="ecd57-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="ecd57-111">Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecd57-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="ecd57-112">Bağlantınızı kapatabilmeniz için önce bir özel durum oluşursa, bu, `finally` bloğu kullanmanın çöp toplama beklerken daha iyi bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="ecd57-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd57-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd57-113">See also</span></span>

- [<span data-ttu-id="ecd57-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ecd57-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ecd57-115">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ecd57-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="ecd57-116">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ecd57-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="ecd57-117">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="ecd57-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="ecd57-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="ecd57-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="ecd57-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="ecd57-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="ecd57-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="ecd57-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
