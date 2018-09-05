---
title: 'Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 1f11ba3981b219d3b3a7817afd75fa78f2ccf78a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521759"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="eb12d-102">Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="eb12d-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="eb12d-103">Dönüştürebilir bir [dize](../../../csharp/language-reference/keywords/string.md) yöntemleri kullanarak sayıya <xref:System.Convert> kullanarak veya sınıf `TryParse` yöntemi (int, long, float, vb.) çeşitli sayısal türler üzerinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="eb12d-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="eb12d-104">Bir dize varsa, biraz daha verimli ve doğrudan çağırmak onu bir `TryParse` yöntemi (örneğin, [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)).</span><span class="sxs-lookup"><span data-stu-id="eb12d-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)).</span></span>  <span data-ttu-id="eb12d-105">Kullanarak bir <xref:System.Convert> yöntemi uygulamak, genel nesneler için daha faydalı <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="eb12d-105">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="eb12d-106">Kullanabileceğiniz `Parse` veya `TryParse` beklediğiniz gibi dize içeren sayısal türün yöntemleri <xref:System.Int32?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="eb12d-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="eb12d-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Yöntemi kullanan <xref:System.Int32.Parse%2A> dahili olarak.</span><span class="sxs-lookup"><span data-stu-id="eb12d-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="eb12d-108">Dize geçerli bir biçimde değilse `Parse` bir özel durum oluşturur `TryParse` döndürür [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="eb12d-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb12d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb12d-109">Example</span></span>  
 <span data-ttu-id="eb12d-110">`Parse` Ve `TryParse` yöntemleri başında ve sonunda dize, beyaz boşluğu yoksay, ancak tüm diğer karakterler uygun sayısal türle form karakter olmalıdır (int, long, ulong, float, ondalık, vs.).</span><span class="sxs-lookup"><span data-stu-id="eb12d-110">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="eb12d-111">Herhangi bir boşluğu sayı form karakteri aşmayan bir hata neden.</span><span class="sxs-lookup"><span data-stu-id="eb12d-111">Any white space within the characters that form the number cause an error.</span></span>  <span data-ttu-id="eb12d-112">Örneğin, kullanabileceğiniz `decimal.TryParse` "10", "10.3", "10", ancak ayrıştırmak için bu yöntem "10 X", 10 ayrıştırmak için kullanamazsınız "1 0" (Not alanı), "10. 3" (Not alanı), "10e1" (`float.TryParse` burada) ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="eb12d-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="eb12d-113">Aşağıdaki örnekler hem başarılı hem de başarısız çağrılarını gösterir `Parse` ve `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="eb12d-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="eb12d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb12d-114">Example</span></span>  
 <span data-ttu-id="eb12d-115">Aşağıdaki tabloda yöntemlerden bazıları listelenmiştir <xref:System.Convert> kullanabileceğiniz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb12d-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="eb12d-116">Sayısal Tür</span><span class="sxs-lookup"><span data-stu-id="eb12d-116">Numeric Type</span></span>|<span data-ttu-id="eb12d-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb12d-117">Method</span></span>|  
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
  
 <span data-ttu-id="eb12d-118">Bu örnek <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> giriş yöntemi [dize](../../../csharp/language-reference/keywords/string.md) için bir [int](../../../csharp/language-reference/keywords/int.md) .</span><span class="sxs-lookup"><span data-stu-id="eb12d-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="eb12d-119">Bu yöntem tarafından oluşturması muhtemel en yaygın iki özel kod yakalar <xref:System.FormatException> ve <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="eb12d-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="eb12d-120">Sayı, tamsayı depolama konumunda taşma olmadan artırılabiliyorsa program sonuca 1 ekler ve sonucu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="eb12d-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="eb12d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb12d-121">See Also</span></span>

- [<span data-ttu-id="eb12d-122">Türler</span><span class="sxs-lookup"><span data-stu-id="eb12d-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="eb12d-123">Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme</span><span class="sxs-lookup"><span data-stu-id="eb12d-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [<span data-ttu-id="eb12d-124">.NET framework 4 biçimlendirme yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="eb12d-124">.NET Framework 4 Formatting Utility</span></span>](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
