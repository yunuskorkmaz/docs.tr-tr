---
title: 'Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: f1e5efca7fb3088064b3f252675b8cae965717f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336592"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="6c487-102">Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6c487-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="6c487-103">Bir dizeyi belirtilen bir sayısal tür geçerli bir gösterimini olup olmadığını belirlemek için statik kullanmak `TryParse` tüm basit sayısal türler ve ayrıca türleri tarafından gibi uygulanır yöntemi <xref:System.DateTime> ve <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="6c487-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="6c487-104">Aşağıdaki örnekte, "108" bir geçerli olup olmadığını belirlemek gösterilmiştir [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="6c487-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="6c487-105">Dize, sayısal karakterler içeriyor veya çok büyük ya da belirttiğiniz, belirli tür için çok küçük sayısal değeri `TryParse` false değerini döndürür ve out parametresi sıfır olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c487-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="6c487-106">Aksi takdirde true değerini döndürür ve out parametresi dizenin sayısal bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c487-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c487-107">Bir dize ve yalnızca sayısal karakterlerden hala özelliği türü için geçerli değil `TryParse` kullandığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c487-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="6c487-108">Örneğin, "256" için geçerli bir değer değil `byte` için geçerlidir, ancak `int`.</span><span class="sxs-lookup"><span data-stu-id="6c487-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="6c487-109">"98,6" değil için geçerli bir değer `int` ancak geçerli bir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6c487-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c487-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c487-110">Example</span></span>  
 <span data-ttu-id="6c487-111">Aşağıdaki örnekler nasıl kullanılacağını `TryParse` dize gösterimlerini ile `long`, `byte`, ve `decimal` değerleri.</span><span class="sxs-lookup"><span data-stu-id="6c487-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6c487-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6c487-112">Robust Programming</span></span>  
 <span data-ttu-id="6c487-113">İlkel sayısal türleri de uygulama `Parse` statik yöntemi dizesi geçerli bir sayı değilse, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c487-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="6c487-114">`TryParse` yalnızca sayı geçerli değilse false döndürür çünkü genellikle daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="6c487-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6c487-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6c487-115">.NET Framework Security</span></span>  
 <span data-ttu-id="6c487-116">Her zaman kullanmak `TryParse` veya `Parse` kullanıcı girişi metin kutuları ve birleşik giriş kutuları gibi denetimlerinden doğrulamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="6c487-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c487-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c487-117">See Also</span></span>  
 [<span data-ttu-id="6c487-118">Nasıl yapılır: byte Dizisini int'e Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6c487-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [<span data-ttu-id="6c487-119">Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6c487-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [<span data-ttu-id="6c487-120">Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6c487-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [<span data-ttu-id="6c487-121">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6c487-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)  
 [<span data-ttu-id="6c487-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="6c487-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
