---
title: 'Nasıl yapılır: İşaretçiyle bir Dizi Öğesine Erişme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 6d334459b0d530ec37925c98abfd061c04ce1290
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485657"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Nasıl yapılır: İşaretçiyle bir Dizi Öğesine Erişme (C# Programlama Kılavuzu)
Güvenli olmayan bir bağlamda, bir öğedeki bir bellek işaretçi öğe erişimi, kullanarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:  
  
```csharp  
char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 Köşeli ayraç ifadesi örtük olarak dönüştürülebilir olmalıdır `int`, `uint`, `long`, veya `ulong`. P [e] işlemi eşdeğerdir *(p+e). C ve C++ gibi işaretçi öğe erişimi işlemleri denetlemez hataları.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir karakter dizisine 123 bellek konumları ayrılır `charPointer`. Dizi küçük harfler ve büyük harfler iki görüntülemek için kullanılan [için](../../../csharp/language-reference/keywords/for.md) döngüleri.  
  
 Dikkat ifade `charPointer[i]` ifadesine eşdeğerdir `*(charPointer + i)`, ve iki ifadeden birini kullanarak aynı sonucu elde edebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Büyük harfler:**  
**ABCÇDEFGĞHIİJKLMNOÖPRSŞTUÜVYZ**  
**Küçük harfler:**  
**abcçdefgğhıijklmnoöprsştuüvyz**   
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
