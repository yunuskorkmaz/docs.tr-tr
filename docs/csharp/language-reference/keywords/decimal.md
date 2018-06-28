---
title: decimal anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 18924abefb85012fc6c61073603c594de906b58d
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027960"
---
# <a name="decimal-c-reference"></a><span data-ttu-id="cb491-102">decimal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cb491-102">decimal (C# Reference)</span></span>

<span data-ttu-id="cb491-103">`decimal` Anahtar sözcüğü 128-bit veri türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb491-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="cb491-104">Diğer kayan nokta türleri için karşılaştırıldığında `decimal` daha yüksek duyarlılık ve finansal ve para hesaplamaları için uygun hale getirir daha küçük bir aralık türü içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cb491-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="cb491-105">İçin duyarlık ve yaklaşık aralığı `decimal` türü aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb491-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>

|<span data-ttu-id="cb491-106">Tür</span><span class="sxs-lookup"><span data-stu-id="cb491-106">Type</span></span>|<span data-ttu-id="cb491-107">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="cb491-107">Approximate Range</span></span>|<span data-ttu-id="cb491-108">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="cb491-108">Precision</span></span>|<span data-ttu-id="cb491-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="cb491-109">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|<span data-ttu-id="cb491-110">(-7.9 x 10<sup>28</sup> 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="cb491-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="cb491-111">28-29 önemli basamaklar</span><span class="sxs-lookup"><span data-stu-id="cb491-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="cb491-112">Varsayılan değer olan bir `decimal` 0 m.</span><span class="sxs-lookup"><span data-stu-id="cb491-112">The default value of a `decimal` is 0m.</span></span>

## <a name="literals"></a><span data-ttu-id="cb491-113">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="cb491-113">Literals</span></span>

<span data-ttu-id="cb491-114">Göreceğini sayısal gerçek değişmez değeri isteyip istemediğinizi `decimal`, sonek m veya M, örneğin kullanın:</span><span class="sxs-lookup"><span data-stu-id="cb491-114">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>

```csharp
decimal myMoney = 300.5m;
```

<span data-ttu-id="cb491-115">M soneki sayı olarak işlem görür bir [çift](../../../csharp/language-reference/keywords/double.md) ve derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb491-115">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>

## <a name="conversions"></a><span data-ttu-id="cb491-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="cb491-116">Conversions</span></span>

<span data-ttu-id="cb491-117">Tam sayı türleri örtük olarak dönüştürülür `decimal` ve sonucu veren `decimal`.</span><span class="sxs-lookup"><span data-stu-id="cb491-117">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="cb491-118">Bu nedenle, bir tamsayı hazır değerini kullanarak, son ek olmadan, bir ondalık değişken başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cb491-118">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>

```csharp
decimal myMoney = 300;
```

<span data-ttu-id="cb491-119">Kayan nokta diğer türleri arasında örtük bir dönüştürme yok ve `decimal` yazın; bu nedenle, bir cast bu iki türleri arasında dönüştürme için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb491-119">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="cb491-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cb491-120">For example:</span></span>

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

<span data-ttu-id="cb491-121">Ayrıca karıştırabilirsiniz `decimal` ve aynı ifadedeki sayısal tam sayı türleri.</span><span class="sxs-lookup"><span data-stu-id="cb491-121">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="cb491-122">Ancak, karıştırma `decimal` ve diğer kayan nokta türleri bir cast olmadan bir derleme hatası neden olur.</span><span class="sxs-lookup"><span data-stu-id="cb491-122">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>

<span data-ttu-id="cb491-123">Örtük sayısal dönüşümler hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="cb491-123">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="cb491-124">Açık sayısal dönüşümler hakkında daha fazla bilgi için bkz: [açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="cb491-124">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="formatting-decimal-output"></a><span data-ttu-id="cb491-125">Ondalık Çıkış biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="cb491-125">Formatting decimal output</span></span>

<span data-ttu-id="cb491-126">Kullanarak sonuçları biçimlendirebilirsiniz `String.Format` yöntemi, aracılığıyla veya <xref:System.Console.Write%2A?displayProperty=nameWithType> çağırır yöntemi `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="cb491-126">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="cb491-127">Para birimi, bu makalenin ilerisinde ikinci örnekte gösterildiği gibi, standart para birimi biçimi dizisi "C" veya "c" kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb491-127">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="cb491-128">Hakkında daha fazla bilgi için `String.Format` yöntemi, bkz: <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb491-128">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="cb491-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb491-129">Example</span></span>

<span data-ttu-id="cb491-130">Aşağıdaki örnek eklemek deneyerek derleyici hatası neden olan [çift](../../../csharp/language-reference/keywords/double.md) ve `decimal` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="cb491-130">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

<span data-ttu-id="cb491-131">Sonuç olarak aşağıdaki hata oluşur:</span><span class="sxs-lookup"><span data-stu-id="cb491-131">The result is the following error:</span></span>

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

<span data-ttu-id="cb491-132">Bu örnekte, bir `decimal` ve bir [int](../../../csharp/language-reference/keywords/int.md) aynı ifadesinde karıştırılır.</span><span class="sxs-lookup"><span data-stu-id="cb491-132">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="cb491-133">Sonucu veren `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="cb491-133">The result evaluates to the `decimal` type.</span></span>

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a><span data-ttu-id="cb491-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb491-134">Example</span></span>

<span data-ttu-id="cb491-135">Bu örnekte, çıktı, para birimi biçim dizesi kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cb491-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="cb491-136">Dikkat `x` ondalık 0,99 aştığından yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb491-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="cb491-137">Değişkeni `y`, en büyük tam sayı temsil eden tam olarak doğru biçimde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb491-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="cb491-138">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cb491-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cb491-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb491-139">See also</span></span>

<xref:System.Decimal>  
[<span data-ttu-id="cb491-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb491-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="cb491-141">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cb491-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="cb491-142">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cb491-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="cb491-143">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="cb491-143">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
[<span data-ttu-id="cb491-144">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cb491-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="cb491-145">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cb491-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="cb491-146">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cb491-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[<span data-ttu-id="cb491-147">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="cb491-147">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)