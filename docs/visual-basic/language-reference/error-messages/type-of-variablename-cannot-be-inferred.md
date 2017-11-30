---
title: "Tür &#39; &lt;variablename&gt;&#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tür &#39; &lt;variablename&gt;&#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor
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
 [İçin... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
