---
title: Güvenli olmayan kod ve işaretçiler-C# Programlama Kılavuzu
description: Güvenli olmayan kod ve işaretçiler hakkında bilgi edinin. C# işaretçileri desteklemez, ancak ' unsafe ' anahtar sözcüğüyle işaretçilerin kullanılabileceği güvenli olmayan bir bağlam tanımlayabilirsiniz.
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
ms.openlocfilehash: 4d624bdc8fc4a756f47d66c9dec6eba8c24a9d9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782396"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="34578-104">Güvenli olmayan kod ve işaretçiler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="34578-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="34578-105">Tür güvenliğini ve güvenliğini sağlamak için, C# varsayılan olarak işaretçi aritmetiğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="34578-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="34578-106">Ancak, [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanarak, işaretçilerin kullanılabileceği güvenli olmayan bir bağlam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34578-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="34578-107">İşaretçiler hakkında daha fazla bilgi için bkz. [işaretçi türleri](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="34578-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34578-108">Ortak dil çalışma zamanında (CLR), güvenli olmayan koda doğrulanamayan kod denir.</span><span class="sxs-lookup"><span data-stu-id="34578-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="34578-109">C# ' deki güvenli olmayan kodun tehlikeli olması gerekmez; yalnızca güvenliği CLR tarafından doğrulanamadığı bir koddur.</span><span class="sxs-lookup"><span data-stu-id="34578-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="34578-110">Bu nedenle, CLR yalnızca tam güvenilir bir derlemede olduğunda güvenli olmayan kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="34578-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="34578-111">Güvenli olmayan kod kullanıyorsanız, kodunuzun güvenlik riskleri veya işaretçi hataları içermediğinden emin olmak sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="34578-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="34578-112">Güvenli olmayan koda genel bakış</span><span class="sxs-lookup"><span data-stu-id="34578-112">Unsafe code overview</span></span>

<span data-ttu-id="34578-113">Güvenli olmayan kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="34578-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="34578-114">Yöntemler, türler ve kod blokları güvenli olmayan şekilde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="34578-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="34578-115">Bazı durumlarda, güvenli olmayan kod, dizi sınırları denetimlerini kaldırarak bir uygulamanın performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="34578-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="34578-116">İşaretçi gerektiren yerel işlevleri çağırdığınızda güvenli olmayan kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="34578-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="34578-117">Güvenli olmayan kod kullanmak güvenlik ve kararlılık riskleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="34578-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="34578-118">Güvenli olmayan bloklar içeren kodun [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="34578-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="34578-119">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="34578-119">Related sections</span></span>

<span data-ttu-id="34578-120">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="34578-120">For more information, see:</span></span>

- [<span data-ttu-id="34578-121">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="34578-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="34578-122">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="34578-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="34578-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="34578-123">C# language specification</span></span>

<span data-ttu-id="34578-124">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="34578-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="34578-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34578-125">See also</span></span>

- [<span data-ttu-id="34578-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="34578-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34578-127">olmayabilecek</span><span class="sxs-lookup"><span data-stu-id="34578-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
