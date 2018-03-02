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
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>Nasıl yapılır: Normal İfadeler Kullanarak Dizeleri Arama (C# Programlama Kılavuzu)
<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı, dizeleri aramak için kullanılabilir. Bu aramalar, normal ifadeler tam kullanımını yapmak karmaşıklığı çok basit değişebilir. Kullanarak arama dizesi iki örnek verilmiştir <xref:System.Text.RegularExpressions.Regex> sınıfı. Daha fazla bilgi için bkz: [.NET Framework normal ifadeleri](https://msdn.microsoft.com/library/hs600312).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir dizide basit duyarsız arama dizelerini gerçekleştiren bir konsol uygulamasıdır. Statik yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> verilen aranacak dize ve arama deseni içeren bir dize arama gerçekleştirir. Bu durumda, üçüncü bağımsız değişkeni, durum göz ardı olduğunu belirtmek için kullanılır. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir dizideki her dizesinin biçimi doğrulamak için normal ifadeler kullanan bir konsol uygulamasıdır. Her dize basamak üç grup çizgilerle ayrılır bir telefon numarası biçiminde olduğunu doğrulama gerektirir, ilk iki grupları üç rakam ve dört basamak üçüncü grubunu içerir. Bu normal ifade kullanılarak yapılır `^\\d{3}-\\d{3}-\\d{4}$`. Daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeler](../../../csharp/programming-guide/strings/index.md)  
 [.NET framework normal ifadeleri](https://msdn.microsoft.com/library/hs600312)  
 [Normal İfade Dili - Hızlı Başvuru](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
