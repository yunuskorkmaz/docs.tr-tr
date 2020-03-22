---
title: Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148290"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
Bu örnek, denetimle çalışmak için basit normal <xref:System.Windows.Forms.MaskedTextBox> ifadeleri nasıl dönüştüreceklerini gösterir.  
  
## <a name="description-of-the-masking-language"></a>Maskeleme Dilinin Tanımı  
 Standart <xref:System.Windows.Forms.MaskedTextBox> maskeleme dili Visual Basic 6.0'daki `Masked Edit` denetim tarafından kullanılan adayalıdır ve bu platformdan geçiş yapan kullanıcılara tanıdık olmalıdır.  
  
 Denetimin <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği, hangi giriş maskesinin kullanılacağını <xref:System.Windows.Forms.MaskedTextBox> belirtir. Maske, aşağıdaki tablodaki maskeleme öğelerinden bir veya daha fazlasından oluşan bir dize olmalıdır.  
  
|Maskeleme elemanı|Açıklama|Normal ifade öğesi|  
|---------------------|-----------------|--------------------------------|  
|0|0 ile 9 arasında herhangi bir tek rakam. Giriş gerekli.|\d|  
|9|Basamak veya boşluk. Giriş isteğe bağlı.|[ \d]?|  
|#|Basamak veya boşluk. Giriş isteğe bağlı. Bu konum maskede boş bırakılırsa, boşluk olarak işlenir. Artı (+) ve eksi (-) işaretlerine izin verilir.|[ \d+-]?|  
|L|ASCII mektubu. Giriş gerekli.|[a-zA-Z]|  
|?|ASCII mektubu. Giriş isteğe bağlı.|[a-zA-Z]?|  
|&|Karakter. Giriş gerekli.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Karakter. Giriş isteğe bağlı.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Alfasayısal. Giriş isteğe bağlı.|\W|  
|.|Kültüre uygun ondalık yer tutucu.|Kullanılamıyor.|  
|,|Kültüre uygun binlerce yer tutucu.|Kullanılamıyor.|  
|:|Kültüre uygun zaman ayırıcısı.|Kullanılamıyor.|  
|/|Kültüre uygun tarih ayırıcısı.|Kullanılamıyor.|  
|$|Kültüre uygun para birimi sembolü.|Kullanılamıyor.|  
|\<|Takip eden tüm karakterleri küçük harfe dönüştürür.|Kullanılamıyor.|  
|>|Takip eden tüm karakterleri büyük harfe dönüştürür.|Kullanılamıyor.|  
|&#124;|Önceki bir vardiyayı yukarı veya aşağı doğru geri alar.|Kullanılamıyor.|  
|&#92;|Bir maske karakterinden kaçıyor, onu gerçek bir karaktere dönüştürüyor. "\\\\" " ters eğik çizgi için kaçış sekansidir.|&#92;|  
|Diğer tüm karakterler.|Hazır. Tüm maske olmayan öğeler içinde <xref:System.Windows.Forms.MaskedTextBox>kendileri olarak görünür.|Diğer tüm karakterler.|  
  
 Ondalık (.), binde (,), saat (:), tarih (/) ve para birimi ($) sembolleri, uygulamanın kültürü tarafından tanımlanan bu sembolleri görüntülemek için varsayılan dır. Özelliği kullanarak onları başka bir kültür için <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> semboller görüntülemeye zorlayabilirsiniz.  
  
## <a name="regular-expressions-and-masks"></a>Düzenli İfadeler ve Maskeler  
 Kullanıcı girişini doğrulamak için normal ifadeler ve maskeler kullanabiliyor olsada, bunlar tamamen eşdeğer değildir. Normal ifadeler maskelerden daha karmaşık desenleri ifade edebilir, ancak maskeler aynı bilgileri daha kısa ve kültürel açıdan uygun bir biçimde ifade edebilir.  
  
 Aşağıdaki tablo, her biri için dört normal ifade ve eşdeğer maskeyi karşılaştırır.  
  
|Normal ifade|Maskeleme|Notlar|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Maskedeki `/` karakter mantıksal bir tarih ayırıcısıdır ve uygulamanın geçerli kültürüne uygun tarih ayırıcısı olarak kullanıcıya görünür.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Üç harfli aylık kısaltmanın ilk büyük harfle ve ardından iki küçük harfle görüntülendiği ABD biçimindeki bir tarih (gün, ay kısaltması ve yıl).|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Amerika Birleşik Devletleri telefon numarası, alan kodu isteğe bağlı. Kullanıcı isteğe bağlı karakterleri girmek istemiyorsa, boşluklara girebilir veya fare işaretçisini doğrudan ilk 0'ın temsil ettiği maskedeki konuma yerleyebilir.|  
|`$\d{6}.00`|`$999,999.00`|0 ile 999999 aralığında bir para birimi değeri. Para birimi, binde ve ondalık karakterler çalışma zamanında kültüre özgü eşdeğerleriyle değiştirilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Visual Basic'de Dizeleri Doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox Denetimi](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
