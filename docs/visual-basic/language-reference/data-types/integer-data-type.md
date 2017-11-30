---
title: "Tamsayı Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a>Tamsayı veri türü (Visual Basic)
Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar
 `Integer` Veri türü bir 32-bit işlemci en iyi performans sağlar. Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.  
  
 Varsayılan değer olan `Integer` 0'dır.  

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirme ve başlatma bir `Integer` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Değişmez değer tamsayı aralığı dışında ise `Integer` (diğer bir deyişle, bu ise değerinden <xref:System.Int32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int32.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 16,342 tamsayılar eşit ve ikili değişmez değerler atanır `Integer` değerleri.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Sayısal değişmez değerleri de dahil edebilirsiniz `I` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Integer` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a>Programlama ipuçları

-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Integer` diğer ortamlarda farklı veri genişliği (16 bit) vardır. Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `Short` yerine `Integer` yeni Visual Basic kodunuzda.  
  
-   **Genişletme.** `Integer` Veri türü widens için `Long`, `Decimal`, `Single`, veya `Double`. Bu dönüştürebilirsiniz anlamına gelir `Integer` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `I` bir hazır değer zorlar `Integer` veri türü. Tanımlayıcı türü karakteri ekleme `%` herhangi bir tanımlayıcı zorlar `Integer`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Int32?displayProperty=nameWithType> yapısı.  
  
## <a name="range"></a>Aralık

Tamsayı türünde bir değişkeni, bu türe ilişkin aralık dışında bir sayıya ayarlamaya çalışırsanız hata meydana gelir. Bir kesir olarak ayarlamaya çalışırsanız, sayı en yakın tamsayı değerine yukarı veya aşağı yuvarlanır. Sayı iki tamsayı değerine de eşit yakınlıkta ise, değer en yakın çift tamsayıya yuvarlanır. Bu davranış, bir orta nokta değerini tek bir yönde sürekli olarak yuvarlamaktan kaynaklanan yuvarlama hatalarını en aza indirir. Aşağıdaki kod, yuvarlama örneklerini göstermektedir.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.Int32?displayProperty=nameWithType>   
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short veri türü](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
