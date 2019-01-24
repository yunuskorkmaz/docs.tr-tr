---
title: Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 58c0caa9d1df49ec53273e5b0f456cf89fc64c42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683696"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
Bu örnek ile çalışmak için basit normal ifadeler dönüştürülmesi gösterilmektedir <xref:System.Windows.Forms.MaskedTextBox> denetimi.  
  
## <a name="description-of-the-masking-language"></a>Maskeleme dil açıklaması  
 Standart <xref:System.Windows.Forms.MaskedTextBox> dil maskeleme temel olarak kullanılan `Masked Edit` denetim Visual Basic 6. 0've kullanıcılara bu platformundan geçirildiğinde tanımanız gerekir.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Özelliği <xref:System.Windows.Forms.MaskedTextBox> denetimi kullanmak için hangi giriş maskesi belirtir. Maske, en az biri aşağıdaki tabloda maskeleme öğelerden oluşan bir dize olmalıdır.  
  
|Maskeleme öğesi|Açıklama|Normal ifade öğesi|  
|---------------------|-----------------|--------------------------------|  
|0|0 ile 9 arasında tek bir basamak. Giriş gerekli.|\d|  
|9|Sayı veya boşluk. Giriş isteğe bağlı.|[\d]?|  
|#|Sayı veya boşluk. Giriş isteğe bağlı. Bu konum maskesi boş bırakılırsa, bir boşluk olarak işlenir. (+) Artı ve eksi (-) işareti izin verilir.|[\d+-]?|  
|L|ASCII harfi. Giriş gerekli.|[a-zA-Z]|  
|?|ASCII harfi. Giriş isteğe bağlı.|[a-zA-Z]?|  
|&|karakter. Giriş gerekli.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|karakter. Giriş isteğe bağlı.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|BİR|Alfasayısal. Giriş isteğe bağlı.|\W|  
|biçimindeki telefon numarasıdır.|Kültüre uygun ondalık yer tutucusu.|Kullanılabilir değil.|  
|,|Kültüre uygun binlerce yer tutucu.|Kullanılabilir değil.|  
|:|Kültüre uygun zaman ayırıcı.|Kullanılabilir değil.|  
|/|Kültüre uygun tarih ayırıcı.|Kullanılabilir değil.|  
|$|Kültüre uygun bir para birimi simgesi.|Kullanılabilir değil.|  
|\<|Tüm karakterleri küçük harfe izleyin dönüştürür.|Kullanılabilir değil.|  
|>|Tüm karakterleri büyük harfe izleyin dönüştürür.|Kullanılabilir değil.|  
|&#124;|Önceki shift yukarı alır ya da aşağı kaydır.|Kullanılabilir değil.|  
|&#92;|Bir sabit değer içinde kapatma bir maske karakter çıkışları. "\\\\" için bir ters eğik çizgi kaçış sırası.|&#92;|  
|Tüm diğer karakterler.|Sabit değerler. Tüm maske olmayan öğeler olarak kendilerini içinde görünür <xref:System.Windows.Forms.MaskedTextBox>.|Tüm diğer karakterler.|  
  
 Ondalık (.), binde (,), zaman (:), tarih (/) ve uygulamanın kültür tarafından tanımlandığı şekilde bu sembolleri görüntüleme (USD) para birimi sembolleri varsayılan. Bunları kullanarak başka bir kültür için bir simge görüntülemek için zorlayabilirsiniz <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> özelliği.  
  
## <a name="regular-expressions-and-masks"></a>Normal ifadeler ve maskeleri  
 Kullanıcı girişini doğrulamak için normal ifadeler ve maskelerini kullanabilirsiniz, ancak bunlar tamamen eşdeğer değildir. Normal ifadeler daha karmaşık desenlerle maskeleri daha ifade edebilirsiniz, ancak daha temellerini ve ilgili kültürel bir biçimde maskeleri aynı bilgileri ifade edebilirsiniz.  
  
 Aşağıdaki tabloda her biri için dört normal ifadeler ve eşdeğer maske karşılaştırır.  
  
|Normal ifade|Maskesi|Notlar|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Maske karakter olduğu mantıksal tarih ayırıcı ve uygulamanın geçerli kültür için uygun tarih ayırıcı olarak kullanıcıya görünür.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Biçimde bir tarih (gün, ay kısaltması ve yıl) tarafından iki küçük harf ve ardından ilk büyük harfle ayın üç harfli kısaltması görüntülendiği Amerika Birleşik Devletleri.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|ABD telefon numarası alan kodu isteğe bağlı. Kullanıcı, isteğe bağlı karakterler girin istiyorsanız değil, Filiz boşluk girin veya doğrudan ilk 0 tarafından temsil edilen maskesi konumda fare işaretçisi yerleştirin.|  
|`$\d{6}.00`|`$999,999.00`|Para birimi değeri için 0 ile 999999 aralığında. Para birimi, 214.748,3648 ve ondalık karakterler çalışma zamanında kültüre özgü eşdeğerleri ile değiştirilecek.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox Denetimi](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
