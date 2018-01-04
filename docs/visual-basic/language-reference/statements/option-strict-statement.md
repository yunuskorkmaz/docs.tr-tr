---
title: Option Strict Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a01edd918ea49c08defddb45bf23c33307e814f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="option-strict-statement"></a>Option Strict Deyimi
Yalnızca genişletme dönüşümleri için örtük veri türü dönüştürmelerini sınırlar, geç bağlama izin vermez ve örtük sonuçlanan yazmaya izin vermez bir `Object` türü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. Etkinleştirir `Option Strict` denetleniyor.|  
|`Off`|İsteğe bağlı. Devre dışı bırakır `Option Strict` denetleniyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `Option Strict On` veya `Option Strict` bir dosyada aşağıdaki durumlar neden bir derleme zamanı hata görünür:  
  
-   Örtük daraltma dönüşümleri  
  
-   Geç bağlama  
  
-   Örtük sonuçlanan yazarak bir `Object` türü  
  
> [!NOTE]
>  Üzerinde ayarlayabilirsiniz uyarı yapılandırmalarında [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), derleme zamanı hatasına neden olan üç koşulları karşılık gelen üç seçenek vardır. Bu ayarları nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [IDE içinde uyarı yapılandırmalarını ayarlamak için](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) bu konuda daha sonra.  
  
 `Option Strict Off` Deyimi kapanmadan hata ve uyarı tüm üç koşulları denetlemeyi dahi bu hatalar veya uyarılar için ilişkili IDE ayarları belirtin. `Option Strict On` Deyimi açar hata ve uyarı tüm üç koşulları denetlemeyi dahi bu hatalar veya uyarılar devre dışı bırakmak için ilişkili IDE ayarları belirtin.  
  
 Kullandıysanız, `Option Strict` deyimi, bir dosyada başka bir kod deyimleri önce görünmelidir.  
  
 Ayarladığınızda `Option Strict` için `On`, Visual Basic veri türleri için tüm programlama öğeleri belirtilir denetler. Veri türleri açıkça belirtilen veya yerel türü çıkarımı kullanılarak belirtilen. Veri türleri için tüm programlama öğeleri belirtme, aşağıdaki nedenlerle önerilir:  
  
-   Değişkenleri ve parametreleri için IntelliSense desteği sağlar. Bu kod yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.  
  
-   Tür denetleme gerçekleştirmek derleyici sağlar. Tür denetleme, çalışma zamanında tür dönüştürme hataları nedeniyle başarısız olabilir deyimleri bulmanıza yardımcı olur. Ayrıca, bu yöntemleri desteklemeyen nesneleri yöntemlere çağrıları tanımlar.  
  
-   Kod yürütmeyi hızlandırır. Bunun bir nedeni olan bir programlama öğesi için bir veri türü belirtmezseniz, Visual Basic derleyici onu atayacağını `Object` türü. Derlenmiş kod arasında ileri ve geri dönüştürmeniz gerekebilir `Object` ve performansını düşürür diğer veri türleri.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Örtük daraltma dönüştürme hataları  
 Daraltma dönüştürme örtük veri türü dönüşümü olduğunda örtük daraltma dönüştürme hataları oluşur.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]birçok veri türü diğer veri türlerine dönüştürebilirsiniz. Bir veri türü değeri daha az duyarlılık veya daha küçük bir kapasite sahip bir veri türüne dönüştürme sırasında veri kaybı oluşabilir. Daraltma bir dönüştürme başarısız olursa bir çalışma zamanı hatası oluşur. `Option Strict`bunları engellemek için bu daraltma dönüşümleri, derleme zamanı bildirim sağlar. Daha fazla bilgi için bkz: [dolaylı ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ve [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Hatalara neden olabilir. dönüşümleri ifadelerinde ortaya örtük dönüşümler içerir. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Ne zaman, birleştirme dizeleri kullanarak [& işleci](../../../visual-basic/language-reference/operators/concatenation-operator.md), tüm dönüştürmeler dizelere genişletme olması kabul edilir. Bu dönüşümleri oluşturmaz şekilde daraltma örtük dönüştürme hatası, bile `Option Strict` açıktır.  
  
 Karşılık gelen parametresinden farklı bir veri türünde bir bağımsız bir yöntemini çağırdığınızda, daraltma dönüşümü bir derleme zamanı hatası durumunda neden `Option Strict` açıktır. Derleme zamanı hata Genişletme dönüşümü veya açık dönüştürme kullanarak önleyebilirsiniz.  
  
 Örtük daraltma dönüştürme hataları öğelerde bulunan dönüştürmeleri için derleme zamanında gizlenir bir `For Each…Next` for döngüsü denetim değişkeni koleksiyonu. Bu meydana olsa bile `Option Strict` açıktır. Daha fazla bilgi için "Daraltma dönüşümleri" bölümüne bakın [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Geç bağlama hataları  
 Bir özellik veya yöntem türü olarak bildirilmiş bir değişkenin atandığında bir nesne geç bağlama `Object`. Daha fazla bilgi için bkz: [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Örtük nesne türü hataları  
 Örtük nesne türü hatalar ortaya uygun bir tür bulunamadığında bildirilen bir değişken için bu nedenle bir tür çıkarımı yapılan `Object` algılanır. Kullandığınızda bu öncelikle oluşur. bir `Dim` kullanmadan bir değişken bildirmek için deyimi bir `As` yan tümcesi ve `Option Infer` kapalıdır. Daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).  
  
 Yöntem parametreleri için `As` yan tümcesi isteğe bağlı ise `Option Strict` kapalıdır. Ancak, herhangi bir parametre kullanıyorsa, bir `As` yan tümcesi, bunların tümü gerekir kullanır. Varsa `Option Strict` açıktır, `As` her parametre tanımı yan tümcesi gereklidir.  
  
 Kullanmadan bir değişken bildirirseniz bir `As` yan tümcesi ve ayarlamak `Nothing`, bir değişken türü `Object`. Bu durumda derleme zamanı hata oluşmaz zaman `Option Strict` açıktır ve `Option Infer` açıktır. Bunun bir örneği `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  
 Veri türü ve Başlatıcı belirtmenin çeşitli birleşimleri sonuçları aşağıdaki tabloda açıklanmaktadır bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Belirtilen veri türü?|Belirtilen başlatıcı?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Varsa `Option Strict` olan kapalı (varsayılan), değişkenini ayarlamak `Nothing`.<br /><br /> Varsa `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|Varsa `Option Infer` Başlatıcı değişken alır veri türü (varsayılan), olduğunda. Bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türü alır `Object`.<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken veri türü için varsayılan değer için başlatılır. Daha fazla bilgi için bkz: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcı'veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Ne zaman Option Strict deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Strict` deyimi, **seçeneği katı** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. **Derle sayfası** hataya neden olan koşulları üzerinde ek denetim sağlayan ayarları vardır.  
  
 Komut satırı derleyicisi kullanıyorsanız, kullanabileceğiniz [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği için bir ayar belirtmek için `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Option Strict IDE'de ayarlamak için  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Üzerinde **derleme** sekmesinde, değer kümesinde **Option Strict** kutusu.  
  
###  <a name="conditions"></a>IDE içinde uyarı yapılandırmalarını ayarlamak için  
 Kullandığınızda [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) yerine bir `Option Strict` deyimi, hatalara neden olan koşulları ek denetime sahiptir. **Uyarı yapılandırmaları** bölümünü **derle sayfası** derleme zamanı hatasına neden olan üç koşulları karşılık gelen ayarlara sahip olduğunda `Option Strict` açıktır. Bu ayarlar aşağıda verilmiştir:  
  
-   **Örtük dönüştürme**  
  
-   **Geç bağlama; Çalışma zamanında çağrısı başarısız olabilir**  
  
-   **Örtük türü; kabul nesnesi**  
  
 Ayarladığınızda **Option Strict** için **üzerinde**, bu uyarı yapılandırma ayarları üçünü kümesine **hata**. Ayarladığınızda **Option Strict** için **kapalı**, tüm üç ayarları ayarlamak **hiçbiri**.  
  
 Tek tek her uyarı yapılandırma ayarını değiştirebilirsiniz **hiçbiri**, **uyarı**, veya **hata**. Tüm üç uyarı yapılandırma ayarları ayarlandıysa **hata**, `On` görünür `Option strict` kutusu. Üç ayarlandıysa **hiçbiri**, `Off` bu kutuda görünür. Bu ayarlar, herhangi bir birleşimini için **(özel)** görüntülenir.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Option Strict varsayılan ayar yeni projeler için ayarlamak için  
 Bir proje oluşturduğunuzda **Option Strict** ayarı **derleme** sekmesini ayarlanmış **Option Strict** ayarı **seçenekleri** iletişim kutusu.  
  
 Ayarlamak için `Option Strict` bu iletişim kutusunda, üzerinde **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **VB varsayılanları** olan `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Option Strict komut satırında ayarlamak için  
 Dahil [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler, derleme zamanı hatalardır daraltma dönüşümleri örtük tür dönüşümleri tarafından göstermektedir. Bu kategori hataların karşılık gelen **örtük dönüşüm** üzerinde koşul **derle sayfası**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geç bağlama tarafından neden bir derleme zamanı hata gösterir. Bu kategori hataların karşılık gelen **Late bağlama; çağrısı çalışma zamanında başarısız olabilir** üzerinde koşul **derle sayfası**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler örtük bir türü ile bildirilmedi değişkenleri nedeni hataları göstermek `Object`. Bu kategori hataların karşılık gelen **örtük türü; kabul nesne** üzerinde koşul **derle sayfası**.  
  
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
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
