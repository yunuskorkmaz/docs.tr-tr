---
title: Adlandırma Kuralları
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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347319"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic Adlandırma Kuralları
Visual Basic uygulamanızda bir öğe belirlediğinizde, bu adın ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır. Ancak, bir alt çizgiyle başlayan adların, [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmadığına unutmayın.  
  
 Aşağıdaki öneriler adlandırma için geçerlidir.  
  
- `FindLastRecord` ve `RedrawMyForm`gibi büyük harfle her bir ada sahip her bir sözcüğe başlayın.  
  
- İşlev ve yöntem adlarını `InitNameArray` veya `CloseDialog`gibi bir fiil ile başlatın.  
  
- `EmployeeName` veya `CarAccessory`içinde olduğu gibi, sınıf, yapı, modül ve özellik adlarını bir ada sahip olarak başlatın.  
  
- Arabirim adlarını "I" önekiyle, ardından `IComponent`gibi bir ad veya bir ad ifadesi ve `IPersistable`gibi arabirimin davranışını açıklayan bir sıfat ile başlatın. Alt çizgi kullanmayın ve kısaltmaların düzgün şekilde kullanılmasını sağlayabilirsiniz çünkü kısaltmalar karışıklıklara neden olabilir.  
  
- Olay işleyicisi adlarını, "`MouseEventHandler`" içinde olduğu gibi "`EventHandler`" son eki tarafından izlenen olay türünü açıklayan bir ad ile başlatın.  
  
- Olay bağımsız değişkeni sınıflarının adlarında, "`EventArgs`" sonekini içerir.  
  
- Bir olayda "önce" veya "After" kavramı varsa, "`ControlAdd`" veya "`ControlAdded`" içinde olduğu gibi, mevcut veya geçmiş zaman hali için bir sonek kullanın.  
  
- Uzun veya sık kullanılan şartlar için, "Köprü Metni Biçimlendirme Dili" yerine "HTML" gibi ad uzunluklarının mantıklı tutulması için kısaltmalar kullanın. Genel olarak, 32 karakterden büyük değişken adları, düşük çözünürlüğe sahip bir izleyici kümesini okumak zordur. Ayrıca, kısaltmalarınızın tüm uygulama genelinde tutarlı olduğundan emin olun. Bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında rastgele geçiş, karışıklıklara yol açabilir.  
  
- Bir dış kapsamdaki adlarla aynı olan bir iç kapsamdaki adları kullanmaktan kaçının. Yanlış değişkene erişildiğinde hatalar oluşabilir. Bir değişken ve aynı ada sahip anahtar sözcük arasında bir çakışma oluşursa, anahtar sözcüğünü uygun tür kitaplığı ile önce tanımlamalısınız. Örneğin, `Date`adlı bir değişkeniniz varsa, iç `Date` işlevini yalnızca <xref:System.DateTime.Date%2A?displayProperty=nameWithType>çağırarak kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code’da Öğe Adları Olarak Anahtar Sözcükler](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
