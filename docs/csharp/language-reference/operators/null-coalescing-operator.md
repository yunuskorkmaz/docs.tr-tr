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
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689339"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0cf49-103">??</span><span class="sxs-lookup"><span data-stu-id="0cf49-103">??</span></span> <span data-ttu-id="0cf49-104">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0cf49-104">operator (C# Reference)</span></span>

<span data-ttu-id="0cf49-105">`??` İşleci, null birleşim işleci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0cf49-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="0cf49-106">İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cf49-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cf49-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cf49-107">Remarks</span></span>

<span data-ttu-id="0cf49-108">Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur).</span><span class="sxs-lookup"><span data-stu-id="0cf49-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="0cf49-109">Kullanabileceğiniz `??` söz dizimsel anlamlılık (sağ el işlenenini) uygun bir değer döndürmek için işlecin sol işlenen null yapılabilir bir tür değeri null olduğunda.</span><span class="sxs-lookup"><span data-stu-id="0cf49-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="0cf49-110">Null bir değer türü kullanmadan bir NULL olmayan değer türüne atamayı denerseniz, `??` işleci, bir derleme zamanı hatası oluşturacağını.</span><span class="sxs-lookup"><span data-stu-id="0cf49-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="0cf49-111">Bir yayın kullanırsanız ve null yapılabilir değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0cf49-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>

<span data-ttu-id="0cf49-112">Daha fazla bilgi için [boş değer atanabilir türler](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cf49-112">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="0cf49-113">Sonucu bir??</span><span class="sxs-lookup"><span data-stu-id="0cf49-113">The result of a ??</span></span> <span data-ttu-id="0cf49-114">işleci, hem bağımsız değişkenlerinden sabitleri olsa bile, bir sabit değer için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="0cf49-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>

## <a name="example"></a><span data-ttu-id="0cf49-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cf49-115">Example</span></span>

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a><span data-ttu-id="0cf49-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0cf49-116">C# language specification</span></span>

<span data-ttu-id="0cf49-117">Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cf49-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="0cf49-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0cf49-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf49-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf49-119">See also</span></span>

- [<span data-ttu-id="0cf49-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0cf49-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0cf49-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0cf49-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0cf49-122">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="0cf49-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="0cf49-123">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="0cf49-123">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="0cf49-124">Hangi tam olarak 'Yükseltilmiş' anlamına mu?</span><span class="sxs-lookup"><span data-stu-id="0cf49-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)