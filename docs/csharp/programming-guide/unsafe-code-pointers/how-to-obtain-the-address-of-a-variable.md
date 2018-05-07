---
title: 'Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb52aee3341194697b40b30ec14afced61a200be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)
Address-of işleci sabit bir değişkene değerlendiren bir tek terimli ifadesi adresini elde etmek için kullanmak `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Address-of işleci yalnızca bir değişkene uygulanabilir. Değişken taşınabilir değişkeni ise kullanabileceğiniz [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) değişkeni adresini almadan önce geçici olarak çözmek için.  
  
 Bu değişkeni başlatıldığından emin olun, sorumluluğundadır. Derleyici bir hata iletisi verilmediğine ve değişken başlatılmadı değil.  
  
 Bir sabit ya da bir değer adresini alınamıyor.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişken adresi atanmış `number`. Değişkeni `number` atamayı sonucunda başlatılmış `*p`. Bu atama deyimi değişkeni başlatma açıklama varsa `number` kaldırılır, ancak hiçbir derleme zamanı hatası verilir.  

> [!NOTE]
> Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
