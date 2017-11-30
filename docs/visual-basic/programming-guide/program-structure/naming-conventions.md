---
title: "Visual Basic Adlandırma Kuralları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a59139b57568810de80de764388eeffa5f8d7ac9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic Adlandırma Kuralları
Visual Basic uygulamanızda öğenin adlandırdığınızda, bu adının ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır. Ancak, alt çizgi ile başlayan adları ile uyumlu olmadığını unutmayın [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 Adlandırma için aşağıdaki önerileri uygulayın.  
  
-   Her ayrı bir sözcük bir büyük harf olan bir ad olarak başlamak `FindLastRecord` ve `RedrawMyForm`.  
  
-   Bir fiil işlevi ve yöntem adları olarak başlamak `InitNameArray` veya `CloseDialog`.  
  
-   Sınıfı, yapısı, modül ve özellik adlarıyla bir isim olarak başlamak `EmployeeName` veya `CarAccessory`.  
  
-   Arabirim adları önek ile başlayan "T", bir isim veya bir isim deyimi gibi izlemelidir `IComponent`, veya arabiriminin davranışı gibi açıklayan gelen ile `IPersistable`. Alt çizgi kullanma ve kısaltmalar karışıklığa neden olabileceğinden kısaltmalar tutumlu, kullanın.  
  
-   Olay işleyici adları ve ardından olay türünü tanımlayan bir isim başlayın "`EventHandler`", ın soneki"`MouseEventHandler`".  
  
-   Olay bağımsız değişkeni sınıfların, adlarında "`EventArgs`" soneki.  
  
-   Bir olay "önce" veya "sonra" kavramı, varsa, bir sonek yoksa veya geçmiş zamanın olarak kullanın "`ControlAdd`"veya"`ControlAdded`".  
  
-   Uzun veya sık kullanılan terimler için ad uzunlukları makul, tutmak için örneğin, "HTML", "Köprü Metni Biçimlendirme Dili" yerine kısaltmalar kullanın. Genel olarak, değişken adları 32 karakterden daha düşük bir çözüm ayarlamak monitörde okumak zordur. Ayrıca, kısaltmalar tüm uygulama genelinde tutarlı olduğundan emin olun. Rastgele bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında geçiş yapma karışıklığa neden olabilir.  
  
-   Bir dış kapsamdaki adları ile aynı olan bir iç kapsamda adlarında kullanmaktan kaçının. Yanlış değişken erişiliyorsa hatalar neden olabilir. Anahtar sözcüğü aynı ada sahip bir değişken arasında bir çakışma meydana gelirse, uygun bir tür kitaplığı ile koyarak anahtar sözcüğü tanımlamanız gerekir. Adlı bir değişken varsa, örneğin, `Date`, iç kullanabilirsiniz `Date` çağırarak yalnızca işlevi <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodda öğe adları olarak anahtar sözcükler](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Program yapısı ve kod kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic Dil Başvurusu](../../../visual-basic/language-reference/index.md)
