---
title: Kültürün Visual Basic'te Dizelere Etkisi
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 2520a7684b8710abd949543e3f17f77d3c631d22
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352474"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Kültürün Visual Basic'de Dizeleri Etkilemesi
Bu yardım sayfası, Visual Basic dize dönüştürmeleri ve karşılaştırmaları gerçekleştirmek için kültür bilgilerini nasıl kullandığını açıklar.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kültüre özgü dizeler ne zaman kullanılır?  
 Genellikle, kullanıcılara sunulan ve buradan okunan tüm veriler için kültüre özgü dizeler kullanmanız ve uygulamanızın iç verileri için kültür sabit dizeler kullanmanız gerekir.  
  
 Örneğin, uygulamanız kullanıcılardan bir tarih olarak bir tarih girmesini isterse, kullanıcıların dizeleri küllerine göre biçimlendirmelerini ve uygulamanın dizeyi uygun şekilde dönüştürmesine de karşı beklemeniz gerekir. Uygulamanız daha sonra bu tarihi Kullanıcı arabiriminde sunmuşsa, kullanıcının kültürüyle sunmalıdır.  
  
 Ancak, uygulama tarihi bir merkezi sunucuya yüklediğinde, potansiyel olarak farklı tarih biçimleri arasında karışıklık oluşmasını önlemek için dizeyi tek bir belirli kültüre göre biçimlendirmelidir.  
  
## <a name="culture-sensitive-functions"></a>Kültüre duyarlı Işlevler  
 Visual Basic dize dönüştürme işlevlerinin tümü (`Str` ve `Val` işlevleri dışında), dönüştürmelerin ve karşılaştırmaların uygulama kullanıcısının kültürü için uygun olduğundan emin olmak için uygulamanın kültür bilgilerini kullanır.  
  
 Farklı kültür ayarlarına sahip bilgisayarlarda çalışan uygulamalarda dize dönüştürme işlevlerini başarılı bir şekilde kullanmaya yönelik anahtar, hangi işlevlerin belirli bir kültür ayarını kullandığını ve geçerli kültür ayarını kullandığını anlamaktır. Uygulamanın kültür ayarlarının, varsayılan olarak işletim sisteminin kültür ayarlarından devralındığını unutmayın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (sayıları dizelere dönüştürür) ve `Val` (dizeleri sayılara dönüştürür) işlevleri, dizeler ve sayılar arasında dönüştürme yaparken uygulamanın kültür bilgilerini kullanmaz. Bunun yerine, yalnızca nokta (.) seçeneğini geçerli bir ondalık ayırıcısı olarak tanır. Bu işlevlerin tam olarak farkında olan özellikleri şunlardır:  
  
- **Geçerli kültürü kullanan dönüştürmeler.** `CStr` ve `Format` işlevleri bir sayıyı dizeye dönüştürür ve `CDbl` ve `CInt` işlevleri bir dizeyi sayıya dönüştürür.  
  
- **Belirli bir kültür kullanan dönüştürmeler.** Her bir Number nesnesinin bir sayıyı dizeye dönüştüren bir `ToString(IFormatProvider)` yöntemi ve bir dizeyi sayıya dönüştüren bir `Parse(String, IFormatProvider)` yöntemi vardır. Örneğin, `Double` türü <xref:System.Double.ToString%28System.IFormatProvider%29> ve <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> yöntemlerini sağlar.  
  
 Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Conversion.Str%2A> ve <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Belirli bir kültürü kullanma  
 Bir Web hizmetine Tarih (dize olarak biçimlendirilir) gönderen bir uygulama geliştirdiğinizi varsayalım. Bu durumda, uygulamanızın dize dönüştürmesi için belirli bir kültür kullanması gerekir. Bunun nedenini anlamak için, tarihin <xref:System.DateTime.ToString> yöntemini kullanmanın sonucunu düşünün: uygulamanız bu yöntemi 4 Temmuz 2005 tarihleri için kullanıyorsa, Birleşik Devletler Ingilizce (en-US) kültürüyle çalışırken "7/4/2005 12:00:00" döndürür, ancak Almanca (de-DE) kültürüyle çalışırken "04.07.2005 00:00:00" döndürür.  
  
 Belirli bir kültür biçiminde bir dize dönüştürmesi gerçekleştirmeniz gerektiğinde, .NET Framework yerleşik `CultureInfo` sınıfını kullanmanız gerekir. Kültür adını <xref:System.Globalization.CultureInfo.%23ctor%2A> oluşturucusuna geçirerek belirli bir kültür için yeni bir `CultureInfo` nesnesi oluşturabilirsiniz. Desteklenen kültür adları <xref:System.Globalization.CultureInfo> sınıfı Yardım sayfasında listelenir.  
  
 Alternatif olarak, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliğinden *sabit kültürün* bir örneğini alabilirsiniz. Sabit kültür, Ingilizce kültürü temel alır, ancak bazı farklılıklar vardır. Örneğin, sabit kültür 12 saatlik bir saat yerine 24 saatlik saati belirtir.  
  
 Bir tarihi kültürün dizesine dönüştürmek için <xref:System.Globalization.CultureInfo> nesnesini Date nesnesinin <xref:System.DateTime.ToString%28System.IFormatProvider%29> yöntemine geçirin. Örneğin, aşağıdaki kod uygulamanın kültür ayarlarından bağımsız olarak "07/04/2005 00:00:00" görüntüler.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Tarih değişmez değerleri her zaman Ingilizce kültüre göre yorumlanır.  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Dize karşılaştırmalarının gerekli olduğu iki önemli durum vardır:  
  
- **Görüntülenecek verileri kullanıcıya sıralama.** Dizelerin uygun şekilde sıralanması için geçerli kültürü temel alan işlemleri kullanın.  
  
- **İki uygulama iç dizesinin tam olarak eşleşip eşleşmediğini belirleme (genellikle güvenlik amaçları için).** Geçerli kültürü gözardı eden işlemleri kullanın.  
  
 Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A> işleviyle her iki karşılaştırma türünü de gerçekleştirebilirsiniz. Karşılaştırma türünü denetlemek için isteğe bağlı `Compare` bağımsız değişkenini belirtin: tam eşleşmeleri belirlemek için çoğu giriş ve çıkış `Binary` için `Text`.  
  
 `StrComp` işlevi, sıralama düzenini temel alan iki karşılaştırılan dize arasındaki ilişkiyi gösteren bir tamsayı döndürür. Sonuç için pozitif bir değer, ilk dizenin ikinci dizeden daha büyük olduğunu gösterir. Negatif sonuç, ilk dizenin daha küçük olduğunu ve sıfır dizeler arasındaki eşitlik olduğunu gösterir.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Ayrıca, <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi olan `StrComp` işlevinin .NET Framework ortağını de kullanabilirsiniz. Bu, temel dize sınıfının statik, aşırı yüklenmiş bir yöntemidir. Aşağıdaki örnek, bu yöntemin nasıl kullanıldığını göstermektedir:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Karşılaştırmaların nasıl gerçekleştirildiği üzerinde daha ayrıntılı denetim sağlamak için <xref:System.String.Compare%2A> yönteminin ek aşırı yüklerini kullanabilirsiniz. <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemiyle, kullanılacak karşılaştırma türünü belirtmek için `comparisonType` bağımsız değişkenini kullanabilirsiniz.  
  
|`comparisonType` bağımsız değişkeninin değeri|Karşılaştırma türü|Kullanılması gereken durumlar|  
|---|---|---|  
|`Ordinal`|Dizelerin bileşen baytlarına göre karşılaştırma.|Bu değeri karşılaştırdığınızda kullanın: büyük/küçük harfe duyarlı tanımlayıcılar, güvenlikle ilgili ayarlar veya baytların tam olarak eşleşmesi gereken diğer dil olmayan tanımlayıcılar.|  
|`OrdinalIgnoreCase`|Dizelerin bileşen baytlarına göre karşılaştırma.<br /><br /> `OrdinalIgnoreCase`, iki karakterin ne zaman büyük harfle farklı olduğunu anlamak için sabit kültür bilgilerini kullanır.|Karşılaştırılırken bu değeri kullanın: büyük/küçük harf duyarsız tanımlayıcılar, güvenlikle ilgili ayarlar ve Windows 'da depolanan veriler.|  
|`CurrentCulture` veya `CurrentCultureIgnoreCase`|Geçerli kültürdeki dizelerin yorumlaması temelinde karşılaştırma.|Karşılaştırılırken bu değerleri kullanın: kullanıcıya görüntülenen veriler, çoğu kullanıcı girişi ve dilsel yorumu gerektiren diğer veriler.|  
|`InvariantCulture` veya `InvariantCultureIgnoreCase`|Sabit kültürdeki dizelerin yorumlanmasını temel alan karşılaştırma.<br /><br /> Bu, `Ordinal` ve `OrdinalIgnoreCase`farklıdır, çünkü sabit kültür karakterleri kabul edilen aralığı dışında eşdeğer sabit karakterler olarak değerlendirir.|Bu değerleri yalnızca kalıcı verileri karşılaştırırken veya sabit bir sıralama düzeni gerektiren dilsel ile ilgili verileri görüntüleyerek kullanın.|  
  
### <a name="security-considerations"></a>Güvenlik Konuları  
 Uygulamanız karşılaştırma veya örnek değişikliği işleminin sonucuna göre güvenlik kararları alıyorsa, işlem <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemini kullanmalı ve `comparisonType` bağımsız değişkeni için `Ordinal` veya `OrdinalIgnoreCase` geçirmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo>
- [Visual Basic dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
