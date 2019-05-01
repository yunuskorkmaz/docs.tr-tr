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
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61828626"
---
# <a name="declared-element-names-visual-basic"></a>Bildirilen Öğe Adları (Visual Basic)
Bildirilen her öğe olarak da bilinen bir ada sahip bir *tanımlayıcı*, olan kod başvurduğu için kullanır.  
  
## <a name="rules"></a>Kurallar  
 Visual Basic'te bir öğe adı, aşağıdaki kurallara uymanız gerekir:  
  
- Alfabetik bir karakter veya alt çizgi ile başlamalıdır (`_`).  
  
- Yalnızca alfabetik karakterler, ondalık sayılar ve alt çizgi içermelidir.  
  
- Bir alt çizgiyle başlıyorsa en az bir alfasayısal karakter veya ondalık sayı içermelidir.  
  
- Daha fazla 1023 karakterden uzun olmamalıdır.  
  
 Uzunluk sınırını 1023 karakteri de tam adı, tüm dize gibi geçerlidir `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Aşağıdaki örnek, bazı geçerli öğe adları gösterir.  
  
 `aB123__45`  
  
 `_567`  
  
 Aşağıdaki örnek, bazı geçersiz öğe adları gösterir. İlk yalnızca bir alt çizgi içeren ikinci bir ondalık basamak ile başlar ve üçüncü geçersiz karakter ($) içeriyor.  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Bir alt çizgiyle başlayan öğe adları (`_`) parçası değildir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod tür adları tanımlayan bir bileşen kullanamazlar. Ancak, diğer konumunda bir öğe adı alt çizgi, CLS uyumlu değildir.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  
 Pratik olursa olsun adınızı öğe yapısını açıkça hala tanımlanırken olabildiğince kısa olmalıdır. Bu, kodunuzun okunabilirliği geliştirir ve satır uzunluğu ve kaynak dosya boyutunu azaltır.  
  
 Öte yandan, adınız, yeterince ne öğesi temsil eder ve nasıl kodunuzun kullandığı tanımlamaz, bu nedenle kısa olmamalıdır. Bu, kodunuzun okunabilirliği için önemlidir. Başka birisi tarafından anlayabilmek çalışıyor ya da sizin, uzun bir süre sonra yazdığınız kullanmak istiyorsanız, uygun öğe adları önemli miktarda zaman kaydedebilirsiniz.  
  
## <a name="escaped-names"></a>Kaçış adları  
 Genellikle, bir öğe adı herhangi bir Visual Basic, gibi ayrılmış anahtar sözcükler eşleşmemelidir `Case` veya `Friend`. Ancak, tanımlayabileceğiniz bir *adı kaçış*, köşeli parantez içine (`[ ]`). Belirsizlik köşeli ayraçları Kaldır beri kaçan bir adı bir Visual Basic anahtar sözcüğü eşleşebilir. Daha sonra kodunuzda adına başvurduğunuzda parantez de kullanabilirsiniz.  
  
 Genel olarak, kaçış adları kullanmanız gereken yalnızca:  
  
- Kodunuzu anahtar sözcüğü bir ad kullanılan yedek değil Visual Basic'in önceki bir sürümden geçiş yaptı; veya  
  
- Belirli bir anahtar değil ayrılmış başka bir dilde yazılmış kodu ile çalışma.  
  
 Aksi takdirde, adını, anahtar sözcüğü ile çakışırsa, öğeyi yeniden adlandırmadan düşünmelisiniz. Tümleşik geliştirme ortamı (IDE), bunu yapmak için kolay bir yol sağlar. Daha fazla bilgi için [yeniden düzenleme](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Adları büyük/küçük harf duyarlılığı  
 Visual Basic'te öğe adları büyük/küçük harfe duyarsızdır. Bu, derleyici alfabetik yalnızca farklı iki ad karşılaştırır, bunların aynı ada yorumlar, anlamına gelir. Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğeye başvurmak üzere.  
  
 Ancak, ortak dil çalışma zamanı (CLR) büyük/küçük harfe bağlama kullanır. Bir derleme veya bir DLL üretmek ve diğer derlemeleri kullandırmak, bu nedenle, adları artık büyük küçük harf duyarlıdır. Örneğin, adında bir öğe ile bir sınıf tanımlama `ABC`, ve diğer derlemeler ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanın, öğesine başvurmalıdır `ABC`. Daha sonra sınıfı yeniden derleyin ve öğenin adını değiştirmek `abc`, sınıfınıza kullanarak diğer derlemeleri artık bu öğeye erişebilir. Bu nedenle, bir derleme güncelleştirilmiş bir sürümünü serbest bıraktığınızda, ortak öğeleri alfabetik durumunu değiştirmemesi gerekir.  
  
## <a name="names-and-locales"></a>Adları ve yerel ayarlar  
 Yerel ayarı karşılaştırma adlarının bağımsızdır. Bir yerel ayarda iki adlarıyla, tüm yerel ayarlarda eşleşecek şekilde garanti edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğeler](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
