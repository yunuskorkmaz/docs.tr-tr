---
title: typeof - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 3fa82a6faee345be77fc8ea3f5aa3342adecb0f5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244849"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="3f264-102">typeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f264-102">typeof (C# Reference)</span></span>

<span data-ttu-id="3f264-103">Elde etmek için kullanılan <xref:System.Type?displayProperty=nameWithType> nesne türü.</span><span class="sxs-lookup"><span data-stu-id="3f264-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="3f264-104">A `typeof` ifade aşağıdaki biçimleri alır:</span><span class="sxs-lookup"><span data-stu-id="3f264-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="3f264-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f264-105">Remarks</span></span>

<span data-ttu-id="3f264-106">Bir ifadenin çalışma zamanı türü elde etmek için .NET Framework yöntemi kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="3f264-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="3f264-107">`typeof` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="3f264-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="3f264-108">`typeof` İşleci açık genel türler üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f264-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="3f264-109">Birden fazla tür parametresi ile türleri belirtiminde virgül uygun sayıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f264-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="3f264-110">Aşağıdaki örnek, bir yöntemin dönüş türü genel olup olmadığını belirlemek gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3f264-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="3f264-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> döndüreceği `null` dönüş türü değilse bir <xref:System.Collections.Generic.IEnumerable%601> genel tür.</span><span class="sxs-lookup"><span data-stu-id="3f264-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="3f264-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f264-112">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="3f264-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f264-113">Example</span></span>

<span data-ttu-id="3f264-114">Bu örnekte <xref:System.Object.GetType%2A> sayısal hesaplama sonucu kapsamak için kullanılmış türünü belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f264-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="3f264-115">Bu, sonuçta elde edilen sayı depolama gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f264-115">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="3f264-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3f264-116">C# language specification</span></span>

<span data-ttu-id="3f264-117">Daha fazla bilgi için [typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f264-117">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3f264-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3f264-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f264-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f264-119">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="3f264-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f264-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3f264-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3f264-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3f264-122">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3f264-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="3f264-123">is</span><span class="sxs-lookup"><span data-stu-id="3f264-123">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="3f264-124">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3f264-124">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)