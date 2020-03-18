---
title: Nasıl nihayet kullanarak temizleme kodu yürütmek için - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705281"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="1d05c-102">Son olarak kullanarak temizleme kodu nasıl çalıştırılatır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1d05c-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="1d05c-103">Bir `finally` deyimin amacı, genellikle dış kaynak tutan nesnelerin gerekli şekilde temizlenmesinin, bir özel durum atılsa bile hemen gerçekleşmesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1d05c-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="1d05c-104">Bu tür bir temizleme <xref:System.IO.Stream.Close%2A> örneği, <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından toplanan çöp olmasını beklemek yerine kullanımdan hemen sonra aşağıdaki gibi çağrı yapmaktır:</span><span class="sxs-lookup"><span data-stu-id="1d05c-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="1d05c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d05c-105">Example</span></span>  
 <span data-ttu-id="1d05c-106">Önceki kodu bir `try-catch-finally` deyime dönüştürmek için, temizleme kodu aşağıdaki gibi çalışma kodundan ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1d05c-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="1d05c-107">Aramadan önce `try` blok içinde herhangi bir zamanda bir `OpenWrite()` özel durum oluşabileceğinden veya aramanın kendisi başarısız olabileceğinden, kapatmaya çalıştığımızda dosyanın açık olduğu garanti edilmez. `OpenWrite()`</span><span class="sxs-lookup"><span data-stu-id="1d05c-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="1d05c-108">Blok, `finally` <xref:System.IO.FileStream> <xref:System.IO.Stream.Close%2A> yöntemi çağırmadan önce nesnenin `null` olmadığından emin olmak için bir denetim ekler.</span><span class="sxs-lookup"><span data-stu-id="1d05c-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="1d05c-109">`null` Kontrol olmadan, `finally` blok kendi <xref:System.NullReferenceException>atabilir, ancak mümkünse bloklarda `finally` özel durumlar atma kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d05c-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="1d05c-110">Veritabanı bağlantısı, bir blokta kapatılması `finally` için iyi bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="1d05c-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="1d05c-111">Veritabanı sunucusuna izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca çabuk kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d05c-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="1d05c-112">Bağlantınızı kapatmadan önce bir özel durum atılırsa, bu, bloğu kullanmanın `finally` çöp toplamayı beklemekten daha iyi olduğu başka bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="1d05c-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d05c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d05c-113">See also</span></span>

- [<span data-ttu-id="1d05c-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d05c-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1d05c-115">Özel Durumlar ve Özel Durum Kullanımı</span><span class="sxs-lookup"><span data-stu-id="1d05c-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="1d05c-116">Özel Durum Taşıma</span><span class="sxs-lookup"><span data-stu-id="1d05c-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="1d05c-117">Ekstresi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="1d05c-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="1d05c-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="1d05c-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="1d05c-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="1d05c-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="1d05c-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="1d05c-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
