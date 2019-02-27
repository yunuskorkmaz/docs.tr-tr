---
title: '[] işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835596"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="24993-102">[] işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="24993-102">[] operator (C# Reference)</span></span>

<span data-ttu-id="24993-103">Köşeli ayraçlar `[]`, genellikle dizi, dizin oluşturucu veya işaretçiyi öğe erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24993-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="24993-104">İşaretçi öğe erişimi hakkında daha fazla bilgi için bkz: [nasıl yapılır: işaretçiyle bir dizi öğesine erişme](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="24993-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="24993-105">Köşeli ayraçlar belirtmek için de [öznitelikleri](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="24993-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="24993-106">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="24993-106">Array access</span></span>

<span data-ttu-id="24993-107">Aşağıdaki örnekte, dizi öğelerinin nasıl erişileceğini gösteren:</span><span class="sxs-lookup"><span data-stu-id="24993-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="24993-108">Bir dizi dizini karşılık gelen boyutuna bir dizinin sınırları dışında ise bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24993-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="24993-109">Yukarıdaki örnekte gösterildiği gibi de köşeli ayraç örnekleme dizi örnekleri bir dizi türü bildirimi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24993-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="24993-110">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="24993-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="24993-111">Dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="24993-111">Indexer access</span></span>

<span data-ttu-id="24993-112">Aşağıdaki örnek, .NET kullanır <xref:System.Collections.Generic.Dictionary%602> dizinleyici erişimi göstermek için türü:</span><span class="sxs-lookup"><span data-stu-id="24993-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="24993-113">Dizin oluşturucular dizi dizini oluşturma olarak benzer şekilde, kullanıcı tanımlı bir tür dizin örneğini olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="24993-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="24993-114">Dizin oluşturucu bağımsız değişken tamsayı olması gerekir, dizi dizinleri, herhangi bir türde olması bildirilir.</span><span class="sxs-lookup"><span data-stu-id="24993-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="24993-115">Dizin oluşturucular hakkında daha fazla bilgi için bkz: [dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="24993-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="24993-116">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="24993-116">Operator overloadability</span></span>

<span data-ttu-id="24993-117">Öğe erişimi `[]` bir aşırı yüklenebilir işleç olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="24993-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="24993-118">Kullanım [dizin oluşturucular](../../programming-guide/indexers/index.md) için kullanıcı tanımlı türler ile dizin oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="24993-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="24993-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="24993-119">C# language specification</span></span>

<span data-ttu-id="24993-120">Daha fazla bilgi için [öğe erişimi](~/_csharplang/spec/expressions.md#element-access) ve [işaretçi öğe erişimi](~/_csharplang/spec/unsafe-code.md#pointer-element-access) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="24993-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24993-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24993-121">See also</span></span>

- [<span data-ttu-id="24993-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="24993-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="24993-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24993-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="24993-124">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="24993-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="24993-125">Diziler</span><span class="sxs-lookup"><span data-stu-id="24993-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="24993-126">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="24993-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="24993-127">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="24993-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="24993-128">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24993-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)
- <span data-ttu-id="24993-129">[?. ve? [] işleçleri](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="24993-129">[?. and ?[] operators](null-conditional-operators.md)</span></span>