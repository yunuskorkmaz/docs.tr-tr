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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404647"
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

|Bölüm|Description|
|----------|-----------------|
|`counter`|`For`İfadesinde gereklidir. Sayısal değişken. Döngünün denetim değişkeni. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|
|`datatype`|İsteğe bağlı. Veri türü `counter` . Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|
|`start`|Gereklidir. Sayısal ifade. Başlangıç değeri `counter` .|
|`end`|Gereklidir. Sayısal ifade. Öğesinin son değeri `counter` .|
|`step`|İsteğe bağlı. Sayısal ifade. `counter`Döngü aracılığıyla her seferinde arttırılan miktar.|
|`statements`|İsteğe bağlı. Ve arasındaki bir veya daha fazla deyim `For` `Next` , belirtilen sayıda kez çalıştırıldı.|
|`Continue For`|İsteğe bağlı. Denetimi sonraki döngü yinelemesine aktarır.|
|`Exit For`|İsteğe bağlı. Denetimi döngünün dışına aktarır `For` .|
|`Next`|Gereklidir. Döngünün tanımını sonlandırır `For` .|

> [!NOTE]
> `To`Anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır. Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](select-case-statement.md) ve dizi bildirimlerinde. Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](dim-statement.md).

## <a name="simple-examples"></a>Basit örnekler

Bir `For` `Next` deyim kümesini bir dizi defa tekrarlamak istediğinizde bir... yapısı kullanırsınız.

Aşağıdaki örnekte, `index` değişken 1 değeri ile başlar ve döngünün her yinelemeyle artırılır, bu değer 5 ' e `index` ulaştığında biter.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

Aşağıdaki örnekte, `number` değişken 2 ' de başlar ve döngünün her yinelemesinde 0,25 tarafından azaltılır ve değeri 0 ' dan sonra sona eriyor `number` . `Step`Öğesinin bağımsız değişkeni, `-.25` döngünün her yinelemede değeri 0,25 azaltır.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> Bir [while... End while ekstresi](while-end-while-statement.md) veya [Do... Loop deyimi](do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır. Ancak, döngüyü belirli sayıda çalıştırmayı beklediğinizi, a `For` ... `Next` döngüsü daha iyi bir seçimdir. Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.

## <a name="nesting-loops"></a>İç içe geçme döngüleri

Bir `For` döngüyü diğerinin içine yerleştirerek döngüleri iç içe geçirebilirsiniz. Aşağıdaki örnek, `For` farklı adım değerlerine sahip iç içe... `Next` yapıları gösterir. Dış döngü, döngünün her yinelemesi için bir dize oluşturur. İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz bir değişkeni olmalıdır `counter` .

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

`Exit For`Deyimden hemen çıkar `For` ...`Next` öğesini Loop ve deyimden sonraki deyime aktarır `Next` .

`Continue For`İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).

Aşağıdaki örnek, `Continue For` ve deyimlerinin kullanımını gösterir `Exit For` .

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

`Exit For`Bir... içinde herhangi bir sayıda deyim yerleştirebilirsiniz. `For``Next` gerçekleştirmek. İç içe yerleştirilmiş `For` ... içinde kullanıldığında`Next` döngüler, en `Exit For` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

`Exit For`genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If` . `Then` .. ...`Else` Yapı). `Exit For`Aşağıdaki koşullar için kullanmak isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.

- A `Try` .. `Catch` . ...`Finally` ifade bir özel durumu yakalar. `Exit For`Bloğunun sonunda kullanabilirsiniz `Finally` .

- Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Böyle bir koşulu tespit ediyorsanız, `Exit For` döngüyü atlamak için kullanabilirsiniz. Daha fazla bilgi için bkz [. do... Loop deyimleri](do-loop-statement.md).

## <a name="technical-implementation"></a>Teknik Uygulama

Bir `For` ... `Next` döngüsü başladığında Visual Basic değerlendirir, `start` `end` ve `step` . Visual Basic bu değerleri yalnızca şu anda değerlendirir ve sonra öğesine atar `start` `counter` . Bildirim bloğu çalıştırılmadan önce, Visual Basic ile karşılaştırılır `counter` `end` . `counter`Zaten değerden daha büyükse `end` (ya da `step` negatifse küçüktür), `For` döngü sonlanır ve denetimi deyimden sonraki deyime geçer `Next` . Aksi halde, ekstre bloğu çalışır.

Her Visual Basic `Next` ifadesiyle karşılaştığında, `counter` tarafından artar `step` ve `For` ifadeye döner. Bu, ile `counter` karşılaştırılır `end` ve sonuca bağlı olarak bloğu çalıştırır ya da döngüden çıkar. Bu işlem `counter` `end` , geçişe veya bir `Exit For` deyimle karşılaşılana kadar devam eder.

Döngü geçene kadar durmaz `counter` `end` . `counter`Eşitse `end` , döngü devam eder. Bloğunun çalıştırılıp çalıştırılmadığını belirleyen karşılaştırma, `counter`  <=  `end` `step` pozitif ise ve `counter`  >=  `end` `step` negatifse.

`counter`Bir döngü içinde değerini değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir. `start`,, Veya değerini değiştirmek, `end` `step` döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.

Döngülerin iç içe geçirilmesi durumunda derleyici, `Next` `Next` iç düzeydeki deyimden önce dış iç içe düzeyin ifadesiyle karşılaşırsa bir hata bildirir. Ancak, derleyici bu çakışan hatayı yalnızca her ifadede belirtirseniz tespit edebilir `counter` `Next` .

### <a name="step-argument"></a>Adım bağımsız değişkeni

Değeri `step` pozitif veya negatif olabilir. Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:

|**Adım değeri**|**Döngü şunu içeriyorsa yürütülür**|
|--------------------|--------------------------|
|Pozitif veya sıfır|`counter` <= `end`|
|Negatif|`counter` >= `end`|

`step` varsayılan değeri 1'dir.

### <a name="counter-argument"></a><a name="BKMK_Counter"></a>Sayaç bağımsız değişkeni

Aşağıdaki tabloda, `counter` Tüm döngünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir `For…Next` . Bu belirleme `datatype` , var olup olmadığına ve önceden tanımlanmış olup olmadığına bağlıdır `counter` .

|`datatype`Var mı?|`counter`Zaten tanımlanmış mı?|Sonuç ( `counter` Tüm döngünün kapsamına alınmış yeni bir yerel değişken tanımlar `For...Next` )|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Hayır|Evet|Hayır, `counter` zaten tanımlanmış. Öğesinin kapsamı, `counter` yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.|
|No|Hayır|Evet. Veri türü `start` ,, `end` ve `step` ifadelerinden algılanır. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md)|
|Yes|Yes|Evet, ancak yalnızca varolan `counter` değişken yordamın dışında tanımlanmışsa. Bu değişken ayrı kalır. Varolan `counter` değişkenin kapsamı yordamın yerelse, bir derleme zamanı hatası oluşur.|
|Yes|Hayır|Evet.|

Veri türü, `counter` aşağıdaki türlerden biri olması gereken yinelemenin türünü belirler:

- A `Byte` , `SByte` , `UShort` , `Short` , `UInteger` , `Integer` , `ULong` , `Long` , `Decimal` , `Single` , veya `Double` .

- Bir [enum ifadesini](enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.

- Bir `Object` .

- `T`Aşağıdaki işleçlere sahip bir tür, burada `B` bir ifadede kullanılabilecek bir tür `Boolean` .

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Bu değişkeni isteğe bağlı olarak `counter` `Next` deyimde belirtebilirsiniz. Bu sözdizimi, özellikle iç içe döngüler varsa programınızın okunabilirliğini geliştirir `For` . Karşılık gelen ifadede görünen değişkeni belirtmeniz gerekir `For` .

`start`, `end` Ve ifadeleri, `step` türü widens olan herhangi bir veri türünü değerlendirebilir `counter` . İçin Kullanıcı tanımlı bir tür kullanırsanız,, `counter` `CType` veya türlerini türüne dönüştürmek için dönüştürme işlecini tanımlamanız gerekebilir `start` `end` `step` `counter` .

## <a name="example"></a>Örnek

Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır. [Her biri için bir değil... Next Ifadesinde](for-each-next-statement.md)örnek, `For` azalan düzende yinelenen bir... `Next` ifadesini gösterir. Bu örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir sabit listesi [bildirimi](enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ifade parametreleri,,, `+` `-` `>=` ve işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır `<=` .

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [Döngü Yapıları](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](while-end-while-statement.md)
- [Do...Loop Deyimi](do-loop-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](exit-statement.md)
- [Koleksiyonlar](../../programming-guide/concepts/collections.md)
