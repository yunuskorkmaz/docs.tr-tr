---
title: ?? Operator - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 153accdc4995065563b00da0fd62992341c06cf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241885"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6f7ee-103">??</span><span class="sxs-lookup"><span data-stu-id="6f7ee-103">??</span></span> <span data-ttu-id="6f7ee-104">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6f7ee-104">Operator (C# Reference)</span></span>
<span data-ttu-id="6f7ee-105">`??` İşleci, null birleşim işleci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="6f7ee-106">İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f7ee-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f7ee-107">Remarks</span></span>  
 <span data-ttu-id="6f7ee-108">Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur).</span><span class="sxs-lookup"><span data-stu-id="6f7ee-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="6f7ee-109">Kullanabileceğiniz `??` söz dizimsel anlamlılık (sağ el işlenenini) uygun bir değer döndürmek için işlecin sol işlenen null yapılabilir bir tür değeri null olduğunda.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="6f7ee-110">Null bir değer türü kullanmadan bir NULL olmayan değer türüne atamayı denerseniz, `??` işleci, bir derleme zamanı hatası oluşturacağını.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="6f7ee-111">Bir yayın kullanırsanız ve null yapılabilir değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="6f7ee-112">Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f7ee-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="6f7ee-113">Sonucu bir??</span><span class="sxs-lookup"><span data-stu-id="6f7ee-113">The result of a ??</span></span> <span data-ttu-id="6f7ee-114">işleci, hem bağımsız değişkenlerinden sabitleri olsa bile, bir sabit değer için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f7ee-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f7ee-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6f7ee-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6f7ee-116">C# Language Specification</span></span>  

<span data-ttu-id="6f7ee-117">Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f7ee-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6f7ee-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f7ee-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f7ee-119">See Also</span></span>

- [<span data-ttu-id="6f7ee-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f7ee-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6f7ee-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6f7ee-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6f7ee-122">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6f7ee-122">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="6f7ee-123">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="6f7ee-123">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="6f7ee-124">Hangi tam olarak 'Yükseltilmiş' anlamına mu?</span><span class="sxs-lookup"><span data-stu-id="6f7ee-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
