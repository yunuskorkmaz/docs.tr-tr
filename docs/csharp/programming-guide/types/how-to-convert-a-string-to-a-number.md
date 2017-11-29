---
title: "Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="e7eae-102">Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e7eae-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="e7eae-103">Dönüştürebilir bir [dize](../../../csharp/language-reference/keywords/string.md) yöntemleri kullanarak bir sayıya <xref:System.Convert> kullanarak veya sınıf `TryParse` yöntemi (int, uzun, float, vb.) çeşitli sayısal türler üzerinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e7eae-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="e7eae-104">Bir dize varsa, biraz daha etkili ve doğrudan çağırmak, bir `TryParse` yöntemi (örneğin, `int.TryParse("11")`).</span><span class="sxs-lookup"><span data-stu-id="e7eae-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="e7eae-105">Kullanarak bir `Convert` yöntemdir uygulayan genel nesneler için daha kullanışlı <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="e7eae-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="e7eae-106">Kullanabileceğiniz `Parse` veya `TryParse` beklediğiniz gibi dizesini içeren sayısal türündeki yöntemlere <xref:System.Int32?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="e7eae-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="e7eae-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Yöntemi kullanan <xref:System.Int32.Parse%2A> dahili olarak.</span><span class="sxs-lookup"><span data-stu-id="e7eae-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="e7eae-108">Dizesi geçerli bir biçimde değilse `Parse` ancak aykırı `TryParse` döndürür [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="e7eae-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7eae-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7eae-109">Example</span></span>  
 <span data-ttu-id="e7eae-110">`Parse` Ve `TryParse` yöntemleri yoksay başında ve dizenin sonunda boşluk, ancak diğer tüm karakterler uygun sayısal türün form karakter olmalıdır (int, uzun, ulong, float, ondalık, vs.).</span><span class="sxs-lookup"><span data-stu-id="e7eae-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="e7eae-111">Hiçbir boşluk form numarayı bir hata neden karakter içinde.</span><span class="sxs-lookup"><span data-stu-id="e7eae-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="e7eae-112">Örneğin, kullanabileceğiniz `decimal.TryParse` "10", "10.3", "10", ancak ayrıştırmak için bu yöntemi "10 X", 10 ayrıştırmak için kullanamazsınız "1 0" (Not alanı), "10. 3" (Not alanı), "10e1" (`float.TryParse` burada çalışır) ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e7eae-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="e7eae-113">Aşağıdaki örneklerde başarılı ve başarısız çağrılar göstermek `Parse` ve `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="e7eae-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="e7eae-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7eae-114">Example</span></span>  
 <span data-ttu-id="e7eae-115">Aşağıdaki tabloda bazı yöntemleri listelenmiştir <xref:System.Convert> kullanabileceğiniz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7eae-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="e7eae-116">Sayısal Tür</span><span class="sxs-lookup"><span data-stu-id="e7eae-116">Numeric Type</span></span>|<span data-ttu-id="e7eae-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e7eae-117">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="e7eae-118">Bu örnek çağırır <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> giriş dönüştürmek için yöntem [dize](../../../csharp/language-reference/keywords/string.md) için bir [int](../../../csharp/language-reference/keywords/int.md) .</span><span class="sxs-lookup"><span data-stu-id="e7eae-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="e7eae-119">Kod bu yöntem tarafından oluşturulan iki en yaygın özel durumları yakalar <xref:System.FormatException> ve <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="e7eae-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="e7eae-120">Sayı, tamsayı depolama konumunda taşma olmadan artırılabiliyorsa program sonuca 1 ekler ve sonucu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e7eae-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e7eae-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7eae-121">See Also</span></span>  
 [<span data-ttu-id="e7eae-122">Türler</span><span class="sxs-lookup"><span data-stu-id="e7eae-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="e7eae-123">Nasıl yapılır: bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="e7eae-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [<span data-ttu-id="e7eae-124">.NET framework 4 biçimlendirme yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="e7eae-124">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
