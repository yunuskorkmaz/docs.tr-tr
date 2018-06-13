---
title: Örtük dönüştürme &#39; &lt;typename1&gt; &#39; için &#39; &lt;typename2&gt; &#39; değerini kopyalayarak içinde &#39;ByRef&#39; parametresi &#39; &lt; parametername&gt; &#39; eşleşen bağımsız değişkene dön.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590006"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Örtük dönüştürme &#39; &lt;typename1&gt; &#39; için &#39; &lt;typename2&gt; &#39; değerini kopyalayarak içinde &#39;ByRef&#39; parametresi &#39; &lt; parametername&gt; &#39; eşleşen bağımsız değişkene dön.
Bir yordam ile adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni, karşılık gelen bir parametre daha farklı bir türde.  
  
 Bir bağımsız değişken geçirirseniz `ByRef`, Visual Basic bazen kopyalar bağımsız değişken değeri bir başvuru geçirme yerine yordamı yerel bir değişkende içine. Yordamın geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değerini geri çağıran kodu değişkeninde kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir. Ancak türleri farklıysa, Visual Basic her iki yönde de dönüştürmeniz gerekir. Kullanamadığından `CType` veya diğer dönüşüm anahtar sözcükleri bir yordam bağımsız değişkenini veya parametresi, bu tür dönüştürme olan her zaman örtük.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC41999  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, Visual Basic herhangi bir dönüştürmeye gerçekleştirmeniz gereken şekilde aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın.  
  
-   Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
