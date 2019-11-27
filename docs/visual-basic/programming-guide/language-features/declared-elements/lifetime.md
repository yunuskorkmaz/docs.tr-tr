---
title: Ömür
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
ms.openlocfilehash: 05a39388e8aa9681af60cf86a3df8346d744b69e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345307"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic'de Ömür
Belirtilen bir öğenin *yaşam süresi* , kullanım için kullanılabilir olduğu süredir. Değişkenler ömrü olan tek öğelerdir. Bu amaçla, derleyici yordam parametreleri ve işlev döndürenleri değişkenlerin özel durumları olarak değerlendirir. Bir değişkenin ömrü, bir değeri tutabileceği süreyi temsil eder. Değeri ömrü boyunca değişebilir, ancak her zaman bir değer tutar.  
  
## <a name="different-lifetimes"></a>Farklı yaşam süreleri  
 Bir *üye değişkeni* (modül düzeyinde, herhangi bir yordam dışında) genellikle, bildirildiği öğeyle aynı yaşam süresine sahiptir. Bir sınıf veya yapıda tanımlanmış paylaşılmayan olmayan bir değişken, bildirildiği sınıf veya yapının her bir örneği için ayrı bir kopya olarak bulunur. Bu tür bir değişken, örneğiyle aynı yaşam süresine sahiptir. Ancak, bir `Shared` değişken yalnızca tek bir yaşam süresine sahiptir ve bu, uygulamanızın çalıştığı sürenin tamamına yönelik olarak sürer.  
  
 *Yerel bir değişken* (bir yordam içinde belirtilen) yalnızca, bildirildiği yordamın çalıştığı sırada bulunur. Bu, bu yordamın parametreleri ve herhangi bir işlev dönüşü için de geçerlidir. Ancak, bu yordam diğer yordamları çağırırsa, çağrılan yordamlar çalışırken yerel değişkenler değerlerini korurlar.  
  
## <a name="beginning-of-lifetime"></a>Yaşam süresi başlangıcı  
 Bir yerel değişkenin ömrü denetim, bildirildiği yordama girdiğinde başlar. Her yerel değişken, yordam çalışmaya başladıktan hemen sonra veri türü için varsayılan değere başlatılır. Yordam, başlangıç değerlerini belirten bir `Dim` bildirimiyle karşılaştığında, kodunuz daha önceden başka değerler atamış olsa bile bu değişkenleri bu değerlere ayarlar.  
  
 Bir yapı değişkeninin her üyesi ayrı bir değişken gibi başlatılır. Benzer şekilde, bir dizi değişkeninin her öğesi ayrı ayrı başlatılır.  
  
 Yordamın içindeki bir blok içinde bildirildiği değişkenler (örneğin, `For` döngüsü), yordama girişte başlatılır. Bu başlatmalar, kodunuzun engellemeyi bir daha yürüttüğünde ya da çalıştırmayacağı kadar etkili olur.  
  
## <a name="end-of-lifetime"></a>Yaşam süresi sonu  
 Bir yordam sonlandırıldığında, yerel değişkenlerinin değerleri korunmaz ve bellek geri kazanır Visual Basic. Yordamı bir sonraki kez çağırdığınızda, tüm yerel değişkenleri baştan ve yeniden başlatılan oluşturulur.  
  
 Bir sınıf veya yapının örneği sonlandırıldığında, paylaşılmayan değişkenleri belleği ve değerlerini kaybeder. Sınıfın veya yapının her yeni örneği, paylaşılmayan değişkenlerini oluşturur ve yeniden başlatır. Ancak `Shared` değişkenler, uygulamanız çalışmayı durdurana kadar korunur.  
  
## <a name="extension-of-lifetime"></a>Yaşam süresi uzantısı  
 `Static` anahtar sözcüğüyle yerel bir değişken bildirirseniz, ömrü yordamının yürütme süresinden daha uzun olur. Aşağıdaki tabloda, yordam bildiriminin bir `Static` değişkeninin ne kadar süre olduğunu nasıl belirlediği gösterilmektedir.  
  
|Yordam konumu ve paylaşımı|Statik değişken ömrü başlar|Statik değişken ömrü bitiyor|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Bir modülde (varsayılan olarak paylaşılır)|Yordamın ilk çağrılışında|Uygulamanız çalışmayı durduruyor|  
|Bir sınıfta `Shared` (yordam bir örnek üye değildir)|Yordamın ilk kez belirli bir örnekte veya sınıf ya da yapı adının kendisinde çağrılması|Uygulamanız çalışmayı durduruyor|  
|Sınıf örneğinde `Shared` değil (yordam bir örnek üyesidir)|Yordamın belirli bir örnekte ilk çağrılışında|Örnek, atık toplama (GC) için bırakıldığında|  
  
## <a name="static-variables-of-the-same-name"></a>Aynı ada sahip statik değişkenler  
 Aynı ada sahip statik değişkenleri birden fazla yordamda bildirebilirsiniz. Bunu yaparsanız, Visual Basic derleyici her bir değişkeni ayrı bir öğe olacak şekilde değerlendirir. Bu değişkenlerden birinin başlatılması, diğerlerinin değerlerini etkilemez. Aynı şekilde, bir dizi aşırı yükleme içeren bir yordam tanımlayabilir ve her bir aşırı yüklemede aynı ada sahip bir statik değişken bildirirseniz aynı durum geçerlidir.  
  
## <a name="containing-elements-for-static-variables"></a>Statik değişkenler için öğeleri içeren  
 Bir sınıf içinde, bu sınıftaki bir yordamın içinde statik bir yerel değişken bildirebilirsiniz. Ancak, yapı üyesi olarak ya da bu yapı içindeki bir yordamın yerel değişkeni olarak bir yapı içinde statik bir yerel değişken bildiremezsiniz.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, [static](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğüyle bir değişken bildirir. ( [Dim ifadesinin](../../../../visual-basic/language-reference/statements/dim-statement.md) `Static`gibi bir değiştirici kullandığında `Dim` anahtar kelimesinin gerekli olmadığına unutmayın.)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Açıklamalar  
 Yukarıdaki örnekte, yordam `runningTotal` çağıran koda döndüğünde `applesSold` değişkeni var olmaya devam eder. `runningTotal` bir sonraki sefer, `applesSold` daha önce hesaplanmış değerini korur.  
  
 `applesSold` `Static`kullanılmadan bildirilirse, önceki birikmiş değerler `runningTotal`çağrıları arasında korunmaz. `runningTotal` bir sonraki çağrılışında, `applesSold` yeniden oluşturulup 0 olarak başlatılır ve `runningTotal` yalnızca çağrıldığı değeri döndürür.  
  
### <a name="compiling-the-code"></a>Kod Derleme  
 Bir statik yerel değişkenin değerini, bildiriminin bir parçası olarak başlatabilirsiniz. Bir diziyi `Static`olarak bildirirseniz, derecesini (boyut sayısı), her boyutun uzunluğunu ve bireysel öğelerin değerlerini başlatabilirsiniz.  
  
### <a name="security"></a>Güvenlik  
 Yukarıdaki örnekte, modül düzeyinde `applesSold` bildirerek aynı yaşam süresini üretebilirsiniz. Bu şekilde bir değişkenin kapsamını değiştirdiyseniz, ancak yordam artık buna özel erişime sahip olmaz. Diğer yordamlar `applesSold` erişebileceği ve değerini değiştirebildiğinden, çalışan Toplam güvenilir olmayabilir ve kodun korunması daha zor olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
