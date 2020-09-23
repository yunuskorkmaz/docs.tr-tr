---
title: Kültürün Visual Basic'te Dizelere Etkisi
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 878e028f7c7f0e93752765272e93baa3ffe1426d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059228"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Kültürün Visual Basic'de Dizeleri Etkilemesi

Bu yardım sayfası, Visual Basic dize dönüştürmeleri ve karşılaştırmaları gerçekleştirmek için kültür bilgilerini nasıl kullandığını açıklar.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kültüre özgü dizeler ne zaman kullanılır?  

 Genellikle, kullanıcılara sunulan ve buradan okunan tüm veriler için kültüre özgü dizeler kullanmanız ve uygulamanızın iç verileri için kültür sabit dizeler kullanmanız gerekir.  
  
 Örneğin, uygulamanız kullanıcılardan bir tarih olarak bir tarih girmesini isterse, kullanıcıların dizeleri küllerine göre biçimlendirmelerini ve uygulamanın dizeyi uygun şekilde dönüştürmesine de karşı beklemeniz gerekir. Uygulamanız daha sonra bu tarihi Kullanıcı arabiriminde sunmuşsa, kullanıcının kültürüyle sunmalıdır.  
  
 Ancak, uygulama tarihi bir merkezi sunucuya yüklediğinde, potansiyel olarak farklı tarih biçimleri arasında karışıklık oluşmasını önlemek için dizeyi tek bir belirli kültüre göre biçimlendirmelidir.  
  
## <a name="culture-sensitive-functions"></a>Kültüre duyarlı Işlevler  

 Tüm Visual Basic dize dönüştürme işlevleri ( `Str` ve `Val` işlevleri hariç), dönüştürmelerin ve karşılaştırmaların uygulamanın kullanıcı kültürü için uygun olduğundan emin olmak için uygulamanın kültür bilgilerini kullanır.  
  
 Farklı kültür ayarlarına sahip bilgisayarlarda çalışan uygulamalarda dize dönüştürme işlevlerini başarılı bir şekilde kullanmaya yönelik anahtar, hangi işlevlerin belirli bir kültür ayarını kullandığını ve geçerli kültür ayarını kullandığını anlamaktır. Uygulamanın kültür ayarlarının, varsayılan olarak işletim sisteminin kültür ayarlarından devralındığını unutmayın. Daha fazla bilgi için bkz.,,,,,, <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Hex%2A> <xref:Microsoft.VisualBasic.Conversion.Oct%2A> ve [tür dönüştürme işlevleri](../../../language-reference/functions/type-conversion-functions.md).  
  
 `Str`(Sayıları dizelere dönüştürür) ve `Val` (dizeleri sayılara dönüştürür) işlevleri, dizeler ve sayılar arasında dönüştürme yaparken uygulamanın kültür bilgilerini kullanmaz. Bunun yerine, yalnızca nokta (.) seçeneğini geçerli bir ondalık ayırıcısı olarak tanır. Bu işlevlerin tam olarak farkında olan özellikleri şunlardır:  
  
- **Geçerli kültürü kullanan dönüştürmeler.** `CStr`Ve `Format` işlevleri bir sayıyı dizeye dönüştürür ve `CDbl` ve `CInt` işlevleri bir dizeyi sayıya dönüştürür.  
  
- **Belirli bir kültür kullanan dönüştürmeler.** Her bir Number nesnesi bir `ToString(IFormatProvider)` sayıyı dizeye dönüştüren bir yönteme ve bir `Parse(String, IFormatProvider)` dizeyi sayıya dönüştüren bir yönteme sahiptir. Örneğin, `Double` türü <xref:System.Double.ToString%28System.IFormatProvider%29> ve <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> yöntemlerini sağlar.  
  
 Daha fazla bilgi için <xref:Microsoft.VisualBasic.Conversion.Str%2A> ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> bölümlerine bakın.  
  
## <a name="using-a-specific-culture"></a>Belirli bir kültürü kullanma  

 Bir Web hizmetine Tarih (dize olarak biçimlendirilir) gönderen bir uygulama geliştirdiğinizi varsayalım. Bu durumda, uygulamanızın dize dönüştürmesi için belirli bir kültür kullanması gerekir. Nedenini anlamak için, tarihin yöntemini kullanmanın sonucunu göz önünde bulundurun <xref:System.DateTime.ToString> : uygulamanız bu yöntemi 4 temmuz 2005 tarihinde biçimlendirmek için kullanıyorsa, Birleşik Devletler İngilizce (en-US) kültürüyle çalışırken "7/4/2005 12:00:00" döndürür, ancak Almanca (de-de) kültürüyle çalışırken "04.07.2005 00:00:00" döndürür.  
  
 Belirli bir kültür biçiminde bir dize dönüştürmesi gerçekleştirmeniz gerektiğinde, `CultureInfo` .NET Framework yerleşik sınıfını kullanmanız gerekir. `CultureInfo`Kültür adını oluşturucuya geçirerek, belirli bir kültür için yeni bir nesne oluşturabilirsiniz <xref:System.Globalization.CultureInfo.%23ctor%2A> . Desteklenen kültür adları <xref:System.Globalization.CultureInfo> sınıf Yardım sayfasında listelenir.  
  
 Alternatif olarak, özelliğinden *sabit kültürün* bir örneğini alabilirsiniz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . Sabit kültür, Ingilizce kültürü temel alır, ancak bazı farklılıklar vardır. Örneğin, sabit kültür 12 saatlik bir saat yerine 24 saatlik saati belirtir.  
  
 Bir tarihi kültürün dizesine dönüştürmek için <xref:System.Globalization.CultureInfo> nesneyi Date nesnesinin <xref:System.DateTime.ToString%28System.IFormatProvider%29> yöntemine geçirin. Örneğin, aşağıdaki kod uygulamanın kültür ayarlarından bağımsız olarak "07/04/2005 00:00:00" görüntüler.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Tarih değişmez değerleri her zaman Ingilizce kültüre göre yorumlanır.  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  

 Dize karşılaştırmalarının gerekli olduğu iki önemli durum vardır:  
  
- **Görüntülenecek verileri kullanıcıya sıralama.** Dizelerin uygun şekilde sıralanması için geçerli kültürü temel alan işlemleri kullanın.  
  
- **İki uygulama iç dizesinin tam olarak eşleşip eşleşmediğini belirleme (genellikle güvenlik amaçları için).** Geçerli kültürü gözardı eden işlemleri kullanın.  
  
 Visual Basic işleviyle her iki karşılaştırma türünü de gerçekleştirebilirsiniz <xref:Microsoft.VisualBasic.Strings.StrComp%2A> . `Compare`Karşılaştırma türünü denetlemek için isteğe bağlı bağımsız değişkeni belirtin: `Text` `Binary` Tam eşleşmeleri belirlemek için çoğu giriş ve çıkış için.  
  
 `StrComp`İşlevi, sıralama düzenini temel alan iki karşılaştırılan dize arasındaki ilişkiyi gösteren bir tamsayı döndürür. Sonuç için pozitif bir değer, ilk dizenin ikinci dizeden daha büyük olduğunu gösterir. Negatif sonuç, ilk dizenin daha küçük olduğunu ve sıfır dizeler arasındaki eşitlik olduğunu gösterir.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Ayrıca, işlevinin .NET Framework ortağını, yöntemi de kullanabilirsiniz `StrComp` <xref:System.String.Compare%2A?displayProperty=nameWithType> . Bu, temel dize sınıfının statik, aşırı yüklenmiş bir yöntemidir. Aşağıdaki örnek, bu yöntemin nasıl kullanıldığını göstermektedir:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Karşılaştırmaların nasıl gerçekleştirildiği üzerinde daha ayrıntılı denetim sağlamak için, yönteminin ek aşırı yüklerini kullanabilirsiniz <xref:System.String.Compare%2A> . <xref:System.String.Compare%2A?displayProperty=nameWithType>Yöntemiyle, `comparisonType` kullanılacak karşılaştırma türünü belirtmek için bağımsız değişkenini kullanabilirsiniz.  
  
|`comparisonType`Bağımsız değişken değeri|Karşılaştırma türü|Kullanılması gereken durumlar|  
|---|---|---|  
|`Ordinal`|Dizelerin bileşen baytlarına göre karşılaştırma.|Bu değeri karşılaştırdığınızda kullanın: büyük/küçük harfe duyarlı tanımlayıcılar, güvenlikle ilgili ayarlar veya baytların tam olarak eşleşmesi gereken diğer dil olmayan tanımlayıcılar.|  
|`OrdinalIgnoreCase`|Dizelerin bileşen baytlarına göre karşılaştırma.<br /><br /> `OrdinalIgnoreCase` iki karakterin ne zaman büyük harfle farklı olduğunu anlamak için sabit kültür bilgilerini kullanır.|Karşılaştırılırken bu değeri kullanın: büyük/küçük harf duyarsız tanımlayıcılar, güvenlikle ilgili ayarlar ve Windows 'da depolanan veriler.|  
|`CurrentCulture` veya `CurrentCultureIgnoreCase`|Geçerli kültürdeki dizelerin yorumlaması temelinde karşılaştırma.|Karşılaştırılırken bu değerleri kullanın: kullanıcıya görüntülenen veriler, çoğu kullanıcı girişi ve dilsel yorumu gerektiren diğer veriler.|  
|`InvariantCulture` veya `InvariantCultureIgnoreCase`|Sabit kültürdeki dizelerin yorumlanmasını temel alan karşılaştırma.<br /><br /> Bu, `Ordinal` ve ' den farklıdır `OrdinalIgnoreCase` , çünkü sabit kültür karakterleri kabul edilen aralığı dışında eşdeğer sabit karakterler olarak değerlendirir.|Bu değerleri yalnızca kalıcı verileri karşılaştırırken veya sabit bir sıralama düzeni gerektiren dilsel ile ilgili verileri görüntüleyerek kullanın.|  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  

 Uygulamanız bir karşılaştırma veya örnek değişikliği işleminin sonucuna göre güvenlik kararları alıyorsa, işlem <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemini kullanmalı ve `Ordinal` `OrdinalIgnoreCase` `comparisonType` bağımsız değişkeni iletmeli.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo>
- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
