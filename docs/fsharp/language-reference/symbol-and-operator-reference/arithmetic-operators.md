---
title: "Aritmetik İşleçler (F#)"
description: "F # programlama dili kullanılabilen aritmetik işleçler hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 75ddcfa3-564e-4382-80a3-f9da73d0f0ea
ms.openlocfilehash: 237b97c24f207b3a9b4661d66f029f1b18b8fec7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="arithmetic-operators"></a>Aritmetik İşleçler

Bu konu, F # dilinde kullanılabilir aritmetik işleçler açıklar.

## <a name="summary-of-binary-arithmetic-operators"></a>İkili aritmetik işleçler özeti
Aşağıdaki tabloda sarmalanmamış ayrılmaz ve kayan nokta türleri için kullanılabilir olan ikili aritmetik işleçler özetler.

|İkili işleç|Notlar|
|---------------|-----|
|`+`(Ayrıca, artı)|İşaretli. Sayılar birlikte eklendiğinde olası taşma koşulunu ve toplamını türü tarafından desteklenen en fazla mutlak değerini aşıyor.|
|`-`(çıkarma, eksi)|İşaretli. Olası underflow imzasız türler çıkarılan veya kayan nokta değer türü tarafından gösterilemeyecek kadar küçük olduğunda koşul.|
|`*`(çarpma, saatler)|İşaretli. Sayı çarpıldığı zaman olası taşma koşulunu ve ürün türü tarafından desteklenen en fazla mutlak değerini aşıyor.|
|`/`(bölü bölme)|Sıfır nedenler bölme bir <xref:System.DivideByZeroException> tam sayı türleri için. Kayan nokta türleri için özel kayan nokta değerlerini verir sıfıra bölme `+Infinity` veya `-Infinity`. Aynı zamanda bir kayan noktalı sayı türü tarafından gösterilemeyecek kadar küçük olduğunda da olası underflow koşulu yoktur.|
|`%`(modül, mod)|Bölme işlemi geri kalanı döndürür. Sonucun oturum ilk işlenen oturum ile aynıdır.|
|`**`(üs, üzeri)|Sonuç türü için en fazla mutlak değeri aştığında olası taşma koşulu.<br /><br />Üs işleci kayan nokta türleri ile çalışır.|

## <a name="summary-of-unary-arithmetic-operators"></a>Birli aritmetik işleçler özeti
Tam sayı ve kayan nokta türleri için kullanılabilen birli aritmetik işleçler aşağıdaki tabloda özetlenmiştir.


|Birli işleç|Notlar|
|--------------|-----|
|`+`(pozitif)|Herhangi bir aritmetik ifade uygulanabilir. Değerin oturum değiştirmez.|
|`-`(değilleme, negatif)|Herhangi bir aritmetik ifade uygulanabilir. Değerin oturum değiştirir.|
Davranış taşması veya tam sayı türleri için yetersiz sarma yüklemektir. Bu, hatalı bir sonuç neden olur. Tamsayı taşma yazılım için hesap için değil yazıldığında, güvenlik sorunları katkıda bulunabilirsiniz ciddi olabilecek bir sorundur. Bu, uygulamanız için önemliyse, checked işleçleri kullanmayı `Microsoft.FSharp.Core.Operators.Checked`.


## <a name="summary-of-binary-comparison-operators"></a>İkili Karşılaştırma işleçleri özeti
Aşağıdaki tabloda ayrılmaz ve kayan nokta türleri için kullanılabilir olan ikili Karşılaştırma işleçleri gösterir. Bu işleçlere dönüş türü değerleri `bool`.

IEEE kayan Noktası temsili bir tam eşitlik işlemi desteklemediği için kayan nokta sayıları hiçbir zaman doğrudan eşitlik için karşılaştırılması gereken. Kod inceleyerek eşit olması için kolayca doğrulayabilirsiniz iki sayı gerçekte farklı bit Beyanları olabilir.



|İşleç|Notlar|
|--------|-----|
|`=`(eşitlik, eşittir)|Bu atama işleci değildir. Yalnızca karşılaştırma için kullanılır. Bu genel bir işlecidir.|
|`>`(büyük)|Bu genel bir işlecidir.|
|`<`(küçüktür)|Bu genel bir işlecidir.|
|`>=`(büyüktür veya eşittir)|Bu genel bir işlecidir.|
|`<=`(küçüktür veya eşittir)|Bu genel bir işlecidir.|
|`<>`(eşit değildir)|Bu genel bir işlecidir.|

## <a name="overloaded-and-generic-operators"></a>Aşırı yüklenmiş ve genel işleçler
Bu konuda tartışılan işleçleri tümünün içinde tanımlanan **Microsoft.FSharp.Core.Operators** ad alanı. İşleçlerin bazıları statik olarak çözümlenmiş tür parametreleri kullanılarak tanımlanır. Bu, bu işleç ile çalışır belirli her tür için tek tek tanımları olduğunu gösterir. Tüm ikili aritmetik ve bit düzeyinde işleçler ve birli Bu kategoride bulunan. Karşılaştırma işleçleri genel ve bu nedenle, her tür ile yalnızca basit aritmetik türler çalışabilirsiniz. Ayrılmış birleşim ve kayıt türleri F # derleyici tarafından üretilen kendi özel uygulamalar vardır. Sınıf türleri yöntemi kullanın <xref:System.Object.Equals%2A>.

Genel işleçler özelleştirilebilir. Karşılaştırma işlevleri özelleştirmek için geçersiz kılma <xref:System.Object.Equals%2A> kendi özel eşitlik karşılaştırması sağlayın ve ardından uygulamak için <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Arabirimi sahip tek bir yöntem <xref:System.IComparable.CompareTo%2A> yöntemi.


## <a name="operators-and-type-inference"></a>İşleçler ve tür çıkarımı
Tür çıkarımı işleç üzerinde bir ifadede bir işleç kullanımını kısıtlar. Ayrıca, işleçler kullanımını aritmetik türü gösterdiğinden otomatik Genelleştirme işleçleri kullanımını engeller. F # derleyici herhangi bir bilgi olmaması durumunda oluşturur `int` aritmetik ifadeler türü. Başka bir tür belirterek bu davranışı geçersiz kılabilirsiniz. Bu nedenle bağımsız değişken türleri ve dönüş türü `function1` olması için aşağıdaki kodu çıkarımı yapılan `int`, ancak türleri için `function2` olarak algılanır `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[Simge ve işleç başvurusu](index.md)

[İşleç aşırı yüklemesi](../operator-overloading.md)

[Bit düzeyinde işleçler](bitwise-operators.md)

[Boole işleçleri](boolean-operators.md)
