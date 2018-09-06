---
title: Ara değerli dizeler (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 313e74d5ce252884f1df2479ef1db8b4b24b5cce
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44040937"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Ara değerli dizeler (Visual Basic Başvurusu)

Dizeleri oluşturmak için kullanılır.  İlişkilendirilmiş dize içeren bir şablon dize gibi görünüyor *ilişkilendirilmiş ifade*.  Bir aradeğerlendirme dizesinde içerdiği ilişkilendirilmiş ifadeler ile bunların dize temsilleri yerini alan bir dize döndürür. Bu özellik, Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.

İlişkilendirilmiş dize bağımsız değişkenleri daha anlamak daha kolay anlaşılır bir [bileşik biçimlendirme dizesi](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Örneğin, ilişkilendirilmiş dize  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
'{name}', iki ilişkilendirilmiş ifadeler içerir ve '{saat: ss}'. Eşdeğer bileşik biçimlendirme dizesi şöyle olur:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Bir aradeğerlendirme dizesinde yapısı şöyledir:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

burada: 

- *Alan genişliği* alanında karakter sayısını belirten işaretli bir tamsayıdır. Pozitif ise sağa hizalı alanıdır; negatif ise sola hizalıdır. 

- *Biçim dizesi* bir biçim dizesi, biçimlendirilen nesnenin türü için uygundur. Örneğin, bir <xref:System.DateTime> değeri olabilir bir [standart tarih ve saat biçim dizesi](~/docs/standard/base-types/standard-date-and-time-format-strings.md) "D" veya "d" gibi.

> [!IMPORTANT]
> Arasında beyaz boşluk olamaz `$` ve `"` , dize başlar. Bunun yapılması, bir derleyici hatasına neden olur.

 Bir aradeğerlendirme dizesinde kullanabileceğiniz bir dize sabit değeri her yerde kullanabilirsiniz.  İlişkilendirilmiş dize ile ilişkilendirilmiş dize kodu yürütür her zaman değerlendirilir. Bu, bir aradeğerlendirme dizesinde değerlendirmesini ve tanımı ayırmanıza olanak sağlar.  
  
 Küme ayracı içerecek şekilde ("{" veya "}") iki küme ayracı, bir aradeğerlendirme dizesinde kullanın "{{" veya "}}".  Daha fazla ayrıntı için örtülü dönüştürmeler bölümüne bakın.  

İlişkilendirilmiş dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi bir aradeğerlendirme dizesinde özel bir anlamı olan diğer karakterler içeriyorsa bunlar değişmez değer metni ortaya ya da ayrılmış bir ifadede eklenmelidir Atlanan Dil öğeleri bir ilişkilendirilmiş ifadede dahil olmaları durumunda parantez. Aşağıdaki örnek, tırnak işaretleri, sonuç dizesine eklemek çıkışları ve ifade sınırlandırmak için parantez kullanan `(age == 1 ? "" : "s")` böylece iki noktadan başlayarak bir biçim dizesi olarak yorumlanır değil.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Örtük dönüşümler  

Bir aradeğerlendirme dizesinde üç örtük tür dönüştürmelerinde vardır:  

1. Bir araya alınmış dizeye dönüştürme bir <xref:System.String>. Aşağıdaki örnek, ilişkilendirilmiş dize ifadeleri ile bunların dize temsilleri değiştirilmiş bir dize döndürür. Örneğin:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Bir dize yorumu sonucunu budur. Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}") için tek bir küme ayracı dönüştürülür. 

2. Bir araya alınmış dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği. Bu, bağımsız kültür için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.  Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}"), açıkça veya dolaylı olarak çağırarak biçim dizesi çift kaşlı ayraçlar ermesine <xref:System.Object.ToString> yöntemi.  Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.  

   Aşağıdaki örnek, üyeleri ve bunun yanı sıra alan ve özellik değerlerini görüntülemek için yansıtma kullanır. bir <xref:System.IFormattable> ilişkilendirilmiş bir dizeden oluşturulan değişken. Bu işlem ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Yalnızca yansıma kullanarak ilişkilendirilmiş dize inceledi olduğunu unutmayın. Aşağıdakiler gibi biçimlendirme yöntemi, bir dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>, biçim öğeleri çözümlendiği ve sonuç dizesi döndürdü. 

3. Bir araya alınmış dizeye dönüştürme bir <xref:System.FormattableString> bir bileşik biçimlendirme dizesi temsil eden değişken. Bileşik biçimlendirme dizesi ve sonuç olarak nasıl dize işleyen İnceleme Örneğin, bir sorgu oluşturuyorsanız bir ekleme saldırısına karşı korumanıza yardımcı. A <xref:System.FormattableString> de içerir:

      - A <xref:System.FormattableString.ToString> için bir sonuç dizesi oluşturur aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> için bir dize üreten yöntemi <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> yönteminin belirtilen kültür için bir sonuç dizesi oluşturur. 
  
    Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}"), biçimlendirme kadar çift kaşlı ayraçlar kalır.  Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Visual Basic Dili Başvurusu](index.md)  
 