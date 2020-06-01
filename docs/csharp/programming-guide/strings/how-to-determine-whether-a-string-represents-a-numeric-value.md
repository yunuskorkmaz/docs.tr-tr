---
title: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 37437460ea4c6ca216f2844d63af3688ccc984c6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241727"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="fdc59-102">Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fdc59-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="fdc59-103">Bir dizenin belirtilen bir sayısal türün geçerli bir gösterimi olup olmadığını anlamak için, `TryParse` tüm ilkel sayısal türler tarafından uygulanan statik yöntemi ve ayrıca ve gibi türleri kullanın <xref:System.DateTime> <xref:System.Net.IPAddress> .</span><span class="sxs-lookup"><span data-stu-id="fdc59-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="fdc59-104">Aşağıdaki örnek, "108" nin geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığını nasıl belirleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc59-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="fdc59-105">Dize sayısal olmayan karakterler içeriyorsa veya belirttiğiniz belirli tür için çok büyük veya çok küçükse, `TryParse` false değerini döndürür ve out parametresini sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fdc59-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="fdc59-106">Aksi takdirde, true döndürür ve out parametresini dizenin sayısal değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fdc59-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdc59-107">Dize yalnızca sayısal karakterler içerebilir ve bu yöntemi kullandığınız tür için geçerli olmayabilir `TryParse` .</span><span class="sxs-lookup"><span data-stu-id="fdc59-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="fdc59-108">Örneğin, "256", için geçerli bir değer değildir `byte` ancak için geçerlidir `int` .</span><span class="sxs-lookup"><span data-stu-id="fdc59-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="fdc59-109">"98,6", için geçerli bir değer değil, `int` ancak geçerli bir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="fdc59-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdc59-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdc59-110">Example</span></span>  
 <span data-ttu-id="fdc59-111">Aşağıdaki örneklerde,, `TryParse` ve değerlerinin dize gösterimiyle nasıl kullanılacağı `long` gösterilmektedir `byte` `decimal` .</span><span class="sxs-lookup"><span data-stu-id="fdc59-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fdc59-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fdc59-112">Robust Programming</span></span>  
 <span data-ttu-id="fdc59-113">İlkel sayısal türler Ayrıca, `Parse` dize geçerli bir sayı değilse özel bir durum oluşturan statik yöntemini de uygular.</span><span class="sxs-lookup"><span data-stu-id="fdc59-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="fdc59-114">`TryParse`Genellikle, sayı geçerli değilse false döndürdüğünden, bu, genellikle daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="fdc59-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="fdc59-115">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="fdc59-115">.NET Security</span></span>  
 <span data-ttu-id="fdc59-116">`TryParse` `Parse` Metin kutuları ve Birleşik giriş kutuları gibi denetimlerden Kullanıcı girişini doğrulamak için her zaman veya yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdc59-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc59-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc59-117">See also</span></span>

- [<span data-ttu-id="fdc59-118">byte dizisini int’e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fdc59-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="fdc59-119">Bir dizeyi sayıya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fdc59-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="fdc59-120">Onaltılık dizeler ve sayısal türler arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fdc59-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="fdc59-121">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="fdc59-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="fdc59-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="fdc59-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
