---
title: Güvenli Olmayan Kod ve İşaretçiler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331610"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="6b8a8-102">Güvenli Olmayan Kod ve İşaretçiler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6b8a8-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="6b8a8-103">Tür güvenliği ve güvenliğini korumak için C# işaretçi aritmetiği, varsayılan olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="6b8a8-104">Kullanarak ancak [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü, işaretçileri kullanılabilecek güvenli olmayan bir bağlam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="6b8a8-105">İşaretçiler hakkında daha fazla bilgi için Ek Yardım konusuna [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="6b8a8-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b8a8-106">Ortak dil çalışma zamanı (CLR), güvenli olmayan kod doğrulanamayan kodu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="6b8a8-107">C# güvenli olmayan kod mutlaka tehlikeli değildir; Bu, güvenlik CLR tarafından doğrulanıp doğrulanamadığını yalnızca kodudur.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="6b8a8-108">Tam güvenilen bir derlemede ise CLR bu nedenle güvenli olmayan kod yalnızca yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="6b8a8-109">Güvenli olmayan kod kullanın, kodunuzu güvenlik riskleri veya işaretçi hataları sunmaz sağlamak sizin sorumluluğunuzdadır olur.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="6b8a8-110">Güvenli Olmayan Koda Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6b8a8-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="6b8a8-111">Güvenli olmayan kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6b8a8-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="6b8a8-112">Yöntemleri, türleri ve kod blokları güvenilmez olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="6b8a8-113">Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimleri kaldırarak bir uygulamanın performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="6b8a8-114">Güvenli olmayan kod işaretçileri gerektiren yerel işlevleri çağırma durumlarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="6b8a8-115">Güvenli olmayan kod kullanarak güvenlik ve kararlılık risklerini de beraberinde getirir.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="6b8a8-116">Güvenli olmayan kod derlemek C# sırada uygulama ile derlenmelidir [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="6b8a8-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6b8a8-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6b8a8-117">Related Sections</span></span>  
 <span data-ttu-id="6b8a8-118">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="6b8a8-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="6b8a8-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="6b8a8-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="6b8a8-120">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="6b8a8-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="6b8a8-121">Nasıl yapılır: bir bayt dizisi kopyalamak için işaretçiler kullanma</span><span class="sxs-lookup"><span data-stu-id="6b8a8-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="6b8a8-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="6b8a8-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6b8a8-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6b8a8-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b8a8-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b8a8-124">See Also</span></span>  
 [<span data-ttu-id="6b8a8-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6b8a8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
