---
title: 'Nasıl yapılır: işaretçileri artırma ve azaltma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128342"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Nasıl yapılır: işaretçileri artırma ve azaltma (C# Programlama Kılavuzu)

Artırma ve azaltma işleçleri kullanan `++` ve `--`işaretçi konuma göre değişmesini `sizeof(pointer-type)` türünde bir işaretçi için `pointer-type*`. Artırma ve azaltma ifadeleri aşağıdaki biçiminde:  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 Tür dışında herhangi bir türde işaretçileri artırma ve azaltma işleçleri uygulanabilir `void*`.  
  
 Artırım işleci türünde bir işaretçiye uygulamak etkisini `pointer-type*` eklemektir `sizeof(pointer-type)` adresine işaretçi değişkeninde yer alır.  
  
 Azaltma işleci türünde bir işaretçiye uygulamak etkisini `pointer-type*` çıkarılacak olan `sizeof(pointer-type)` adresinden işaretçi değişkeninde yer alır.  
  
 Hiçbir özel durum, etki alanı işaretçinin işlemi taşıyor ve sonuç uygulamasının bağlıdır, üretilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir dizi aracılığıyla işaretçinin boyutuna artırılarak adım `int`. Her adımda adresi ve dizi öğenin içeriğini görüntüler.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
**Değer: 0 @ adresi: 12860272**
**değer: 1 @ adresi: 12860276**
**değer: 2 @ adresi: 12860280**
**değer: 3 @ adresi : 12860284**
**değer: 4 @ adresi: 12860288**

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [İşaretçileri İşleme](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
