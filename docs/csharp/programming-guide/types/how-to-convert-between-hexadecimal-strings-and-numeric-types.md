---
title: 'Nasıl yapılır: Onaltılık dizeler ve sayısal türler - arasında dönüştürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: ed943948888110b76df9c9ce22b4e9b6f4bb679f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200383"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="194ea-102">Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="194ea-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="194ea-103">Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="194ea-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="194ea-104">Her bir karakteri onaltılık değerini almak bir [dize](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="194ea-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="194ea-105">Elde [char](../../../csharp/language-reference/keywords/char.md) karşılık gelen her değeri bir onaltılık dize.</span><span class="sxs-lookup"><span data-stu-id="194ea-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="194ea-106">On altılı dönüştürme `string` için bir [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="194ea-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="194ea-107">On altılı dönüştürme `string` için bir [float](../../../csharp/language-reference/keywords/float.md).</span><span class="sxs-lookup"><span data-stu-id="194ea-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="194ea-108">Dönüştürme bir [bayt](../../../csharp/language-reference/keywords/byte.md) dizi için bir onaltılık `string`.</span><span class="sxs-lookup"><span data-stu-id="194ea-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="194ea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="194ea-109">Example</span></span>  
 <span data-ttu-id="194ea-110">Bu örnekte her bir karakteri onaltılık değerini çıkarır bir `string`.</span><span class="sxs-lookup"><span data-stu-id="194ea-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="194ea-111">İlk ayrıştırır `string` karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="194ea-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="194ea-112">Çağrı sonra <xref:System.Convert.ToInt32%28System.Char%29> üzerinde sayısal değerini almak için her bir karakter.</span><span class="sxs-lookup"><span data-stu-id="194ea-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="194ea-113">Son olarak, onaltılı gösterimine olarak sayı biçimlendiren bir `string`.</span><span class="sxs-lookup"><span data-stu-id="194ea-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="194ea-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="194ea-114">Example</span></span>  
 <span data-ttu-id="194ea-115">Bu örnekte ayrıştırmak için bir `string` , on altılık değerleri ve her onaltılı değerine karşılık gelen karakteri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="194ea-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="194ea-116">İlk çağrı [bölme (Char\[\])](xref:System.String.Split(System.Char[])) bireysel olarak her bir onaltılık değer elde etmek için yöntemi `string` dizi.</span><span class="sxs-lookup"><span data-stu-id="194ea-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="194ea-117">Çağrı sonra <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> olarak temsil edilen bir ondalık değer onaltılı değerine dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md). Bu, o karakteri koduna karşılık gelen karakteri almak için iki farklı şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="194ea-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="194ea-118">İlk tekniği kullanan <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, tamsayı bağımsız değişken olarak karşılık gelen karakteri döndürür bir `string`.</span><span class="sxs-lookup"><span data-stu-id="194ea-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="194ea-119">İkinci yöntem açıkça bıraktığı `int` için bir [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="194ea-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="194ea-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="194ea-120">Example</span></span>  
 <span data-ttu-id="194ea-121">Bu örnek bir onaltılık dönüştürmek için başka bir yolunu gösterir `string` çağırarak bir tamsayıya <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="194ea-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="194ea-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="194ea-122">Example</span></span>  
 <span data-ttu-id="194ea-123">Aşağıdaki örnek, bir onaltılık dönüştürülecek gösterilmektedir `string` için bir [float](../../../csharp/language-reference/keywords/float.md) kullanarak <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="194ea-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="194ea-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="194ea-124">Example</span></span>  
 <span data-ttu-id="194ea-125">Aşağıdaki örnek nasıl dönüştürüleceğini gösterir bir [bayt](../../../csharp/language-reference/keywords/byte.md) kullanarak bir onaltılık dize dizisine <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="194ea-125">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="194ea-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="194ea-126">See also</span></span>

- [<span data-ttu-id="194ea-127">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="194ea-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="194ea-128">Türler</span><span class="sxs-lookup"><span data-stu-id="194ea-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="194ea-129">Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="194ea-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
