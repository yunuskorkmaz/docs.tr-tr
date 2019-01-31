---
title: "'<typename1>' 'ByRef' parametresinin değerini eşleşen bağımsız değişkene geri kopyalarken '<typename2>' türünden '<parametername>' türüne örtük dönüştürme"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: f875206b15ee048311e43624e197e78413de522e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279623"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Arasında örtük dönüşüm '\<typename1 >' için '\<typename2 >' 'ByRef' parametresinin değeri kopyalarken '\<parametername >' eşleşen bağımsız değişkene geri dönün.
Bir yordam adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) , karşılık gelen parametre farklı bir tür bağımsız değişkeni.  
  
 Bağımsız değişken geçirirseniz `ByRef`, Visual Basic bazen kopyalar bağımsız değişken değeri yordamda bir başvuru geçirmek yerine yerel bir değişken içine. Yordamı geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değeri çağıran koddaki bağımsız değişken uygulamasına geri kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişken ile parametre aynı tür dönüştürme gerekli değildir. Ancak, Visual Basic türleri farklı ise, her iki yönde dönüştürmeniz gerekir. Kullanamazsınız çünkü `CType` veya herhangi bir dönüştürme anahtar bir yordam bağımsız değişkeninin veya parametre, böyle bir dönüştürme her zaman kesin.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC41999  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, Visual Basic, herhangi bir dönüştürme yapmak gerekmez. Bu nedenle aynı türde çağıran bir bağımsız değişken yordam parametresi kullanın.  
  
-   Bağımsız değişken içeren bir yordamı çağırma gerekiyorsa parametre türünden farklı yazın ancak ihtiyaç duymayan çağırma bağımsız değişkeni bir değer döndürmek parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
