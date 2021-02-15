---
description: 'Hakkında daha fazla bilgi edinin: sorun giderme yordamları (Visual Basic)'
title: Sorun giderme yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: a36e2ef9442fc0e76c9a98e83007976393e7957b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471155"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Sorun giderme yordamları (Visual Basic)

Bu sayfada, yordamlarla çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Bir işlev yordamından dizi türü döndürme

Bir `Function` yordam bir dizi veri türü döndürürse, `Function` değerleri dizinin öğelerinde depolamak için bu adı kullanamazsınız. Bunu yapmayı denerseniz, derleyici onu öğesine bir çağrı olarak yorumlar `Function` . Aşağıdaki örnek derleyici hataları üretir:
  
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

İfade, `AllOnes(i) = 1` `AllOnes` yanlış veri türünde bir bağımsız değişkenle ( `Integer` bir dizi yerine skaler) çağrı göründüğünden bir derleyici hatası oluşturur `Integer` . İfade, `Return AllOnes()` hiçbir bağımsız değişken olmadan çağrıda göründüğünden bir derleyici hatası oluşturuyor `AllOnes` .  
  
 **Doğru yaklaşım:** Döndürülecek bir dizinin öğelerini değiştirebilmek için, bir iç diziyi yerel bir değişken olarak tanımlayın. Aşağıdaki örnek hata olmadan derlenir:

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>Bağımsız değişken yordam çağrısı tarafından değiştirilmedi

Çağıran koddaki bağımsız değişkenin temelindeki bir programlama öğesini değiştirme yordamına izin vermeyi düşünüyorsanız, başvuruya göre geçirmeniz gerekir. Ancak bir yordam, bir başvuru türü bağımsız değişkeninin öğelerine değere göre geçseniz bile bu öğelere erişebilir.

- **Temel alınan değişken**. Yordamın temel alınan değişken öğesinin değerini değiştirmesine izin vermek için, yordam [ByRef](../../../language-reference/modifiers/byref.md)parametresini bildirmelidir. Ayrıca, çağıran kod, geçirilen mekanizmayı geçersiz kılacağından, bağımsız değişkeni parantez içine içermemelidir `ByRef` .

- **Başvuru türü öğeleri**. Bir [ByVal](../../../language-reference/modifiers/byval.md)parametresi bildirirseniz yordam, temeldeki değişken öğesinin kendisini değiştiremez. Ancak bağımsız değişken bir başvuru türü ise, yordam değişkenin değerini değiştiremese de, işaret ettiği nesnenin üyelerini değiştirebilir. Örneğin, bağımsız değişken bir dizi değişkenidir, yordam buna yeni bir dizi atayamaz, ancak bir veya daha fazla öğesini değiştirebilir. Değiştirilen öğeler, çağıran koddaki temeldeki dizi değişkenine yansıtılır.

Aşağıdaki örnek, bir dizi değişkenini değere göre alan ve öğelerinde çalışan iki yordamı tanımlar. Yordam `increase` her bir öğeye yalnızca bir tane ekler. Yordam `replace` parametreye yeni bir dizi atar `a()` ve sonra her öğeye bir tane ekler. Ancak, yeniden atama, bildirildiği için çağıran kodda temeldeki dizi değişkenini etkilemez `a()` `ByVal` .

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

Aşağıdaki örnek, ve için çağrılar `increase` yapar `replace` :

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
İlk `MsgBox` çağrı, "Artdıktan sonra (n): 11, 21, 31, 41" görüntüler. `n`Bir başvuru türü olduğu için, `increase` başarılı olsa bile üyelerini değiştirebilir `ByVal` .

İkinci `MsgBox` çağrı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" görüntüler. `n`Geçirildiğinden `ByVal` , `replace` `n` kendisine yeni bir dizi atayarak değişkeni değiştiremezsiniz. `replace`Yeni dizi örneğini oluşturur `k` ve yerel değişkene atarsa `a` , `n` çağıran kod tarafından geçirilen başvuruyu kaybeder. Üyelerini artırdığı zaman `a` yalnızca yerel dizi `k` etkilenir.

**Doğru yaklaşım:** Temel bir değişken öğesinin kendisini değiştirebilmek için, başvuruya göre geçirin. Aşağıdaki örnek, öğesinin bildirimi içindeki değişikliği gösterir ve `replace` Bu, çağıran kodda bir diziyi başka bir diziyi ile değiştirmesine izin verir:

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>Aşırı yükleme tanımlanamıyor

Bir yordamın aşırı yüklenmiş bir sürümünü tanımlamak istiyorsanız, aynı adı ancak farklı bir imzayı kullanmanız gerekir. Derleyici, bildirimi aynı imzaya sahip bir aşırı yükten ayırt edemez bir hata oluşturur.

Bir yordamın *imzası* , yordam adı ve parametre listesine göre belirlenir. Her aşırı yükleme diğer tüm aşırı yüklemeleriyle aynı ada sahip olmalıdır, ancak imzaların diğer bileşenlerinden en az birinde farklı olmalıdır. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](./procedure-overloading.md).

Aşağıdaki öğeler, parametre listesine ait olsalar bile bir yordamın imzasının bileşenleri değildir:

- , Ve gibi yordam değiştirici anahtar `Public` sözcükleri `Shared` `Static` .
- Parametre adları.
- Ve gibi parametre değiştirici anahtar sözcükleri `ByRef` `Optional` .
- Dönüş değerinin veri türü (bir dönüştürme işleci dışında).

Bir yordamı yalnızca bir veya daha fazla önceki öğeden farklı şekilde değiştirerek aşırı yükleyemezsiniz.

**Doğru yaklaşım:** Bir yordam aşırı yüklemesi tanımlayabilmek için imzayı değişiklik yapmanız gerekir. Aynı adı kullanmanız gerektiğinden, parametrelerin sayı, sıra veya veri türleri arasında değişiklik yapmanız gerekir. Genel yordamda, tür parametrelerinin sayısını değiştirebilirsiniz. Bir dönüştürme işlecinde ([CType işlevi](../../../language-reference/functions/ctype-function.md)), dönüş türünü değiştirebilirsiniz.

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Isteğe bağlı ve ParamArray bağımsız değişkenleriyle aşırı yükleme çözümü

Bir veya daha fazla [Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametre ya da bir [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresiyle bir yordamı aşırı yüklüyorsanız, *örtük aşırı yüklemelerin* hiçbirini çoğaltmaktan kaçınmanız gerekir. Daha fazla bilgi için bkz. [yordamları aşırı yükleme](./considerations-in-overloading-procedures.md).

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>Aşırı yüklenmiş yordamın yanlış sürümünü çağırma

Bir yordamda birkaç aşırı yüklenmiş sürüm varsa, tüm parametre listelerine alışkın olmanız ve Visual Basic aşırı yüklemeler arasında çağrıların nasıl çözümlendiğini anlamanız gerekir. Aksi takdirde, amaçlanan bir aşırı yüklemeyi çağırabilirsiniz.

Hangi aşırı yüklemeyi çağırmak istediğinizi belirledikten sonra, aşağıdaki kuralları gözlemlemeye dikkat edin:

- Doğru sayıda bağımsız değişken sağlayın ve doğru sırada.  
- İdeal olarak, bağımsız değişkenleriniz karşılık gelen parametrelerle tam olarak aynı veri türlerine sahip olmalıdır. Herhangi bir durumda, her bağımsız değişkenin veri türü karşılık gelen parametresinden sonra genişlemelidir. Bu, [katı ifadesiyle ayarlanmış seçenek](../../../language-reference/statements/option-strict-statement.md) ile de geçerlidir `Off` . Aşırı yükleme, bağımsız değişken listenizden herhangi bir daraltma dönüştürmesi gerektiriyorsa, bu aşırı yükleme çağrılabilir.
- Genişleyen bir bağımsız değişken sağlarsanız, veri türlerini karşılık gelen parametre veri türlerine mümkün olduğunca yakın hale getirin. İki veya daha fazla aşırı yükleme bağımsız değişken veri türlerinizi kabul ettiğinde, derleyici en az genişletme miktarını çağıran aşırı yüklemeye yönelik çağrınızı çözer.

Bağımsız değişkenlerinizi hazırlarken [CType işlev](../../../language-reference/functions/ctype-function.md) dönüştürme anahtar sözcüğünü kullanarak veri türü uyuşmazlığı olasılığını azaltabilirsiniz.

### <a name="overload-resolution-failure"></a>Aşırı yükleme çözümleme hatası

Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici aşırı yüklerden biri hariç tümünü ortadan kaldırmaya çalışır. Başarılı olursa, bu aşırı yüklemeye çağrı çözülür. Tüm aşırı yüklemeleri ortadan kaldırarsa veya uygun olan aşırı yüklemeleri tek bir aday için azaltamazsanız bir hata oluşturur.

Aşağıdaki örnek, aşırı yükleme çözümleme işlemini göstermektedir:

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
İlk çağrıda derleyici ilk tekrar yüklemeyi ortadan kaldırır çünkü ilk bağımsız değişkenin türü ( `Short` ), karşılık gelen parametrenin türüne () göre daraltır `Byte` . İkinci aşırı yükteki (ve) her bağımsız değişken türü `Short` `Single` üçüncü aşırı yüklemede karşılık gelen türe (ve) widens için, daha sonra üçüncü aşırı yüklemeyi ortadan kaldırır `Integer` `Single` . İkinci aşırı yükleme daha az genişletme gerektirir, bu nedenle derleyici onu çağrı için kullanır.

İkinci çağrıda, derleyici daraltma temelinde aşırı yüklemelerin hiçbirini ortadan kaldırmaz. İkinci aşırı yükleme, bağımsız değişken türlerini daha az genişletme ile çağırabildiğinden, birinci çağrıdan itibaren aynı nedenden dolayı üçüncü aşırı yüklemeyi ortadan kaldırır. Ancak, derleyici birinci ve ikinci aşırı yüklemeler arasında çözümlenemez. Her biri, diğer ( `Byte` `Short` , ancak `Single` için) öğesine karşılık gelen türe widens bir tanımlı parametre türüne sahiptir `Double` . Bu nedenle derleyici aşırı yükleme çözümlemesi hatası oluşturur.

**Doğru yaklaşım:** Aşırı yüklenmiş bir yordamı belirsizlik olmadan çağırabilmek için [CType işlevini](../../../language-reference/functions/ctype-function.md) kullanarak bağımsız değişken veri türlerini parametre türleriyle eşleştirin. Aşağıdaki örnek, ikinci aşırı yüklemeye çözüm zorlayan öğesine yönelik bir çağrı gösterir `z` .

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Isteğe bağlı ve ParamArray bağımsız değişkenleriyle aşırı yükleme çözümü

Bir yordamın iki aşırı yüklemesi aynı imzaya sahip ise, son parametrenin diğer bir ve [ParamArray](../../../language-reference/modifiers/paramarray.md) 'de [isteğe bağlı](../../../language-reference/modifiers/optional.md) olarak bildirildiği durumlar dışında, derleyici en yakın eşleşmeye göre o yordama bir çağrı çözer. Daha fazla bilgi için bkz. [aşırı yükleme çözünürlüğü](./overload-resolution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [Alt Yordamlar](sub-procedures.md)
- [İşlev Yordamları](function-procedures.md)
- [Özellik Yordamları](property-procedures.md)
- [İşleç Yordamları](operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Yordam Aşırı Yüklemesi](procedure-overloading.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](considerations-in-overloading-procedures.md)
- [Aşırı yükleme çözümlemesi](overload-resolution.md)
