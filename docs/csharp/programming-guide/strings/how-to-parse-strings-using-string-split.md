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
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>Nasıl yapılır: String.Split (C# programlama Kılavuzu) kullanarak dizeleri ayrıştırma
Aşağıdaki kod örneğinde nasıl bir dize gösterilmektedir kullanarak Ayrıştırılan <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi. Giriş, olarak <xref:System.String.Split%2A> hedef dizesi ilginç alt dizeleri hangi karakterleri ayrı belirtmek karakterden oluşan bir dizi alır.  İşlevi bir alt dize dizisi döndürür.  
  
 Bu örnekte boşluk, virgül, nokta, iki nokta üst üste ve sekmeler, bunlar ayıran karakter içeren bir dizi içindeki tüm geçirilen <xref:System.String.Split%2A>.  Her sözcüğün hedef dizesinin tümcedeki dizeleri elde edilen diziden ayrı olarak görüntüler.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>Örnek  
 Varsayılan olarak, iki ayıran karakter bitişik hedef dizesinde görüntülendiğinde String.Split boş dize döndürür.  Tüm boş dizeler çıktıda dışlamak için isteğe bağlı bir StringSplitOptions.RemoveEmptyEntries parametre geçirebilirsiniz.  
  
 String.Split (tek karakter yerine hedef dizesini ayrıştırmak için ayırıcı olarak davranmak karakter sıraları) bir dizeler dizisi alabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)  
 [.NET framework normal ifadeleri](https://msdn.microsoft.com/library/hs600312)
