---
title: Visual Basic'de Ömür
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14a75a2c3af52f63051d02df9341faf19c3b76c7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic'de Ömür
*Ömrü* bir bildirilen süre hangi BT sırasında kullanılabilir durumda öğesidir. Değişkenleri ömürlü yalnızca öğelerdir. Bu amaç için yordam parametreleri derleyici değerlendirir ve değişkenlerin özel durumlar işlevi döndürür. Bir değişken ömrü sırasında değeri barındırabilir süreyi temsil eder. Değerini yaşam süresi boyunca değiştirebilirsiniz, ancak her zaman bir değer içerir.  
  
## <a name="different-lifetimes"></a>Farklı yaşam süresi  
 A *üye değişkeni* (herhangi bir yordam dışında Modül düzeyinde bildirilen) genellikle bu bildirilen öğesi olarak aynı yaşam süresi vardır. Sınıf veya yapı içinde bildirilmiş her örneği için ayrı bir kopya olarak bir sınıf veya yapı bildirilen paylaşılmayan bir değişken mevcut. Her bir değişken kendi örnekle aynı yaşam süresi vardır. Ancak, bir `Shared` değişkeni, uygulamanızı çalıştıran tüm zamanı sürer yalnızca bir tek ömrünü sahiptir.  
  
 A *yerel değişken* (yordam içinde bildirilen) yalnızca onu bildirilen yordamı çalışırken bulunmaktadır. Bu durum bu yordam parametrelerini ve dönüş herhangi bir işlev için de geçerlidir. Ancak, bu yordamı diğer yordamlar çağırırsa, yerel değişkenleri değerlerine çağrılan yordamları çalışırken korur.  
  
## <a name="beginning-of-lifetime"></a>Etkin kalma süresi başlangıcı  
 Denetim içinde bildirilmiş yordamı girdiğinde yerel değişken ömrü başlar. Yordam başlar başlamaz her yerel değişken veri türü için varsayılan değer başlatılmadan çalışıyor. Yordam karşılaştığında bir `Dim` ilk değerleri belirten ifade, bu ayarlar değişkenlere bu değerleri, kodunuzu zaten diğer değerleri atanmış olsa bile.  
  
 Ayrı bir değişken değilmiş gibi her bir yapı değişkeni üyesi başlatıldı. Benzer şekilde, bir dizi değişkeni her öğesinin tek tek başlatılır.  
  
 Değişkenleri bildirilen bir yordam bloğunda içinde (gibi bir `For` döngü) girişinde yordama başlatılır. Kodunuzun her zamankinden bloğu yürütür olup olmadığına bakılmaksızın bu başlatmaları etkili olur.  
  
## <a name="end-of-lifetime"></a>Yaşam süresi sonu  
 Bir yordam sonlandırıldığında kendi yerel değişkenlerin değerleri korunmaz ve Visual Basic kendi bellek geri kazanır. Yordam çağrısı başlatıldığında tüm yerel değişkenler afresh oluşturulur ve yeniden başlatıldı.  
  
 Bir sınıf veya yapı örneği sonlandırıldığında paylaşılmayan değişkenlerini kendi bellek ve bunların değerleri kaybedersiniz. Her bir yeni sınıf veya yapı örneği oluşturur ve paylaşılmayan değişkenlerini yeniden başlatır. Ancak, `Shared` değişkenleri uygulamanızı çalışmadığında kadar korunur.  
  
## <a name="extension-of-lifetime"></a>Ömür uzantısı  
 Sahip yerel bir değişken bildirirseniz `Static` anahtar sözcüğü, yaşam süresi, yordam yürütme süreden daha uzun. Aşağıdaki tabloda, nasıl yordamı bildirimi ne kadar belirler gösterilmektedir bir `Static` değişkeni yok.  
  
|Yordam konumu ve paylaşma|Statik değişken ömrü başlar|Statik değişken ömrü sona erer|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Bir modüle (varsayılan olarak paylaşılan)|İlk kez yordamı çağrılır|Uygulamanızı çalışmayı durdurduğunda|  
|Bir sınıf `Shared` (yordamı örnek üyesine değil)|İlk kez yordamı belirli bir örneğe veya sınıf veya yapı adı kendisini çağrılır|Uygulamanızı çalışmayı durdurduğunda|  
|Bir sınıf örneği içinde değil `Shared` (yordam, örnek üyesine kullanılır)|İlk kez yordamı belirli örneğinde çağrılır|Çöp toplama (GC) örneği serbest bırakıldığında|  
  
## <a name="static-variables-of-the-same-name"></a>Aynı ada sahip statik değişkenler  
 Statik değişkenler birden fazla yordam aynı adla bildirebilir. Bunu yaparsanız, Visual Basic derleyici ayrı bir öğe olması gibi her bir değişken olarak değerlendirir. Bu değişkenler birinin başlatma diğer değerlerini etkilemez. Bir yordamı aşırı kümesiyle tanımlayın ve her aşırı alanında aynı ada sahip bir statik değişken bildirme aynı geçerlidir.  
  
## <a name="containing-elements-for-static-variables"></a>Statik değişkenler için öğeleri içeren  
 Diğer bir deyişle, o sınıfta yordam içindeki bir sınıf içinde statik bir yerel değişken bildirebilirsiniz. Ancak, yapı üyesi veya bir yordam yapıyı içinde yerel bir değişken olarak bir yapı içinde statik bir yerel değişken bildiremezsiniz.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek sahip bir değişken bildirir [statik](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğü. (İhtiyacınız olmayan Not `Dim` anahtar sözcüğü zaman [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) bir değiştirici gibi kullanan `Static`.)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>Açıklamalar  
 Önceki örnekte, değişken `applesSold` yordam sonra var olmaya devam `runningTotal` çağıran kodu döndürür. Sonraki `runningTotal` olarak adlandırılır, `applesSold` önceden hesaplanan değerini korur.  
  
 Varsa `applesSold` kullanmadan bildirilmiş `Static`, önceki birikmiş değerleri çağrıları arasında korunamadı `runningTotal`. Sonraki `runningTotal` çağrıldı, `applesSold` alınan yeniden ve 0 olarak başlatılır ve `runningTotal` basitçe, onu çağrıldı aynı değeri döndürmüş.  
  
### <a name="compiling-the-code"></a>Kod Derleniyor  
 Bildiriminden bir parçası olarak statik yerel bir değişkenin değerini başlatabilirsiniz. Olması için bir dizi bildirirseniz `Static`, başlatabilir, derece (dimensions sayısı), her boyutun uzunluğu ve tek tek öğelerin değerleri.  
  
### <a name="security"></a>Güvenlik  
 Önceki örnekte bildirerek aynı yaşam üretebilir `applesSold` modülü düzeyinde. Ancak, bu şekilde bir değişkenin kapsamını değiştirdiyseniz, yordamı artık özel erişim gerekir. Diğer yordamlar erişmek için `applesSold` ve değerini değiştirmek, toplam güvenilir olabilir ve kod korumak daha zor olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
