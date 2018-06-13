---
title: Tür &#39; &lt;variablename&gt; &#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: d6fdd9445b5336773d150c643c7bf1ca58a0c87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597159"
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tür &#39; &lt;variablename&gt; &#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor
Yazdığınız bir `For...Next` döngü içinde derleyici olamaz Infer for döngüsü denetim değişkeni için bir veri türü aşağıdaki koşulların geçerli olması için:  
  
-   For döngüsü denetim değişkeni veri türü ile belirtilmemiş bir `As` yan tümcesi.  
  
-   Döngü sınırları ve adım değişkeni en az iki veri türleri içerir.  
  
-   Hiçbir standart dönüşümler veri türleri arasında mevcut.  
  
 Bu nedenle, derleyici bir döngünün denetim değişkeninin veri türü gösterilemiyor.  
  
 Aşağıdaki örnekte, adım değişken karakter ve döngü sınırları iki tamsayı. Karakterler ve tamsayılar arasında standart dönüştürme olduğundan, bu hata bildirilir.  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **Hata Kimliği:** BC30982  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   En az biri diğerleri genişletmek için bir tür şekilde türlerini döngü sınırları ve adım değişkeni gerektiği gibi değiştirin. Önceki örnekte türünü değiştirme `stepVar` için `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —veya—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Açık dönüşüm işlevleri adım değişken ve döngü sınırlarını uygun türlerine dönüştürmek için kullanın. Önceki örnekte, geçerli `Val` için işlev `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
