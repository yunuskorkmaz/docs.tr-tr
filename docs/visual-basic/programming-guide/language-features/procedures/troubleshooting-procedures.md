---
title: Sorun giderme yordamları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: c74947e21de8ba26ffde01f6f28aea67346c2071
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002081"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Sorun giderme yordamları (Visual Basic)

Bu sayfada, yordamlarla çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Bir işlev yordamından dizi türü döndürme

@No__t-0 yordamı bir dizi veri türü döndürürse, değerleri dizinin öğelerine depolamak için `Function` adını kullanamazsınız. Bunu yapmayı denerseniz, derleyici onu `Function` ' a bir çağrı olarak yorumlar. Aşağıdaki örnek derleyici hataları üretir:
  
```vb
Function AllOnes(n As Integer) As Integer()
   For i As Integer = 1 To n - 1  
      ' The following statement generates a COMPILER ERROR.  
      AllOnes(i) = 1  
   Next  

   ' The following statement generates a COMPILER ERROR.  
   Return AllOnes()  
End Function
```

@No__t-0 ifadesi, yanlış veri türünde bir bağımsız değişkenle (`Integer` dizisi yerine bir skaler `Integer`) `AllOnes` çağrısında göründüğünden bir derleyici hatası oluşturur. @No__t-0 ifadesi, bağımsız değişken olmadan `AllOnes` çağrısında göründüğünden bir derleyici hatası oluşturuyor.  
  
 **Doğru yaklaşım:** Döndürülecek bir dizinin öğelerini değiştirebilmek için, bir iç diziyi yerel bir değişken olarak tanımlayın. Aşağıdaki örnek hata olmadan derlenir:

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>Bağımsız değişken yordam çağrısı tarafından değiştirilmedi

Çağıran koddaki bağımsız değişkenin temelindeki bir programlama öğesini değiştirme yordamına izin vermeyi düşünüyorsanız, başvuruya göre geçirmeniz gerekir. Ancak bir yordam, bir başvuru türü bağımsız değişkeninin öğelerine değere göre geçseniz bile bu öğelere erişebilir.

- **Temel alınan değişken**. Yordamın temel alınan değişken öğesinin değerini değiştirmesine izin vermek için, yordam [ByRef](../../../language-reference/modifiers/byref.md)parametresini bildirmelidir. Ayrıca, çağıran kod bağımsız değişkeni parantez içine içermemelidir, çünkü bu `ByRef` geçen mekanizmayı geçersiz kılar.

- **Başvuru türü öğeleri**. Bir [ByVal](../../../language-reference/modifiers/byval.md)parametresi bildirirseniz yordam, temeldeki değişken öğesinin kendisini değiştiremez. Ancak bağımsız değişken bir başvuru türü ise, yordam değişkenin değerini değiştiremese de, işaret ettiği nesnenin üyelerini değiştirebilir. Örneğin, bağımsız değişken bir dizi değişkenidir, yordam buna yeni bir dizi atayamaz, ancak bir veya daha fazla öğesini değiştirebilir. Değiştirilen öğeler, çağıran koddaki temeldeki dizi değişkenine yansıtılır.

Aşağıdaki örnek, bir dizi değişkenini değere göre alan ve öğelerinde çalışan iki yordamı tanımlar. @No__t-0 yordamı her bir öğeye yalnızca bir tane ekler. @No__t-0 yordamı, `a()` parametresine yeni bir dizi atar ve sonra her öğeye bir tane ekler. Ancak, `a()` `ByVal` olarak bildirildiği için yeniden atama, çağıran koddaki temel alınan dizi değişkenini etkilemez.

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

Aşağıdaki örnek `increase` ve `replace` için çağrılar yapar:

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
İlk `MsgBox` çağrısı "artdıktan sonra (n): 11, 21, 31, 41" görüntüler. @No__t-0 bir başvuru türü olduğundan, `increase` `ByVal` ' den geçirilse bile üyelerini değiştirebilir.

İkinci `MsgBox` çağrısı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" olarak görüntülenir. @No__t-0 `ByVal` geçirildiğinden `replace` ' ye yeni bir dizi atayarak `n` değişkeni değiştirilemez. @No__t-0, yeni `k` dizi örneğini oluşturduğunda ve onu `a` yerel değişkenine atadığında, çağıran kod tarafından geçirilen `n` başvurusunu kaybeder. @No__t-0 üyelerini artırdığı zaman, yalnızca `k` yerel dizisi etkilenir.

**Doğru yaklaşım:** Temel bir değişken öğesinin kendisini değiştirebilmek için, başvuruya göre geçirin. Aşağıdaki örnek `replace` bildiriminde, çağıran koddaki bir diziyi bir dizi ile değiştirmesine izin veren değişikliği gösterir:

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>Aşırı yükleme tanımlanamıyor

Bir yordamın aşırı yüklenmiş bir sürümünü tanımlamak istiyorsanız, aynı adı ancak farklı bir imzayı kullanmanız gerekir. Derleyici, bildirimi aynı imzaya sahip bir aşırı yükten ayırt edemez bir hata oluşturur.

Bir yordamın *imzası* , yordam adı ve parametre listesine göre belirlenir. Her aşırı yükleme diğer tüm aşırı yüklemeleriyle aynı ada sahip olmalıdır, ancak imzaların diğer bileşenlerinden en az birinde farklı olmalıdır. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](./procedure-overloading.md).

Aşağıdaki öğeler, parametre listesine ait olsalar bile bir yordamın imzasının bileşenleri değildir:

- @No__t-0, `Shared` ve `Static` gibi yordam değiştirici anahtar sözcükleri.
- Parametre adları.
- @No__t-0 ve `Optional` gibi parametre değiştirici anahtar sözcükleri.
- Dönüş değerinin veri türü (bir dönüştürme işleci dışında).

Bir yordamı yalnızca bir veya daha fazla önceki öğeden farklı şekilde değiştirerek aşırı yükleyemezsiniz.

**Doğru yaklaşım:** Bir yordam aşırı yüklemesi tanımlayabilmek için imzayı değişiklik yapmanız gerekir. Aynı adı kullanmanız gerektiğinden, parametrelerin sayı, sıra veya veri türleri arasında değişiklik yapmanız gerekir. Genel yordamda, tür parametrelerinin sayısını değiştirebilirsiniz. Bir dönüştürme işlecinde ([CType işlevi](../../../language-reference/functions/ctype-function.md)), dönüş türünü değiştirebilirsiniz.

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Isteğe bağlı ve ParamArray bağımsız değişkenleriyle aşırı yükleme çözümü

Bir veya daha fazla [Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametre ya da bir [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresiyle bir yordamı aşırı yüklüyorsanız, *örtük aşırı yüklemelerin*hiçbirini çoğaltmaktan kaçınmanız gerekir. Daha fazla bilgi için bkz. [yordamları aşırı yükleme](./considerations-in-overloading-procedures.md).

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>Aşırı yüklenmiş yordamın yanlış sürümünü çağırma

Bir yordamda birkaç aşırı yüklenmiş sürüm varsa, tüm parametre listelerine alışkın olmanız ve Visual Basic aşırı yüklemeler arasında çağrıların nasıl çözümlendiğini anlamanız gerekir. Aksi takdirde, amaçlanan bir aşırı yüklemeyi çağırabilirsiniz.

Hangi aşırı yüklemeyi çağırmak istediğinizi belirledikten sonra, aşağıdaki kuralları gözlemlemeye dikkat edin:

- Doğru sayıda bağımsız değişken sağlayın ve doğru sırada.  
- İdeal olarak, bağımsız değişkenleriniz karşılık gelen parametrelerle tam olarak aynı veri türlerine sahip olmalıdır. Herhangi bir durumda, her bağımsız değişkenin veri türü karşılık gelen parametresinden sonra genişlemelidir. Bu, [katı ifadesiyle](../../../language-reference/statements/option-strict-statement.md) `Off` olarak ayarlanan seçenek de geçerlidir. Aşırı yükleme, bağımsız değişken listenizden herhangi bir daraltma dönüştürmesi gerektiriyorsa, bu aşırı yükleme çağrılabilir.
- Genişleyen bir bağımsız değişken sağlarsanız, veri türlerini karşılık gelen parametre veri türlerine mümkün olduğunca yakın hale getirin. İki veya daha fazla aşırı yükleme bağımsız değişken veri türlerinizi kabul ettiğinde, derleyici en az genişletme miktarını çağıran aşırı yüklemeye yönelik çağrınızı çözer.

Bağımsız değişkenlerinizi hazırlarken [CType işlev](../../../language-reference/functions/ctype-function.md) dönüştürme anahtar sözcüğünü kullanarak veri türü uyuşmazlığı olasılığını azaltabilirsiniz.

### <a name="overload-resolution-failure"></a>Aşırı yükleme çözümleme hatası

Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici aşırı yüklerden biri hariç tümünü ortadan kaldırmaya çalışır. Başarılı olursa, bu aşırı yüklemeye çağrı çözülür. Tüm aşırı yüklemeleri ortadan kaldırarsa veya uygun olan aşırı yüklemeleri tek bir aday için azaltamazsanız bir hata oluşturur.

Aşağıdaki örnek, aşırı yükleme çözümleme işlemini göstermektedir:

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
İlk çağrıda, derleyici ilk yeniden yüklemeyi ortadan kaldırır çünkü ilk bağımsız değişken türü (`Short`) karşılık gelen parametrenin türüne (`Byte`) daraltır. İkinci aşırı yükteki (`Short` ve `Single`) her bağımsız değişken türü üçüncü aşırı yüklemede (`Integer` ve `Single`) karşılık gelen türe widens için üçüncü aşırı yüklemeyi ortadan kaldırır. İkinci aşırı yükleme daha az genişletme gerektirir, bu nedenle derleyici onu çağrı için kullanır.

İkinci çağrıda, derleyici daraltma temelinde aşırı yüklemelerin hiçbirini ortadan kaldırmaz. İkinci aşırı yükleme, bağımsız değişken türlerini daha az genişletme ile çağırabildiğinden, birinci çağrıdan itibaren aynı nedenden dolayı üçüncü aşırı yüklemeyi ortadan kaldırır. Ancak, derleyici birinci ve ikinci aşırı yüklemeler arasında çözümlenemez. Her biri, widens-1 ' @no__t e @no__t, ancak `Single` ' ye `Double`) karşılık gelen türe sahip bir tanımlı parametre türüne sahiptir. Bu nedenle derleyici aşırı yükleme çözümlemesi hatası oluşturur.

**Doğru yaklaşım:** Aşırı yüklenmiş bir yordamı belirsizlik olmadan çağırabilmek için [CType işlevini](../../../language-reference/functions/ctype-function.md) kullanarak bağımsız değişken veri türlerini parametre türleriyle eşleştirin. Aşağıdaki örnek, ikinci aşırı yüklemeye çözüm zorlayan `z` ' a bir çağrı gösterir.

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Isteğe bağlı ve ParamArray bağımsız değişkenleriyle aşırı yükleme çözümü

Bir yordamın iki aşırı yüklemesi aynı imzaya sahip ise, son parametrenin diğer bir ve [ParamArray](../../../language-reference/modifiers/paramarray.md) 'de [isteğe bağlı](../../../language-reference/modifiers/optional.md) olarak bildirildiği durumlar dışında, derleyici en yakın eşleşmeye göre o yordama bir çağrı çözer. Daha fazla bilgi için bkz. [aşırı yükleme çözünürlüğü](./overload-resolution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamların](index.md)
- [Alt yordamlar](sub-procedures.md)
- [İşlev yordamları](function-procedures.md)
- [Özellik yordamları](property-procedures.md)
- [İşleç yordamları](operator-procedures.md)
- [Yordam parametreleri ve bağımsız değişkenleri](procedure-parameters-and-arguments.md)
- [Yordam aşırı yüklemesi](procedure-overloading.md)
- [Prosedürleri aşırı yükleme konuları](considerations-in-overloading-procedures.md)
- [Aşırı yükleme çözümlemesi](overload-resolution.md)
