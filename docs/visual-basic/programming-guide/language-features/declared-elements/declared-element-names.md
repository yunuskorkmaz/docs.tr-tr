---
title: Bildirilen Öğe Adları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 2f48f885b66f99ecc8c6c7e13fea7e75f0e3d24a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651485"
---
# <a name="declared-element-names-visual-basic"></a>Bildirilen Öğe Adları (Visual Basic)
Bildirilen her öğe olarak da adlandırılan bir ada sahip bir *tanımlayıcısı*, olduğu kod başvurduğu için kullanır.  
  
## <a name="rules"></a>Kurallar  
 Visual Basic'te bir öğe adı aşağıdaki kurallara uymanız gerekir:  
  
-   Alfabetik bir karakter veya alt çizgi ile başlaması gerekir (`_`).  
  
-   Yalnızca alfasayısal karakterler, ondalık sayılar ve alt çizgi içermelidir.  
  
-   Bir alt çizgiyle başlıyorsa, en az bir alfasayısal karakter veya ondalık sayı içermelidir.  
  
-   Birden fazla 1023 karakterden uzun olmamalıdır.  
  
 1023 karakter uzunluğunu de bir tam ad tüm dizeye gibi geçerlidir `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Aşağıdaki örnek, bazı geçerli öğe adları gösterir.  
  
 `aB123__45`  
  
 `_567`  
  
 Aşağıdaki örnek, bazı geçersiz öğe adları gösterir. İlk yalnızca bir alt çizgi, ikinci bir ondalık sayı ile başlar, ve üçüncü geçersiz bir karakter ($) içerir.  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Öğe adları alt çizgi ile başlayan (`_`) parçası olan [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod tür adları tanımlayan bir bileşen kullanamazlar. Ancak, alt çizgi herhangi bir öğe adı konumunda CLS uyumlu değildir.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  
 Pratik geçtiğinden bağımsız adınızı hala açık bir şekilde öğe yapısını tanımlanırken olabildiğinde kısa olması gerekir. Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğu ve kaynak dosya boyutu azaltır.  
  
 Diğer taraftan, adınızı, yeterli ne öğeyi temsil eder ve nasıl kodunuzu kullanır tanımlamaz, bu nedenle kısa olmamalıdır. Bu, kodunuzu okunabilirlik için önemlidir. Başkası anladığınızı çalışıyor ya da sizin, uzun süre yazdığınız sonra arıyorsanız, uygun öğe adları önemli miktarda zaman kaydedebilirsiniz.  
  
## <a name="escaped-names"></a>Kaçış adları  
 Genellikle, bir öğe adı herhangi bir Visual Basic tarafından gibi ayrılmış anahtar sözcükler eşleşmemelidir `Case` veya `Friend`. Ancak, tanımlayabilirsiniz bir *adı kaçışlı*, köşeli parantez içine (`[ ]`). Köşeli ayraçlar herhangi belirsizliğini kaldırmak bu yana bir kaçış karakterli adı tüm Visual Basic anahtar sözcüğü eşleştirebilirsiniz. Daha sonra kodunuzda adına başvurduğunuzda köşeli ayraçlar de kullanabilirsiniz.  
  
 Kaçış adları kullanması gereken genel olarak, yalnızca:  
  
-   Kodunuzu ad olarak kullanılan anahtar sözcüğü yedek değil Visual Basic önceki bir sürümünden geçiş yaptı; veya  
  
-   Belirtilen anahtar sözcüğü olmayan ayrılmış başka bir dilde yazılan kod ile çalışmaktadır.  
  
 Aksi takdirde, adı olan bir anahtar sözcük çakışırsa öğesini yeniden adlandırma göz önünde bulundurmalısınız. Tümleşik geliştirme ortamı (IDE), bunu yapmak için kolay bir yol sağlar. Daha fazla bilgi için bkz: [Refactoring](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Adları büyük/küçük harfe duyarlılık  
 Visual Basic'te öğe adları büyük/küçük harfe duyarsızdır. Bu, yalnızca alfabetik durumlarda farklı iki ad derleyici karşılaştırır, bunları aynı adı taşıyan yorumlar olduğunu anlamına gelir. Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğe başvurmak için.  
  
 Ancak, ortak dil çalışma zamanı (CLR) büyük küçük harfe duyarlı bağlama kullanır. Bir derlemeyi ya da bir DLL oluşturabilir ve diğer derlemeler için kullanılabilir hale getirmek, bu nedenle, adlarınızı artık büyük küçük harfe duyarsızdır. Örneğin, bir sınıf olarak adlandırılan bir öğesiyle tanımlarsanız `ABC`, ve diğer derlemelerden ortak dil çalışma zamanı sınıfınızın kullanın, öğesine başvurmalıdır `ABC`. Daha sonra sınıfınız derlenir ve öğenin adını değiştirmek, `abc`, sınıfınız kullanarak diğer derlemeler artık o öğeye erişebilir. Bu nedenle, bir derlemeyi güncelleştirilmiş bir sürümünü serbest bıraktığınızda, herhangi bir genel öğesi alfabetik durumunda değiştirmemelisiniz.  
  
## <a name="names-and-locales"></a>Adları ve yerel ayarlar  
 Yerel ayarı karşılaştırma adlarının bağımsızdır. İki adı bir yerel ayarda eşleşirse, bunlar tüm yerel eşleşen sağlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilen Öğeler](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
