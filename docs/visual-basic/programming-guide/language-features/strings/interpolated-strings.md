---
title: Ara değerli dizeler (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95f79c5cdff1a48da2bb0eaf92229570ced631b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="interpolated-strings-visual-basic-reference"></a>Ara değerli dizeler (Visual Basic Başvurusu)

Dizeleri oluşturmak için kullanılır.  Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*.  Ara değerli bir dize içeriyor Ara değerli ifadeleri kendi dize Beyanları ile değiştiren bir dize döndürür. Bu özellik, Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.

Ara değerli bir dize bağımsız değişkenleri daha anlamak daha kolay bir [bileşik biçim dizesi](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Örneğin, Ara değerli dize  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
'{name}', iki ara değerli ifadeleri içerir ve '{saatleri: ss}'. Eşdeğer bileşik biçim dizesi şöyledir:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Ara değerli bir dize yapıdır:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

burada: 

- *Alan genişliği* alanında karakter sayısını gösteren imzalı bir tamsayıdır. Pozitif ise sağa hizalı alanıdır; negatifse, sola hizalı. 

- *Biçim dizesi* bir biçim dizesi biçimlendirilen nesne türü için uygundur. Örneğin, bir <xref:System.DateTime> değeri, onu olabilir bir [standart tarih ve saat biçim dizesi](~/docs/standard/base-types/standard-date-and-time-format-strings.md) "D" veya "d" gibi.

> [!IMPORTANT]
> Arasında bir boşluk olamaz `$` ve `"` dize başlar. Bunun yapılması bir derleyici hatasına neden olur.

 Ara değerli bir dize kullanabileceğiniz bir değişmez dize değeri her yerde kullanabilirsiniz.  Ara değerli dize ara değerli dizesiyle kodu yürütür her zaman değerlendirilir. Bu, tanım ve Ara değerli bir dize değerlendirmesine ayırmanıza olanak sağlar.  
  
 Süslü ayraç içerecek şekilde ("{" veya "}") iki süslü ayraçlar, bir ara değerli dizesinde kullanmak "{{" veya "}}".  Daha fazla ayrıntı için örtük dönüşümler bölümüne bakın.  

Ara değerli dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi ara değerli bir dize olarak özel bir anlamı olan diğer karakterler içeriyorsa, bunlar değişmez değer metinde oluşma ya da virgülle ayrılan bir ifadede eklenmelidir kaçış Dil öğeleri ara değerli bir ifadede dahil olmaları durumunda parantez. Aşağıdaki örnek sonuç dizesinde eklemek için tırnak işaretleri çıkışları ve ifade sınırlandırmak için parantez kullanır `(age == 1 ? "" : "s")` böylece iki nokta üst üste bir biçim dizesi başlayan olarak yorumlanır değil.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Örtük dönüşümler  

Ara değerli bir dizeden üç örtük tür dönüşümleri vardır:  

1. Ara değerli bir dizeye dönüştürme bir <xref:System.String>. Aşağıdaki örnek, Ara değerli dizesi ifadeleri kendi dize Beyanları ile değiştirilmiş bir dize döndürür. Örneğin:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Bu dize yorumlama son sonucudur. Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}") için tek bir büyük ayraç dönüştürülür. 

2. Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği. Bu, tek tek kültürler için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.  Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), açıkça veya örtük çağırarak biçim dizesi kadar çift ayraç kalır <xref:System.Object.ToString> yöntemi.  Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.  

   Aşağıdaki örnek, alan ve özellik değerlerini yanı sıra üyeleri görüntülemek için yansıma kullanır. bir <xref:System.IFormattable> Ara değerli bir dizeden oluşturulmuş değişkeni. Ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Ara değerli dize yalnızca yansıma kullanarak Denetlenmekte olduğunu unutmayın. Yöntemi, aşağıdaki gibi biçimlendirme dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>biçimi öğelerinden çözümlendiği ve sonucu dize döndürdü. 

3. Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> bileşik biçim dizesi gösteren değişkeni. Bileşik biçim dizesi ve nasıl dizeyi sonucunda işler İnceleme Örneğin, bir sorgu oluşturuyorsanız ekleme saldırılara karşı korunmaya yardımcı olabilir. A <xref:System.FormattableString> de içerir:

      - A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> için bir dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem. 
  
    Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), format kadar çift ayraç kalır.  Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Visual Basic Dil Başvurusu](index.md)  
 