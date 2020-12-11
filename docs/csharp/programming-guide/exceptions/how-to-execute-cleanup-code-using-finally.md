---
title: Finally-C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
description: "' Finally ' ifadesini kullanarak Temizleme kodunu yürütmeyi öğrenin. Finally deyimleri, tüm gerekli nesne temizleme işleminin hemen gerçekleşmesini güvence altına aldığından emin olur."
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110188"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="c9b7e-104">Finally kullanarak temizleme kodu yürütme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c9b7e-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="c9b7e-105">Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="c9b7e-106">Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:</span><span class="sxs-lookup"><span data-stu-id="c9b7e-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a><span data-ttu-id="c9b7e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9b7e-107">Example</span></span>

<span data-ttu-id="c9b7e-108">Önceki kodu bir ifadeye dönüştürmek için `try-catch-finally` , temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

<span data-ttu-id="c9b7e-109">Bir özel durum, çağrıdan önce blok içinde herhangi bir zamanda olabileceği `try` `OpenWrite()` veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğunu garanti etmedik.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we aren't guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="c9b7e-110">`finally`Blok, <xref:System.IO.FileStream> `null` yöntemi çağırmadan önce nesnenin olmadığından emin olmak için bir denetim ekler <xref:System.IO.Stream.Close%2A> .</span><span class="sxs-lookup"><span data-stu-id="c9b7e-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object isn't `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="c9b7e-111">Denetim olmadan, `null` `finally` blok kendi kendine fırlatabilir <xref:System.NullReferenceException> , ancak mümkünse özel durumların atma `finally` yapılabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it's possible.</span></span>

<span data-ttu-id="c9b7e-112">Veritabanı bağlantısı, bir blokta kapanmakta olan başka bir adaydır `finally` .</span><span class="sxs-lookup"><span data-stu-id="c9b7e-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="c9b7e-113">Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="c9b7e-114">Bağlantınızı kapatabilmeniz için önce bir özel durum oluşturulursa, `finally` blok kullanmak çöp toplama için beklerken daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-114">If an exception is thrown before you can close your connection, using the `finally` block is better than waiting for garbage collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9b7e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9b7e-115">See also</span></span>

- [<span data-ttu-id="c9b7e-116">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="c9b7e-116">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="c9b7e-117">try-catch</span><span class="sxs-lookup"><span data-stu-id="c9b7e-117">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="c9b7e-118">try-finally</span><span class="sxs-lookup"><span data-stu-id="c9b7e-118">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="c9b7e-119">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="c9b7e-119">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
