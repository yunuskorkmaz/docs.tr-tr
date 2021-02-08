---
description: "Hakkında daha fazla bilgi edinin: BC32053: ' ByRef ' parametresinin ' ' değeri, <parametername> ' ' türünden ' ' türüne daralan eşleşen bağımsız değişkene geri kopyalanıyor <typename1><typename2>"
title: "'ByRef' '<parametername>' parametresinin değeri '<typename1>' türünden '<typename2>' türüne daralan eşleşen bağımsız değişkene geri kopyalanıyor"
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: a90e64cd81443831a7b8f934fea646411eb5a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796710"
---
# <a name="bc32053-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>BC32053: ' ByRef ' parametresinin ' ' değeri ' ' \<parametername> türünden ' ' türüne daralan eşleşen bağımsız değişkene geri \<typename1> kopyalanıyor \<typename2>

Bir yordam, karşılık gelen parametre türüne widens bir bağımsız değişkenle çağrılır ve parametresinden bağımsız değişkene dönüştürme daraltma olur.

 Bir sınıf veya yapı tanımladığınızda, bu sınıf veya yapı türünü diğer türlere dönüştürmek için bir veya daha fazla dönüştürme işleci tanımlayabilirsiniz. Ayrıca, bu diğer türleri sınıfınıza veya yapı türüne geri dönüştürmek için ters dönüştürme işleçleri tanımlayabilirsiniz. Sınıf veya yapı türünü bir yordam çağrısında kullandığınızda Visual Basic, bir bağımsız değişkenin türünü karşılık gelen parametresinin türüne dönüştürmek için bu dönüştürme işleçlerini kullanabilir.

 [ByRef](../modifiers/byref.md)bağımsız değişkenini geçirirseniz Visual Basic bazen bağımsız değişken değerini bir başvuruyu geçirmek yerine yordamda yerel bir değişkene kopyalar. Böyle bir durumda, yordam döndürüldüğünde Visual Basic, ardından yerel değişken değerini çağıran koddaki bağımsız değişkene geri kopyalamanız gerekir.

 Bir `ByRef` bağımsız değişken değeri yordama kopyalanırsa ve bağımsız değişkeni ve parametresi aynı türde ise, dönüştürme gerekli değildir. Ancak türler farklıysa Visual Basic her iki yönde de dönüştürmeniz gerekir. Türlerden biri sınıfınız veya yapı türtipinizdeki Visual Basic, bunu diğer türden ve arasında dönüştürmelidir. Bu dönüşümlerden biri genişletme ise, ters dönüştürme daraltma olabilir.

 **Hata kimliği:** BC32053

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Mümkünse, yordam parametresiyle aynı türde bir çağırma bağımsız değişkeni kullanın, bu nedenle Visual Basic herhangi bir dönüştürme yapması gerekmez.

- Parametre türünden farklı bir bağımsız değişken türü olan yordamı çağırmanız gerekiyorsa, ancak çağıran bağımsız değişkenine bir değer döndürmemelidir, yerine [ByVal](../modifiers/byval.md) olacak parametreyi tanımlayın `ByRef` .

- Çağırma bağımsız değişkenine bir değer döndürmenize gerek varsa, uygunsa ters dönüştürme işlecini [genişletme](../modifiers/widening.md)olarak tanımlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [İşleç Yordamları](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Operator Deyimi](../statements/operator-statement.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Visual Basic'de Tür Dönüştürmeleri](../../programming-guide/language-features/data-types/type-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
