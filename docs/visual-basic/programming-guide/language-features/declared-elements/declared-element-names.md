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
ms.openlocfilehash: 8a1b4869588c8dd030cf6276969063ec99b79e33
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046591"
---
# <a name="declared-element-names-visual-basic"></a>Bildirilen Öğe Adları (Visual Basic)
Her beyan edilen öğe *tanımlayıcı*olarak da bilinen ve kodun buna başvurmak için kullandığı bir ada sahiptir.  
  
## <a name="rules"></a>Kurallar  
 Visual Basic bir öğe adı aşağıdaki kuralları gözlemlemelidir:  
  
- Alfabetik bir karakter veya alt çizgi (`_`) ile başlamalıdır.  
  
- Yalnızca alfabetik karakter, ondalık rakam ve alt çizgi içermelidir.  
  
- Alt çizgiyle başlıyorsa, en az bir alfabetik karakter veya ondalık basamak içermesi gerekir.  
  
- En fazla 1023 karakter uzunluğunda olmalıdır.  
  
 1023 karakterlik uzunluk sınırı, tam nitelikli bir ada sahip tüm dize için de geçerlidir (örneğin `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`,).  
  
 Aşağıdaki örnekte bazı geçerli öğe adları gösterilmektedir.  
  
 `aB123__45`  
  
 `_567`  
  
 Aşağıdaki örnekte bazı geçersiz öğe adları gösterilmektedir. Birincisi yalnızca bir alt çizgi içerir, ikincisi ondalık sayıyla başlar ve üçüncüsü geçersiz bir karakter ($) içerir.  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> Alt çizgi (`_`) ile başlayan öğe adları, [Dil bağımsızlığı ve dilden bağımsız bileşenlerin](../../../../standard/language-independence-and-language-independent-components.md) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod bu adı tanımlayan bir bileşeni kullanamaz. Ancak, bir öğe adında başka bir konumdaki alt çizgi CLS uyumludur.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  
 Pratik bir şekilde, sizin de öğenin doğasını açıkça tanımlarken adınızın olabildiğince kısa olması gerekir. Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğunu ve kaynak dosya boyutunu azaltır.  
  
 Öte yandan, adınız öğenin neyi temsil ettiğini ve kodunuzun onu nasıl kullandığını yeterince tanımlamaz. Bu, kodunuzun okunabilirliğini açısından önemlidir. Başka birisi bunu anlamayı denmişse veya siz onu yazdıktan sonra uzun bir süre arıyorsanız, uygun öğe adları önemli miktarda zaman kazandırabilir.  
  
## <a name="escaped-names"></a>Kaçan adlar  
 Genellikle, öğe adı, `Case` veya `Friend`gibi Visual Basic tarafından ayrılmış bir anahtar kelimelerle eşleşmemelidir. Ancak, köşeli ayraç (`[ ]`) içine alınmış bir kaçan *adı*tanımlayabilirsiniz. Kaçış adı herhangi bir Visual Basic anahtar sözcüğüyle eşleşemez, köşeli ayraçlar herhangi bir belirsizliği ortadan kaldırır. Ayrıca, kodunuzun sonraki kısımlarında bulunan ada başvurduğunuzda de ayraçları kullanırsınız.  
  
 Genel olarak, yalnızca şu durumlarda atlanan kaçış adlarını kullanmanız gerekir:  
  
- Kodunuz, bir ad olarak kullanılmakta olan anahtar sözcüğü ayırmayan Visual Basic önceki bir sürümünden geçirildi; veya  
  
- Verilen anahtar sözcüğünün ayrılmadığından, başka bir dilde yazılmış kodla çalışıyorsunuz.  
  
 Aksi takdirde, adı bir anahtar sözcükle çakışırsa öğesini yeniden adlandırmayı düşünmelisiniz. Tümleşik geliştirme ortamı (IDE) bunu yapmanın kolay bir yolunu sağlar. Daha fazla bilgi için bkz. yeniden [düzenleme](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Adlarda büyük/küçük harf duyarlılığı  
 Visual Basic öğe adları büyük/küçük harfe duyarlıdır. Bu, derleyici yalnızca alfabetik durumda farklılık gösteren iki adı karşılaştırırken, bunları aynı ad olarak yorumladığı anlamına gelir. Örneğin, aynı tanımlanmış öğeye `ABC` başvurmak `abc` için ve öğesini dikkate alır.  
  
 Ancak, ortak dil çalışma zamanı (CLR) büyük/küçük harfe duyarlı bağlama kullanır. Bu nedenle, bir derleme veya DLL oluşturduğunuzda ve diğer derlemeler için kullanılabilir hale getirmek istediğinizde, adlarınız artık büyük/küçük harf duyarsız değildir. Örneğin, adlı `ABC`bir öğesi olan bir sınıfı tanımlarsanız ve diğer derlemeler, ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanımını kullanıyorsa, öğesini olarak `ABC`öğesine başvurmalıdır. Daha sonra sınıfınızı yeniden derlemenize ve öğenin adını olarak `abc`değiştirirseniz, sınıfınızı kullanan diğer derlemeler artık bu öğeye erişemez. Bu nedenle, bir derlemenin güncelleştirilmiş bir sürümünü serbest bırakırsanız, tüm ortak öğelerin alfabetik durumunu değiştirmemelisiniz.  
  
## <a name="names-and-locales"></a>Adlar ve yerel ayarlar  
 Adların karşılaştırılması yerel ayardan bağımsızdır. İki ad bir yerel ayarda eşleşiyorsa, bunların tüm yerel ayarlarda eşleşmesi garanti edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğeler](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
