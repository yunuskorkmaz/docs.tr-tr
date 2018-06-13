---
title: volatile (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 7f3aafc1255667f2a3917c6e171ce4ddf0343b41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272590"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="61519-102">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="61519-102">volatile (C# Reference)</span></span>
<span data-ttu-id="61519-103">`volatile` Anahtar sözcüğü gösteren bir alan aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="61519-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="61519-104">Bildirilen alanları `volatile` olan değil tek bir iş parçacığı tarafından erişim varsayın derleyici iyileştirmelerini tabidir.</span><span class="sxs-lookup"><span data-stu-id="61519-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="61519-105">Bu, en güncel değeri her zaman alanında mevcut olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="61519-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="61519-106">`volatile` Değiştiricisi kullanmadan birden çok iş parçacığı tarafından erişilen bir alan için kullanılan genellikle [kilit](../../../csharp/language-reference/keywords/lock-statement.md) erişim serileştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="61519-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="61519-107">`volatile` Anahtar sözcüğü bu tür alanlar için uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="61519-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="61519-108">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="61519-108">Reference types.</span></span>  
  
-   <span data-ttu-id="61519-109">İşaretçi türleri (güvenli olmayan içerik).</span><span class="sxs-lookup"><span data-stu-id="61519-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="61519-110">İşaretçi geçici olmasına karşın işaret nesnesi olamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61519-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="61519-111">Diğer bir deyişle, "için bir işaretçi geçici." bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="61519-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="61519-112">Sbyte, bayt, short, ushort, int, uint, char, float ve bool gibi türleri.</span><span class="sxs-lookup"><span data-stu-id="61519-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="61519-113">Aşağıdaki temel türlerinden biriyle bir numaralandırma türü: byte, sbyte, short, ushort, int veya uint.</span><span class="sxs-lookup"><span data-stu-id="61519-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="61519-114">Başvuru türleri olduğu bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="61519-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="61519-115"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="61519-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="61519-116">Volatile anahtar sözcüğü yalnızca bir sınıf veya yapı alanlar için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="61519-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="61519-117">Yerel değişkenler bildirilemez `volatile`.</span><span class="sxs-lookup"><span data-stu-id="61519-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61519-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="61519-118">Example</span></span>  
 <span data-ttu-id="61519-119">Aşağıdaki örnek, bir ortak alan değişken olarak bildirmek gösterilmiştir `volatile`.</span><span class="sxs-lookup"><span data-stu-id="61519-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="61519-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="61519-120">Example</span></span>  
 <span data-ttu-id="61519-121">Aşağıdaki örnekte nasıl yardımcı veya çalışan iş parçacığı oluşturulabilir ve birincil iş parçacığının ile paralel işleme gerçekleştirmek için kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="61519-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="61519-122">Arka plan bilgileri için hakkında çoklu iş parçacığı kullanımı, bkz: [parçacıkları (C#)](../../../standard/threading/index.md) ve [yönetilen iş parçacığı oluşturma](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="61519-122">For background information about multithreading, see [Threading (C#)](../../../standard/threading/index.md) and [Managed Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="61519-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="61519-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61519-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61519-124">See Also</span></span>  
 [<span data-ttu-id="61519-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="61519-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="61519-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61519-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="61519-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="61519-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="61519-128">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="61519-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
