---
title: Visual Basic'de Ömür
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824929"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic'de Ömür
*Ömrü* bir bildirilen süre sırasında hangi BT kullanıma açık öğesidir. Değişkenleri ömürlü yalnızca öğelerdir. Bu amaçla, derleyici parametreler değerlendirir ve değişkenlerin özel durumlar işlevi döndürür. Bir değişkenin ömrü değeri biriken içerebileceği süreyi temsil eder. Yaşam süresi boyunca değerini değiştirebilirsiniz, ancak her zaman belirli bir değeri tutar.  
  
## <a name="different-lifetimes"></a>Farklı bir yaşam süresi yok  
 A *üye değişkeni* (dışında her türlü yordam, Modül düzeyinde bildirilmiş) genellikle bunu bildirilen öğe olarak aynı kullanım ömrü vardır. Bir sınıf veya yapı içinde bildirilen bir paylaşılmayan değişken sınıf veya yapı içinde bildirildiği her örneği için ayrı bir kopya olarak mevcut. Her bir değişken, örnek olarak aynı kullanım ömrü vardır. Ancak, bir `Shared` değişkeni, uygulamanızı çalıştıran tüm zamanı sürer yalnızca bir tek ömür, sahip.  
  
 A *yerel değişken* (bir yordam içinde bildirilen) yalnızca onu bildirilen yordamı çalışırken mevcut. Bu da bu yordamın parametreleri ve dönüş herhangi bir işlev için de geçerlidir. Ancak, bu yordamı diğer yordamlar çağırırsa, çağrılan yordamları çalışırken yerel değişkenlerin değerlerini korur.  
  
## <a name="beginning-of-lifetime"></a>Etkin kalma süresi başlangıcı  
 Yerel değişkenin ömrü içinde bildirildiği yordamı denetime girdiğinde başlar. Yordamı başlar başlamaz her yerel değişken veri türü için varsayılan değer başlatılır çalışıyor. Yordamı karşılaştığında bir `Dim` başlangıç değerleri belirten bir deyimi ayarlar değişkenlere bu değerleri, kodunuzu zaten diğer değerleri atanmış bile.  
  
 Ayrı bir değişken gibi bir yapı değişken her üyesi başlatıldı. Benzer şekilde, bir dizi değişkeni her öğe ayrı ayrı başlatılır.  
  
 Bir blok içinde bir yordam içinde tanımlanan değişkenleri (gibi bir `For` döngü) girişi yordama başlatılır. Kodunuzu şimdiye kadar bloğun olup olmadığına bakılmaksızın bu başlatmalar geçerli olur.  
  
## <a name="end-of-lifetime"></a>Yaşam süresi sonu  
 Bir yordam sonlandığında, kendi yerel değişkenlerin değerleri korunmaz ve Visual Basic kullandığı belleği geri kazanır. Yordamı, bir sonraki çağırışınızda tüm yerel değişkenlerin parçalarından oluşturulur ve yeniden başlatıldı.  
  
 Bir sınıfın veya yapının örneği sonlandığında, kendi paylaşılmayan değişkenler, bellek ve bunların değerlerini kaybedersiniz. Her yeni bir sınıf veya yapının örneğini oluşturur ve kendi paylaşılmayan değişkenler yeniden başlatır. Ancak, `Shared` değişkenleri uygulamanızın çalışmayı kadar korunur.  
  
## <a name="extension-of-lifetime"></a>Yaşam süresi uzantısı  
 Yerel bir değişken bildirirseniz `Static` anahtar sözcüğü, yaşam süresi, kendi yordamı yürütme süreden daha uzun. Aşağıdaki tabloda yordam bildirimi ne kadar süreyle nasıl belirlediğini gösterir bir `Static` değişkeni yok.  
  
|Yordam konumu ve paylaşma|Statik değişken ömrü başlar|Statik değişken ömrü sona erer|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Bir modüle (varsayılan olarak paylaşılan)|İlk kez yordamı çağrılır|Uygulamanızın çalışmayı durdurduğunda|  
|Bir sınıftaki `Shared` (yordamı bir örnek üyesi değildir)|İlk kez yordamı belirli bir örneğine veya sınıf veya yapı adı kendisi üzerinde çağrılır|Uygulamanızın çalışmayı durdurduğunda|  
|İçinde bir sınıfın bir örneği değil `Shared` (yordamı, bir örnek üyesi olduğu)|İlk kez yordamı belirli bir örneği üzerinde çağrılır|Çöp toplama (GC) örneği yayınlandığında|  
  
## <a name="static-variables-of-the-same-name"></a>Statik değişkenler aynı ada sahip  
 Statik değişkenler aynı adla birden fazla yordam bildirebilirsiniz. Bunu yaparsanız, Visual Basic Derleyicisi ayrı bir öğe gibi her bir değişken olarak değerlendirir. Bu değişkenlerin birinin başlatma diğer değerlerini etkilemez. Bir yordamı aşırı sayıda tanımlayın ve her aşırı yükleme aynı ada sahip bir statik değişken bildirimini durumunda da aynısı geçerlidir.  
  
## <a name="containing-elements-for-static-variables"></a>Statik değişkenler için öğeleri içeren  
 Bu sınıfta bir yordam içinde statik bir yerel değişken bir sınıf içindeki diğer bir deyişle, bildirebilirsiniz. Ancak, yapı üyesi veya bir yordam, yapı içinde yerel bir değişken olarak bir yapı içinde statik bir yerel değişken bildiremezsiniz.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir değişken bildirir [statik](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğü. (Gerekmeyen Not `Dim` anahtar sözcüğü, [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) gibi bir değiştirici kullanan `Static`.)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Açıklamalar  
 Yukarıdaki örnekte, değişken `applesSold` yordam sonra varolmaya devam eder `runningTotal` çağrıldığı koda döndürür. Sonraki `runningTotal` çağrıldığında `applesSold` önceden hesaplanmış değerini korur.  
  
 Varsa `applesSold` olmadan bildirilmiş `Static`, önceki birikmiş değerleri çağrılar üzerinden korunamadı `runningTotal`. Sonraki `runningTotal` çağrıldı, `applesSold` alınan yeniden oluşturulması ve 0 olarak başlatılır ve `runningTotal` yalnızca aynı değeri ile bunu çağrıldı döndüğünüzü.  
  
### <a name="compiling-the-code"></a>Kod Derleniyor  
 Bildiriminin bir parçası olarak bir statik yerel değişkenin değerini yeniden başlatabilirsiniz. Bir dizi olarak bildirirseniz `Static`, başlatabilir, rank (boyut sayısı), tek tek öğelerin değerlerinin yanı sıra her boyutun uzunluğu.  
  
### <a name="security"></a>Güvenlik  
 Önceki örnekte, aynı yaşam bildirerek üretebilir `applesSold` Modül düzeyinde. Ancak, bu şekilde bir değişkenin kapsamını değiştirdiyseniz, yordam artık bu özel kullanım erişimi yoktur. Diğer yordamlar erişemiyor çünkü `applesSold` ve değerini değiştirmek, değişen toplamı güvenilir olabilir ve kod korumak daha zor olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
