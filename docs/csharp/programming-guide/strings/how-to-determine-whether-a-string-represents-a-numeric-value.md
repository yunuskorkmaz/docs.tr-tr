---
title: 'Nasıl yapılır: Bir dizenin sayısal değeri temsil edip etmediğini belirleme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 831f0fc83c8a7066b40d64e4765a312b8b4847bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921778"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="fd6b5-102">Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirlemeC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fd6b5-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="fd6b5-103">Bir dizenin belirtilen bir sayısal türün geçerli bir gösterimi olup olmadığını anlamak için, tüm ilkel sayısal türler `TryParse` tarafından uygulanan statik yöntemi ve ayrıca <xref:System.DateTime> ve <xref:System.Net.IPAddress>gibi türleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="fd6b5-104">Aşağıdaki örnek, "108" nin geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığını nasıl belirleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="fd6b5-105">Dize sayısal olmayan karakterler içeriyorsa veya belirttiğiniz belirli tür için çok büyük veya çok küçükse, `TryParse` false değerini döndürür ve out parametresini sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="fd6b5-106">Aksi takdirde, true döndürür ve out parametresini dizenin sayısal değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd6b5-107">Dize yalnızca sayısal karakterler içerebilir ve bu `TryParse` yöntemi kullandığınız tür için geçerli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="fd6b5-108">Örneğin, "256", için `byte` geçerli bir değer değildir ancak için `int`geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="fd6b5-109">"98,6", için `int` geçerli bir değer değil, ancak geçerli `decimal`bir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd6b5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6b5-110">Example</span></span>  
 <span data-ttu-id="fd6b5-111">Aşağıdaki `TryParse` örneklerde,, ve `long` `byte` değerlerinin`decimal` dize gösterimiyle nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fd6b5-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fd6b5-112">Robust Programming</span></span>  
 <span data-ttu-id="fd6b5-113">İlkel sayısal türler Ayrıca, dize `Parse` geçerli bir sayı değilse özel bir durum oluşturan statik yöntemini de uygular.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="fd6b5-114">`TryParse`Genellikle, sayı geçerli değilse false döndürdüğünden, bu, genellikle daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fd6b5-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fd6b5-115">.NET Framework Security</span></span>  
 <span data-ttu-id="fd6b5-116">Metin kutuları ve `TryParse` Birleşik `Parse` giriş kutuları gibi denetimlerden Kullanıcı girişini doğrulamak için her zaman veya yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6b5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6b5-117">See also</span></span>

- [<span data-ttu-id="fd6b5-118">Nasıl yapılır: Byte dizisini int 'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fd6b5-118">How to: Convert a byte Array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="fd6b5-119">Nasıl yapılır: Bir dizeyi sayıya Dönüştür</span><span class="sxs-lookup"><span data-stu-id="fd6b5-119">How to: Convert a String to a Number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="fd6b5-120">Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fd6b5-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="fd6b5-121">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="fd6b5-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="fd6b5-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="fd6b5-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
