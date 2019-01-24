---
title: Değerini kopyalayarak &#39;ByRef&#39; parametre &#39; &lt;parametername&gt; &#39; eşleşen bağımsız değişkene geri türüne daralan &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: ec733ecd605d0a9db840ea3f0c3e0e3b5b698054
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506293"
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Değerini kopyalayarak &#39;ByRef&#39; parametre &#39; &lt;parametername&gt; &#39; eşleşen bağımsız değişkene geri türüne daralan &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;
Bir yordam bağımsız değişken için karşılık gelen parametre türü widens çağrılır ve bağımsız değişken parametre dönüştürme daraltma.  
  
 Bir sınıf veya yapı tanımladığınızda, bu sınıf veya yapı türü diğer türlerine dönüştürmek için bir veya daha fazla dönüştürme işleçleri tanımlayabilirsiniz. Bu bir sınıfınız geri türlerine veya yapı türü dönüştürmek için geriye doğru dönüştürme işleçleri de tanımlayabilirsiniz. Bir yordam çağrısında, sınıf veya yapı türünü kullandığınızda, Visual Basic, karşılık gelen bir parametresinin türü için bir bağımsız değişken türünü dönüştürmek için bu dönüştürme işleçlerini kullanabilirsiniz.  
  
 Bağımsız değişken geçirirseniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bazen kopyalar bağımsız değişken değeri yordamda bir başvuru geçirmek yerine yerel bir değişken içine. Yordamı geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değeri çağıran koddaki bağımsız değişken uygulamasına geri kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişken ile parametre aynı tür dönüştürme gerekli değildir. Ancak, Visual Basic türleri farklı ise, her iki yönde dönüştürmeniz gerekir. Türlerinden biri, sınıf veya yapı türü ise, Visual Basic, için ve diğer türden dönüştürmeniz gerekir. Bu dönüştürmeler birini genişletme, ters dönüştürme daraltma.  
  
 **Hata Kimliği:** BC32053  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, Visual Basic, herhangi bir dönüştürme yapmak gerekmez. Bu nedenle aynı türde çağıran bir bağımsız değişken yordam parametresi kullanın.  
  
-   Bağımsız değişken içeren bir yordamı çağırma gerekiyorsa parametre türünden farklı yazın ancak ihtiyaç duymayan çağırma bağımsız değişkeni bir değer döndürmek parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
-   Çağırma bağımsız değişkeni bir değer döndürmesi gerekiyorsa, geriye doğru dönüştürme işleci olarak tanımlama [Widening](../../../visual-basic/language-reference/modifiers/widening.md), mümkünse.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Nasıl yapılır: Bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
