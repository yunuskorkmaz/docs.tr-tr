---
title: "Değeri &#39;kopyalama; ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; türündeki &#39; eşleşen bağımsız değişken daraltır için yeniden&lt; TypeName1&gt;& yazmak için #39; &#39;&lt; TypeName2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Değeri &#39;kopyalama; ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; türündeki &#39; eşleşen bağımsız değişken daraltır için yeniden&lt; TypeName1&gt;& yazmak için #39; &#39;&lt; TypeName2&gt;&#39;
Bir yordam, karşılık gelen parametre türüyle widens bağımsız değişkeni adı verilir ve parametre bağımsız değişkeni dönüştürme daraltma.  
  
 Bir sınıf veya yapı tanımladığınızda, diğer türleri için bu sınıf veya yapı türüne dönüştürmek için bir veya daha fazla dönüşüm işleçleri tanımlayabilirsiniz. Ayrıca, diğer geri sınıfınız türlerine veya bir yapı türüne dönüştürmek için Geri Dönüşüm işleçleri tanımlayabilirsiniz. Bir yordam çağrısı, sınıf veya yapı türünü kullandığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişken türü, karşılık gelen bir parametre türüne dönüştürmek için bu dönüşüm işleçleri kullanabilirsiniz.  
  
 Bağımsız değişken geçirirseniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bazen bir başvuru geçirme yerine yordamdaki yerel bir değişken bağımsız değişken değeri kopyalar. Yordamın geri döndüğünde, böyle bir durumda, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sonra yerel değişken değerini geri çağırma kodu değişkeninde kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir. Ancak türleri farklıysa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] her iki yönde de dönüştürmeniz gerekir. Türlerinden birini, sınıf veya yapı türü ise [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] için hem de diğer türünden dönüştürmeniz gerekir. Bu dönüşümleri birini genişletme, geriye doğru dönüştürme daraltma.  
  
 **Hata Kimliği:** BC32053  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] herhangi bir dönüştürmeye yapmak gerekmez.  
  
-   Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
-   Çağırma bağımsız değişkeni bir değer döndürmesi gerekiyorsa, olarak geri dönüşüm işleci tanımlama [Widening](../../../visual-basic/language-reference/modifiers/widening.md), mümkün olduğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [İşleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
