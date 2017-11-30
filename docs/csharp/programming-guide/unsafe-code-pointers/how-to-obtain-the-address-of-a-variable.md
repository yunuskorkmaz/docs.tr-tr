---
title: "Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)
Sabit bir değişkene değerlendiren bir tek terimli ifadesi adresini elde etmek için address-of işleci kullanın:  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Address-of işleci yalnızca bir değişkene uygulanabilir. Değişken taşınabilir değişkeni ise kullanabileceğiniz [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) değişkeni adresini almadan önce geçici olarak çözmek için.  
  
 Bu değişkeni başlatıldığından emin olun, sorumluluğundadır. Değişkeni başlatılmadı, derleyici bir hata iletisi veremez.  
  
 Bir sabit ya da bir değer adresini alınamıyor.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişken adresi atanmış `number`. Değişkeni `number` atamayı sonucunda başlatılmış * p. Bu atama deyimi bir yorum, değişkeni başlatma yaptığınız varsa `number` kaldırılacak, ancak hiçbir derleme zamanı hatası verilir. Kullanımına dikkat edin [üye erişimi](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) işleci `->` elde edilir ve işaretçiyi depolanan adresini görüntüler.  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi ifadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
