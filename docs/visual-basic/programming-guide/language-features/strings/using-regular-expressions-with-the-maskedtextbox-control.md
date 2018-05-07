---
title: Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: afc19ccf476317e8c30a1cc6964c64f1a59a0ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
Bu örnek ile çalışmak için basit normal ifadeler dönüştürülmesi gösterilmektedir <xref:System.Windows.Forms.MaskedTextBox> denetim.  
  
## <a name="description-of-the-masking-language"></a>Maskeleme dil açıklaması  
 Standart <xref:System.Windows.Forms.MaskedTextBox> dil maskeleme temel tarafından kullanılan bir `Masked Edit` denetim Visual Basic 6. 0've bu platformundan geçirildiğinde kullanıcılara bilgi sahibi olmanız gerekir.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Özelliği <xref:System.Windows.Forms.MaskedTextBox> denetimi kullanmak için hangi giriş maskesi belirtir. Maske, bir veya daha fazla aşağıdaki tabloda maskeleme öğelerinden oluşan bir dize olması gerekir.  
  
|Maskeleme öğesi|Açıklama|Normal ifade öğesi|  
|---------------------|-----------------|--------------------------------|  
|0|Tüm tek sayı 0 ile 9 arasında. Giriş gerekli.|\d|  
|9|Basamak veya aralık. Giriş isteğe bağlı.|[\d]?|  
|#|Basamak veya aralık. Giriş isteğe bağlı. Bu konum maskesinde boş bırakılırsa, bir alan olarak işlenir. Artı (+) ve eksi (-) işaretlerini izin verilir.|[\d+-]?|  
|L|ASCII harfi. Giriş gerekli.|[a-zA-Z]|  
|?|ASCII harfi. Giriş isteğe bağlı.|[a-zA-Z]?|  
|&|Karakter. Giriş gerekli.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Karakter. Giriş isteğe bağlı.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|BİR|Alfasayısal. Giriş isteğe bağlı.|\W|  
|biçimindeki telefon numarasıdır.|Kültür uygun ondalık yer tutucu.|Mevcut değil.|  
|,|Kültür uygun binlerce yer tutucu.|Mevcut değil.|  
|:|Kültür uygun zaman ayırıcı.|Mevcut değil.|  
|/|Kültür uygun tarih ayırıcı.|Mevcut değil.|  
|$|Kültür uygun para birimi simgesi.|Mevcut değil.|  
|\<|Küçük harfe izleyen tüm karakterlerin dönüştürür.|Mevcut değil.|  
|>|Büyük harfe izleyen tüm karakterlerin dönüştürür.|Mevcut değil.|  
|&#124;|Önceki bir vardiya yukarı alır veya shift.|Mevcut değil.|  
|\|Bir hazır değer kapatma bir maskesi karakter çıkışları. "\\\\" bir ters eğik çizgi kaçış sırası.|\|  
|Diğer tüm karakterler.|Değişmez değerler. Tüm Maskesi olmayan öğeler kendilerini içinde görünecektir <xref:System.Windows.Forms.MaskedTextBox>.|Diğer tüm karakterler.|  
  
 Ondalık (.), duyarlığıyla (,), saat (:), tarih (/) ve uygulamanın kültürü tarafından tanımlandığı şekilde bu simgeleri görüntüleme simgeleri varsayılan para birimi ($). Bunları kullanarak başka bir kültür simgelerini görüntülemek için zorlayabilirsiniz <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> özelliği.  
  
## <a name="regular-expressions-and-masks"></a>Normal ifadeler ve maskeleri  
 Kullanıcı girişi doğrulamak için normal ifadeler ve maskeleri kullanabilmenize karşın, tamamen eşdeğer değiller. Normal ifadeler daha karmaşık desenleri maskeleri daha hızlı, ancak maskeleri aynı bilgileri daha temellerini ve culturally ilgili biçiminde ifade edebilirsiniz.  
  
 Aşağıdaki tabloda her biri için dört normal ifadeler ve eşdeğer maskesi karşılaştırır.  
  
|Normal ifade|Maskesi|Notlar|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Karakteridir maskesinde mantıksal tarih ayırıcı ve kullanıcıya uygulamanın geçerli kültür için uygun tarih ayırıcı olarak görünür.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Biçimde bir tarih (gün, ay kısaltması ve yıl) üç harfli ay kısaltması iki küçük harfler tarafından izlenen bir ilk büyük harf ile görüntülendiği Amerika Birleşik Devletleri.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Amerika Birleşik Devletleri telefon numarası alan kodu isteğe bağlı. Kullanıcı, isteğe bağlı karakterleri girin isterseniz değil, aynen alanları girin ya da doğrudan ilk 0 ile temsil edilen maskesi konumunda fare işaretçisini yerleştirin.|  
|`$\d{6}.00`|`$999,999.00`|İçin 0 ile 999999 aralığında para birimi değeri. Para birimi, 214.748,3648 ve ondalık karakter çalışma zamanında kültüre özgü eşdeğerlerine ile değiştirilecek.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [MaskedTextBox Denetimi](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
