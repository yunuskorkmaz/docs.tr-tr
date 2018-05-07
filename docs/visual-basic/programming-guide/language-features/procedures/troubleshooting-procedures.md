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
ms.openlocfilehash: f66e7f7444f2d3b1bb58bae6008f8896c81c2f76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-procedures-visual-basic"></a>Yordam Sorunlarını Giderme (Visual Basic)
Bu sayfada yordamlarla çalışırken ortaya çıkabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Bir dizi türü bir işlev yordamından döndürme  
 Varsa bir `Function` yordamı bir dizi veri türünü döndürüyor, kullanamazsınız `Function` dizisinin öğelerinde değerlerini depolamak için ad. Bunu yapmak çalışırsanız, derleyici, çağrı olarak yorumlar `Function`. Aşağıdaki örnek derleyici hataları oluşturur.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Deyim `allOnes(i) = 1` çağrısı göründüğünden derleyici hatası oluşturur `allOnes` bağımsız değişkeni yanlış veri türü (tek `Integer` yerine bir `Integer` dizisi). Deyim `Return allOnes()` çağrısı göründüğünden derleyici hatası oluşturur `allOnes` bağımsız değişken ile.  
  
 **Doğru yaklaşım:** dizi döndürülür öğelerini değiştirebilmesi için dahili bir dizi yerel bir değişken tanımlayın. Aşağıdaki örnek, hatasız derler.  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Bağımsız değişken değil değiştirilen yordam çağrısı tarafından  
 Çağıran kodu bir bağımsız değişken temel bir programlama öğesi değiştirmek bir yordam izin vermek istiyorsanız, başvuruya göre geçmesi gerekir. Ancak değer göre geçirin olsa bile bir yordam öğeleri bir başvuru türü bağımsız değişkenin erişebilirsiniz.  
  
-   **Değişken temel**. Temel alınan değişken öğenin kendisinin değerini değiştirmek için yordamı izin vermek için yordam parametresi bildirmelidir [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Geçersiz kılarsınız çünkü Ayrıca, çağrıyı yapan kod bağımsız değişkeni parantez içinde almalısınız değil `ByRef` mekanizması geçirme.  
  
-   **Başvuru türü öğeleri**. Bir parametre bildirirseniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), yordam temel değişken öğenin kendisini değiştiremezsiniz. Ancak, bağımsız değişkeni bir başvuru türü ise, değişkenin değeri değiştirilemiyor olsa bile yordamı, işaret ettiği, nesnenin üyelerine değiştirebilirsiniz. Örneğin, bağımsız değişken bir dizi değişkeni ise yordamı için yeni bir dizi nesnesine atanamaz, ancak bir veya daha fazla öğeleri değiştirebilirsiniz. Değiştirilen öğeler çağıran kodu temel alınan dizi değişkeni yansıtılır.  
  
 Aşağıdaki örnek, bir dizi değişkeni değere göre alabilir ve çalışan iki yordam üzerinde öğeleri tanımlar. Yordam `increase` yalnızca biri her öğesine ekler. Yordam `replace` yeni bir dizi parametre atar `a()` ve her öğe için ekler. Ancak, yeniden atama çağıran kodu temel alınan dizi değişkeni etkilemez `a()` bildirilmiş `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 Aşağıdaki örnek çağrılar `increase` ve `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü `n` bir başvuru türü `increase` kendisine geçirilen olsa da, bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 11, 21, 31, 41". Çünkü `n` geçirilen `ByVal`, `replace` değişkeni değiştirilemiyor `n` yeni bir dizi atayarak. Zaman `replace` yeni dizi örneği oluşturur `k` ve yerel bir değişkene atar `a`, başvuru kaybederse `n` çağıran kodu tarafından geçirilen. Üyeleri, artırır zaman `a`, yalnızca yerel dizi `k` etkilenir.  
  
 **Doğru yaklaşım:** temel değişken öğenin kendisini değiştirebilmesi için başvuruya göre geçirin. Aşağıdaki örnek bildiriminde değişiklik gösterir `replace` izin veren başka arama kodda bir dizi yerine için.  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Bir aşırı tanımlamak için  
 Bir yordamı aşırı yüklenmiş bir sürümünü tanımlamak istiyorsanız, farklı bir imza ancak aynı adı kullanmanız gerekir. Derleyici, aşırı aynı imzayla bildiriminden ayrım, bir hata oluşturur.  
  
 *İmza* bir yordam yordam adı ve parametre listesi tarafından belirlenir. Her aşırı tüm aşırı adıyla aynı olmalıdır ancak, en az bir imza diğer bileşenlerinin tümünü farklı olmalıdır. Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
 Aşağıdaki öğeler parametre listesine ait olsa bile bir yordam imza bileşenlerinin değil:  
  
-   Yordam değiştiricisi anahtar sözcükler gibi `Public`, `Shared`, ve `Static`  
  
-   Parametre adları  
  
-   Parametresi değiştiricisi anahtar sözcükler gibi `ByRef` ve `Optional`  
  
-   Dönüş değeri (dışında bir dönüşüm işleci) veri türü  
  
 Bir veya daha önceki öğeler yalnızca değiştirerek bir yordamı aşırı yükleme yapılamıyor.  
  
 **Doğru yaklaşım:** bir yordamı aşırı tanımlayabilmek için imza değişir. Aynı adı kullanmanız gerekir çünkü sayısını, sipariş veya parametrelerinin veri türleri farklı gerekir. Genel bir yordamda türü parametre sayısı değişebilir. İçinde bir dönüşüm işleci ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)), dönüş türü değişebilir.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>İsteğe bağlı bir çözümleme ve ParamArray bağımsız değişkenleri aşırı yükleme  
 Bir veya daha fazla bir yordamı aşırı yükleme varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri veya [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi gerekir kaçının herhangi bir çoğaltma *örtük aşırı yüklemeleri*. Bilgi için bkz: [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Aşırı yüklenmiş bir yordamı yanlış sürümünü çağırma  
 Bir yordamın birden fazla aşırı yüklenmiş sürümleri varsa, tüm parametre listelerine ile ilgili bilgi sahibi olmanız ve Visual Basic çağrıları aşırı arasında nasıl çözümlediği anlamanız gerekir. Aksi takdirde hedeflenen farklı bir aşırı çağırabilirsiniz.  
  
 Aramak istediğiniz hangi aşırı yüklemenin belirlediğinizde aşağıdaki kuralları inceleyip dikkatli olun:  
  
-   Bağımsız değişkenler ve doğru sırada doğru numarası sağlayın.  
  
-   İdeal olarak, bağımsız değişkenleri aynı veri türlerine karşılık gelen parametre olarak olmalıdır. Herhangi bir durumda, her bağımsız değişkeninin veri türü, karşılık gelen parametrenin genişletmek gerekir. Bu bile geçerlidir [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kümesine `Off`. Bir aşırı aşırı yükleme, bağımsız değişken listesi, herhangi bir daraltma dönüştürme gerektiriyorsa çağrılacak uygun değil.  
  
-   Genişletme gerektiren bağımsız değişkenleri eklemek, olabildiğince karşılık gelen parametre veri türleri için mümkün olduğunca yakın veri türlerini sağlayın. Bağımsız değişken veri türleri iki veya daha fazla aşırı kabul ederseniz, derleyici çağrınızı genişletme en az miktarını için çağırır aşırı çözümler.  
  
 Veri türü uyuşmazlığı olasılığını kullanarak küçültebilirsiniz [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) da bağımsız hazırlanırken dönüştürme anahtar sözcüğü.  
  
### <a name="overload-resolution-failure"></a>Çözümleme hatası aşırı yükleme  
 Aşırı yüklenmiş bir yordamı çağırdığınızda, biri dışındaki tüm aşırı ortadan kaldırmak derleyici çalışır. Başarılı olursa, bu aşırı çağrısı çözümler. Tüm aşırı ortadan veya tek bir aday için uygun aşırı indiremezsiniz, bir hata oluşturur.  
  
 Aşağıdaki örnek aşırı çözümleme işlemi gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 İlk çağrıda derleyici ilk aşırı çünkü ortadan kaldıran ilk bağımsız değişken türü (`Short`) daraltır karşılık gelen parametrenin türünü (`Byte`). Tür bağımsız değişkeni, her olduğundan ikinci aşırı sonra üçüncü aşırı ortadan (`Short` ve `Single`) üçüncü aşırı içinde karşılık gelen türüne widens (`Integer` ve `Single`). Böylece isteğe bağlı olarak derleyici çağrısı kullanır ikinci aşırı daha az genişletme gerektirir.  
  
 İkinci çağrıda derleyici daraltma temel alarak aşırı hiçbirini ortadan olamaz. Daha az bağımsız değişken türleri genişletme ile ikinci aşırı çağırabilirsiniz olduğundan, üçüncü aşırı ilk çağrıda olduğu gibi aynı nedenden dolayı ortadan kaldırır. Ancak, derleyici arasında birinci ve ikinci aşırı yüklemeleri çözümlenemiyor. Her karşılık gelen türü diğer widens bir tanımlanan parametre türüne sahip (`Byte` için `Short`, ancak `Single` için `Double`). Derleyici, bu nedenle bir aşırı yüklemesini çözümleme hatası oluşturur.  
  
 **Doğru yaklaşım:** karışıklık olmadan aşırı yüklenmiş bir yordamı çağırma yapabilmek için kullanmak [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bağımsız değişken veri türleri parametre türleri ile eşleşecek şekilde. Aşağıdaki örnekte bir çağrı gösterilmektedir `z` , ikinci aşırı yüklemesine çözümleme zorlar.  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>İsteğe bağlı bir çözümleme ve ParamArray bağımsız değişkenleri aşırı yükleme  
 Bir yordamın iki aşırı son parametre bildirilmiş dışında aynı imzaları varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) birinde ve [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) diğer, bu yordam çağrısına derleyici çözümler göre en yakın eşleşme. Daha fazla bilgi için bkz: [aşırı yükleme çözümü](./overload-resolution.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı Yükleme Çözümü](./overload-resolution.md)
