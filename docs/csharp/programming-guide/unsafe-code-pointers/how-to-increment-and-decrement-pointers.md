---
title: 'Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)
Artırma ve azaltma işleçleri kullanmak `++` ve `--`, işaretçi konuma göre değiştirmek için [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) için bir işaretçi türü işaretçinin-türü *. Artırma ve azaltma ifadeleri aşağıdaki biçimde alın:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Türü dışında herhangi bir türde işaretçileri artırma ve azaltma işleçleri uygulanabilir `void*`.  
  
 Artış işleci türü için bir işaretçi uygulama etkisini `pointer-type` eklemektir [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) işaretçi değişkeninde bulunan adresine.  
  
 Uygulamanın etkisini azaltma işleci türü için bir işaretçi uygulama `pointer-type` çıkarmak için `sizeof` (`pointer-type`) işaretçi değişkeninde bulunan adresinden.  
  
 Hiçbir özel durum, etki alanı işaretçinin işlemi taşar ve sonucu uygulamasına bağlıdır, üretilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir dizi boyunca boyutuyla işaretçinin artırılarak adım `int`. Her adım ile adres ve dizi öğenin içeriğini görüntüler.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Değer: 0 @ adresi: 12860272**  
**Değer: 1 @ adresi: 12860276**  
**Değer: 2 @ adresi: 12860280**  
**Değer: 3 @ adresi: 12860284**  
**Değer: 4 @ adresi: 12860288**   
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
 [İşaretçileri İşleme](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
