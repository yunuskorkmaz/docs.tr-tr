---
title: 'Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 66f341e193a0f018adb76a40617f85266519e602
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138272"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)
İşaretçi yöneltme işleci için bir işaretçi tarafından işaret edilen konumda bir değişkeni almak için kullanın. İfade, aşağıdaki biçimi alır burada `p` bir işaretçi türü:  
  
```  
*p;  
```  
  
 İşaretçi türünün dışındaki herhangi bir türde bir ifade üzerinde birli yöneltme işlecini kullanamazsınız. Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.  
  
 Yöneltme işleci uygulandığında bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçiler kullanılarak erişilebilir. Unutmayın adresini `theChar` gelen çalıştıracak çalışma için bir değişkene ayrılan fiziksel adresi geçebileceğiniz farklılık gösterir.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
**TheChar değerini Z =**
**theChar adresini 12F718 =**
**pChar değerini Z =**
**pInt değerini 90 =**

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
