---
title: 'Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a7109945192fe1577cd1b96c8b4d6c05270d54e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588376"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="9640b-102">Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9640b-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="9640b-103">Bu örneklerde aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9640b-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="9640b-104">[Dizedeki](../../language-reference/keywords/string.md)her karakterin onaltılık değerini elde edin.</span><span class="sxs-lookup"><span data-stu-id="9640b-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="9640b-105">Onaltılık dizedeki her değere karşılık gelen [char](../../language-reference/keywords/char.md) 'ı alın.</span><span class="sxs-lookup"><span data-stu-id="9640b-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="9640b-106">Onaltılı `string` bir [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9640b-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="9640b-107">Bir onaltılık tabandaki `string` bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md)öğesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9640b-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="9640b-108">Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini onaltılı `string`olarak dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9640b-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9640b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9640b-109">Example</span></span>  
 <span data-ttu-id="9640b-110">Bu örnek, içindeki her bir `string`karakterin onaltılık değerini verir.</span><span class="sxs-lookup"><span data-stu-id="9640b-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="9640b-111">İlk olarak, `string` bir karakter dizisi olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9640b-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="9640b-112">Ardından, sayısal <xref:System.Convert.ToInt32%28System.Char%29> değerini elde etmek için her bir karakter üzerinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="9640b-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="9640b-113">Son olarak, sayıyı içinde `string`onaltılık gösterimi olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="9640b-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="9640b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9640b-114">Example</span></span>  
 <span data-ttu-id="9640b-115">Bu örnek, onaltılı `string` değerleri ayrıştırır ve her onaltılık değere karşılık gelen karakteri verir.</span><span class="sxs-lookup"><span data-stu-id="9640b-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="9640b-116">İlk olarak, her onaltılı değeri bir dizide bir kişi `string` olarak almak için [Split (Char\[\])](xref:System.String.Split(System.Char[])) yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9640b-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="9640b-117">Ardından, onaltılı <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> değeri [tamsayı](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen bir ondalık değere dönüştürmek için çağırır. Bu karakter koduna karşılık gelen karakteri almanın iki farklı yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9640b-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="9640b-118">İlk tekniği kullanır <xref:System.Char.ConvertFromUtf32%28System.Int32%29>ve tamsayı bağımsız değişkenine karşılık gelen karakteri bir `string`olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="9640b-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="9640b-119">İkinci teknik, `int` öğesini açıkça bir [char](../../language-reference/keywords/char.md)öğesine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="9640b-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="9640b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9640b-120">Example</span></span>  
 <span data-ttu-id="9640b-121">Bu örnek, `string` <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemini çağırarak, onaltılı bir tamsayıyı bir tamsayıya dönüştürmenin başka bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9640b-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="9640b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9640b-122">Example</span></span>  
 <span data-ttu-id="9640b-123">Aşağıdaki örnek, `string` <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi kullanılarak bir onaltılık tabandaki bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md) öğesine nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9640b-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="9640b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9640b-124">Example</span></span>  
 <span data-ttu-id="9640b-125">Aşağıdaki örnek, <xref:System.BitConverter?displayProperty=nameWithType> sınıfını kullanarak bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisinin onaltılık dizeye nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9640b-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="9640b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9640b-126">See also</span></span>

- [<span data-ttu-id="9640b-127">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="9640b-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="9640b-128">Türler</span><span class="sxs-lookup"><span data-stu-id="9640b-128">Types</span></span>](./index.md)
- [<span data-ttu-id="9640b-129">Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="9640b-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
