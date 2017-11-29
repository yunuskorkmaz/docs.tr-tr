---
title: "Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91e5cff52c67e1e7930d92da7c87ab1f4a3120af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="65f46-102">Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="65f46-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="65f46-103">Bu örnekler aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="65f46-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="65f46-104">Her karakteri on altılık değeri elde bir [dize](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="65f46-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="65f46-105">Elde [char](../../../csharp/language-reference/keywords/char.md) , her bir onaltılık dize değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="65f46-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="65f46-106">On altılı Dönüştür `string` için bir [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="65f46-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="65f46-107">On altılı Dönüştür `string` için bir [float](../../../csharp/language-reference/keywords/float.md).</span><span class="sxs-lookup"><span data-stu-id="65f46-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="65f46-108">Dönüştürme bir [bayt](../../../csharp/language-reference/keywords/byte.md) on altılı dizisine `string`.</span><span class="sxs-lookup"><span data-stu-id="65f46-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65f46-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f46-109">Example</span></span>  
 <span data-ttu-id="65f46-110">Bu örnekte her karakter on altılık değeri çıkarır bir `string`.</span><span class="sxs-lookup"><span data-stu-id="65f46-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="65f46-111">İlk ayrıştırır `string` karakterden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="65f46-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="65f46-112">Çağırır sonra <xref:System.Convert.ToInt32%28System.Char%29> sayısal değerini almak için her karakter üzerinde.</span><span class="sxs-lookup"><span data-stu-id="65f46-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="65f46-113">Son olarak, kendi onaltılık gösterimi olarak sayıyı biçimler bir `string`.</span><span class="sxs-lookup"><span data-stu-id="65f46-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="65f46-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f46-114">Example</span></span>  
 <span data-ttu-id="65f46-115">Bu örnek ayrıştırır bir `string` , onaltılık değerler ve her bir onaltılı değere karşılık gelen karakter çıkarır.</span><span class="sxs-lookup"><span data-stu-id="65f46-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="65f46-116">İlk çağıran [bölme (Char\[\])](xref:System.String.Split(System.Char[])) her on altılık değeri tek bir olarak elde etmek için yöntemi `string` dizi.</span><span class="sxs-lookup"><span data-stu-id="65f46-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="65f46-117">Çağırır sonra <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> on altılık değeri olarak gösterilen bir ondalık değer dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md). Bu karakter koduna karşılık gelen karakter almak için iki farklı yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="65f46-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="65f46-118">İlk tekniği kullanan <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, tamsayı bağımsız değişken olarak karşılık gelen karakter döndüren bir `string`.</span><span class="sxs-lookup"><span data-stu-id="65f46-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="65f46-119">İkinci tekniği açıkça bıraktığı `int` için bir [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="65f46-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="65f46-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f46-120">Example</span></span>  
 <span data-ttu-id="65f46-121">Bu örnek bir onaltılık dönüştürmek için başka bir yolunu gösterir `string` çağırarak bir tamsayıya <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="65f46-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="65f46-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f46-122">Example</span></span>  
 <span data-ttu-id="65f46-123">Aşağıdaki örnek, bir onaltılık dönüştürmek gösterilmiştir `string` için bir [float](../../../csharp/language-reference/keywords/float.md) kullanarak <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.Int32.Parse%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="65f46-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.Int32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="65f46-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f46-124">Example</span></span>  
 <span data-ttu-id="65f46-125">Aşağıdaki örnekte nasıl dönüştürüleceğini gösterir bir [bayt](../../../csharp/language-reference/keywords/byte.md) kullanarak bir onaltılık dize dizisine <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="65f46-125">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="65f46-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65f46-126">See Also</span></span>  
 [<span data-ttu-id="65f46-127">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="65f46-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="65f46-128">Türler</span><span class="sxs-lookup"><span data-stu-id="65f46-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="65f46-129">Nasıl yapılır: bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="65f46-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
