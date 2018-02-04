---
title: "Long Veri Türü (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cf03afc6b2e77ccca74fc26365fc50110e1f71
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="long-data-type-visual-basic"></a>Long veri türü (Visual Basic)

Ayrı tutma imzalı-9,223,372,036,854,775,808 değerinden 9,223,372,036,854,775,807 arasında değişen 64-bit (8-bayt) tamsayılar (9.2... E + 18).  
  
## <a name="remarks"></a>Açıklamalar

 Kullanım `Long` veri türü sığmayacak kadar büyük tamsayı sayılardan `Integer` veri türü.  
  
 Varsayılan değer olan `Long` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları 

Bildirme ve başlatma bir `Long` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Değişmez değer tamsayı aralığı dışında ise `Long` (diğer bir deyişle, bu ise değerinden <xref:System.Int64.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int64.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 4,294,967,296 tamsayılar eşit ve ikili değişmez değerler atanır `Long` değerleri.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak. Örneğin:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `L` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Long` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Programlama ipuçları

-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Long` diğer ortamlarda farklı veri genişliği (32 bit) vardır. Bu tür bir bileşen için 32-bit bağımsız değişkeni geçirilirse olarak bildirme `Integer` yerine `Long` yeni Visual Basic kodunuzda.  
  
-   **Genişletme.** `Long` Veri türü widens için `Decimal`, `Single`, veya `Double`. Bu dönüştürebilirsiniz anlamına gelir `Long` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `L` bir hazır değer zorlar `Long` veri türü. Tanımlayıcı türü karakteri ekleme `&` herhangi bir tanımlayıcı zorlar `Long`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Int64?displayProperty=nameWithType> yapısı.  

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.Int64>[Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[Integer veri türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Short veri türü](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
