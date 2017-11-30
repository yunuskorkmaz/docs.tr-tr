---
title: "Nasıl yapılır: String.Split (C# programlama Kılavuzu) kullanarak dizeleri ayrıştırma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="31087-102">Nasıl yapılır: String.Split (C# programlama Kılavuzu) kullanarak dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="31087-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="31087-103">Aşağıdaki kod örneğinde nasıl bir dize gösterilmektedir kullanarak Ayrıştırılan <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31087-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31087-104">Giriş, olarak <xref:System.String.Split%2A> hedef dizesi ilginç alt dizeleri hangi karakterleri ayrı belirtmek karakterden oluşan bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="31087-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="31087-105">İşlevi bir alt dize dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="31087-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="31087-106">Bu örnekte boşluk, virgül, nokta, iki nokta üst üste ve sekmeler, bunlar ayıran karakter içeren bir dizi içindeki tüm geçirilen <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="31087-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="31087-107">Her sözcüğün hedef dizesinin tümcedeki dizeleri elde edilen diziden ayrı olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="31087-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31087-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="31087-108">Example</span></span>  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="31087-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="31087-109">Example</span></span>  
 <span data-ttu-id="31087-110">Varsayılan olarak, iki ayıran karakter bitişik hedef dizesinde görüntülendiğinde String.Split boş dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="31087-110">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="31087-111">Tüm boş dizeler çıktıda dışlamak için isteğe bağlı bir StringSplitOptions.RemoveEmptyEntries parametre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31087-111">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="31087-112">String.Split (tek karakter yerine hedef dizesini ayrıştırmak için ayırıcı olarak davranmak karakter sıraları) bir dizeler dizisi alabilir.</span><span class="sxs-lookup"><span data-stu-id="31087-112">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="31087-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31087-113">See Also</span></span>  
 [<span data-ttu-id="31087-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31087-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="31087-115">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="31087-115">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="31087-116">.NET framework normal ifadeleri</span><span class="sxs-lookup"><span data-stu-id="31087-116">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)
