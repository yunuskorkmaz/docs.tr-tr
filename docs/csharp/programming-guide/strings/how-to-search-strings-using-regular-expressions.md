---
title: "Nasıl yapılır: Normal İfadeler Kullanarak Dizeleri Arama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="88381-102">Nasıl yapılır: Normal İfadeler Kullanarak Dizeleri Arama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="88381-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="88381-103"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı, dizeleri aramak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88381-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="88381-104">Bu aramalar, normal ifadeler tam kullanımını yapmak karmaşıklığı çok basit değişebilir.</span><span class="sxs-lookup"><span data-stu-id="88381-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="88381-105">Kullanarak arama dizesi iki örnek verilmiştir <xref:System.Text.RegularExpressions.Regex> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88381-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="88381-106">Daha fazla bilgi için bkz: [.NET Framework normal ifadeleri](https://msdn.microsoft.com/library/hs600312).</span><span class="sxs-lookup"><span data-stu-id="88381-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88381-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="88381-107">Example</span></span>  
 <span data-ttu-id="88381-108">Aşağıdaki kod bir dizide basit duyarsız arama dizelerini gerçekleştiren bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="88381-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="88381-109">Statik yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> verilen aranacak dize ve arama deseni içeren bir dize arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="88381-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="88381-110">Bu durumda, üçüncü bağımsız değişkeni, durum göz ardı olduğunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88381-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="88381-111">Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88381-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="88381-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="88381-112">Example</span></span>  
 <span data-ttu-id="88381-113">Aşağıdaki kod, bir dizideki her dizesinin biçimi doğrulamak için normal ifadeler kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="88381-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="88381-114">Her dize basamak üç grup çizgilerle ayrılır bir telefon numarası biçiminde olduğunu doğrulama gerektirir, ilk iki grupları üç rakam ve dört basamak üçüncü grubunu içerir.</span><span class="sxs-lookup"><span data-stu-id="88381-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="88381-115">Bu normal ifade kullanılarak yapılır `^\\d{3}-\\d{3}-\\d{4}$`.</span><span class="sxs-lookup"><span data-stu-id="88381-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="88381-116">Daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span><span class="sxs-lookup"><span data-stu-id="88381-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="88381-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88381-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="88381-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="88381-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88381-119">Dizeler</span><span class="sxs-lookup"><span data-stu-id="88381-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="88381-120">.NET framework normal ifadeleri</span><span class="sxs-lookup"><span data-stu-id="88381-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="88381-121">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="88381-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
