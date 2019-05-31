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
ms.openlocfilehash: 7962a3d0a5885e64701cb9d9a4d689cd982b9830
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422546"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="e5432-102">typeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e5432-102">typeof (C# Reference)</span></span>

<span data-ttu-id="e5432-103">Elde etmek için kullanılan <xref:System.Type?displayProperty=nameWithType> nesne türü.</span><span class="sxs-lookup"><span data-stu-id="e5432-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="e5432-104">A `typeof` ifade aşağıdaki biçimleri alır:</span><span class="sxs-lookup"><span data-stu-id="e5432-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="e5432-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5432-105">Remarks</span></span>

<span data-ttu-id="e5432-106">Bir ifadenin çalışma zamanı türü elde etmek için .NET Framework yöntemi kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="e5432-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="e5432-107">`typeof` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e5432-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="e5432-108">`typeof` İşleci açık genel türler üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5432-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="e5432-109">Birden fazla tür parametresi ile türleri belirtiminde virgül uygun sayıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5432-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="e5432-110">Örneğin, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> olduğundan iki tür bağımsız değişkenleri, bir virgül kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5432-110">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> has two type arguments, so you use one comma:</span></span>

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

<span data-ttu-id="e5432-111">Aşağıdaki örnek, bir yöntemin dönüş türü genel olup olmadığını belirlemek gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e5432-111">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e5432-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> döndüreceği `null` dönüş türü değilse bir <xref:System.Collections.Generic.IEnumerable%601> genel tür.</span><span class="sxs-lookup"><span data-stu-id="e5432-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="e5432-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5432-113">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="e5432-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5432-114">Example</span></span>

<span data-ttu-id="e5432-115">Bu örnekte <xref:System.Object.GetType%2A> sayısal hesaplama sonucu kapsamak için kullanılmış türünü belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5432-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="e5432-116">Bu, sonuçta elde edilen sayı depolama gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5432-116">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="e5432-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5432-117">C# language specification</span></span>

<span data-ttu-id="e5432-118">Daha fazla bilgi için [typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5432-118">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="e5432-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="e5432-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5432-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5432-120">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="e5432-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e5432-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="e5432-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5432-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e5432-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e5432-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="e5432-124">is</span><span class="sxs-lookup"><span data-stu-id="e5432-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
