---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic adlandırma kuralları'
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
ms.openlocfilehash: 058d3b06ca1da71c4d8993c6bd451531ec758dbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461014"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic Adlandırma Kuralları

Visual Basic uygulamanızda bir öğe belirlediğinizde, bu adın ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır. Ancak, bir alt çizgiyle başlayan adların, [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmadığına unutmayın.  
  
 Aşağıdaki öneriler adlandırma için geçerlidir.  
  
- Bir ad içindeki her bir sözcüğü, ve ' de olduğu gibi büyük harfle `FindLastRecord` başlatın `RedrawMyForm` .  
  
- Veya gibi bir fiil ile işlev ve yöntem adlarını başlatın `InitNameArray` `CloseDialog` .  
  
- Ya da ' de olduğu gibi, sınıf, yapı, modül ve özellik adlarını bir ad ile başlatın `EmployeeName` `CarAccessory` .  
  
- Arabirim adlarını "I" önekiyle, ardından bir ad veya bir ad ifadesi ile, örneğin gibi `IComponent` arabirimin davranışını açıklayan bir sıfat ile başlatın `IPersistable` . Alt çizgi kullanmayın ve kısaltmaların düzgün şekilde kullanılmasını sağlayabilirsiniz çünkü kısaltmalar karışıklıklara neden olabilir.  
  
- Olay işleyicisi adlarını olay türünü açıklayan bir ad ile başlatın ve "" `EventHandler` içinde olduğu gibi "" son eki tarafından gelir `MouseEventHandler` .  
  
- Olay bağımsız değişkeni sınıflarının adlarında " `EventArgs` " sonekini ekleyin.  
  
- Bir olayda "önce" veya "After" kavramı varsa, " `ControlAdd` " veya "" içinde olduğu gibi, mevcut veya geçmiş zaman hali için bir sonek kullanın `ControlAdded` .  
  
- Uzun veya sık kullanılan şartlar için, "Köprü Metni Biçimlendirme Dili" yerine "HTML" gibi ad uzunluklarının mantıklı tutulması için kısaltmalar kullanın. Genel olarak, 32 karakterden büyük değişken adları, düşük çözünürlüğe sahip bir izleyici kümesini okumak zordur. Ayrıca, kısaltmalarınızın tüm uygulama genelinde tutarlı olduğundan emin olun. Bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında rastgele geçiş, karışıklıklara yol açabilir.  
  
- Bir dış kapsamdaki adlarla aynı olan bir iç kapsamdaki adları kullanmaktan kaçının. Yanlış değişkene erişildiğinde hatalar oluşabilir. Bir değişken ve aynı ada sahip anahtar sözcük arasında bir çakışma oluşursa, anahtar sözcüğünü uygun tür kitaplığı ile önce tanımlamalısınız. Örneğin, adlı bir değişkene sahipseniz `Date` , `Date` yalnızca çağırarak iç işlevi kullanabilirsiniz <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code’da Öğe Adları Olarak Anahtar Sözcükler](keywords-as-element-names-in-code.md)
- [Me, My, MyBase ve MyClass](me-my-mybase-and-myclass.md)
- [Bildirilen Öğe Adları](../language-features/declared-elements/declared-element-names.md)
- [Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)
- [Visual Basic dil başvurusu](../../language-reference/index.md)
