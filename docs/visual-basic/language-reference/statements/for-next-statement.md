---
title: For...Next Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351192"
---
# <a name="fornext-statement-visual-basic"></a>For...Next Deyimi (Visual Basic)

Bir deyim grubunu belirtilen sayıda yineler.

## <a name="syntax"></a>Sözdizimi

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a>Bölümler

|Bölümüyle|Açıklama|
|----------|-----------------|
|`counter`|`For` bildiriminde gereklidir. Sayısal değişken. Döngünün denetim değişkeni. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|
|`datatype`|İsteğe bağlı. `counter`veri türü. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|
|`start`|Gerekli. Sayısal ifade. `counter`başlangıç değeri.|
|`end`|Gerekli. Sayısal ifade. `counter`son değeri.|
|`step`|İsteğe bağlı. Sayısal ifade. `counter` döngüyle her seferinde artırılır.|
|`statements`|İsteğe bağlı. `For` ve `Next` arasındaki, belirtilen sayıda kez çalışan bir veya daha fazla deyim.|
|`Continue For`|İsteğe bağlı. Denetimi sonraki döngü yinelemesine aktarır.|
|`Exit For`|İsteğe bağlı. `For` döngüsünün dışına denetimini aktarır.|
|`Next`|Gerekli. `For` döngüsünün tanımını sonlandırır.|

> [!NOTE]
> `To` anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır. Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimlerinde. Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).

## <a name="simple-examples"></a>Basit örnekler

Bir dizi deyimin kümesini birkaç kez yinelemek istediğinizde `For`...`Next` yapısını kullanırsınız.

Aşağıdaki örnekte, `index` değişkeni 1 değeriyle başlar ve döngünün her yinelemeyle artırılır, `index` değeri 5 ' e ulaştığında sona eriyor.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

Aşağıdaki örnekte, `number` değişkeni 2 ' de başlar ve döngünün her yinelemesi için 0,25 tarafından azaltılır, `number` değeri 0 ' a ulaştığında sona eriyor. `-.25` `Step` bağımsız değişkeni, döngünün her yinelemede değeri 0,25 azaltır.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> Bir [while... End while ekstresi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [Do... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır. Ancak, döngüyü belirli sayıda çalıştırmayı düşünüyorsanız, bir `For`...`Next` döngüsü daha iyi bir seçimdir. Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.

## <a name="nesting-loops"></a>İç içe geçme döngüleri

Bir döngüyü diğerinin içine yerleştirerek `For` döngüleri iç içe geçirebilirsiniz. Aşağıdaki örnek, farklı adım değerlerine sahip iç içe `For`...`Next` yapılarını gösterir. Dış döngü, döngünün her yinelemesi için bir dize oluşturur. İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz bir `counter` değişkeni olmalıdır.

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

`Exit For` deyimden hemen çıkış `For`...`Next` `Next` deyimlerini izleyen deyime döngü ve denetim aktarır.

`Continue For` bildiri, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).

Aşağıdaki örnekte `Continue For` ve `Exit For` deyimlerinin kullanımı gösterilmektedir.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Bir `For`...`Next` istediğiniz sayıda `Exit For` deyimi koyabilirsiniz Gerçekleştirmek. İç içe geçmiş `For`içinde kullanıldığında...`Next` döngüler, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

`Exit For`, genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If`...`Then`...`Else` yapısı). Aşağıdaki koşullarda `Exit For` kullanmak isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.

- Bir `Try`...`Catch`...`Finally` ifadesinde bir özel durum yakalar. `Finally` bloğunun sonunda `Exit For` kullanabilirsiniz.

- Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Böyle bir koşulu tespit ediyorsanız, döngüden çıkmak için `Exit For` kullanabilirsiniz. Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="technical-implementation"></a>Teknik Uygulama

Bir `For`...`Next` döngüsü başladığında Visual Basic `start`, `end`ve `step`değerlendirir. Visual Basic bu değerleri yalnızca şu anda değerlendirir ve `counter``start` atar. Bildirim bloğu çalıştırılmadan önce, `counter` `end`Visual Basic karşılaştırır. `counter` zaten `end` değerden daha büyükse (veya `step` negatifse küçüktür), `For` döngüsü sonlanır ve denetim `Next` ifadesiyle sonraki deyime geçer. Aksi halde, ekstre bloğu çalışır.

Visual Basic `Next` deyimle karşılaştığında, `step` tarafından `counter` artırır ve `For` bildirimine geri döndürür. `counter`, `end`ile karşılaştırır ve sonuca bağlı olarak engellemeyi çalıştırır ya da döngüden çıkar. Bu işlem, `counter` `end` geçirene veya bir `Exit For` ifadesiyle karşılaşana kadar devam eder.

`counter` `end`geçirene kadar döngü durdurulmaz. `counter` `end`eşitse, döngü devam eder. Bloğunun çalıştırılıp çalıştırılmayacağını belirleyen karşılaştırma, `step` pozitif ve `counter` >= negatifse `end` `end`  <= `counter`.`step`

Bir döngü içinde `counter` değerini değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir. `start`, `end`veya `step` değerini değiştirmek, döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.

Döngüleri iç içe alırsanız derleyici bir iç düzeyin `Next` ifadesinden önce bir dış iç içe geçme düzeyinin `Next` ifadesiyle karşılaşırsa bir hata bildirir. Ancak, derleyici yalnızca her `Next` bildiriminde `counter` belirtirseniz bu çakışan hatayı algılayabilir.

### <a name="step-argument"></a>Adım bağımsız değişkeni

`step` değeri pozitif veya negatif olabilir. Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:

|**Adım değeri**|**Döngü şunu içeriyorsa yürütülür**|
|--------------------|--------------------------|
|Pozitif veya sıfır|`counter` <= `end`|
|Negatif|`counter` >= `end`|

`step` varsayılan değeri 1 ' dir.

### <a name="BKMK_Counter"></a>Sayaç bağımsız değişkeni

Aşağıdaki tabloda `counter`, tüm `For…Next` döngüsünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir. Bu belirleme `datatype` var olup olmadığına ve `counter` önceden tanımlanmış olup olmadığına bağlıdır.

|`datatype` var mı?|`counter` zaten tanımlandı mı?|Sonuç (`counter`, tüm `For...Next` döngüsünün kapsamına alınmış yeni bir yerel değişken tanımlıyor)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Hayır|Evet|Hayır, `counter` zaten tanımlanmış. `counter` kapsamı yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.|
|Hayır|Hayır|Evet. Veri türü `start`, `end`ve `step` ifadelerinden algılanır. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)|
|Evet|Evet|Evet, ancak yalnızca varolan `counter` değişkeni yordam dışında tanımlanmışsa. Bu değişken ayrı kalır. Varolan `counter` değişkeninin kapsamı yordamda yerelse, bir derleme zamanı hatası oluşur.|
|Evet|Hayır|Evet.|

`counter` veri türü yinelemenin türünü belirler ve bu türlerden biri olmalıdır:

- `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`veya `Double`.

- Bir [enum ifadesini](../../../visual-basic/language-reference/statements/enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.

- Bir `Object`.

- `T`, `B` `Boolean` ifadesinde kullanılabilecek bir tür olan aşağıdaki işleçlere sahip bir tür.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

İsteğe bağlı olarak, `Next` bildiriminde `counter` değişkenini belirtebilirsiniz. Bu sözdizimi, özellikle iç içe geçmiş `For` döngülerine sahipseniz programınızın okunabilirliğini geliştirir. Karşılık gelen `For` ifadesinde görünen değişkeni belirtmeniz gerekir.

`start`, `end`ve `step` ifadeleri, `counter`türüne sahip herhangi bir veri türü için değerlendirebilirler. `counter`için Kullanıcı tanımlı bir tür kullanıyorsanız, `start`, `end`veya `step` türlerini `counter`türüne dönüştürmek için `CType` dönüştürme işlecini tanımlamanız gerekebilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır. [Her biri için bir değil... Next Ifadesinde](../../../visual-basic/language-reference/statements/for-each-next-statement.md)örnek, azalan düzende yinelenen bir `For`...`Next` ifadesini gösterir. Örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir sabit listesi [bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ifade parametreleri `+`, `-`, `>=`ve `<=` işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır.

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Koleksiyonlar](../../programming-guide/concepts/collections.md)
