---
title: Option Strict ekstresi (Visual Basic)
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
ms.openlocfilehash: 8b7dfcfa394ed2c45adec9661ee1ea5823435223
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775437"
---
# <a name="option-strict-statement"></a>Option Strict Deyimi
Örtük veri türü dönüştürmelerini yalnızca genişletme dönüştürmelerine kısıtlar, geç bağlamaya izin vermez ve bir `Object` türüyle sonuçlanan örtülü yazmaya izin vermez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. @No__t_0 denetlemeye izin vermez.|  
|`Off`|İsteğe bağlı. @No__t_0 denetlemesini devre dışı bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dosyada `Option Strict On` veya `Option Strict` göründüğünde, aşağıdaki koşullar derleme zamanı hatasına neden olur:  
  
- Örtük daraltma dönüşümleri  
  
- Geç bağlama  
  
- @No__t_0 türü ile sonuçlanan örtük yazma  
  
> [!NOTE]
> [Derleme sayfasında, proje Tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)ayarlayabileceğiniz uyarı yapılandırmalarında, derleme zamanı hatasına neden olan üç koşula karşılık gelen üç ayar vardır. Bu ayarların nasıl kullanılacağı hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında [IDE 'de uyarı yapılandırması ayarlamak için](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) bölümüne bakın.  
  
 @No__t_0 ifade, ilişkili IDE ayarları bu hataları veya uyarıları açmak için belirtse bile, her üç koşulun hata ve uyarı denetimini devre dışı bırakır. @No__t_0 ifade, ilişkili IDE ayarları bu hataları veya uyarıları kapatmak için belirtse bile, her üç koşulun hata ve uyarı denetimini etkinleştirir.  
  
 Kullanıldıysa, `Option Strict` deyimi bir dosyadaki diğer kod deyimlerinin önüne gelmelidir.  
  
 @No__t_0 `On` ayarladığınızda, Visual Basic tüm programlama öğeleri için veri türlerinin belirtildiğini denetler. Veri türleri açıkça belirtilebilir veya yerel tür çıkarımı kullanılarak belirtilebilir. Aşağıdaki nedenlerden dolayı tüm programlama öğelerinizin veri türlerini belirtme önerilir:  
  
- Değişkenleriniz ve parametreleriniz için IntelliSense desteği sunar. Bu, kod yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.  
  
- Derleyicinin tür denetlemesi gerçekleştirmesini sağlar. Tür denetimi, tür dönüştürme hataları nedeniyle çalışma zamanında başarısız olan deyimler bulmanıza yardımcı olur. Ayrıca, bu yöntemleri desteklemeyen nesnelerdeki yöntemlere yapılan çağrıları tanımlar.  
  
- Kod yürütülmesini hızlandırır. Bunun bir nedeni, bir programlama öğesi için bir veri türü belirtplanlamıyorsanız Visual Basic derleyicisinin onu `Object` türüne atamasını sağlamaz. Derlenmiş kodun, `Object` ve diğer veri türleri arasında geri ve ileri bir şekilde dönüştürülmesi gerekebilir ve bu da performansı azaltır.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Örtük daraltma dönüştürme hataları  
 Örtük daraltma dönüştürme hataları, daraltma dönüştürmesi olan bir örtük veri türü dönüştürmesi olduğunda oluşur.  
  
 Visual Basic, birçok veri türünü diğer veri türlerine dönüştürebilir. Bir veri türünün değeri, daha az duyarlık veya daha küçük bir kapasiteye sahip bir veri türüne dönüştürüldüğünde veri kaybı oluşabilir. Bu tür bir daraltma dönüştürmesi başarısız olursa, bir çalışma zamanı hatası oluşur. `Option Strict`, bu daraltma dönüştürmelerinde derleme zaman bildirimini sağlar, böylece bunları önleyebilirsiniz. Daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ve [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Hatalara neden olabilecek dönüştürmeler, ifadelerde oluşan örtük dönüşümler içerir. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 [& işlecini](../../../visual-basic/language-reference/operators/concatenation-operator.md)kullanarak dizeleri birleştirme sırasında, dizelerin tüm dönüştürmeleri genişletme olarak kabul edilir. Bu nedenle, `Option Strict` açık olsa bile bu dönüşümler örtük bir daraltma dönüştürme hatası oluşturmaz.  
  
 Karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişkeni olan bir yöntemi çağırdığınızda, `Option Strict` açık olduğunda bir daraltma dönüştürmesi derleme zamanı hatasına neden olur. Bir genişletme dönüşümü veya açık bir dönüştürme kullanarak derleme zamanı hatasından kaçınabilirsiniz.  
  
 Örtük daraltma dönüştürme hataları, bir `For Each…Next` koleksiyonundaki öğelerden döngü denetim değişkenine dönüşümler için derleme zamanında bastırılır. @No__t_0 açık olsa bile bu oluşur. Daha fazla bilgi için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Geç bağlama hataları  
 Bir nesne, `Object` türünde olduğu bildirilmiştir bir özelliğin ya da yönteminin bir özelliğine atandığında geç bağlanır. Daha fazla bilgi için bkz. [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Örtük nesne türü hataları  
 Örtük nesne türü hataları, tanımlı bir değişken için uygun bir tür çıkarsanmadığında oluşur, bu nedenle bir `Object` türü algılanır. Bu öncelikle bir `As` yan tümcesi kullanmadan bir değişkeni bildirmek için bir `Dim` deyimi kullandığınızda oluşur ve `Option Infer` kapalı olur. Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Visual Basic Language belirtimi](../../../visual-basic/reference/language-specification/index.md).  
  
 Yöntem parametreleri için, `Option Strict` kapalıysa `As` yan tümcesi isteğe bağlıdır. Ancak, herhangi bir parametre `As` yan tümcesi kullanıyorsa, tümünün onu kullanması gerekir. @No__t_0 açık ise, her parametre tanımı için `As` yan tümcesi gereklidir.  
  
 Bir `As` yan tümcesi kullanmadan bir değişken bildirir ve `Nothing` olarak ayarlarsanız, değişkenin türü `Object` olur. @No__t_0 açık olduğunda ve `Option Infer` açık olduğunda bu durumda derleme zamanı hatası oluşmaz. Buna bir örnek `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  
 Aşağıdaki tabloda, bir [Dim ifadesinde](../../../visual-basic/language-reference/statements/dim-statement.md)veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.  
  
|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|@No__t_0 kapalıysa (varsayılan), değişken `Nothing` olarak ayarlanır.<br /><br /> @No__t_0 açık ise, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|@No__t_0 açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> @No__t_0 kapalıysa ve `Option Strict` kapalıysa, değişken `Object` veri türünü alır.<br /><br /> @No__t_0 kapalıysa ve `Option Strict` açık ise, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict bir Ifade yoksa  
 Kaynak kodu `Option Strict` bir ifade içermiyorsa, derleme sayfasındaki **katı** ayarı, [proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. **Derleme sayfasında** , hata oluşturan koşullar üzerinde ek denetim sağlayan ayarlar bulunur.  
  
 Komut satırı derleyicisini kullanıyorsanız, `Option Strict` bir ayar belirtmek için [-OptionStrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneğini kullanabilirsiniz.  
  
### <a name="to-set-option-strict-in-the-ide"></a>IDE 'de Option Strict ayarlamak için  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesinde, **katı kutu seçeneğini** belirleyin.  
  
### <a name="conditions"></a>IDE 'de uyarı yapılandırması ayarlamak için  
 Derleme sayfasını, bir `Option Strict` bildiri yerine [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullandığınızda, hata oluşturan koşullar üzerinde ek denetime sahip olursunuz. **Derleme sayfasının** **Uyarı yapılandırması** bölümü, `Option Strict` olduğunda derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlara sahiptir. Aşağıdaki ayarlar şunlardır:  
  
- **Örtük dönüştürme**  
  
- **Geç bağlama; çağrı çalışma zamanında başarısız olabilir**  
  
- **Örtük tür; nesne varsayıldı**  
  
 **Option Strict** **on on**olarak ayarlandığında, bu uyarı yapılandırma ayarlarının üçü de **hata**olarak ayarlanır. **Option Strict** ' i **off**olarak ayarlarsanız, üç ayar **hiçbiri None**olarak ayarlanır.  
  
 Her uyarı yapılandırma ayarını **hiçbiri**, **Uyarı**veya **hata**olarak tek tek değiştirebilirsiniz. Üç uyarı yapılandırma ayarı **hata**olarak ayarlanırsa, `On` `Option strict` kutusunda görünür. Üçü de **hiçbiri**olarak ayarlandıysa, bu kutuda `Off` görüntülenir. Bu ayarların diğer birleşimleri için **(özel)** görüntülenir.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Yeni projeler için katı varsayılan ayar seçeneğini ayarlamak için  
 Bir proje oluşturduğunuzda, **Derle** sekmesindeki **katı** ayarı **Seçenekler** iletişim kutusunda **katı** ayarına ayarlanır.  
  
 Bu iletişim kutusunda `Option Strict` ayarlamak için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** içindeki ilk varsayılan ayar `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Komut satırında Strict seçeneğini ayarlamak için  
 **Vbc** komutuna [-OptionStrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, dönüştürmeleri daraltma örtük tür dönüştürmelerinden kaynaklanan derleme zamanı hataları gösterilmektedir. Bu hata kategorisi, **derleme sayfasındaki** **örtük dönüştürme** koşuluna karşılık gelir.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geç bağlamanın neden olduğu bir derleme zamanı hatası gösterir. Bu hata kategorisi, geç bağlamaya karşılık gelir; çağrı **derleme sayfasındaki** **çalışma zamanında başarısız olabilir** .  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, örtük bir `Object` türü ile belirtilen değişkenlerin neden olduğu hatalar gösterilmektedir. Bu hata kategorisi, **derleme sayfasındaki** **örtük tür; nesne varsayıldı** koşulunu karşılık gelir.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office Çözümlerinde Geç Bağlama](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
