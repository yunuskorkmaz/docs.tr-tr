---
title: "Ara değerli dizeler (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a>Ara değerli dizeler (C# Başvurusu)

Dizeleri oluşturmak için kullanılır.  Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*.  Ara değerli bir dize içeriyor Ara değerli ifadeleri kendi dize Beyanları ile değiştiren bir dize döndürür. Bu özellik, C# 6 ve sonraki sürümlerinde kullanılabilir.

Ara değerli bir dize bağımsız değişkenleri daha anlamak daha kolay bir [bileşik biçim dizesi](../../../standard/base-types/composite-formatting.md#composite-format-string).  Örneğin, Ara değerli dize  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
'{name}', iki ara değerli ifadeleri içerir ve '{saatleri: ss}'. Eşdeğer bileşik biçim dizesi şöyledir:

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Ara değerli bir dize yapıdır:  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

burada: 

- *Alan genişliği* alanında karakter sayısını gösteren imzalı bir tamsayıdır. Pozitif ise sağa hizalı alanıdır; negatifse, sola hizalı. 

- *Biçim dizesi* bir biçim dizesi biçimlendirilen nesne türü için uygundur. Örneğin, bir <xref:System.DateTime> değeri, bir standart tarih ve saat biçim dizesi "D" veya "d" gibi olabilir.

> [!IMPORTANT]
> Arasında bir boşluk olamaz `$` ve `"` dize başlar. Bunun yapılması, derleme zamanı hata neden olur.

 Ara değerli bir dize kullanabileceğiniz bir değişmez dize değeri her yerde kullanabilirsiniz.  Ara değerli dize ara değerli dizesiyle kodu yürütür her zaman değerlendirilir. Bu, tanım ve Ara değerli bir dize değerlendirmesine ayırmanıza olanak sağlar.  
  
 Süslü ayraç içerecek şekilde ("{" veya "}") iki süslü ayraçlar, bir ara değerli dizesinde kullanmak "{{" veya "}}".  Daha fazla ayrıntı için örtük dönüşümler bölümüne bakın.  

Ara değerli dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi ara değerli bir dize olarak özel bir anlamı olan diğer karakterler içeriyorsa, bunlar değişmez değer metinde oluşma ya da virgülle ayrılan bir ifadede eklenmelidir kaçış Dil öğeleri ara değerli bir ifadede dahil olmaları durumunda parantez. Aşağıdaki örnek sonuç dizesinde eklemek için tırnak işaretleri çıkışları ve ifade sınırlandırmak için parantez kullanır `(age == 1 ? "" : "s")` böylece iki nokta üst üste bir biçim dizesi başlayan olarak yorumlanır değil.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

Harfi harfine dizeler Kullan'ı değiştirilmiş `$` karakter arkasından `@` karakter. Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](string.md) konu. Aşağıdaki kod verbatim Ara değerli bir dize kullanarak önceki kod parçacığında, değiştirilmiş bir sürümüdür:

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

Harfi harfine dizeler değil uyma biçimlendirme değişiklikleri gerekli olduğu `\` çıkış sıraları.

> [!IMPORTANT]
> `$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.


## <a name="implicit-conversions"></a>Örtük dönüşümler  

Ara değerli bir dizeden üç örtük tür dönüşümleri vardır:  

1. Ara değerli bir dizeye dönüştürme bir <xref:System.String>. Aşağıdaki örnek, Ara değerli dizesi ifadeleri kendi dize Beyanları ile değiştirilmiş bir dize döndürür. Örneğin:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Bu dize yorumlama son sonucudur. Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}") için tek bir büyük ayraç dönüştürülür. 

2. Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği. Bu, tek tek kültürler için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.  Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), açıkça veya örtük çağırarak biçim dizesi kadar çift ayraç kalır <xref:System.Object.ToString> yöntemi.  {0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.  

   Aşağıdaki örnek, alan ve özellik değerlerini yanı sıra üyeleri görüntülemek için yansıma kullanır. bir <xref:System.IFormattable> Ara değerli bir dizeden oluşturulmuş değişkeni. Ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Ara değerli dize yalnızca yansıma kullanarak Denetlenmekte olduğunu unutmayın. Yöntemi, aşağıdaki gibi biçimlendirme dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>biçimi öğelerinden çözümlendiği ve sonucu dize döndürdü. 

3. Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> bileşik biçim dizesi gösteren değişkeni. Bileşik biçim dizesi ve nasıl dizeyi sonucunda işler İnceleme Örneğin, bir sorgu oluşturuyorsanız ekleme saldırılara karşı korunmaya yardımcı olabilir. <xref:System.FormattableString> Ayrıca içerir <xref:System.FormattableString.ToString> olanak tanıyan aşırı üretmek için sonuç dizeleri <xref:System.Globalization.CultureInfo.InvariantCulture> ve <xref:System.Globalization.CultureInfo.CurrentCulture>.  Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), format kadar çift süslü ayraçlar kalır.  {0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Dil belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
