---
title: Kültürün Visual Basic'de Dizeleri Etkilemesi
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c95dcc8d04725f7a072e8c8bc7fe058e53a95c05
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Kültürün Visual Basic'de Dizeleri Etkilemesi
Bu Yardım sayfası kültür bilgilerini Visual Basic dize dönüştürmeleri ve karşılaştırmaları gerçekleştirmek için nasıl kullandığını açıklar.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kültüre özgü dizeleri kullanmak ne zaman  
 Genellikle, için sunulan tüm veriler için kültüre özgü dizelerini kullanın ve kullanıcılardan okuyun ve kültür değişmez değer dizeleri uygulamanızın iç verileri için kullanın.  
  
 Örneğin, uygulamanız kullanıcıların bir tarih olarak bir dize girin isterse, kullanıcıların biçim dizeleri kültüre göre beklemelisiniz ve uygulama dize uygun şekilde dönüştürmeniz gerekir. Kullanıcı arabiriminde bu tarihten sonra uygulamanızın gösterir, bu kullanıcının kültürün sunmalıdır.  
  
 Ancak, uygulama tarihi merkezi sunucusuna yükler, potansiyel olarak farklı tarih biçimleri arasında Karışıklığı önlemek için bir özel kültüre göre dize biçiminde.  
  
## <a name="culture-sensitive-functions"></a>Kültüre duyarlı işlevleri  
 Tüm Visual Basic dize dönüştürme işlevleri (dışında `Str` ve `Val` işlevleri) karşılaştırmaları ve dönüşümler uygulamanın kültür için uygun olduğundan emin olmak için uygulamanın kültür bilgilerini kullanın Kullanıcı.  
  
 Dize dönüştürme işlevleri farklı kültür ayarları olan bilgisayarlarda çalıştırılan uygulamalardaki kullanarak başarıyla anahtarını hangi işlevleri belirli kültür ayarı kullanın ve geçerli kültür ayarı kullanan anlamaktır. Uygulamanın kültür ayarları varsayılan olarak, işletim sistemi kültür ayarlarından devralınacağı dikkat edin. Daha fazla bilgi için bkz: <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (Numaraları dönüştürür dizelere) ve `Val` dizeleri ve numaralar arasında dönüştürme (dönüştürür dizeleri sayılara) işlevleri uygulamanın kültür bilgilerini kullanmayın. Bunun yerine, bunlar yalnızca nokta (.) geçerli bir ondalık ayırıcısı olarak tanır. Bu işlevlerin culturally algılayan analogues şunlardır:  
  
-   **Geçerli kültür kullanmak dönüşümler.** `CStr` Ve `Format` işlevleri bir sayı bir dizeye dönüştürmek ve `CDbl` ve `CInt` işlevleri bir dize bir sayıya dönüştürün.  
  
-   **Belirli bir kültür kullanmak dönüşümler.** Her sayı nesnesi olan bir `ToString(IFormatProvider)` bir sayı bir dizeye dönüştürür yöntemi ve `Parse(String, IFormatProvider)` bir dizeyi sayıya dönüştürür yöntemi. Örneğin, `Double` türü sağlar <xref:System.Double.ToString%28System.IFormatProvider%29> ve <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> yöntemleri.  
  
 Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Conversion.Str%2A> ve <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Belirli bir kültür kullanma  
 Bir Web hizmetine (bir dize olarak biçimlendirilmiş) bir tarih gönderen uygulama geliştirme düşünün. Bu durumda, uygulamanızın belirli bir kültür dize dönüştürme için kullanmanız gerekir. Nedenini anlamak için tarihin kullanmanın sonucu düşünün <xref:System.DateTime.ToString> yöntemi: uygulamanız 4 Temmuz 2005 tarih biçimlendirmek için bu yöntem kullanıyorsa döndürür "4/7/2005 12:00:00 AM" ile Amerika Birleşik Devletleri İngilizce (en-US) kültür çalıştırdığınızda, ancak bunu döndürür " 04.07.2005 00:00:00 "ile Almanca (de-DE) kültür çalıştırdığınızda.  
  
 Belirli kültür biçiminde bir dize dönüştürme gerçekleştirmek gerektiğinde, kullanması gereken `CultureInfo` içinde yerleşik sınıfı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Yeni bir oluşturabilirsiniz `CultureInfo` kültürün adını geçirerek belirli bir kültür için nesne <xref:System.Globalization.CultureInfo.%23ctor%2A> Oluşturucusu. Desteklenen bir kültür adları listelenen <xref:System.Globalization.CultureInfo> sınıfı Yardım sayfası.  
  
 Alternatif olarak, bir örneği elde edebilirsiniz *sabit kültür* gelen <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği. Sabit kültür üzerinde İngilizce kültürüne dayanır, ancak bazı farklılıklar vardır. Örneğin, 24 saatlik 12 saatlik yerine sabit kültür belirtir.  
  
 Bir tarihi kültürün dizeye dönüştürmek için geçirmek <xref:System.Globalization.CultureInfo> tarih nesnenin nesnesine <xref:System.DateTime.ToString%28System.IFormatProvider%29> yöntemi. Örneğin, aşağıdaki görüntüler kod "07/04/2005 00:00:00" ne olursa olsun, uygulamanın kültür ayarları.  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  Tarih değişmez değerleri her zaman İngilizce kültürüne uygun olarak yorumlanır.  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Dize karşılaştırmaları burada gereken iki önemli durum vardır:  
  
-   **Kullanıcıya görünen sıralama verileri.** Dizeleri uygun şekilde sıralamak için geçerli kültür üzerinde temel işlemleri kullanın.  
  
-   **İki uygulama iç dizeleri (genellikle güvenlik nedenleriyle) tam olarak eşleşmesi olup olmadığı belirleniyor.** Geçerli kültür göz ardı işlemleri kullanın.  
  
 Visual Basic ile karşılaştırmaları her iki tür gerçekleştirebilirsiniz <xref:Microsoft.VisualBasic.Strings.StrComp%2A> işlevi. İsteğe bağlı belirtin `Compare` karşılaştırma türünü denetlemek için bağımsız değişken: `Text` çoğu giriş ve çıkış için `Binary` tam eşleşme belirlemek için.  
  
 `StrComp` İşlevi sıralama sırasına göre iki karşılaştırılan dizeler arasındaki ilişkiyi gösteren bir tamsayı döndürür. Sonuç için pozitif bir değer ilk dizesi ikinci dize büyük olduğunu gösterir. Negatif bir sonuç ilk dize küçüktür, sıfır dizeleri arasındaki eşitlik belirtir.  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 Aynı zamanda [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] iş ortağı `StrComp` işlevi, <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi. Temel dize sınıfının statik, aşırı yüklenmiş bir yöntem budur. Aşağıdaki örnek, bu yöntem nasıl kullanıldığı gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 Karşılaştırmaları nasıl gerçekleştirileceğini üzerinde daha hassas denetim için ek aşırı kullanabilirsiniz <xref:System.String.Compare%2A> yöntemi. İle <xref:System.String.Compare%2A?displayProperty=nameWithType> kullanabileceğiniz yöntemi, `comparisonType` kullanmak için karşılaştırma türünü belirtmek için bağımsız değişken.  
  
|Değeri `comparisonType` bağımsız değişken|Karşılaştırma türü|Ne zaman kullanmalı|  
|---|---|---|  
|`Ordinal`|Dizeleri bileşeni bayt alarak karşılaştırmayı.|Karşılaştırma olduğunda bu değeri kullanın: büyük küçük harfe duyarlı tanımlayıcıları, güvenlikle ilgili ayarları veya diğer dil olmayan tanımlayıcıları burada bayt eşleşmelidir.|  
|`OrdinalIgnoreCase`|Dizeleri bileşeni bayt alarak karşılaştırmayı.<br /><br /> `OrdinalIgnoreCase` büyük harf yalnızca iki karakter farklı olduğunda belirlemek için sabit kültür bilgilerini kullanır.|Karşılaştırma olduğunda bu değeri kullanın: büyük küçük harf duyarsız tanımlayıcıları, güvenlikle ilgili ayarları ve Windows'ta depolanan verileri.|  
|`CurrentCulture` Veya `CurrentCultureIgnoreCase`|Geçerli kültür dizeleri yorumu temel alarak karşılaştırmayı.|Bu değerleri karşılaştırılırken kullanın: kullanıcı, çoğu kullanıcı girişi ve dil yorumlama gerektiren diğer veriler için görüntülenen verileri.|  
|`InvariantCulture` Veya `InvariantCultureIgnoreCase`|Sabit kültür dizeleri yorumu temel alarak karşılaştırmayı.<br /><br /> Bu farklıdır `Ordinal` ve `OrdinalIgnoreCase`, sabit kültür kabul edilebilir aralık dışında karakterler eşdeğer değişmez karakter olarak davrandığı için.|Kalıcı veri veya görüntüleme incelemeye ilgili verileri karşılaştırılırken sabit bir sıralama gerektiren yalnızca bu değerleri kullanın.|  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Uygulamanızı bir karşılaştırma ya da durum değiştirme işlemi sonucuna güvenlik kararları sonra işlemi kullanması gereken <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi ve geçişi `Ordinal` veya `OrdinalIgnoreCase` için `comparisonType` bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.CultureInfo>  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
