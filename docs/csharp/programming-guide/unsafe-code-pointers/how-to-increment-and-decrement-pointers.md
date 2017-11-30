---
title: "Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi ifadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)  
 [İşaretçileri işleme](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
