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
ms.openlocfilehash: 8c54189499b7d5b52cf93b4a0ae6cc47356bf57e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605335"
---
# <a name="fornext-statement-visual-basic"></a>For...Next Deyimi (Visual Basic)
Bir grup ifadeleri, belirtilen sayıda yineler.  
  
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
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`counter`|Gerekli `For` deyimi. Sayısal değişkeni. For döngüsü denetim değişkeni. Daha fazla bilgi için bkz: [sayaç bağımsız değişkeni](#BKMK_Counter) bu konuda daha sonra.|  
|`datatype`|İsteğe bağlı. Veri türü `counter`. Daha fazla bilgi için bkz: [sayaç bağımsız değişkeni](#BKMK_Counter) bu konuda daha sonra.|  
|`start`|Gerekli. Sayısal ifade. Başlangıç değeri `counter`.|  
|`end`|Gerekli. Sayısal ifade. Son değerini `counter`.|  
|`step`|İsteğe bağlı. Sayısal ifade. Miktarda `counter` her döngü artırılır.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimleri arasında `For` ve `Next` belirtilen sayıda çalıştırın.|  
|`Continue For`|İsteğe bağlı. Sonraki döngü tekrarında aktarımları denetimi.|  
|`Exit For`|İsteğe bağlı. Denetimin dışarı aktarır `For` döngü.|  
|`Next`|Gerekli. Tanımını sonlandırır `For` döngü.|  
  
> [!NOTE]
>  `To` Sayaç aralığını belirtmek için bu deyim içinde anahtar sözcüğü kullanılır. Bu anahtar sözcük de kullanabilirsiniz [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimleri. Dizi bildirimleri hakkında daha fazla bilgi için bkz: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Basit örnekler  
 Kullandığınız bir `For`... `Next` yapısı deyimleri kümesi kümesi birkaç kez yineleyin istediğinizde.  
  
 Aşağıdaki örnekte, `index` değişkeni 1 değeri ile başlar ve değeri sonra bitiş döngünün her yinelemesinden ile artırılır `index` 5 ulaşır.  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 Aşağıdaki örnekte, `number` değişkeni 2'de başlar ve 0,25 değeri sonra bitiş döngünün her yinelemesinden üzerinde daha az `number` 0 ulaşır. `Step` Bağımsız değişkeni `-.25` her döngü tekrarında üzerinde 0,25 tarafından değeri azaltır.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  A [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) ne zaman önceden deyimleri döngüde çalıştırılacak kaç kez tanımadığınız iyi çalışır. Ancak, ne zaman beklediğiniz zaman, belirli sayıda döngüsü çalıştırmak bir `For`... `Next` döngü daha iyi bir seçimdir. Döngü ilk girdiğinizde yineleme sayısını belirler.  
  
## <a name="nesting-loops"></a>Döngüler iç içe geçme  
 Geçirebilmenize `For` döngüler içinde başka bir döngü koyarak kullanılabilir. Aşağıdaki örnek, iç içe geçmiş gösterir `For`... `Next` farklı adım değerlere sahip yapıları. Dış döngü her döngü için bir dize oluşturur. Her döngü için bir döngü sayacı değişkeni iç döngü azaltır.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Döngüler iç içe geçme, her döngü benzersiz olmalıdır `counter` değişkeni.  
  
 Ayrıca, farklı denetim yapıları birbirine içinde yerleştirebilirsiniz. Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>İçin çıkın ve devam etmek için  
 `Exit For` Deyimi hemen çıkar `For`...`Next` aşağıdaki deyim döngü ve aktarımları denetimine `Next` deyimi.  
  
 `Continue For` Deyimi aktarır denetim hemen sonraki döngü için. Daha fazla bilgi için bkz: [devam deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Aşağıdaki örnek kullanımını göstermektedir `Continue For` ve `Exit For` deyimleri.  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Herhangi bir sayıda koyabilirsiniz `Exit For` deyimlerinde bir `For`...`Next` Döngü. Kullanıldığında içinde iç içe geçmiş `For`...`Next` Döngüler, `Exit For` en içteki döngüden çıkılıp ve iç içe geçme sonraki yüksek düzeyde denetim aktarır.  
  
 `Exit For` Bazı koşulunu sonra çoğunlukla kullanılır (örneğin, bir `If`... `Then`... `Else` yapısı). Kullanmak istediğiniz `Exit For` aşağıdaki koşulları için:  
  
-   Yinelemek etmeden gereksiz veya mümkün değil. Bu durum, hatalı bir değer veya bir sonlandırma isteği oluşturabilirsiniz.  
  
-   A `Try`... `Catch`... `Finally` deyimi bir özel durum yakalar. Kullanabileceğinize `Exit For` sonunda `Finally` bloğu.  
  
-   Bir büyük veya hatta sonsuz sayıda çalışacak bir döngü sonsuz bir döngüde var. Böyle bir durum tespit ederse kullanabileceğiniz `Exit For` döngü kaçınmak için. Daha fazla bilgi için bkz: [yapın... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Zaman bir `For`... `Next` döngü başlatır, Visual Basic değerlendirir `start`, `end`, ve `step`. Visual Basic, yalnızca bu zaman ve atar ardından bu değerleri değerlendirir `start` için `counter`. Önce deyim bloğu çalışır, Visual Basic karşılaştırır `counter` için `end`. Varsa `counter` zaten daha büyük `end` değeri (veya daha küçük `step` negatif), `For` döngü sona erer ve denetim geçişleri izleyen deyimine `Next` deyimi. Aksi takdirde deyimi bloğu çalıştırır.  
  
 Visual Basic karşılaştığı her zaman `Next` deyimi, onu artırır `counter` tarafından `step` ve döndürür `For` deyimi. Yeniden karşılaştırır `counter` için `end`, ve yeniden bloğu çalışır ya da sonucuna döngüden çıkılıp. Bu işlemi kadar sürer `counter` geçirir `end` veya bir `Exit For` deyimi karşılaştı.  
  
 Döngü kadar bitmez `counter` geçti `end`. Varsa `counter` eşittir `end`, döngünün devam eder. Blok çalıştırılıp çalıştırılmayacağını belirler karşılaştırma `counter`  <=  `end` varsa `step` pozitif ve `counter`  >=  `end` varsa `step` negatiftir.  
  
 Değeri değiştirirseniz `counter` döngü sırasında içinde kodunuzu okuyun ve hata ayıklama daha zor olabilir. Değerinin değiştirilmesi `start`, `end`, veya `step` döngü ilk girildiğinde belirlenen yineleme değerleri etkilemez.  
  
 Döngüler iç içe, derleyici bir hata durumunda bulduğu sinyalleri `Next` önce dış bir iç içe geçirme düzeyi deyiminin `Next` bir iç düzey ifadesi. Ancak, derleyici bu hata yalnızca belirtirseniz, çakışan algılayabilir `counter` içinde her `Next` deyimi.  
  
### <a name="step-argument"></a>Adım bağımsız değişken  
 Değeri `step` olumlu veya olumsuz olabilir. Bu parametre, döngü işleme aşağıdaki tabloya göre belirler:  
  
|**Adım değeri**|**Varsa döngü yürütür**|  
|--------------------|--------------------------|  
|Pozitif veya sıfır|`counter` <= `end`|  
|Negatif|`counter` >= `end`|  
  
 Varsayılan değer olan `step` 1'dir.  
  
###  <a name="BKMK_Counter"></a> Sayaç bağımsız değişken  
 Aşağıdaki tablo gösterir olup olmadığını `counter` tüm kapsamlıdır yeni bir yerel değişken tanımlar `For…Next` döngü. Bu belirleme bağlıdır `datatype` mevcut olup `counter` zaten tanımlandı.  
  
|Olan `datatype` var?|Olan `counter` önceden tanımlanmış?|Sonuç (olup olmadığını `counter` tüm kapsamlıdır yeni bir yerel değişken tanımlar `For...Next` döngü)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Hayır|Evet|Hayır, çünkü `counter` zaten tanımlandı. Varsa kapsamını `counter` yordamı için yerel olmayan bir derleme zamanı uyarı oluşur.|  
|Hayır|Hayır|Evet. Veri Türü alanından çıkarımı yapılan `start`, `end`, ve `step` ifadeler. Tür çıkarımı hakkında daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Evet|Evet|Evet, ancak yalnızca varolan `counter` değişkeni yordamın dışında tanımlanır. Bu değişken ayrı kalır. Varsa mevcut kapsamını `counter` değişkenidir yordamı için yerel bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|Evet.|  
  
 Veri türü `counter` aşağıdaki türlerden biri olmalıdır yineleme türünü belirler:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, veya `Double`.  
  
-   Kullanarak bildirme bir numaralandırma bir [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   Bir `Object`.  
  
-   Bir tür `T` aşağıdaki işleçleri sahip olduğu `B` kullanılabilir bir tür bir `Boolean` ifade.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 İsteğe bağlı olarak belirtebilirsiniz `counter` değişkeni `Next` deyimi. Özellikle, iç içe geçmiş durumunda bu sözdizimi, programınızı okunabilirliğini artırır `For` döngüler. İlgili görünür değişkeni belirtmeniz gerekir `For` deyimi.  
  
 `start`, `end`, Ve `step` ifadeleri değerlendirme türü için widens herhangi bir veri türü için `counter`. Kullanıcı tanımlı bir tür için kullanırsanız, `counter`, tanımlamak zorunda kalabilirsiniz `CType` türlerini dönüştürmek için dönüştürme işleci `start`, `end`, veya `step` türüne `counter`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır. Yerine bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md), örnekte gösterildiği bir `For`... `Next` azalan sırada tekrarlanan deyimi. Örneğin bu tekniği kullanır, çünkü `removeAt` yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılan öğeden sonra öğeleri neden olur.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanarak bildirilmiş bir numaralandırma dolaşır bir [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, deyimi parametreleri için işleç aşırı yüklemeye sahip bir sınıf kullanma `+`, `-`, `>=`, ve `<=` işleçler.  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic.List%601>  
 [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Koleksiyonlar](../../programming-guide/concepts/collections.md)
