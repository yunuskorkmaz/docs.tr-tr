---
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 2dc7793a837c588b98365a97ada58c67dc07fa03
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664261"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tür '\<variablename >' döngü sınırları ve step değişkeni aynı türe genişletmek değil çıkarsanamıyor
Yazdığınız bir `For...Next` döngü içinde derleyici olamaz Infer döngü denetim değişkeni için bir veri türü aşağıdaki koşulların geçerli olması için:  
  
- Döngü denetim değişkeni veri türü ile belirtilmemiş bir `As` yan tümcesi.  
  
- Döngü sınırları ve step değişkeni en az iki veri türü içeriyor.  
  
- Veri türleri arasında standart dönüştürme yok.  
  
 Bu nedenle, derleyici bir döngü denetim değişkeni veri türü çıkarsanamıyor.  
  
 Aşağıdaki örnekte, step değişkeni bir karakterse ve döngü sınırları hem tam sayılardır. Karakterler ve tam sayılar arasında standart dönüştürme olmadığından, bu hata bildirilir.  
  
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
  
- Döngü sınırları ve step değişkeni gerektiğinde türlerini değiştirin, böylece en az bir tanesi, diğerleri için genişletmek bir türdür. Önceki örnekte türünü değiştirme `stepVar` için `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —veya—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
- Döngü sınırları ve step değişkeni uygun türe dönüştürmek için açık dönüştürme işlevlerini kullanın. Önceki örnekte, geçerli `Val` işlevi `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
