---
title: float anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 98f89ba3d79f7679b69ce10fd875b3caf69c5257
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489909"
---
# <a name="float-c-reference"></a><span data-ttu-id="78625-102">float (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="78625-102">float (C# Reference)</span></span>

<span data-ttu-id="78625-103">`float` Anahtar sözcüğü, 32 bit kayan nokta değerlerini depolayan bir basit türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="78625-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="78625-104">İçin yaklaşık aralık ve duyarlık aşağıdaki tabloda gösterilmektedir `float` türü.</span><span class="sxs-lookup"><span data-stu-id="78625-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="78625-105">Tür</span><span class="sxs-lookup"><span data-stu-id="78625-105">Type</span></span>|<span data-ttu-id="78625-106">Yaklaşık aralık</span><span class="sxs-lookup"><span data-stu-id="78625-106">Approximate range</span></span>|<span data-ttu-id="78625-107">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="78625-107">Precision</span></span>|<span data-ttu-id="78625-108">.NET türü</span><span class="sxs-lookup"><span data-stu-id="78625-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="78625-109">±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="78625-109">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="78625-110">7 basamakla</span><span class="sxs-lookup"><span data-stu-id="78625-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="78625-111">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="78625-111">Literals</span></span>

<span data-ttu-id="78625-112">Varsayılan olarak, atama işlecinin sağ tarafında gerçek sayısal bir dize olarak işlem görür [çift](double.md).</span><span class="sxs-lookup"><span data-stu-id="78625-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="78625-113">Bu nedenle, bir kayan nokta değişkeni başlatmak için'ın soneki kullanıp `f` veya `F`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="78625-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="78625-114">Önceki bildirimde soneki kullanmazsanız depolamak çalıştığınız için bir derleme hatası alırsınız bir [çift](double.md) içine değeri bir `float` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="78625-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="78625-115">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="78625-115">Conversions</span></span>

<span data-ttu-id="78625-116">Tamsayı sayısal türleri ve kayan nokta türleri bir ifadede karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78625-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="78625-117">Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="78625-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="78625-118">İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="78625-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="78625-119">Kayan nokta türlerinden biri ise [çift](double.md), ifadenin değerlendirdiği [çift](double.md), veya [bool](bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="78625-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md), or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

- <span data-ttu-id="78625-120">Yoksa hiçbir [çift](double.md) değerlendirilen ifade ifadenin türü `float`, veya [bool](bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="78625-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="78625-121">Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="78625-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="78625-122">Pozitif ve negatif sıfırı</span><span class="sxs-lookup"><span data-stu-id="78625-122">Positive and negative zero</span></span>

- <span data-ttu-id="78625-123">Pozitif ve negatif sonsuz</span><span class="sxs-lookup"><span data-stu-id="78625-123">Positive and negative infinity</span></span>

- <span data-ttu-id="78625-124">Bir sayı değil değeri (NaN)</span><span class="sxs-lookup"><span data-stu-id="78625-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="78625-125">Sıfır olmayan değerler sınırlı kümesi</span><span class="sxs-lookup"><span data-stu-id="78625-125">The finite set of nonzero values</span></span>

<span data-ttu-id="78625-126">Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](http://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="78625-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="78625-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="78625-127">Example</span></span>

<span data-ttu-id="78625-128">Aşağıdaki örnekte, bir [int](int.md), [kısa](short.md)ve `float` vererek bir matematik ifadesindeki dahil edilen bir `float` sonucu.</span><span class="sxs-lookup"><span data-stu-id="78625-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="78625-129">(Unutmayın `float` için bir diğer addır <xref:System.Single?displayProperty=nameWithType> türü.) Var olduğuna dikkat edin hiçbir [çift](double.md) ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="78625-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="78625-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="78625-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="78625-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78625-131">See also</span></span>

- <xref:System.Single>  
- [<span data-ttu-id="78625-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="78625-132">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="78625-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="78625-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="78625-134">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="78625-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="78625-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="78625-135">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="78625-136">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="78625-136">Integral Types Table</span></span>](integral-types-table.md)  
- [<span data-ttu-id="78625-137">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="78625-137">Built-In Types Table</span></span>](built-in-types-table.md)  
- [<span data-ttu-id="78625-138">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="78625-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="78625-139">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="78625-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  