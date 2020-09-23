---
title: Normal İfadeleri MaskedTextBox Denetimi ile Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 493da7b8583b5cc73a9832afa81b7b1d84742f2d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072437"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic'de Normal İfadeleri MaskedTextBox Denetimi ile Kullanma

Bu örnek, denetimin ile nasıl çalıştığını basit normal ifadelerin nasıl dönüştürüleceğini gösterir <xref:System.Windows.Forms.MaskedTextBox> .  
  
## <a name="description-of-the-masking-language"></a>Maskeleme dilinin açıklaması  

 Standart <xref:System.Windows.Forms.MaskedTextBox> maskeleme dili, `Masked Edit` Visual Basic 6,0 ' deki denetim tarafından kullanılan bir temel alır ve bu platformdan geçiş yapan kullanıcılara tanıdık gelmelidir.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> <xref:System.Windows.Forms.MaskedTextBox> Denetimin özelliği kullanılacak giriş maskesini belirtir. Maske, aşağıdaki tablodaki bir veya daha fazla maskeleme öğelerinden oluşan bir dize olmalıdır.  
  
|Maskeleme öğesi|Description|Normal ifade öğesi|  
|---------------------|-----------------|--------------------------------|  
|0|0 ile 9 arasında herhangi bir tek basamak. Giriş gerekiyor.|\d|  
|9|Sayı veya boşluk. Giriş isteğe bağlı.|[\d]?|  
|#|Sayı veya boşluk. Giriş isteğe bağlı. Bu konum maskede boş bırakılırsa, bir boşluk olarak işlenir. Artı (+) ve eksi (-) işaretlerine izin verilir.|[\d +-]?|  
|L|ASCII harfi. Giriş gerekiyor.|[a-zA-Z]|  
|?|ASCII harfi. Giriş isteğe bağlı.|[a-zA-Z]?|  
|&|İnde. Giriş gerekiyor.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|İnde. Giriş isteğe bağlı.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Sayısal. Giriş isteğe bağlı.|\W|  
|.|Kültüre uygun ondalık yer tutucusu.|Kullanılamıyor.|  
|,|Kültüre uygun binlerce yer tutucu.|Kullanılamıyor.|  
|:|Kültüre uygun zaman ayırıcısı.|Kullanılamıyor.|  
|/|Kültüre uygun Tarih ayırıcısı.|Kullanılamıyor.|  
|$|Kültüre uygun para birimi simgesi.|Kullanılamıyor.|  
|\<|İzleyen tüm karakterleri küçük harfe dönüştürür.|Kullanılamıyor.|  
|>|İzleyen tüm karakterleri büyük harfe dönüştürür.|Kullanılamıyor.|  
|&#124;|Önceki SHIFT 'i geri alır veya Aşağı Ötele.|Kullanılamıyor.|  
|&#92;|Bir maske karakteriyle çıkar ve onu değişmez değere dönüştürür. " \\ \\ " bir ters eğik çizgi için kaçış sırasıdır.|&#92;|  
|Diğer tüm karakterler.|Leri. Maskenin dışındaki tüm öğeler içinde görünür <xref:System.Windows.Forms.MaskedTextBox> .|Diğer tüm karakterler.|  
  
 Ondalık (.), binde (,), saat (:), Tarih (/) ve para birimi ($) sembolleri, bu sembolleri uygulamanın kültürüyle tanımlandığı şekilde görüntülemek için varsayılandır. Özelliğini kullanarak, başka bir kültür için sembolleri görüntülemeye zorlayabilirsiniz <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> .  
  
## <a name="regular-expressions-and-masks"></a>Normal Ifadeler ve maskeler  

 Kullanıcı girişini doğrulamak için normal ifadeleri ve maskeleri kullanabilseniz de tamamen eşdeğer değildir. Normal ifadeler maskelerden daha karmaşık desenler ifade edebilir, ancak maskeler aynı bilgileri daha succinctly ve ilgili bir biçimde ifade edebilir.  
  
 Aşağıdaki tabloda dört normal ifade ve her biri için eşdeğer maske karşılaştırılmaktadır.  
  
|Normal ifade|Maskeleme|Notlar|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`Maskenin içindeki karakter bir mantıksal Tarih ayırıcısıdır ve uygulamanın geçerli kültürüne uygun olan Tarih ayırıcısı olarak kullanıcıya görünür.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Bir tarih (gün, ay kısaltması ve yıl), üç harfli ay kısaltmasının ilk büyük harfle ve ardından iki küçük harf ile görüntülendiği Birleşik Devletler biçimde görüntülenir.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Birleşik Devletler telefon numarası, alan kodu isteğe bağlıdır. Kullanıcı isteğe bağlı karakterleri girmek istemezseniz, boşluk girebilir veya fare işaretçisini, ilk 0 ile temsil edilen maskenin içindeki konuma doğrudan yerleştirebilir.|  
|`$\d{6}.00`|`$999,999.00`|0 ile 999999 arasında bir para birimi değeri. Para birimi, thousandth ve ondalık karakterler çalışma zamanında kültüre özgü eşdeğerleriyle değiştirilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Visual Basic'de Dizeleri Doğrulama](validating-strings.md)
- [MaskedTextBox Denetimi](/dotnet/desktop/winforms/controls/maskedtextbox-control-windows-forms)
