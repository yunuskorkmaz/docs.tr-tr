---
title: Aritmetik İşleçler (F#)
description: Kullanılabilen aritmetik işleçler hakkında bilgi edinin F# programlama dilidir.
ms.date: 04/04/2018
ms.openlocfilehash: 2c0e2e25a4f79d00455d978e235e4bef16b52586
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2018
ms.locfileid: "45597447"
---
# <a name="arithmetic-operators"></a>Aritmetik İşleçler

Bu konu, kullanılabilen aritmetik işleçler açıklar F# dili.

## <a name="summary-of-binary-arithmetic-operators"></a>İkili aritmetik işleçler özeti

Kutulanmamış integral ve kayan nokta türleri için kullanılabilen ikili aritmetik işleçleri aşağıdaki tabloda özetlenmiştir.

|İkili işleç|Notlar|
|---------------|-----|
|`+` (Ayrıca, artı)|İşaretlenmemiş. Sayı birlikte eklendiğinde olası taşma durumu ve toplama türü tarafından desteklenen en fazla mutlak değeri aşıyor.|
|`-` (çıkarma, eksi)|İşaretlenmemiş. Olası underflow imzasız türler çıkarılan veya kayan nokta değerleri türüne göre gösterilemeyecek kadar çok küçük olduğunda koşul.|
|`*` (çarpma, saatler)|İşaretlenmemiş. Sayı çarpıldığında olası taşma durumu ve ürün türüne göre desteklenen maksimum mutlak değeri aşıyor.|
|`/` (bölme, bölünen)|Neden sıfır ile bölme bir <xref:System.DivideByZeroException> tam sayı türleri için. Kayan nokta türleri için özel bir kayan nokta değerleri verir sıfıra bölünme `+Infinity` veya `-Infinity`. Aynı zamanda bir kayan noktalı sayı türü ile ifade için çok küçük olduğunda da olası yetersiz koşulu yoktur.|
|`%` (geri kalan, rem)|Bölme işlemindeki kalanı döndürür. Sonucun işaretine göre birinci işlenenin oturum ile aynıdır.|
|`**` (üs olarak gösterme üzeri)|Sonuç türü için en fazla mutlak değeri aştığında olası taşma durumu.<br /><br />Üs olarak gösterme işlecini yalnızca kayan nokta türleriyle çalışır.|

## <a name="summary-of-unary-arithmetic-operators"></a>Birli aritmetik işleçler özeti

İntegral ve kayan nokta türleri için kullanılabilen birli aritmetik işleçler aşağıdaki tabloda özetlenmiştir.

|Birli işleç|Notlar|
|--------------|-----|
|`+` (pozitif)|Herhangi bir aritmetik ifade uygulanabilir. Değerin oturum değiştirmez.|
|`-` (olumsuzlama, negatif)|Herhangi bir aritmetik ifade uygulanabilir. Oturum değeri değiştirir.|

Taşma veya yetersiz gelme tam sayı türleri için davranış sarma yüklemektir. Bu, hatalı bir sonuç neden olur. Tamsayı taşması yazılım için hesap için değil yazıldığında, güvenlik sorunlarına katkıda bulunabilir Potansiyel ciddi bir sorundur. Bu, uygulamanız için önemliyse, işaretli işleçleri kullanarak göz önünde bulundurun `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>İkili Karşılaştırma işleçleri özeti

İntegral ve kayan nokta türleri için kullanılabilen ikili Karşılaştırma işleçleri aşağıdaki tabloda gösterilmektedir. Bu işleçler dönüş türü değerleri `bool`.

IEEE kayan Noktası temsili bir tam eşitlik işlemi desteklemediği için kayan nokta sayıları hiçbir zaman doğrudan eşitlik için karşılaştırılması gereken. Kodu inceleyerek eşit olacak şekilde kolayca doğrulayabilirsiniz iki sayı aslında farklı bit temsilleri olabilir.

|İşleç|Notlar|
|--------|-----|
|`=` (eşitlik, eşittir)|Bu, bir atama işleci değil. Karşılaştırma için kullanılır. Bu genel bir işlecidir.|
|`>` (büyüktür)|Bu genel bir işlecidir.|
|`<` (küçüktür)|Bu genel bir işlecidir.|
|`>=` (büyüktür veya eşittir)|Bu genel bir işlecidir.|
|`<=` (küçüktür veya eşittir)|Bu genel bir işlecidir.|
|`<>` (eşit değildir)|Bu genel bir işlecidir.|

## <a name="overloaded-and-generic-operators"></a>Aşırı yüklenmiş ve genel işleçler

Tüm bu konuda tartışılan işleçlerinin tanımlanan **Microsoft.FSharp.Core.Operators** ad alanı. İşleçlerin bazıları, statik olarak çözümlenmiş tür parametreleri kullanılarak tanımlanır. Bu, tek tek operatörü ile çalışan her belirli tür tanımlarında olduğu anlamına gelir. Bu kategoride olan tüm tekli veya ikili aritmetik ve bit düzeyinde işleçler. Karşılaştırma işleçleri geneldir ve bu nedenle değil yalnızca temel aritmetik türlerin her tür ile çalışma. Ayrılmış birleşim ve kayıt türleri tarafından oluşturulan kendi özel uygulamalar sahip F# derleyici. Sınıf türleri yöntemi kullanın <xref:System.Object.Equals%2A>.

Genel işleçler özelleştirilebilir. Karşılaştırma işlevleri özelleştirmek için geçersiz kılma <xref:System.Object.Equals%2A> kendi özel eşitlik karşılaştırması sağlayın ve ardından uygulamak için <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Arabirimi tek bir yöntemi vardır <xref:System.IComparable.CompareTo%2A> yöntemi.

## <a name="operators-and-type-inference"></a>İşleçler ve tür çıkarımı

Bu işlecinde tür çıkarımı bir işleç bir ifadede kullanılmasını kısıtlar. Ayrıca, işleçlerinin kullanımı bir aritmetik tür gösterdiğinden otomatik Genelleştirme işleçleri kullanımını engeller. Diğer herhangi bir bilgi olmadığında F# derleyici çıkarsar `int` aritmetik ifade türü. Başka bir tür belirterek bu davranışı geçersiz kılabilirsiniz. Bu nedenle bağımsız değişken türleri ve dönüş türünü `function1` olması için aşağıdaki kodda algılanır `int`, ancak türleri için `function2` olmasını çıkarılan `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Simge ve İşleç Başvurusu](index.md)
- [İşleç Aşırı Yüklemesi](../operator-overloading.md)
- [Bit Düzeyinde İşleçler](bitwise-operators.md)
- [Boole İşleçleri](boolean-operators.md)
