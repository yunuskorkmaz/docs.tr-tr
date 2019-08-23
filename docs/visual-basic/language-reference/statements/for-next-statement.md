---
title: For...Next Deyimi (Visual Basic)
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
ms.openlocfilehash: 9a9aed51f6d7bf3233e6e89116b8209b22f3d15d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912413"
---
# <a name="fornext-statement-visual-basic"></a>For...Next Deyimi (Visual Basic)
Bir deyim grubunu belirtilen sayıda yineler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`counter`|`For` İfadesinde gereklidir. Sayısal değişken. Döngünün denetim değişkeni. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|  
|`datatype`|İsteğe bağlı. Veri türü `counter`. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.|  
|`start`|Gerekli. Sayısal ifade. Başlangıç değeri `counter`.|  
|`end`|Gerekli. Sayısal ifade. Öğesinin `counter`son değeri.|  
|`step`|İsteğe bağlı. Sayısal ifade. Döngü aracılığıyla her seferinde `counter` arttırılan miktar.|  
|`statements`|İsteğe bağlı. `For` Ve`Next` arasındaki bir veya daha fazla deyim, belirtilen sayıda kez çalıştırıldı.|  
|`Continue For`|İsteğe bağlı. Denetimi sonraki döngü yinelemesine aktarır.|  
|`Exit For`|İsteğe bağlı. Denetimi `For` döngünün dışına aktarır.|  
|`Next`|Gerekli. `For` Döngünün tanımını sonlandırır.|  
  
> [!NOTE]
> `To` Anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır. Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimlerinde. Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Basit örnekler  
 Şunu kullanıyorsunuz `For`... `Next` bir deyim kümesini bir dizi kez yinelemek istediğinizde yapı.  
  
 Aşağıdaki örnekte, `index` değişken 1 değeri ile başlar ve döngünün her yinelemeyle artırılır, bu `index` değer 5 ' e ulaştığında biter.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 Aşağıdaki örnekte, `number` değişken 2 ' de başlar ve döngünün her yinelemesinde 0,25 tarafından azaltılır ve `number` değeri 0 ' dan sonra sona eriyor. `Step` Öğesinin`-.25` bağımsız değişkeni, döngünün her yinelemede değeri 0,25 azaltır.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  Bir [while... End while ekstresi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [Do... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır. Ancak, döngüyü belirli sayıda kez çalıştırmayı beklediğinizi, a `For`... `Next` döngü daha iyi bir seçenektir. Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.  
  
## <a name="nesting-loops"></a>İç içe geçme döngüleri  
 Bir döngüyü diğerinin `For` içine yerleştirerek döngüleri iç içe geçirebilirsiniz. Aşağıdaki örnek iç içe geçmiş `For`... `Next` farklı adım değerlerine sahip yapılar. Dış döngü, döngünün her yinelemesi için bir dize oluşturur. İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Döngüleri iç içe aktardığınızda her döngünün benzersiz `counter` bir değişkeni olmalıdır.  
  
 Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et  
 Deyimden hemen `For`çıkar... `Exit For``Next` öğesini Loop ve `Next` deyimden sonraki deyime aktarır.  
  
 `Continue For` İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Aşağıdaki örnek, `Continue For` ve `Exit For` deyimlerinin kullanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Bir... içinde herhangi `Exit For` bir `For`sayıda deyim yerleştirebilirsiniz.`Next` gerçekleştirmek. İç içe yerleştirilmiş `For`... içinde kullanıldığında`Next` döngüler, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.  
  
 `Exit For`genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If`... `Then`... `Else` yapı). Aşağıdaki koşullar için kullanmak `Exit For` isteyebilirsiniz:  
  
- Tekrarlamaya devam etmek gereksiz veya imkansız. Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.  
  
- A `Try`... `Catch`... `Finally` ifade bir özel durumu yakalar. Bloğunun`Finally` sonunda kullanabilirsiniz `Exit For` .  
  
- Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Böyle bir koşulu tespit ediyorsanız, döngüyü atlamak için kullanabilirsiniz `Exit For` . Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Bir `For`... döngü başlar, Visual Basic `start` `step`değerlendirir, ve. `end` `Next` Visual Basic bu değerleri yalnızca şu anda değerlendirir ve sonra öğesine `start` `counter`atar. Bildirim bloğu çalıştırılmadan önce, Visual Basic ile `counter` `end`karşılaştırılır. `end` `For` Zatendeğerdendaha`Next` büyükse (ya da negatifse küçüktür ),döngüsonlanırvedenetimideyimdensonrakideyimegeçer.`step` `counter` Aksi halde, ekstre bloğu çalışır.  
  
 Her Visual Basic `Next` ifadesiyle karşılaştığında, `counter` `step` tarafındanartarveifadeyedöner.`For` Bu `end`, ile `counter` karşılaştırılır ve sonuca bağlı olarak bloğu çalıştırır ya da döngüden çıkar. Bu işlem, geçişe `counter` `end` veya bir `Exit For` deyimle karşılaşılana kadar devam eder.  
  
 Döngü geçene `counter` `end`kadar durmaz. `counter` Eşitse`end`, döngü devam eder. `counter` Bloğunun `counter` çalıştırılıpçalıştırılmadığını >=  belirleyen karşılaştırma, pozitif ise ve`end` negatifse. `step`  <=  `end` `step`  
  
 Bir döngü içinde değerini `counter` değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir. `start` ,`end`, Veya`step` değerini değiştirmek, döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.  
  
 Döngülerin iç içe geçirilmesi durumunda derleyici, iç düzeydeki `Next` `Next` deyimden önce dış iç içe düzeyin ifadesiyle karşılaşırsa bir hata bildirir. Ancak, derleyici bu çakışan hatayı yalnızca her `counter` `Next` ifadede belirtirseniz tespit edebilir.  
  
### <a name="step-argument"></a>Adım bağımsız değişkeni  
 Değeri `step` pozitif veya negatif olabilir. Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:  
  
|**Adım değeri**|**Döngü şunu içeriyorsa yürütülür**|  
|--------------------|--------------------------|  
|Pozitif veya sıfır|`counter` <= `end`|  
|Negatif|`counter` >= `end`|  
  
 Varsayılan değeri `step` 1 ' dir.  
  
### <a name="BKMK_Counter"></a>Sayaç bağımsız değişkeni  
 Aşağıdaki tabloda, tüm `counter` `For…Next` döngünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir. Bu belirleme, var olup `datatype` olmadığına `counter` ve önceden tanımlanmış olup olmadığına bağlıdır.  
  
|`datatype` Var mı?|`counter` Zaten tanımlanmış mı?|Sonuç ( `counter` tüm `For...Next` döngünün kapsamına alınmış yeni bir yerel değişken tanımlar)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Hayır|Evet|Hayır, `counter` zaten tanımlanmış. Öğesinin `counter` kapsamı, yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.|  
|Hayır|Hayır|Evet. Veri türü `start`, `end`, ve `step` ifadelerinden algılanır. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)|  
|Evet|Evet|Evet, ancak yalnızca varolan `counter` değişken yordamın dışında tanımlanmışsa. Bu değişken ayrı kalır. Varolan `counter` değişkenin kapsamı yordamın yerelse, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|Evet.|  
  
 Veri türü `counter` , aşağıdaki türlerden biri olması gereken yinelemenin türünü belirler:  
  
- A `Byte`, `SByte`, ,`UShort` ,,`ULong`,, ,`Decimal`,, veya .`Double` `Integer` `UInteger` `Short` `Long` `Single`  
  
- Bir [enum ifadesini](../../../visual-basic/language-reference/statements/enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.  
  
- Bir `Object`.  
  
- Aşağıdaki işleçlere sahip bir tür `T` , burada `B` bir `Boolean` ifadede kullanılabilecek bir tür.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Bu `counter` değişkeni isteğe bağlı olarak `Next` deyimde belirtebilirsiniz. Bu sözdizimi, özellikle iç içe `For` döngüler varsa programınızın okunabilirliğini geliştirir. Karşılık gelen `For` ifadede görünen değişkeni belirtmeniz gerekir.  
  
 , Ve `end`ifadeleri,türü widens olan herhangi bir `counter`veri türünü değerlendirebilir. `step` `start` `counter`İçin Kullanıcı tanımlı bir tür kullanırsanız,, veya `step` türlerini `end` `start`türüne `counter`dönüştürmek için `CType` dönüştürme işlecini tanımlamanız gerekebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır. [Her biri için bir değil... Next Ifadesinde](../../../visual-basic/language-reference/statements/for-each-next-statement.md), örnek bir `For`... `Next` azalan düzende yinelenen bir ifade. Bu örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sabit listesi [bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `+`ifade parametreleri `>=`, `-`,, ve `<=` işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Koleksiyonlar](../../programming-guide/concepts/collections.md)
