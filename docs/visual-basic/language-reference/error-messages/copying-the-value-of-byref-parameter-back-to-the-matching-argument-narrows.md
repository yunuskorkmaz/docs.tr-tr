---
title: Değerini kopyalayarak &#39;ByRef&#39; parametresi &#39; &lt;parametername&gt; &#39; eşleşen bağımsız daraltır türünden &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18c72e56e4b2cc9c2251de2417a9f12a6688323f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Değerini kopyalayarak &#39;ByRef&#39; parametresi &#39; &lt;parametername&gt; &#39; eşleşen bağımsız daraltır türünden &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;
Bir yordam, karşılık gelen parametre türüyle widens bağımsız değişkeni adı verilir ve parametre bağımsız değişkeni dönüştürme daraltma.  
  
 Bir sınıf veya yapı tanımladığınızda, diğer türleri için bu sınıf veya yapı türüne dönüştürmek için bir veya daha fazla dönüşüm işleçleri tanımlayabilirsiniz. Ayrıca, diğer geri sınıfınız türlerine veya bir yapı türüne dönüştürmek için Geri Dönüşüm işleçleri tanımlayabilirsiniz. Bir yordam çağrısında sınıf veya yapı türünüzü kullandığınızda, Visual Basic bağımsız değişken türü, karşılık gelen bir parametre türüne dönüştürmek için bu dönüşüm işleçleri kullanabilirsiniz.  
  
 Bağımsız değişken geçirirseniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bazen kopyalar bağımsız değişken değeri bir başvuru geçirme yerine yordamı yerel bir değişkende içine. Yordamın geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değerini geri çağıran kodu değişkeninde kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir. Ancak türleri farklıysa, Visual Basic her iki yönde de dönüştürmeniz gerekir. Türlerinden birini sınıf veya yapı türü ise, Visual Basic, hem gelen ve diğer tür dönüştürmeniz gerekir. Bu dönüşümleri birini genişletme, geriye doğru dönüştürme daraltma.  
  
 **Hata Kimliği:** BC32053  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, Visual Basic herhangi bir dönüştürmeye gerçekleştirmeniz gereken şekilde aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın.  
  
-   Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
-   Çağırma bağımsız değişkeni bir değer döndürmesi gerekiyorsa, olarak geri dönüşüm işleci tanımlama [Widening](../../../visual-basic/language-reference/modifiers/widening.md), mümkün olduğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
