---
title: Kültürün Visual Basic'de Dizeleri Etkilemesi
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834627"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Kültürün Visual Basic'de Dizeleri Etkilemesi
Bu Yardım sayfası kültür bilgilerini Visual Basic dize dönüştürme ve karşılaştırma gerçekleştirmek için nasıl kullandığını açıklar.  
  
## <a name="when-to-use-culture-specific-strings"></a>Ne zaman kültüre özel dize kullanılır?  
 Genellikle, sunulan tüm veriler için kültüre özgü dizeleri kullanın ve kullanıcıların okuma ve kültür sabit dizelerini uygulamanızın iç verileri için kullanın gerekir.  
  
 Örneğin, uygulamanız kullanıcıların bir dize olarak bir tarih girin isterse, biçim dizeleri kültüre göre kullanıcıların beklemelisiniz ve uygulama dizesi uygun şekilde dönüştürmeniz gerekir. Ardından, uygulamanızın kullanıcı arabiriminde o tarih sunarsa, bu kullanıcının kültürünü sunmalıdır.  
  
 Ancak uygulama tarih merkezi sunucusuna yükler, büyük olasılıkla farklı tarih biçimleri arasında Karışıklığı önlemek için bir özel kültüre göre dize biçiminde.  
  
## <a name="culture-sensitive-functions"></a>Kültüre duyarlı işlevleri  
 Tüm Visual Basic dize dönüştürme işlevleri (dışında `Str` ve `Val` işlevler) dönüştürme ve karşılaştırmalar uygulamanın kültür için uygun olduğundan emin olmak için uygulamanın kültür bilgilerini kullanın. Kullanıcı.  
  
 Anahtar başarıyla farklı kültür ayarları olan bilgisayarlarda çalıştırılan uygulamalardaki dize dönüştürme işlevlerini kullanarak belirli bir kültür ayarı hangi işlevleri'ni kullanın ve geçerli kültür ayarı kullanan öğrenmektir. Uygulamanın kültür ayarları işletim sisteminin kültür ayarları varsayılan olarak, devralınan olan dikkat edin. Daha fazla bilgi için <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (Sayıları dizeleri dönüştürür) ve `Val` (sayıları dizeleri dönüştürür) işlevleri dizeleri ve numaralar arasında dönüştürme yaparken uygulamanın kültür bilgilerini kullanmaz. Bunun yerine, bunlar yalnızca nokta (.) geçerli bir ondalık ayırıcı olarak tanır. Bu işlevlerin duyarlıymış algılayan analogues şunlardır:  
  
-   **Geçerli kültürü kullanan dönüştürme.** `CStr` Ve `Format` işlevleri bir sayıyı bir dizeye dönüştürür ve `CDbl` ve `CInt` işlevler bir dizeyi sayıya dönüştürme.  
  
-   **Belirli bir kültür kullanan dönüştürme.** Her sayı nesnesi olan bir `ToString(IFormatProvider)` bir sayıyı bir dizeye dönüştürür yöntemi ve bir `Parse(String, IFormatProvider)` yönteminin bir dizeyi sayıya dönüştürür. Örneğin, `Double` sağlayan türü <xref:System.Double.ToString%28System.IFormatProvider%29> ve <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> yöntemleri.  
  
 Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Conversion.Str%2A> ve <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Belirli bir kültür kullanarak  
 Bir Web hizmeti için (bir dize olarak biçimlendirilmiş) bir tarih gönderen bir uygulama geliştiriyorsanız düşünün. Bu durumda, uygulamanızın belirli bir kültür dize dönüştürme için kullanmanız gerekir. Nedenini anlamak için tarihin kullanmanın sonucu göz önünde bulundurun. <xref:System.DateTime.ToString> yöntemi: Uygulamanız 4 Temmuz 2005 tarihi biçimlendirmek için bu yöntem kullanıp kullanmadığını döndürür "4/7/2005 12:00:00 AM" Amerika Birleşik Devletleri İngilizce (en-US) kültür ile çalıştırdığınızda, ancak döndürür "04.07.2005 00:00:00" Almanca (de-DE) kültür ile çalıştırdığınızda.  
  
 Belirli bir kültür biçiminde bir dize dönüştürme yapmak gerektiğinde, kullanmanız gereken `CultureInfo` yerleşiktir sınıfı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Yeni bir oluşturabilirsiniz `CultureInfo` kültürün adını geçirerek belirli bir kültür için nesne <xref:System.Globalization.CultureInfo.%23ctor%2A> Oluşturucusu. Desteklenen kültürü adların listelenme <xref:System.Globalization.CultureInfo> sınıfı Yardım sayfası.  
  
 Alternatif olarak, örneği alabilirsiniz *sabit kültür* gelen <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği. Sabit kültürü İngilizce kültürü temel alan, ancak bazı farklar vardır. Örneğin, sabit kültür, 24 saatlik bir 12 saatlik düzende yerine belirtir.  
  
 Bir tarih kültürün dizeye dönüştürülecek geçirmek <xref:System.Globalization.CultureInfo> tarih nesnesinin nesnesine <xref:System.DateTime.ToString%28System.IFormatProvider%29> yöntemi. Örneğin, aşağıdaki görüntüler kod "04/07/2005 00:00:00" uygulamanın kültür ayarları ne olursa olsun.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Tarih değişmez değerleri, her zaman İngilizce kültürüne göre yorumlanır.  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Dize karşılaştırmaları gerekmesi iki önemli durumlar vardır:  
  
-   **Kullanıcıya görüntülenecek veri sıralama.** Uygun şekilde dizeleri sıralamak için geçerli kültürü temel alarak işlemler kullanın.  
  
-   **İki uygulama iç dizeleri (genellikle. Güvenlik amaçları için) tam olarak eşleşip eşleşmediğini belirleyin.** Geçerli kültürü dikkate işlemlerini kullanın.  
  
 Visual Basic ile karşılaştırma her iki türdeki gerçekleştirebileceğiniz <xref:Microsoft.VisualBasic.Strings.StrComp%2A> işlevi. İsteğe bağlı belirtin `Compare` karşılaştırma türünü denetlemek için bağımsız değişken: `Text` çoğu girdi ve çıktı `Binary` tam eşleşme belirlemek için.  
  
 `StrComp` İşlevi bir sıralama ölçütüne göre iki karşılaştırılan dizeler arasındaki ilişkiyi gösteren bir tamsayı döndürür. Birinci dize ikinci dizeden büyükse sonuç için pozitif bir değer belirtir. Negatif bir sonuç ilk dize küçüktür, sıfır dizeler arasındaki belirtir.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Ayrıca [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] iş ortağı `StrComp` işlevi <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi. Temel dize sınıfının statik, aşırı yüklenmiş bir yöntem budur. Aşağıdaki örnekte, bu yöntem nasıl kullanıldığı gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Karşılaştırmalar nasıl gerçekleştirileceğini denetleyebilmek için ek bir aşırı yüklemesini kullanabilirsiniz <xref:System.String.Compare%2A> yöntemi. İle <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi kullanabileceğiniz `comparisonType` kullanmak için karşılaştırma türünü belirtmek için bağımsız değişken.  
  
|Değerini `comparisonType` bağımsız değişken|Karşılaştırma türü|Ne zaman kullanmalı|  
|---|---|---|  
|`Ordinal`|Karşılaştırma dizeleri bileşen baytlara bağlı.|Bu değeri karşılaştırılırken kullanın: büyük küçük harf duyarlı tanımlayıcıları, güvenlikle ilgili ayarları ya da diğer dilsel olmayan tanımlayıcıları yeri bayt eşleşmelidir.|  
|`OrdinalIgnoreCase`|Karşılaştırma dizeleri bileşen baytlara bağlı.<br /><br /> `OrdinalIgnoreCase` yalnızca büyük harf karakter iki farklı olduğunda belirlemek için sabit kültür bilgilerini kullanır.|Bu değeri karşılaştırılırken kullanın: büyük küçük harf duyarsız tanımlayıcılar, güvenlikle ilgili ayarlar ve Windows içinde depolanan veriler.|  
|`CurrentCulture` veya `CurrentCultureIgnoreCase`|Geçerli kültürü dizeleri yorumu temel alarak karşılaştırmayı.|Karşılaştırılırken şu değerleri kullanın: kullanıcı, çoğu kullanıcı girişi ve dilsel yorumlama gerektiren diğer veriler için görüntülenen verileri.|  
|`InvariantCulture` veya `InvariantCultureIgnoreCase`|Sabit kültür dizelerin yorumu temel alarak karşılaştırmayı.<br /><br /> Bu farklıdır `Ordinal` ve `OrdinalIgnoreCase`, sabit kültür, kabul edilen aralığın dışındaki karakterleri eşdeğer sabit karakter değerlendirir.|Kalıcı veri veya görüntüleme dilsel olarak gerekli veri karşılaştırılırken sabit bir sıralama düzeni olmasını gerektirir. yalnızca şu değerleri kullanın.|  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Uygulamanız bir karşılaştırma veya harf değiştirme işleminin sonucuna dayalı güvenlik kararları hale getirir. ardından işlemi kullanması gereken <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi ve pass `Ordinal` veya `OrdinalIgnoreCase` için `comparisonType` bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo>
- [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
