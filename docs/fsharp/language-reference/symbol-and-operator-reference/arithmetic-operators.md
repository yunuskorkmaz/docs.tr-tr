---
title: Aritmetik İşleçler
description: F# Programlama dilinde kullanılabilen aritmetik işleçler hakkında bilgi edinin.
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630788"
---
# <a name="arithmetic-operators"></a>Aritmetik İşleçler

Bu konuda, F# dilde kullanılabilen aritmetik işleçler açıklanmaktadır.

## <a name="summary-of-binary-arithmetic-operators"></a>Ikili aritmetik Işleçlerin Özeti

Aşağıdaki tabloda, kutulanmamış integral ve kayan nokta türleri için kullanılabilen ikili aritmetik işleçler özetlenmektedir.

|İkili işleç|Notlar|
|---------------|-----|
|`+`(toplama, artı)|Olmayan. Sayılar birlikte eklendiğinde olası taşma koşulu ve toplam, türün desteklediği en büyük mutlak değeri aşıyor.|
|`-`(çıkarma, eksi)|Olmayan. İşaretsiz türler çıkarıldığında veya kayan nokta değerleri tür tarafından gösterilemeyecek kadar küçük olduğunda olası yetersiz yer durumu.|
|`*`(çarpma, saatler)|Olmayan. Sayılar çarpıldığı zaman ve ürün, türün desteklediği en büyük mutlak değeri aştığında olası taşma koşulu.|
|`/`(bölme, bölünmüş olarak)|Sıfıra bölme, tam sayı <xref:System.DivideByZeroException> türlerine neden olur. Kayan nokta türleri için, sıfıra bölme size özel kayan nokta değerleri `+Infinity` veya `-Infinity`sağlar. Bir kayan noktalı sayı, tür tarafından gösterilemeyecek kadar küçük olduğunda da olası bir yetersiz yer vardır.|
|`%`(kalan, REM)|Bölüm işleminin kalanını döndürür. Sonucun işareti, İlk işlenenin işaretiyle aynıdır.|
|`**`(üs, kuvvetle)|Sonuç, türün en büyük mutlak değerini aştığında olası taşma koşulu.<br /><br />Üs işleci yalnızca kayan nokta türleri ile kullanılabilir.|

## <a name="summary-of-unary-arithmetic-operators"></a>Birli aritmetik Işleçlerin Özeti

Aşağıdaki tabloda, integral ve kayan nokta türleri için kullanılabilen birli aritmetik işleçler özetlenmektedir.

|Birli işleç|Notlar|
|--------------|-----|
|`+`pozitif|Herhangi bir aritmetik ifadeye uygulanabilir. Değerin işaretini değiştirmez.|
|`-`(olumsuzlama, negatif)|Herhangi bir aritmetik ifadeye uygulanabilir. Değerin işaretini değiştirir.|

Tam sayı türleri için taşma veya yetersiz gelme davranışı etrafında sarılmalıdır. Bu, hatalı bir sonuca neden olur. Tamsayı taşması, yazılım hesaba yazılmadığından güvenlik sorunlarına katkıda bulunabilecek ciddi bir sorundur. Uygulamanız için bir sorun varsa, içindeki `Microsoft.FSharp.Core.Operators.Checked`işaretli işleçleri kullanmayı göz önünde bulundurun.

## <a name="summary-of-binary-comparison-operators"></a>Ikili karşılaştırma Işleçleri Özeti

Aşağıdaki tabloda, integral ve kayan nokta türleri için kullanılabilen ikili karşılaştırma işleçleri gösterilmektedir. Bu işleçler tür `bool`değerlerini döndürür.

IEEE kayan nokta temsili tam bir eşitlik işlemini desteklemediğinden, kayan nokta numaraları asla eşitlik için karşılaştırılamaz. Kodu inceleyerek kolayca doğrulayabilecek iki sayı, aslında farklı bit temsillerine sahip olabilir.

|İşleç|Notlar|
|--------|-----|
|`=`(eşitlik, eşittir)|Bu bir atama işleci değildir. Yalnızca karşılaştırma için kullanılır. Bu genel bir işleçtir.|
|`>`(büyüktür)|Bu genel bir işleçtir.|
|`<`(küçüktür)|Bu genel bir işleçtir.|
|`>=`(büyüktür veya eşittir)|Bu genel bir işleçtir.|
|`<=`(küçüktür veya eşittir)|Bu genel bir işleçtir.|
|`<>`(eşit değildir)|Bu genel bir işleçtir.|

## <a name="overloaded-and-generic-operators"></a>Aşırı yüklenmiş ve genel Işleçler

Bu konuda açıklanan tüm işleçler **Microsoft. FSharp. Core. Operators** ad alanında tanımlanmıştır. Bazı işleçlerden bazıları statik olarak çözümlenen tür parametreleri kullanılarak tanımlanır. Bu, bu işleçle birlikte çalışarak her bir özel tür için ayrı tanımlar olduğu anlamına gelir. Birli ve ikili aritmetik ve bit düzeyinde işleçlerin hepsi bu kategoride bulunur. Karşılaştırma işleçleri geneldir ve bu nedenle yalnızca temel aritmetik türler değil, herhangi bir türle çalışır. Ayırt edici birleşim ve kayıt türlerinin, F# derleyici tarafından oluşturulan kendi özel uygulamaları vardır. Sınıf türleri yöntemini <xref:System.Object.Equals%2A>kullanır.

Genel işleçler özelleştirilebilir. Karşılaştırma işlevlerini özelleştirmek için, özel eşitlik <xref:System.Object.Equals%2A> karşılaştırmayı sağlamak üzere geçersiz kılın ve ardından uygulayın. <xref:System.IComparable> Arabirimin tek bir yöntemi <xref:System.IComparable.CompareTo%2A> , yöntemi vardır. <xref:System.IComparable?displayProperty=nameWithType>

## <a name="operators-and-type-inference"></a>İşleçler ve tür çıkarımı

Bir ifadede işleç kullanımı, bu işlecin tür çıkarımını kısıtlar. Ayrıca, işleçlerin kullanımı aritmetik bir tür gösterdiği için işleçlerin kullanılması otomatik genelleştirmeyi engeller. Diğer tüm bilgiler yokluğunda, F# derleyici `int` aritmetik ifadeler türü olarak ifade ediyor. Başka bir tür belirterek bu davranışı geçersiz kılabilirsiniz. Bu nedenle, aşağıdaki kodda bağımsız değişken türleri `function1` ve dönüş türü olarak algılanır `int` `function2` , ancak türleri olarak algılanır `float`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Simge ve İşleç Başvurusu](index.md)
- [İşleç Aşırı Yüklemesi](../operator-overloading.md)
- [Bit Düzeyinde İşleçler](bitwise-operators.md)
- [Boole İşleçleri](boolean-operators.md)
