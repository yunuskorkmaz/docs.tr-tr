---
title: Option Strict deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: ac8f6fa2ebd2f8d846c3662184c83a83477e2311
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659267"
---
# <a name="option-strict-statement"></a>Option Strict Deyimi
Örtük veri türü dönüşümünü sadece genişletme dönüştürmeleri için sınırlar, geç bağlamaya izin vermiyor ve örtük sonuçlanan yazmaya izin vermeyen bir `Object` türü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. Sağlar `Option Strict` denetleniyor.|  
|`Off`|İsteğe bağlı. Devre dışı bırakır `Option Strict` denetleniyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `Option Strict On` veya `Option Strict` görünür bir dosyada, aşağıdaki durumlar neden bir derleme zamanı hatası:  
  
-   Örtük daraltma dönüşümleri  
  
-   Geç bağlama  
  
-   Örtük sonuçlanan yazarak bir `Object` türü  
  
> [!NOTE]
>  Üzerinde ayarlanmış uyarı yapılandırmalarında [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), bir derleme zamanı hatasına neden olan üç koşulları karşılık gelen üç seçenek vardır. Bu ayarları nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [IDE'de uyarı yapılandırmaları ayarlamak için](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) bu konuda.  
  
 `Option Strict Off` Deyimi kapatır hata ve uyarı tüm üç koşullarını denetleme bile bu hataları veya uyarıları kapatma ilişkili IDE ayarları belirtin. `Option Strict On` Deyimi kapatır hata ve uyarı tüm üç koşullarını denetleme bile bu hataları veya uyarıları kapatmak için ilişkili IDE ayarları belirtin.  
  
 Kullandıysanız, `Option Strict` deyimi, bir dosyada başka bir kod deyimlerini önce görünmelidir.  
  
 Ayarladığınızda `Option Strict` için `On`, Visual Basic veri türleri için tüm programlama öğeleri belirtildiğinden emin denetler. Veri türleri açıkça belirtilen veya yerel tür çıkarımı kullanılarak belirtilen. Tüm programlama öğeleriniz için veri türlerini belirtme, aşağıdaki nedenlerden dolayı önerilir:  
  
-   Bu değişkenler ve parametreler için IntelliSense desteği sağlar. Bu kod yazarken özelliklerini ve diğer üyeleri görmenizi sağlar.  
  
-   Ancak, tür denetimi gerçekleştirmek derleyiciyi etkinleştirir. Tür denetimini çalışma zamanında tür dönüştürme hataları nedeniyle başarısız olabilir deyimleri bulmanıza yardımcı olur. Ayrıca, bu yöntemleri desteği olmayan nesneler üzerinde yöntemlere yapılan çağrılar da tanımlar.  
  
-   Onu kod yürütmeyi hızlandırır. Bunun bir nedeni olduğundan bir programlama öğesi için bir veri türü belirtmezseniz, Visual Basic Derleyicisi, atamasını `Object` türü. Derlenmiş kod arasında ileri ve geri dönüştürmek sahip olabileceği `Object` ve diğer veri türleri, performansı azaltır.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Daraltma örtük dönüştürme hataları  
 Bir daraltma dönüştürmesi olan bir örtük veri türü dönüştürme olduğunda daraltma örtük dönüştürme hataları oluşur.  
  
 Visual Basic birçok veri türleri, diğer veri türlerine dönüştürme yapabilirsiniz. Bir veri türünün değeri daha az duyarlılık ya da daha küçük bir kapasite olan bir veri türüne dönüştürülürken veri kaybı oluşabilir. Böyle bir daraltma dönüşümü başarısız olursa, bir çalışma zamanı hatası oluşur. `Option Strict` bunları engellemek için bu daraltma dönüştürmelerini derleme zamanında bildirim sağlar. Daha fazla bilgi için [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ve [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Hatalara neden olabilir. dönüştürme ifadelerinde oluşan örtük dönüşümler içerir. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Ne zaman, birleştirme dizeleri kullanarak [& işleci](../../../visual-basic/language-reference/operators/concatenation-operator.md), dizelere tüm dönüştürmeleri genişletme olması kabul edilir. Bir daraltma örtük dönüştürme hatası, olsa bile bu dönüştürmeleri oluşturmaz şekilde `Option Strict` açıktır.  
  
 Karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken içeren bir yöntem çağırdığınızda bir daraltma dönüşümü bir derleme zamanı hatasına neden olur `Option Strict` açıktır. Bir genişletme dönüşümü veya açık bir dönüştürme kullanarak derleme zamanı hatası önleyebilirsiniz.  
  
 Daraltma örtük dönüştürme hataları öğeleri dönüştürmelerinde derleme zamanında gizlenir bir `For Each…Next` döngü denetim değişkeni koleksiyonu. Bu meydana bile `Option Strict` açıktır. Daha fazla bilgi için bkz: "Daraltma dönüştürmeleri" bölümünde [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Geç bağlama hataları  
 Bir özellik veya yöntem türü olarak bildirilmiş bir değişken atandığında, nesnenin geç bağlama `Object`. Daha fazla bilgi için [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Örtük nesne türü hataları  
 Örtük nesne türü hatalar ortaya uygun bir tür olamaz bildirilmiş bir değişken için bu nedenle bir tür çıkarımı yapılan `Object` algılanır. Kullandığınızda öncelikle böyle bir `Dim` kullanmadan bir değişken bildirmek için deyimi bir `As` yan tümcesi ve `Option Infer` kapalıdır. Daha fazla bilgi için [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).  
  
 Yöntem parametreleri için `As` yan tümcesi ise isteğe bağlı ise `Option Strict` kapalıdır. Ancak, herhangi bir parametre kullanıyorsa bir `As` yan tümcesi, bunların tümü gerekir kullanır. Varsa `Option Strict` açıktır, `As` yan tümcesi için her bir parametre tanımında gereklidir.  
  
 Kullanmadan bir değişken bildirirseniz bir `As` yan tümcesi ve `Nothing`, değişkeni bir tür olan `Object`. Bu durumda hiçbir derleme zamanı hatası oluşur, `Option Strict` açıktır ve `Option Infer` açıktır. Bunun bir örneği `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  
 Aşağıdaki tabloda çeşitli birleşimlerini başlatıcısında ve veri türünü belirtmenin sonuçlarını açıklar bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Belirtilen veri türü?|Belirtilen başlatıcı?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Varsa `Option Strict` olan kapalı (varsayılan), değişkeni ayarlanır `Nothing`.<br /><br /> Varsa `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|Varsa `Option Infer` değişken alır veri öğesinin başlatıcısını yazın (varsayılan), olan. Bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türünü alan `Object`.<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken veri türü için varsayılan değer için başlatılır. Daha fazla bilgi için [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcı veri türü belirtilen veri türüne dönüştürülebilir değil, bir derleme zamanı hatası oluşur.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Ne zaman Option Strict deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Strict` deyimi **katı tanımlama seçeneği** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. **Derle sayfası** hataya neden olan koşulları üzerinde ek denetim sağlayan ayarları vardır.  
  
 Komut satırı derleyicisini kullanıyorsanız, kullanabileceğiniz [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği için bir ayarı belirtmek `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Option Strict IDE içinde ayarlamak için  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2.  Üzerinde **derleme** sekmesinde, değer kümesi'nde **Option Strict** kutusu.  
  
###  <a name="conditions"></a> IDE'de uyarı yapılandırmaları ayarlamak için  
 Kullanırken [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) yerine bir `Option Strict` deyimi, hatalara neden olan koşulları üzerinde ek denetim vardır. **Uyarı yapılandırmaları** bölümünü **derle sayfası** karşılık gelen bir derleme zamanı hatasına neden olan üç koşulları ayarlarına sahip olduğunda `Option Strict` açıktır. Bu ayarlar şunlardır:  
  
-   **Örtük dönüştürme**  
  
-   **Geç bağlama; Çağrı çalışma zamanında başarısız olabilir**  
  
-   **Örtük tür; Nesne varsayıldı**  
  
 Ayarladığınızda **Option Strict** için **üzerinde**, bu uyarı yapılandırma ayarlarını üç kümesine **hata**. Ayarladığınızda **Option Strict** için **kapalı**, tüm üç ayarları kümesine **hiçbiri**.  
  
 Her uyarı yapılandırma ayarı ayrı ayrı değiştirebileceğiniz **hiçbiri**, **uyarı**, veya **hata**. Üç uyarı yapılandırma ayarlarını ayarlandıysa **hata**, `On` görünür `Option strict` kutusu. Üç ayarlandıysa **hiçbiri**, `Off` bu kutuda görünür. Bu ayarlar, diğer herhangi bir birleşimini için **(özel)** görünür.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Yeni projeler için Option Strict varsayılan ayarını ayarlamak için  
 Bir proje oluşturduğunuzda **Option Strict** ayarını **derleme** sekmesinde ayarlanmış **Option Strict** ayarı **seçenekleri** iletişim kutusu.  
  
 Ayarlanacak `Option Strict` bu iletişim kutusunda, üzerinde **Araçları** menüsünde tıklayın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarda **VB varsayılanları** olduğu `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Option Strict komut satırında ayarlamak için  
 Dahil [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneğini **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler, derleme zamanı hatalarına daraltma dönüşümleri örtük tür dönüştürmelerini neden gösterir. Bu hata kategorisi karşılık gelen **örtük dönüştürme** üzerinde koşul **derle sayfası**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme zamanı hatası geç bağlama tarafından neden gösterir. Bu hata kategorisi karşılık gelen **Late bağlama; çağrı çalışma zamanında başarısız olabilir** üzerinde koşul **derle sayfası**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek örtük bir türü ile bildirilen değişkenler kaynaklanan hatalar gösterir `Object`. Bu hata kategorisi karşılık gelen **örtük tür; nesne kabul** üzerinde koşul **derle sayfası**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Office Çözümlerinde Geç Bağlama](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
