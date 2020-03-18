---
title: Güvenli olmayan kod ve işaretçiler - C# Programlama Kılavuzu
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
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711837"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="88461-102">Güvenli olmayan kod ve işaretçiler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="88461-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="88461-103">C# türü güvenliğini ve güvenliğini korumak için varsayılan olarak işaretçi aritmetiklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="88461-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="88461-104">Ancak, güvenli [olmayan](../../language-reference/keywords/unsafe.md) anahtar sözcüğü kullanarak, işaretçilerin kullanılabildiği güvenli olmayan bir bağlam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88461-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="88461-105">İşaretçiler hakkında daha fazla bilgi için [Işaretçi türlerine](pointer-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="88461-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88461-106">Ortak dil çalışma zamanında (CLR), güvenli olmayan kod doğrulanamayan kod olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="88461-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="88461-107">C#'daki güvenli olmayan kod mutlaka tehlikeli değildir; güvenliği CLR tarafından doğrulanamayan bir koddur.</span><span class="sxs-lookup"><span data-stu-id="88461-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="88461-108">Bu nedenle CLR, yalnızca tam olarak güvenilen bir derlemede yse güvenli olmayan kodu yürütecektir.</span><span class="sxs-lookup"><span data-stu-id="88461-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="88461-109">Güvenli olmayan kod kullanıyorsanız, kodunuzu güvenlik riskleri veya işaretçi hataları tanıtmak olmadığından emin olmak sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="88461-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="88461-110">Güvenli olmayan koda genel bakış</span><span class="sxs-lookup"><span data-stu-id="88461-110">Unsafe code overview</span></span>

<span data-ttu-id="88461-111">Güvenli olmayan kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="88461-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="88461-112">Yöntemler, türler ve kod blokları güvenli olmayan olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="88461-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="88461-113">Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimlerini kaldırarak bir uygulamanın performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="88461-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="88461-114">İşaretçiler gerektiren yerel işlevleri çağırdığınızda güvenli olmayan kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="88461-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="88461-115">Güvenli olmayan kod kullanmak güvenlik ve kararlılık risklerini doğurrreder.</span><span class="sxs-lookup"><span data-stu-id="88461-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="88461-116">Güvenli olmayan bloklar içeren kod [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği ile derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="88461-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="88461-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="88461-117">Related sections</span></span>

<span data-ttu-id="88461-118">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="88461-118">For more information, see:</span></span>

- [<span data-ttu-id="88461-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="88461-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="88461-120">Sabit boyut arabellekleri</span><span class="sxs-lookup"><span data-stu-id="88461-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="88461-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="88461-121">C# language specification</span></span>

<span data-ttu-id="88461-122">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Güvenli Olmayan kod](~/_csharplang/spec/unsafe-code.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="88461-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88461-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88461-123">See also</span></span>

- [<span data-ttu-id="88461-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="88461-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88461-125">Güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="88461-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
