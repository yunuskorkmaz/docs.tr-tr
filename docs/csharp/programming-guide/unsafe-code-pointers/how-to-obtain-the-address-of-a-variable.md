---
title: 'Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 40a7ac34a4e68df7aa316adc3cbd1999d975eabe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532958"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)
Sabit bir değişkene değerlendirir, tekli ifade adresini almak için address-of işlecini kullanın `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Address-of işleci yalnızca bir değişkene uygulanabilir. Değişken taşınabilir bir değişken ise kullanabileceğiniz [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) adresini almadan önce değişkeni geçici olarak çözmek için.  
  
 Bu değişkeni başlatıldığından emin olmak sizin sorumluluğunuzdur. Değişken başlatılmadı, derleyici bir hata iletisi sorunu değildir.  
  
 Bir sabit bir değer veya adresi alınamıyor.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişkeninin adresi atanan `number`. Değişken `number` atamaya sonucu olarak başlatılır `*p`. Bu atama deyimi, değişkenin başlatılması yorum `number` kaldırılır, ancak hiçbir derleme zamanı hata verilir.  

> [!NOTE]
> Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
