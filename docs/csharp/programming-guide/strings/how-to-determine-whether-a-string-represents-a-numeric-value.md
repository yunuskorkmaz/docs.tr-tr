---
title: Bir dize sayısal bir değeri temsil edip etmediğini belirleme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157071"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="b32da-102">Bir dize sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b32da-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="b32da-103">Bir dize belirli bir sayısal türün geçerli bir temsili `TryParse` olup olmadığını belirlemek için, tüm ilkel sayısal türleri <xref:System.DateTime> tarafından <xref:System.Net.IPAddress>uygulanan statik yöntemi kullanın ve aynı zamanda .</span><span class="sxs-lookup"><span data-stu-id="b32da-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="b32da-104">Aşağıdaki örnekte, "108"in geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığı nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b32da-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="b32da-105">Dize sayısal olmayan karakterler içeriyorsa veya sayısal değer belirttiğiniz belirli tür için çok `TryParse` büyük veya çok küçükse, yanlış döndürür ve parametreyi sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b32da-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="b32da-106">Aksi takdirde, doğru döndürür ve dize sayısal değeri ne kadar parametre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b32da-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b32da-107">Bir dize yalnızca sayısal karakterler içerebilir ve yine de `TryParse` kullandığınız yöntem için geçerli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b32da-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="b32da-108">Örneğin, "256" için `byte` geçerli bir değer değil, `int`ancak .</span><span class="sxs-lookup"><span data-stu-id="b32da-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="b32da-109">"98.6" için `int` geçerli bir değer değil `decimal`ama geçerli bir .</span><span class="sxs-lookup"><span data-stu-id="b32da-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b32da-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b32da-110">Example</span></span>  
 <span data-ttu-id="b32da-111">`TryParse` Aşağıdaki `long`örnekler, , , `byte`ve `decimal` değerleri dize gösterimleri ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b32da-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b32da-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b32da-112">Robust Programming</span></span>  
 <span data-ttu-id="b32da-113">İlkel sayısal türleri, `Parse` dize geçerli bir sayı değilse bir özel durum atan statik yöntemi de uygular.</span><span class="sxs-lookup"><span data-stu-id="b32da-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="b32da-114">`TryParse`sayı geçerli değilse, yalnızca yanlış döndürür, çünkü genellikle daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="b32da-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b32da-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b32da-115">.NET Framework Security</span></span>  
 <span data-ttu-id="b32da-116">Metin kutuları `TryParse` `Parse` ve açılan kutular gibi denetimlerden kullanıcı girdisini doğrulamak için her zaman veya yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="b32da-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32da-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b32da-117">See also</span></span>

- [<span data-ttu-id="b32da-118">byte dizisini int’e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b32da-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="b32da-119">Bir dizeyi sayıya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b32da-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="b32da-120">Onaltılık dizeler ve sayısal türler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b32da-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="b32da-121">Sayısal Dizeleri Ayrıştma</span><span class="sxs-lookup"><span data-stu-id="b32da-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="b32da-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="b32da-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
