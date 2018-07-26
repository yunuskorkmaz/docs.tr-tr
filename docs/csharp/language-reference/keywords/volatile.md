---
title: volatile (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936884"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="d30f4-102">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d30f4-102">volatile (C# Reference)</span></span>
<span data-ttu-id="d30f4-103">`volatile` Anahtar sözcüğü gösteren bir alan, aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d30f4-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="d30f4-104">Bildirilen alanları `volatile` olan tek bir iş parçacığı tarafından erişim varsayar derleyici iyileştirmeleri değil tabidir.</span><span class="sxs-lookup"><span data-stu-id="d30f4-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="d30f4-105">Bu kısıtlamalar, tüm iş parçacıkları tarafından gerçekleştirilen sırada başka bir iş parçacığı tarafından gerçekleştirilen geçici yazma dikkate aldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d30f4-105">These restrictions ensure that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="d30f4-106">Bir tek toplam geçici yazma olarak görülen yürütme tüm iş parçacıklarından sıralama garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d30f4-106">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>  
  
 <span data-ttu-id="d30f4-107">`volatile` Değiştiricisi kullanmadan birden çok iş parçacığı tarafından erişilebilir bir alan için kullanılan genellikle [kilit](../../../csharp/language-reference/keywords/lock-statement.md) deyimi erişim serileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="d30f4-107">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="d30f4-108">`volatile` Anahtar sözcüğü, bu tür alanlar için uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="d30f4-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="d30f4-109">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="d30f4-109">Reference types.</span></span>  
  
-   <span data-ttu-id="d30f4-110">İşaretçi türleri (güvenli olmayan bir bağlamda).</span><span class="sxs-lookup"><span data-stu-id="d30f4-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="d30f4-111">İşaretçi geçici olabilir, ancak işaret nesnesi dönüştürülemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d30f4-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="d30f4-112">Diğer bir deyişle, "işaretçisi geçici." bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d30f4-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="d30f4-113">Sbyte, byte, kısa, ushort, int, uint, char, float ve bool gibi türler.</span><span class="sxs-lookup"><span data-stu-id="d30f4-113">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="d30f4-114">Aşağıdaki temel türlerden birine sahip bir sabit listesi türü: byte, sbyte, short, ushort, int veya uint.</span><span class="sxs-lookup"><span data-stu-id="d30f4-114">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="d30f4-115">Başvuru türleri olarak bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d30f4-115">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="d30f4-116"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="d30f4-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="d30f4-117">Volatile anahtar sözcüğü, yalnızca bir sınıfın veya yapının alanlarına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d30f4-117">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="d30f4-118">Yerel değişkenler bildirilemez `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d30f4-118">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d30f4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d30f4-119">Example</span></span>  
 <span data-ttu-id="d30f4-120">Aşağıdaki örnek, bir ortak alan değişken olarak bildirmek gösterilmektedir `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d30f4-120">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d30f4-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d30f4-121">Example</span></span>  
 <span data-ttu-id="d30f4-122">Aşağıdaki örnek nasıl yardımcı veya çalışan iş parçacığı oluşturulabilir ve birincil iş parçacığının ile paralel işleme gerçekleştirmek için kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="d30f4-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="d30f4-123">Arka plan bilgileri için çoklu iş parçacığı hakkında bkz: [yönetilen iş parçacığı](../../../standard/threading/index.md) ve [parçacıkları (C#)](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="d30f4-123">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d30f4-124">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d30f4-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d30f4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d30f4-125">See Also</span></span>  
 [<span data-ttu-id="d30f4-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d30f4-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d30f4-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d30f4-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d30f4-128">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d30f4-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d30f4-129">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d30f4-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
