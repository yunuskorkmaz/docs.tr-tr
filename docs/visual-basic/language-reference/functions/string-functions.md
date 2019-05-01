---
title: Dize İşlevleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 645d19219481d22ade90f44aaecb62471eb915d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802007"
---
# <a name="string-functions-visual-basic"></a>Dize İşlevleri (Visual Basic)
Aşağıdaki tabloda, Visual Basic dizeleri arama ve işleme için sağladığı işlevleri listeler.  
  
|.NET framework yöntemi|Açıklama|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Döndürür bir `Integer` bir karakterin karakter kodunu temsil eden değer.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Belirtilen karakter koduyla ilişkili karakteri döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Bir alt kümesini içeren sıfır tabanlı bir dizi döndürür bir `String` belirtilen filtre ölçütlerine göre alan dizisi.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Bir biçimde bulunan yönergelere göre biçimlendirilen bir dize döndürür `String` ifade.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Sistem denetim masasında tanımlanan para birimi sembolünü kullanarak para birimi değeri olarak biçimlendirilmiş bir ifade döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Bir tarih/saat değerini temsil eden bir dize ifadesi döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Bir sayı olarak biçimlendirilmiş bir ifade döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|(Yani 100 ile çarpılmış), sonunda % karakteriyle yüzde olarak biçimlendirilmiş bir ifade döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Bir dizenin içindeki başka bir dizenin başlangıç konumunu belirten bir tamsayı döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Bir dizenin içindeki başka bir dizenin sağ tarafından başlayarak ilk oluşum konumunu döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Bir dizi içindeki alt dizelerin sayısı birleştirilerek oluşturulan bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Bir dize veya karakteri küçük harfe döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Belirtilen sayıda karakteri bir dizenin solundan içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Bir dizedeki karakter sayısını içeren bir tamsayı döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|İstenen uzunluğa getirilmiş belirtilen dizeyi içeren sola hizalanmış bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Belirtilen dizenin başında boşluk olmayan bir kopyasını içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Belirtilen sayıda karakteri bir dizeden içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Döndürür içinde belirtilen bir alt dizenin başka bir dizenin belirtilen sayıda alt dize.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Belirtilen sayıda karakteri bir dizenin sağından içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|İstenen uzunluğa getirilmiş belirtilen dizeyi içeren sağa hizalanmış bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Belirtilen bir dizenin sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Belirtilen sayıda boşluktan oluşan bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Belirtilen sayıda alt dize içeren sıfır tabanlı, tek boyutlu bir dizi döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|-1, 0 veya 1, bir dize karşılaştırmasının sonucuna göre döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Belirtilen şekilde dönüştürülmüş bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Bir dize veya nesne belirtilen karakterin belirtilen sayıda yinelenen döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|İçinde belirtilen bir dizenin karakter sırasının ters çevrildiği bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Belirtilen dizenin başında veya sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Bir dize ya da belirtilen dizeyi büyük harfe dönüştürülmüş içeren karakter döndürür.|  
  
 Kullanabileceğiniz [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) deyimi yoksa dizeleri büyük küçük harf duyarsız bir metin sıralama düzeni, sisteminizin yerel ayarı tarafından belirlenen (`Text`) veya karakterleri (iç ikili gösterimi `Binary`). Varsayılan metin karşılaştırma yöntemi: `Binary`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `UCase` bir dizeyi büyük harfli sürümünü döndürmek için işlevi.  
  
 [!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte `LTrim` değişkenden önce gelen boşlukları işlevi ve `RTrim` önceki boşlukları kaldırır işlevi bir dize değişkeninden yerleştirir. Kullandığı `Trim` her iki türdeki alanı kesmek için işlevi.  
  
 [!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Mid` işlevini bir dizeden belirtilen sayıda karakteri döndürür.  
  
 [!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Len` bir dizedeki karakter sayısını döndürmek için.  
  
 [!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte `InStr` içindeki başka bir dizenin ilk geçtiği konumu döndürmek için işlevi.  
  
 [!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, çeşitli kullanımları gösterir `Format` kullanarak işleve `String` biçimleri ve kullanıcı tanımlı biçimleri. Tarih Ayırıcı (`/`), zaman ayırıcı (`:`) ve AM/PM göstergeleri (`t` ve `tt`), sisteminiz tarafından gösterilecek biçimlendirilmiş Sonuç kodu kullanarak yerel ayarlara bağlıdır. Saatler ve tarihler görüntülendiğinde geliştirme ortamında, kısa saat biçimini ve kod yerel ayarının kısa tarih biçimi kullanılır.  
  
> [!NOTE]
>  24 saatlik düzende, AM/PM göstergeleri kullanan yerel ayarlar için (`t` ve `tt`) herhangi bir şey görüntülemez.  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic Çalışma Süresi Kitaplık Üyeleri](../../../visual-basic/language-reference/runtime-library-members.md)
- [Dize Düzenleme Özeti](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
