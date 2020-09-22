---
title: Option Strict Deyimi
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
ms.openlocfilehash: ab1094961e2bc3aed0e975e40369a5f5c1ba93eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873139"
---
# <a name="option-strict-statement"></a>Option Strict Deyimi

Örtük veri türü dönüşümlerini yalnızca genişletme dönüştürmelerine kısıtlar, geç bağlamaya izin vermez ve bir tür ile sonuçlanan örtülü yazmaya izin vermez `Object` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. Denetlemeye izin vermez `Option Strict` .|  
|`Off`|İsteğe bağlı. Denetlemeyi devre dışı bırakır `Option Strict` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `Option Strict On` `Option Strict` Bir dosyada olduğunda veya göründüğünde, aşağıdaki koşullar derleme zamanı hatasına neden olur:  
  
- Örtük daraltma dönüşümleri  
  
- Geç bağlama  
  
- Bir tür ile sonuçlanan örtük yazma `Object`  
  
> [!NOTE]
> [Derleme sayfasında, proje Tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)ayarlayabileceğiniz uyarı yapılandırmalarında, derleme zamanı hatasına neden olan üç koşula karşılık gelen üç ayar vardır. Bu ayarların nasıl kullanılacağı hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında [IDE 'de uyarı yapılandırması ayarlamak için](option-strict-statement.md#conditions) bölümüne bakın.  
  
 `Option Strict Off`İfade, ILIŞKILI IDE ayarları bu hataları veya uyarıları açmak için belirtse bile, her üç koşulun hata ve uyarı denetimini devre dışı bırakır. `Option Strict On`İfade, ILIŞKILI IDE ayarları bu hataları veya uyarıları kapatmak için belirtse bile, her üç koşulun hata ve uyarı denetimini etkinleştirir.  
  
 Kullanıldıysa, `Option Strict` deyimi bir dosyadaki diğer kod deyimlerinin önüne gelmelidir.  
  
 `Option Strict`Olarak ayarladığınızda `On` , Visual Basic tüm programlama öğeleri için veri türlerinin belirtildiğini denetler. Veri türleri açıkça belirtilebilir veya yerel tür çıkarımı kullanılarak belirtilebilir. Aşağıdaki nedenlerden dolayı tüm programlama öğelerinizin veri türlerini belirtme önerilir:  
  
- Değişkenleriniz ve parametreleriniz için IntelliSense desteği sunar. Bu, kod yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.  
  
- Derleyicinin tür denetlemesi gerçekleştirmesini sağlar. Tür denetimi, tür dönüştürme hataları nedeniyle çalışma zamanında başarısız olan deyimler bulmanıza yardımcı olur. Ayrıca, bu yöntemleri desteklemeyen nesnelerdeki yöntemlere yapılan çağrıları tanımlar.  
  
- Kod yürütülmesini hızlandırır. Bunun bir nedeni, bir programlama öğesi için bir veri türü belirtplanlamıyorsanız Visual Basic derleyicisinin bu türü atamasını sağlamaz `Object` . Derlenmiş kodun ve diğer veri türleri arasında geri ve ileri dönüştürülmesi gerekebilir `Object` ve bu da performansı azaltır.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Örtük daraltma dönüştürme hataları  

 Örtük daraltma dönüştürme hataları, daraltma dönüştürmesi olan bir örtük veri türü dönüştürmesi olduğunda oluşur.  
  
 Visual Basic, birçok veri türünü diğer veri türlerine dönüştürebilir. Bir veri türünün değeri, daha az duyarlık veya daha küçük bir kapasiteye sahip bir veri türüne dönüştürüldüğünde veri kaybı oluşabilir. Bu tür bir daraltma dönüştürmesi başarısız olursa, bir çalışma zamanı hatası oluşur. `Option Strict` Bu daraltma dönüştürmelerinde derleme zamanı bildirimini sağlar, böylece bunları önleyebilirsiniz. Daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ve [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Hatalara neden olabilecek dönüştürmeler, ifadelerde oluşan örtük dönüşümler içerir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [+ İşleci](../operators/addition-operator.md)  
  
- [+ = İşleci](../operators/addition-assignment-operator.md)  
  
- [\ İşleci (Visual Basic)](../operators/integer-division-operator.md)  
  
- [/= İşleci (Visual Basic)](../operators/floating-point-division-assignment-operator.md)  
  
- [Char Veri Türü](../data-types/char-data-type.md)  
  
 [& işlecini](../operators/concatenation-operator.md)kullanarak dizeleri birleştirme sırasında, dizelerin tüm dönüştürmeleri genişletme olarak kabul edilir. Bu nedenle, açık olsa bile bu dönüştürmeler örtük bir daraltma dönüştürme hatası oluşturmaz `Option Strict` .  
  
 Karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişkeni olan bir yöntemi çağırdığınızda, bir daraltma dönüştürmesi açık olursa derleme zamanı hatasına neden olur `Option Strict` . Bir genişletme dönüşümü veya açık bir dönüştürme kullanarak derleme zamanı hatasından kaçınabilirsiniz.  
  
 Örtük daraltma dönüştürme hataları `For Each…Next` , bir koleksiyondaki öğelerden döngü denetim değişkenine dönüşümler için derleme zamanında bastırılır. Açık olsa bile bu durum oluşur `Option Strict` . Daha fazla bilgi için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Geç bağlama hataları  

 Bir nesne, tür olarak belirtilen bir özelliğin veya yöntemin bir özelliğine atandığında geç bağlanır `Object` . Daha fazla bilgi için bkz. [erken ve geç bağlama](../../programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Örtük nesne türü hataları  

 Örtük nesne türü hataları, tanımlı bir değişken için uygun bir tür çıkarsanmadığında oluşur, bu nedenle bir türü `Object` algılanır. Bu öncelikle `Dim` , bir yan tümce kullanmadan bir değişkeni bildirmek için bir deyimi kullandığınızda oluşur `As` ve `Option Infer` kapalı olur. Daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Visual Basic Language belirtimi](../../reference/language-specification/index.md).  
  
 Yöntem parametreleri için, `As` yan tümcesi kapalıysa isteğe bağlıdır `Option Strict` . Ancak, herhangi bir parametre bir `As` yan tümce kullanıyorsa, tümünün onu kullanması gerekir. `Option Strict`Açık ise, `As` yan tümce her parametre tanımı için gereklidir.  
  
 Bir yan tümce kullanmadan bir değişken bildirir `As` ve öğesini olarak ayarlarsanız `Nothing` , değişkenin türü vardır `Object` . Bu durumda açık ve açık olduğunda derleme zamanı hatası oluşmaz `Option Strict` `Option Infer` . Buna bir örnektir `Dim something = Nothing` .  
  
### <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  

 Aşağıdaki tabloda, bir [Dim ifadesinde](dim-statement.md)veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.  
  
|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|`Option Strict`Kapalıysa (varsayılan), değişkeni olarak ayarlanır `Nothing` .<br /><br /> `Option Strict`Açık ise, bir derleme zamanı hatası oluşur.|  
|Hayır|Yes|`Dim qty = 5`|`Option Infer`Açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> `Option Infer`Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü alır `Object` .<br /><br /> `Option Infer`Kapalıysa ve açık ise `Option Strict` , bir derleme zamanı hatası oluşur.|  
|Yes|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Daha fazla bilgi için bkz. [Dim deyimleri](dim-statement.md).|  
|Yes|Yes|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict bir Ifade yoksa  

 Kaynak kodu bir `Option Strict` ifade içermiyorsa, derleme sayfasındaki **katı ayar seçeneğini** , [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. **Derleme sayfasında** , hata oluşturan koşullar üzerinde ek denetim sağlayan ayarlar bulunur.  
  
 Komut satırı derleyicisini kullanıyorsanız, için bir ayar belirtmek üzere [-OptionStrict](../../reference/command-line-compiler/optionstrict.md) derleyici seçeneğini kullanabilirsiniz `Option Strict` .  
  
### <a name="to-set-option-strict-in-the-ide"></a>IDE 'de Option Strict ayarlamak için  

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesinde, **katı kutu seçeneğini** belirleyin.  
  
### <a name="to-set-warning-configurations-in-the-ide"></a><a name="conditions"></a> IDE 'de uyarı yapılandırması ayarlamak için  

 [Derleme sayfasını, bir ifade yerine proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullandığınızda `Option Strict` , hata oluşturan koşullar üzerinde ek denetime sahip olursunuz. **Derleme sayfasının** **Uyarı yapılandırması** bölümü, açık olduğunda derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlara sahiptir `Option Strict` . Aşağıdaki ayarlar şunlardır:  
  
- **Örtük dönüştürme**  
  
- **Geç bağlama; çağrı çalışma zamanında başarısız olabilir**  
  
- **Örtük tür; nesne varsayıldı**  
  
 **Option Strict** **on on**olarak ayarlandığında, bu uyarı yapılandırma ayarlarının üçü de **hata**olarak ayarlanır. **Option Strict** ' i **off**olarak ayarlarsanız, üç ayar **hiçbiri None**olarak ayarlanır.  
  
 Her uyarı yapılandırma ayarını **hiçbiri**, **Uyarı**veya **hata**olarak tek tek değiştirebilirsiniz. Üç uyarı yapılandırma ayarı **hata**olarak ayarlanırsa, `On` `Option strict` kutusunda görünür. Üçü de **hiçbiri**olarak ayarlandıysa, `Off` Bu kutuda görüntülenir. Bu ayarların diğer birleşimleri için **(özel)** görüntülenir.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Yeni projeler için katı varsayılan ayar seçeneğini ayarlamak için  

 Bir proje oluşturduğunuzda, **Derle** sekmesindeki **katı** ayarı **Seçenekler** iletişim kutusunda **katı** ayarına ayarlanır.  
  
 `Option Strict`Bu iletişim kutusunda ayarlamak için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak ilk varsayılan ayar `Off` .  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Komut satırında Strict seçeneğini ayarlamak için  

 **Vbc** komutuna [-OptionStrict](../../reference/command-line-compiler/optionstrict.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örneklerde, dönüştürmeleri daraltma örtük tür dönüştürmelerinden kaynaklanan derleme zamanı hataları gösterilmektedir. Bu hata kategorisi, **derleme sayfasındaki** **örtük dönüştürme** koşuluna karşılık gelir.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, geç bağlamanın neden olduğu bir derleme zamanı hatası gösterir. Bu hata kategorisi, geç bağlamaya karşılık gelir; çağrı **derleme sayfasındaki** **çalışma zamanında başarısız olabilir** .  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örneklerde, örtülü bir türle belirtilen değişkenlerin neden olduğu hatalar gösterilmektedir `Object` . Bu hata kategorisi, **derleme sayfasındaki** **örtük tür; nesne varsayıldı** koşulunu karşılık gelir.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit Deyimi](option-explicit-statement.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML'de Katıştırılmış İfadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office Çözümlerinde Geç Bağlama](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
