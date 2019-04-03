---
title: Visual Basic Adlandırma Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837084"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic Adlandırma Kuralları
Visual Basic uygulamanızda bir öğe adı, adının ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır. Ancak, alt çizgi ile başlayan adları ile uyumlu olmayan unutmayın [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Aşağıdaki öneriler, adlandırma için geçerlidir.  
  
-   Her ayrı bir sözcüğün bir ada sahip bir büyük harf olarak başlayan `FindLastRecord` ve `RedrawMyForm`.  
  
-   Bir fiil, işlevi ve yöntem adları olarak başlayan `InitNameArray` veya `CloseDialog`.  
  
-   Sınıfı, yapı, modül ve özellik adlarını içeren bir isim olarak başlayan `EmployeeName` veya `CarAccessory`.  
  
-   Arabirimi adları önek ile başlayan "I", ardından bir isim veya bir isim tümceciği gibi `IComponent`, veya arabiriminin davranışı gibi açıklayan bir sıfat `IPersistable`. Değil çizgi kullanın ve kısaltmalar kullanıcılarda kafa karışıklığına neden olabileceği için kısaltmalar gerektiğinde, kullanın.  
  
-   Olay işleyici adlarının ardından olayın türünü tanımlayan bir isim başlayın "`EventHandler`", olarak soneki"`MouseEventHandler`".  
  
-   Olay bağımsız değişkeni sınıflarının adları dahil "`EventArgs`" soneki.  
  
-   Bir olayı "önce" veya "sonra" kavramı, varsa, bir son eki var veya geçmiş şimdiki olarak kullanın "`ControlAdd`"veya"`ControlAdded`".  
  
-   Uzun veya sık kullanılan terimler için ad uzunlukları makul, tutmak için örneğin, "HTML", "Köprü Metni İşaretleme Dili" yerine kısaltmalar kullanın. Genel olarak, 32 karakterden değişken adları ayarlamak için düşük çözünürlüklü bir monitörde okunması zordur. Ayrıca, tüm uygulamanın tamamında tutarlı bir kısaltmalar emin olun. Rastgele bir projede "HTML" ve "Köprü Metni İşaretleme Dili" arasında geçiş yapma karışıklığa neden olabilir.  
  
-   Bir iç kapsamındaki bir dış kapsamdaki adları aynı adları kullanmaktan kaçının. Yanlış değişken erişildiği durumda hatalar oluşabilir. Bir değişken ile aynı ada sahip bir anahtar sözcüğü arasında bir çakışma ortaya çıkarsa, uygun bir tür kitaplığı ile koyarak anahtar sözcüğü belirlemeniz gerekir. Örneğin, adında bir değişkene varsa `Date`, iç kullanabilirsiniz `Date` işlevini çağırarak yalnızca <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code’da Öğe Adları Olarak Anahtar Sözcükler](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
