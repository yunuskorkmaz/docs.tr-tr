---
title: Finally-C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
description: "' Finally ' ifadesini kullanarak Temizleme kodunu yürütmeyi öğrenin. Finally deyimleri, tüm gerekli nesne temizleme işleminin hemen gerçekleşmesini güvence altına aldığından emin olur."
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 148c1f9fba67659a07c667bb15619d6f3f7c3b2f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302028"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="8bbc7-104">Finally kullanarak temizleme kodu yürütme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8bbc7-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="8bbc7-105">Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="8bbc7-106">Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:</span><span class="sxs-lookup"><span data-stu-id="8bbc7-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="8bbc7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bbc7-107">Example</span></span>  
 <span data-ttu-id="8bbc7-108">Önceki kodu bir ifadeye dönüştürmek için `try-catch-finally` , temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="8bbc7-109">Bir özel durum, çağrıdan önce blok içinde herhangi bir zamanda olabileceği `try` `OpenWrite()` veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="8bbc7-110">`finally`Blok, <xref:System.IO.FileStream> `null` yöntemi çağırmadan önce nesnenin olmadığından emin olmak için bir denetim ekler <xref:System.IO.Stream.Close%2A> .</span><span class="sxs-lookup"><span data-stu-id="8bbc7-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="8bbc7-111">Denetim olmadan, `null` `finally` blok kendi kendine oluşturabilir <xref:System.NullReferenceException> , ancak mümkünse özel durumların atma `finally` işlemi mümkünse kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="8bbc7-112">Veritabanı bağlantısı, bir blokta kapanmakta olan başka bir adaydır `finally` .</span><span class="sxs-lookup"><span data-stu-id="8bbc7-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="8bbc7-113">Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="8bbc7-114">Bağlantınızı kapatabilmeniz için önce bir özel durum oluşursa, bu, `finally` bloğu kullanmanın çöp toplama beklerken daha iyi bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbc7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bbc7-115">See also</span></span>

- [<span data-ttu-id="8bbc7-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8bbc7-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8bbc7-117">Özel durumlar ve özel durum Işleme</span><span class="sxs-lookup"><span data-stu-id="8bbc7-117">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="8bbc7-118">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="8bbc7-118">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="8bbc7-119">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="8bbc7-119">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="8bbc7-120">try-catch</span><span class="sxs-lookup"><span data-stu-id="8bbc7-120">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="8bbc7-121">try-finally</span><span class="sxs-lookup"><span data-stu-id="8bbc7-121">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="8bbc7-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="8bbc7-122">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
