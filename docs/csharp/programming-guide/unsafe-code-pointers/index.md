---
title: Güvenli olmayan kod ve işaretçiler - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959486"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="0b2c2-102">Güvenli olmayan kod ve işaretçiler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0b2c2-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="0b2c2-103">Tür güvenliği ve emniyeti korumak için C# işaretçi aritmetik, varsayılan olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="0b2c2-104">Kullanarak ancak [güvenli](../../language-reference/keywords/unsafe.md) anahtar sözcüğü, işaretçileri kullanılabilecek güvenli olmayan bir bağlam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="0b2c2-105">İşaretçiler hakkında daha fazla bilgi için bkz. [işaretçi türleri](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="0b2c2-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b2c2-106">Ortak dil çalışma zamanı (CLR), güvenli olmayan kod, doğrulanamayan kodu adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="0b2c2-107">C# güvenli olmayan kod tehlikeli olmak zorunda değildir; Bu, güvenlik CLR tarafından doğrulanamıyor yalnızca kodudur.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="0b2c2-108">Tam olarak güvenilen bir derlemede ise CLR bu nedenle güvenli olmayan kod yalnızca yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="0b2c2-109">Güvenli olmayan kod kullanın, kodunuz güvenlik riskleri veya işaretçi hataları sunmaz sağlamak sizin sorumluluğunuzdadır olur.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="0b2c2-110">Güvenli olmayan koda genel bakış</span><span class="sxs-lookup"><span data-stu-id="0b2c2-110">Unsafe code overview</span></span>

<span data-ttu-id="0b2c2-111">Güvenli olmayan kod, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0b2c2-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="0b2c2-112">Yöntemleri, türleri ve kod blokları güvenli olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="0b2c2-113">Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimleri kaldırarak bir uygulamanın performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="0b2c2-114">İşaretçileri gerektiren yerel işlevler çağırdığınızda, güvenli olmayan kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="0b2c2-115">Güvenli olmayan kod kullanarak güvenlik ve sağlamlık risklerini de beraberinde getirir.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="0b2c2-116">Güvenli olmayan bloklar içeren kod ile derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="0b2c2-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="0b2c2-117">Related sections</span></span>

<span data-ttu-id="0b2c2-118">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="0b2c2-118">For more information, see:</span></span>

- [<span data-ttu-id="0b2c2-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="0b2c2-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="0b2c2-120">Sabit boyutlu arabellekler</span><span class="sxs-lookup"><span data-stu-id="0b2c2-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="0b2c2-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0b2c2-121">C# language specification</span></span>

<span data-ttu-id="0b2c2-122">Daha fazla bilgi için [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) konuyu [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0b2c2-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b2c2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b2c2-123">See also</span></span>

- [<span data-ttu-id="0b2c2-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b2c2-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0b2c2-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="0b2c2-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
