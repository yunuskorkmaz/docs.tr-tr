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
ms.openlocfilehash: 5d47d57b75005d5c13dbf8633981dfb2d57d3e90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826333"
---
# <a name="fornext-statement-visual-basic"></a>For...Next Deyimi (Visual Basic)
Belirtilen sayıda deyim grubunu yineler.  
  
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
|`counter`|Gerekli `For` deyimi. Sayısal değişkeni. Denetim değişkeni for döngüsü. Daha fazla bilgi için [sayaç değişkeni](#BKMK_Counter) bu konuda.|  
|`datatype`|İsteğe bağlı. Veri türü `counter`. Daha fazla bilgi için [sayaç değişkeni](#BKMK_Counter) bu konuda.|  
|`start`|Gerekli. Sayısal ifade. Başlangıç değeri oluşan `counter`.|  
|`end`|Gerekli. Sayısal ifade. Son değeri `counter`.|  
|`step`|İsteğe bağlı. Sayısal ifade. Tutarı `counter` döngü her zaman artırılır.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyim arasında `For` ve `Next` belirtilen sayıda çalıştırın.|  
|`Continue For`|İsteğe bağlı. Sonraki döngü yinelemesi denetimine aktarımlarına.|  
|`Exit For`|İsteğe bağlı. Dışı denetim aktarır `For` döngü.|  
|`Next`|Gerekli. Tanımını sonlandırır `For` döngü.|  
  
> [!NOTE]
>  `To` Sayaç aralığını belirtmek için Bu deyimde anahtar sözcüğü kullanılır. Bu anahtar sözcüğünü kullanabilirsiniz [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimleri. Dizi bildirimleri hakkında daha fazla bilgi için bkz: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>İlişkin basit örnekler  
 Kullandığınız bir `For`... `Next` yapısı deyimleri bir dizi kümesi birkaç kez yineleyin istediğinizde.  
  
 Aşağıdaki örnekte, `index` değişkeni 1 değeriyle başlatır ve sonra değerini bitiş döngünün her yineleme ile artırılır `index` 5 ulaşır.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 Aşağıdaki örnekte, `number` değişkeni 2'de başlar ve değerini sonra biten bir döngü her yinelemede 0,25 tarafından azaltılmış `number` 0 ulaşır. `Step` Bağımsız değişkeni `-.25` 0,25 döngünün her yinelemesinden şirket tarafından değeri azaltır.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) ne zaman önceden deyimleri bir döngüde çalıştırılacak kaç kez tanımadığınız iyi çalışır. Ancak, ne zaman beklediğiniz zaman, belirli sayıda döngü çalıştırılacak bir `For`... `Next` döngü daha iyi bir seçimdir. Döngü girdiğinizde yineleme sayısını belirler.  
  
## <a name="nesting-loops"></a>İç içe döngüleri  
 İç içe yerleştirebilirsiniz `For` içindeki başka bir döngü koyarak döngüleri. Aşağıdaki örnek, iç içe geçmiş gösterir `For`... `Next` adım farklı değerlere sahip yapılar. Dış döngü, her döngü için bir dize oluşturur. Döngünün her yinelemesinden için bir döngü sayaç değişkeni iç döngü azaltır.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 İç içe döngüleri, her döngü benzersiz olması gerekir `counter` değişkeni.  
  
 Birbirine farklı denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>İçin çıkmak ve için devam edin  
 `Exit For` Deyimi hemen çıkar `For`...`Next` izleyen deyime döngüsü ve aktarımları denetimine `Next` deyimi.  
  
 `Continue For` Deyime aktarır denetimi hemen döngünün sonraki yinelemesine. Daha fazla bilgi için [Continue deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Aşağıdaki örnek, kullanımını gösterir `Continue For` ve `Exit For` deyimleri.  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Herhangi bir sayıda koyabilirsiniz `Exit For` deyimlerinde bir `For`...`Next` Döngü. Kullanıldığında içinde iç içe geçmiş `For`...`Next` Döngüler, `Exit For` en içteki döngüden çıkılıp ve yüksek düzeye iç içe aktarır.  
  
 `Exit For` Bazı koşullar değerlendirdikten sonra genellikle kullanılır (örneğin, bir `If`... `Then`... `Else` yapısı). Kullanmak istediğiniz `Exit For` aşağıdaki koşulları için:  
  
-   Yineleme devam gereksiz veya imkansız olabilir. Bu durum, hatalı bir değer veya bir sonlandırma isteği oluşturabilirsiniz.  
  
-   A `Try`... `Catch`... `Finally` deyimi bir özel durumu yakalar. Kullanabileceğinize `Exit For` sonunda `Finally` blok.  
  
-   Büyük veya hatta sonsuz birkaç kez çalıştırabileceğiniz bir döngü sonsuz bir döngü var. Bir koşul algılama, kullanabileceğiniz `Exit For` döngüden çıkma. Daha fazla bilgi için [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Olduğunda bir `For`... `Next` döngü başlatır, Visual Basic değerlendirir `start`, `end`, ve `step`. Visual Basic, yalnızca bu zaman ve atar ardından bu değerleri değerlendirir `start` için `counter`. Önce deyim bloğu çalışır, Visual Basic karşılaştırır `counter` için `end`. Varsa `counter` zaten değerinden daha büyük `end` değeri (veya daha küçük `step` negatif ise), `For` döngüsü sona erdiğinde ve denetim izleyen deyime geçer `Next` deyimi. Aksi takdirde, deyim bloğunu çalıştırır.  
  
 Her zaman Visual Basic karşılaştığı `Next` deyimi artırır `counter` tarafından `step` ve döndürür `For` deyimi. Yeniden karşılaştırır `counter` için `end`, ve tekrar bu bloğu çalışır veya sonuca bağlı olarak döngüden çıkılıp. Bu işlem kadar devam eder `counter` geçirir `end` veya `Exit For` deyimi karşılaştı.  
  
 Döngü kadar bitmez `counter` geçti `end`. Varsa `counter` eşittir `end`, döngü devam eder. Blok çalıştırılıp çalıştırılmayacağını belirleyen karşılaştırma `counter`  <=  `end` varsa `step` pozitif ve `counter`  >=  `end` varsa `step` negatiftir.  
  
 Değerini değiştirirseniz `counter` iç ederken döngü, kodunuzu ve hata ayıklaması daha zor olabilir. Değerinin değiştirilmesi `start`, `end`, veya `step` döngü ilk kez girildiğinde belirlenen yineleme değerleri etkilemez.  
  
 İç içe döngüleri, derleyici bir hata varsa bulduğu sinyalleri `Next` ifadesi bir dış iç içe geçme düzeyi önce `Next` iç düzeyine ifadesi. Ancak, derleyici bu hata yalnızca belirtirseniz, çakışan algılayabilir `counter` içinde her `Next` deyimi.  
  
### <a name="step-argument"></a>Adım bağımsız değişken  
 Değerini `step` pozitif veya negatif olabilir. Bu parametre aşağıdaki tabloya göre bir çevrim işleme belirler:  
  
|**Adım değeri**|**Döngü ise yürütülür.**|  
|--------------------|--------------------------|  
|Pozitif veya sıfır|`counter` <= `end`|  
|Negatif|`counter` >= `end`|  
  
 Varsayılan değer olan `step` 1'dir.  
  
### <a name="BKMK_Counter"></a> Sayaç değişkeni  
 Aşağıdaki tablo belirtir olup olmadığını `counter` tüm kapsamlıdır yeni bir yerel değişken tanımlar `For…Next` döngü. Bu belirleme bağlıdır `datatype` var olup olmadığını ve `counter` zaten tanımlandı.  
  
|Olan `datatype` var?|Olan `counter` zaten tanımlanmış?|Sonuç (olmadığını `counter` tüm kapsamlıdır yeni bir yerel değişken tanımlar `For...Next` döngüsü)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Hayır|Evet|Hayır, çünkü `counter` zaten tanımlandı. Varsa kapsamını `counter` yordamı için yerel olmayan bir derleme zamanı uyarı oluşur.|  
|Hayır|Hayır|Evet. Veri türü içinden gösterilen `start`, `end`, ve `step` ifadeler. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Evet|Evet|Evet, ancak yalnızca mevcut `counter` değişkeni dışında yordamı tanımlanır. Bu değişken ayrı olarak kalır. Varsa varolan kapsamı `counter` değişkendir yordamı için yerel bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|Evet.|  
  
 Veri türü `counter` türü aşağıdaki türlerden biri olmalıdır yinelemenin belirler:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, veya `Double`.  
  
-   Kullanarak bildirdiğiniz bir numaralandırma bir [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   Bir `Object`.  
  
-   Bir tür `T` aşağıdaki işleçleri olan burada `B` kullanılabilir bir tür bir `Boolean` ifade.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 İsteğe bağlı olarak belirtebilirsiniz `counter` değişkeninde `Next` deyimi. Özellikle, iç içe bu söz dizimi programınızı okunabilirliğini artırır `For` döngüleri. İlgili görünen değişkeni belirtmeniz gerekir `For` deyimi.  
  
 `start`, `end`, Ve `step` nevyhodnocovat türüne widens herhangi bir veri türü için `counter`. Kullanıcı tanımlı bir tür için kullanıyorsanız `counter`, tanımlamak zorunda `CType` türlerini dönüştürmek için dönüştürme işleci `start`, `end`, veya `step` türüne `counter`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir genel listeden tüm öğeleri kaldırır. Yerine bir [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md), örnekte gösterildiği bir `For`... `Next` azalan sırada yenileyen deyimi. Örneğin bu tekniği kullanır, çünkü `removeAt` yöntemi kaldırılan öğeyi sonra bir daha düşün dizin değerine sahip öğeleri neden olur.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanılarak bildirilen bir sabit listesi üzerinden yinelenir bir [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, İşleç aşırı yüklemeleri için bir sınıf deyimi parametreleri kullanmak `+`, `-`, `>=`, ve `<=` işleçleri.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Koleksiyonlar](../../programming-guide/concepts/collections.md)
