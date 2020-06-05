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
ms.openlocfilehash: 377f0e0b5240c3da931dc4af5439aba8924f1e81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357147"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic'de Ömür
Belirtilen bir öğenin *yaşam süresi* , kullanım için kullanılabilir olduğu süredir. Değişkenler ömrü olan tek öğelerdir. Bu amaçla, derleyici yordam parametreleri ve işlev döndürenleri değişkenlerin özel durumları olarak değerlendirir. Bir değişkenin ömrü, bir değeri tutabileceği süreyi temsil eder. Değeri ömrü boyunca değişebilir, ancak her zaman bir değer tutar.  
  
## <a name="different-lifetimes"></a>Farklı yaşam süreleri  
 Bir *üye değişkeni* (modül düzeyinde, herhangi bir yordam dışında) genellikle, bildirildiği öğeyle aynı yaşam süresine sahiptir. Bir sınıf veya yapıda tanımlanmış paylaşılmayan olmayan bir değişken, bildirildiği sınıf veya yapının her bir örneği için ayrı bir kopya olarak bulunur. Bu tür bir değişken, örneğiyle aynı yaşam süresine sahiptir. Ancak, bir `Shared` değişken yalnızca tek bir yaşam süresine sahiptir ve bu, uygulamanızın çalıştığı sürenin tamamına yönelik olarak sürer.  
  
 *Yerel bir değişken* (bir yordam içinde belirtilen) yalnızca, bildirildiği yordamın çalıştığı sırada bulunur. Bu, bu yordamın parametreleri ve herhangi bir işlev dönüşü için de geçerlidir. Ancak, bu yordam diğer yordamları çağırırsa, çağrılan yordamlar çalışırken yerel değişkenler değerlerini korurlar.  
  
## <a name="beginning-of-lifetime"></a>Yaşam süresi başlangıcı  
 Bir yerel değişkenin ömrü denetim, bildirildiği yordama girdiğinde başlar. Her yerel değişken, yordam çalışmaya başladıktan hemen sonra veri türü için varsayılan değere başlatılır. Yordam, `Dim` başlangıç değerlerini belirten bir deyimle karşılaştığında, kodunuz kendisine zaten başka değerler atamış olsa bile bu değişkenleri bu değerlere ayarlar.  
  
 Bir yapı değişkeninin her üyesi ayrı bir değişken gibi başlatılır. Benzer şekilde, bir dizi değişkeninin her öğesi ayrı ayrı başlatılır.  
  
 Yordam içindeki bir blok içinde belirtilen değişkenler (örneğin, `For` döngü) yordama girişte başlatılır. Bu başlatmalar, kodunuzun engellemeyi bir daha yürüttüğünde ya da çalıştırmayacağı kadar etkili olur.  
  
## <a name="end-of-lifetime"></a>Yaşam süresi sonu  
 Bir yordam sonlandırıldığında, yerel değişkenlerinin değerleri korunmaz ve bellek geri kazanır Visual Basic. Yordamı bir sonraki kez çağırdığınızda, tüm yerel değişkenleri baştan ve yeniden başlatılan oluşturulur.  
  
 Bir sınıf veya yapının örneği sonlandırıldığında, paylaşılmayan değişkenleri belleği ve değerlerini kaybeder. Sınıfın veya yapının her yeni örneği, paylaşılmayan değişkenlerini oluşturur ve yeniden başlatır. Ancak, `Shared` uygulamanız çalışmayı durdurana kadar değişkenler korunur.  
  
## <a name="extension-of-lifetime"></a>Yaşam süresi uzantısı  
 Anahtar sözcüğü ile yerel bir değişken bildirirseniz `Static` , ömrü yordamının yürütme süresinden daha uzun olur. Aşağıdaki tabloda, yordam bildiriminin bir değişkenin ne kadar süre olduğunu nasıl belirlediği gösterilmektedir `Static` .  
  
|Yordam konumu ve paylaşımı|Statik değişken ömrü başlar|Statik değişken ömrü bitiyor|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Bir modülde (varsayılan olarak paylaşılır)|Yordamın ilk çağrılışında|Uygulamanız çalışmayı durduruyor|  
|Bir sınıfta `Shared` (yordam bir örnek üye değildir)|Yordamın ilk kez belirli bir örnekte veya sınıf ya da yapı adının kendisinde çağrılması|Uygulamanız çalışmayı durduruyor|  
|Sınıf örneğinde değil `Shared` (yordam bir örnek üyesidir)|Yordamın belirli bir örnekte ilk çağrılışında|Örnek, atık toplama (GC) için bırakıldığında|  
  
## <a name="static-variables-of-the-same-name"></a>Aynı ada sahip statik değişkenler  
 Aynı ada sahip statik değişkenleri birden fazla yordamda bildirebilirsiniz. Bunu yaparsanız, Visual Basic derleyici her bir değişkeni ayrı bir öğe olacak şekilde değerlendirir. Bu değişkenlerden birinin başlatılması, diğerlerinin değerlerini etkilemez. Aynı şekilde, bir dizi aşırı yükleme içeren bir yordam tanımlayabilir ve her bir aşırı yüklemede aynı ada sahip bir statik değişken bildirirseniz aynı durum geçerlidir.  
  
## <a name="containing-elements-for-static-variables"></a>Statik değişkenler için öğeleri içeren  
 Bir sınıf içinde, bu sınıftaki bir yordamın içinde statik bir yerel değişken bildirebilirsiniz. Ancak, yapı üyesi olarak ya da bu yapı içindeki bir yordamın yerel değişkeni olarak bir yapı içinde statik bir yerel değişken bildiremezsiniz.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, [static](../../../language-reference/modifiers/static.md) anahtar sözcüğüyle bir değişken bildirir. ( `Dim` [Dim ifadesinde](../../../language-reference/statements/dim-statement.md) gibi bir değiştirici kullandığında anahtar kelimesinin gerekli olmadığına unutmayın `Static` .)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Yorumlar  
 Önceki örnekte, `applesSold` yordam `runningTotal` çağıran koda geri döndüğünde değişken mevcut olmaya devam eder. Bir sonraki sefer `runningTotal` çağrıldığında, `applesSold` önceden hesaplanan değerini korur.  
  
 Kullanılmadan `applesSold` bildirilirse `Static` , önceki birikmiş değerler öğesine yapılan çağrılar arasında korunmaz `runningTotal` . Bir sonraki sefer `runningTotal` çağrıldığında, yeniden `applesSold` oluşturulup 0 olarak başlatılmış ve `runningTotal` yalnızca çağrılan aynı değeri döndürmüş olabilir.  
  
### <a name="compile-the-code"></a>Kodu derle  
 Bir statik yerel değişkenin değerini, bildiriminin bir parçası olarak başlatabilirsiniz. Bir dizi belirtmek istiyorsanız `Static` , derecesini (boyut sayısı), her boyutun uzunluğunu ve tek tek öğelerin değerlerini başlatabilirsiniz.  
  
### <a name="security"></a>Güvenlik  
 Yukarıdaki örnekte, modül düzeyinde bildirerek aynı yaşam süresini üretebilirsiniz `applesSold` . Bu şekilde bir değişkenin kapsamını değiştirdiyseniz, ancak yordam artık buna özel erişime sahip olmaz. Diğer yordamlar erişebileceği `applesSold` ve değerini değiştirebildiğinden, çalışan Toplam güvenilir olmayabilir ve kodun korunması daha zor olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../language-reference/modifiers/shared.md)
- [Nothing](../../../language-reference/nothing.md)
- [Bildirilen Öğe Adları](declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Kapsam](scope.md)
- [Visual Basic erişim düzeyleri](access-levels.md)
- [Değişkenler](../variables/index.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
- [Veri Türü Sorunlarını Giderme](../data-types/troubleshooting-data-types.md)
- [Se](../../../language-reference/modifiers/static.md)
