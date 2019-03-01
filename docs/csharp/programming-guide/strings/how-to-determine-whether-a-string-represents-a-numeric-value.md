---
title: 'Nasıl yapılır: Bir dizenin sayısal bir değer - temsil edip etmediğini belirleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: dcba1651c736b58b2c95bac21f086c46417629df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980756"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="1fc40-102">Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1fc40-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="1fc40-103">Bir dizeyi, belirtilen bir sayısal tür geçerli bir temsilini olup olmadığını belirlemek için statik kullanın `TryParse` gibi tüm basit sayısal türlerin ve tür tarafından uygulanır yöntemi <xref:System.DateTime> ve <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="1fc40-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="1fc40-104">Aşağıdaki örnek, "108" bir geçerli olup olmadığını belirlemek gösterilmektedir [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="1fc40-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="1fc40-105">Dize, sayısal olmayan karakterler içeriyor veya çok büyük veya çok küçük, belirttiğiniz, belirli bir türe ilişkin sayısal değer varsa `TryParse` out parametresi sıfır olarak ayarlıyor ve false döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fc40-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="1fc40-106">Aksi takdirde true değerini döndürür ve out parametresi dize sayısal değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1fc40-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fc40-107">Bir dize yalnızca sayısal karakterlerden ve hala ayarlanmış türü için geçerli olmayan `TryParse` kullandığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fc40-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="1fc40-108">Örneğin, "256" için geçerli bir değer değil `byte` ancak için geçerli olduğundan `int`.</span><span class="sxs-lookup"><span data-stu-id="1fc40-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="1fc40-109">"98,6" değil için geçerli bir değer `int` ancak geçerli bir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="1fc40-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fc40-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fc40-110">Example</span></span>  
 <span data-ttu-id="1fc40-111">Aşağıdaki örnekler nasıl kullanılacağını `TryParse` dize temsillerini ile `long`, `byte`, ve `decimal` değerleri.</span><span class="sxs-lookup"><span data-stu-id="1fc40-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1fc40-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1fc40-112">Robust Programming</span></span>  
 <span data-ttu-id="1fc40-113">Temel sayısal türleri de uygulama `Parse` statik yöntemi dizesi geçerli bir sayı değilse, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fc40-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="1fc40-114">`TryParse` yalnızca sayı geçerli değilse false döndürdüğü için genellikle daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="1fc40-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1fc40-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1fc40-115">.NET Framework Security</span></span>  
 <span data-ttu-id="1fc40-116">Her zaman `TryParse` veya `Parse` metin kutuları ve birleşik giriş kutuları gibi denetimler kullanıcı girişini doğrulamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="1fc40-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc40-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fc40-117">See also</span></span>

- [<span data-ttu-id="1fc40-118">Nasıl yapılır: Byte dizisini int'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1fc40-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="1fc40-119">Nasıl yapılır: Bir dizeyi sayıya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1fc40-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="1fc40-120">Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1fc40-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="1fc40-121">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1fc40-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="1fc40-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="1fc40-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
