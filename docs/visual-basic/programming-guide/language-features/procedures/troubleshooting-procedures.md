---
title: Yordam Sorunlarını Giderme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 492a7474a38a7e41b7e3b3f59dfa118c30256ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791800"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Yordam Sorunlarını Giderme (Visual Basic)
Bu sayfada yordamlarla çalışırken oluşabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Bir dizi türü döndüren bir işlev yordamdan  
 Varsa bir `Function` yordamı, bir dizi veri türü döndürür; kullanamazsınız `Function` dizinin öğeleri içinde değerleri depolamak için ad. Bunu yapmayı denerseniz derleyici, bir çağrı olarak yorumlar `Function`. Aşağıdaki örnek, derleyici hataları oluşturur.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Deyim `allOnes(i) = 1` çağrılacak göründüğü için bir derleyici hatasına neden olur `allOnes` yanlış veri türünde bir bağımsız değişken ile (bir singleton `Integer` yerine bir `Integer` dizisi). Deyim `Return allOnes()` çağrılacak göründüğü için bir derleyici hatası oluşturur `allOnes` ile hiçbir bağımsız değişken.  
  
 **Doğru yaklaşım:** Döndürülecek bir dizi öğelerini değiştirebilmesi için dahili bir dizi yerel bir değişken tanımlayın. Aşağıdaki örnek, hata olmadan derler.  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Bağımsız değişken değil değiştirilen yordam çağrısı tarafından  
 Bir yordam çağıran koddaki bağımsız değişken arka plandaki bir programlama öğesi değiştirmeye izin vermek istiyorsanız, başvuruya göre geçmesi gerekir. Ancak geçirdiğiniz değere göre olsa bile bir yordam bir başvuru türü bağımsız değişkeni öğelerine erişebilirsiniz.  
  
- **Değişken arka plandaki**. Temel alınan değişken öğenin kendisinin değerini değiştirmek yordamı izin vermek için yordam parametre bildirmeniz gerekir [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Geçersiz kılarsınız çünkü Ayrıca, çağıran kodun bağımsız değişken parantez içine almalısınız değil `ByRef` mekanizması geçirme.  
  
- **Başvuru türü öğeleri**. Bir parametre bildirirseniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), temel alınan değişken öğenin kendisinin yordamı değiştiremezsiniz. Ancak, bağımsız değişken bir başvuru türü ise, değişken değerini değiştiremez olsa bile yordamı işaret ettiği, nesnenin üyeleri değiştirebilir. Örneğin, bir dizi değişken bağımsız değişken ise yordamı için yeni bir dizi atama yapılamaz ancak bir veya daha fazla alt öğeleri değiştirebilirsiniz. Değiştirilen öğeler, temel alınan dizi değişkeni çağıran koddaki yansıtılır.  
  
 Aşağıdaki örnek, bir dizi değişkenini değere göre alabilir ve çalışan iki yordamı alt öğelerde tanımlar. Yordam `increase` yalnızca her öğeye ekler. Yordam `replace` yeni bir dizi parametresine atar `a()` ve sonra her öğeye ekler. Ancak, yakaladığından çağıran koddaki temel alınan dizi değişkeni etkilemez çünkü `a()` bildirildiği `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 Aşağıdaki örnek çağrılar `increase` ve `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü `n` bir başvuru türüdür `increase` kendisine geçirilen olsa bile, bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrı görüntüler "replace(n) sonra: 11, 21, 31, 41". Çünkü `n` geçirilen `ByVal`, `replace` değişkeni değiştiremezsiniz `n` yeni bir dizi atayarak. Zaman `replace` yeni dizi örneği oluşturur `k` ve yerel bir değişkene atar `a`, başvuru kaybeder `n` çağıran kod tarafından geçirilen. Artırır, üyelerinin `a`, yalnızca yerel dizi `k` etkilenir.  
  
 **Doğru yaklaşım:** Temel alınan değişken öğenin kendisini değiştirebilmesi için başvuruya göre geçirin. Aşağıdaki örnek, değişiklik bildiriminde gösterir. `replace` çağıran koddaki başka bir dizi yerine kendisine sağlayan.  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>Aşırı tanımlamak oluşturulamıyor  
 Bir yordamı aşırı yüklenmiş bir sürümünü tanımlamak istiyorsanız, aynı ada ancak farklı bir imza kullanmanız gerekir. Derleyici, aynı imzaya sahip bir aşırı bildirimden ayırt edilemiyor, bir hata oluşturur.  
  
 *İmza* bir yordam yordam adı ve parametre listesine göre belirlenir. Her aşırı yükleme tüm diğer aşırı yüklemeler aynı ada sahip olmalıdır, ancak tüm bunları bir imza bileşenlerinin en az birinde farklı olmalıdır. Daha fazla bilgi için [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
 Aşağıdaki öğeler, bunlar parametre listesine ait olsa bile yordamın imza bileşenlerinin değildir:  
  
- Yordam değiştiricisi anahtar sözcükler gibi `Public`, `Shared`, ve `Static`  
  
- Parametre adları  
  
- Parametre değiştiricisi anahtar sözcükler gibi `ByRef` ve `Optional`  
  
- (bir dönüşüm işleci dışında) dönüş değerinin veri türü  
  
 Yalnızca bir veya daha fazla önceki öğelerin değiştirerek bir yordamı aşırı yükleyemez.  
  
 **Doğru yaklaşım:** Bir yordamı aşırı yükleme tanımlayabilmek için imza değişiklik gerekir. Aynı adı kullanmanız gerektiğinden, sayısını, sırasını veya parametrelerinin veri türleri farklı olmalıdır. Genel bir yordamda türü parametre sayısı değişebilir. İçinde bir dönüştürme operatörünün ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)), dönüş türü farklılık gösterebilir.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>İsteğe bağlı bir çözümleme ve ParamArray bağımsız değişkenleri, aşırı yükleme  
 Bir veya daha fazla bilgi içeren bir yordamı aşırı yükleme varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri veya [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre gerekir önlemek herhangi bir çoğaltma *örtük aşırı yüklemeleri*. Bilgi için [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Yanlış bir sürümü, aşırı yüklenmiş bir yordamı çağırma  
 Bir yordamın birden fazla aşırı yüklenmiş sürümleri varsa, ile tüm bunların parametre listeleri hakkında bilgi sahibi olmanız ve Visual Basic çağrıları aşırı yüklemeler arasında nasıl çözümler? anlamanız gerekir. Aksi takdirde hedeflenen farklı bir aşırı yüklemesini çağırabilir.  
  
 Hangi aşırı yüklemesini çağırmak istediğinizde belirlediğinizde, aşağıdaki kurallara uymanız dikkat edin:  
  
- Bağımsız değişkenlerin ve doğru sırada doğru numarayı girin.  
  
- İdeal olarak, değişkenleriniz, aynı veri türleri karşılık gelen parametre olmalıdır. Herhangi bir durumda, her bağımsız değişken veri türünü, karşılık gelen parametre genişlemesi gerekir. Bu bile geçerlidir [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kümesine `Off`. Aşırı yükleme, bağımsız değişken listesinde, herhangi bir daraltma dönüşümü bir aşırı gerektiriyorsa, çağrılması için uygun değil.  
  
- Genişletme gerektiren bağımsız değişkenleri sağlayın, veri türlerini olabildiğince karşılık gelen parametre veri türleri için mümkün olduğunca yakın olun. İki veya daha fazla aşırı yüklemeler, bağımsız değişken veri türleri kabul ederseniz, derleyici çağrınız genişletme için en az miktarını çağıran aşırı çözümler.  
  
 Kullanarak veri türü uyuşmazlığı olasılığını azaltabilirsiniz [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) değişkenleriniz hazırlanırken dönüştürme anahtar sözcüğü.  
  
### <a name="overload-resolution-failure"></a>Aşırı yükleme çözümlemesi başarısız  
 Aşırı yüklenmiş bir yordamı çağırdığınızda derleyici aşırı tüm birini ortadan kaldırmak çalışır. Başarılı olursa, bu aşırı yükleme çağrısı çözümler. Tüm aşırı yüklemeler ortadan veya tek bir aday için uygun aşırı indiremezsiniz gerekiyorsa, bir hata oluşturur.  
  
 Aşağıdaki örnekte, aşırı yükleme çözümleme işlemi gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 İlk çağrıda nedeniyle derleyici ilk aşırı yükleme ortadan ilk bağımsız değişken türünü (`Short`) daraltır karşılık gelen parametre türüne (`Byte`). Çünkü ikinci aşırı yükleme her bağımsız değişken türü, daha sonra üçüncü aşırı yükleme ortadan kaldırır (`Short` ve `Single`) üçüncü aşırı yükleme türüne karşılık gelen widens (`Integer` ve `Single`). İsteğe bağlı olarak derleyici arama için kullanır, böylece daha az genişletme, ikinci aşırı yükleme gerektirir.  
  
 İkinci çağrıda, derleyici aşırı daraltma göndermemeniz hiçbirini ortadan olamaz. Daha az bir bağımsız değişken türlerini genişletme ile ikinci aşırı yükleme çağırabilirsiniz çünkü aynı nedenle, ilk çağrıda olduğu gibi üçüncü aşırı yükleme kaldırır. Ancak, derleyici ilk ve ikinci aşırı yükler arasında çözümlenemiyor. Her diğer karşılık gelen türe widens bir tanımlanan parametre türüne sahip (`Byte` için `Short`, ancak `Single` için `Double`). Derleyici, bu nedenle bir aşırı yükleme çözünürlüğü hata oluşturur.  
  
 **Doğru yaklaşım:** Belirsizlik olmadan aşırı yüklenmiş bir yordamı çağırma yapabilmek için kullanmak [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) parametre türleri için bağımsız değişken veri türleri eşleştirmek için. Aşağıdaki örnek, bir çağrı gösterir `z` , ikinci aşırı yükleme çözünürlüğü zorlar.  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>İsteğe bağlı bir çözümleme ve ParamArray bağımsız değişkenleri, aşırı yükleme  
 Son parametre bildirilen dışında aynı imzaya bir yordamın iki aşırı yükleme varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) birinde ve [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) diğerinde derleyici Bu yordam çağrısı çözümler en yakın eşleşme göre. Daha fazla bilgi için [aşırı yükleme çözünürlüğü](./overload-resolution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
