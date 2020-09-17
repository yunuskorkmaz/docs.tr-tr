---
title: XML Belgeleri
description: "Açıklamalardan belge oluşturmak için F # ' da destek hakkında bilgi edinin."
ms.date: 09/15/2020
ms.openlocfilehash: a5bec20f27c23caee951cda2dc5d17808f69d384
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679409"
---
# <a name="document-your-code-with-xml-comments"></a>Kodunuzu XML açıklamalarıyla belgeleme

F # ' da Üçlü eğik çizgi (///) kod açıklamalarından belgeler oluşturabilirsiniz. XML açıklamaları, kod dosyaları (. FS) veya imza (. fsi) dosyalarındaki bildirimlerden önce olabilir.

XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.
Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.
Derleyici tarafından oluşturulan XML dosyası, .NET derlemenizin yanı sıra, türler veya üyeler hakkında hızlı bilgileri göstermek için araç ipuçları kullanabilmesi için, .NET derlemeniz ile dağıtılabilir. Ayrıca, XML dosyası [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) gibi araçlar aracılığıyla, API başvuru Web siteleri oluşturmak için çalıştırılabilir.

Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır, aşağıda açıklanan seçenekler derleme zamanında, açıklamaların geçerliliğini ve tamamlananmasını denetlemek için etkin değildir.

XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:

- Proje `GenerateDocumentationFile` `<PropertyGroup>` `.fsproj` dosyanızın bölümüne, derleme ile aynı kök dosya ADıNA sahip bir XML dosyası üreten bir öğe ekleyebilirsiniz. Örneğin:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin. Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin. Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.

XML belge açıklamalarını yazmanın iki yolu vardır: XML etiketleriyle ve olmadan. Her ikisi de Üçlü eğik çizgi açıklamaları kullanır.

## <a name="comments-without-xml-tags"></a>XML etiketleri olmayan Yorumlar

Bir `///` yorum ile başlamadıysanız, `<` tüm açıklama metni hemen izleyen kod yapısına ait Özet belgeler olarak alınır. Her yapı için yalnızca kısa bir özet yazmak istediğinizde bu yöntemi kullanın.

Yorum, belge hazırlığı sırasında XML olarak kodlanır, bu nedenle ve gibi karakterlerin kaçış olmaması `<` `>` `&` gerekir. Açıkça bir Özet etiketi belirtmezseniz, **param** veya etiket **döndüren** Etiketler gibi başka Etiketler belirtmemelisiniz.

Aşağıdaki örnek, XML etiketleri olmadan alternatif yöntemi gösterir. Bu örnekte, açıklama içindeki metnin tamamı bir Özet olarak değerlendirilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a>XML etiketleriyle ilgili açıklamalar

Bir yorum gövdesi ile başlıyorsa `<` (normalde `<summary>` ) XML ETIKETLERI kullanılarak XML biçimli bir açıklama gövdesi olarak kabul edilir. Bu ikincisi, kısa bir Özet, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumlar için belgeler ve dönüş değerinin bir açıklaması için ayrı notlar belirlemenizi sağlar.

Aşağıda, bir imza dosyasındaki tipik bir XML belgesi yorumu verilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a>Önerilen Etiketler

XML etiketleri kullanıyorsanız, aşağıdaki tabloda F # XML kod açıklamalarında tanınan dış Etiketler açıklanmaktadır.

| Etiket sözdizimi                                  | Description |
|---------------------------------------------|-----------|
| `<summary>`**_metinleri_**`</summary>`           | *Metnin* program öğesinin kısa bir açıklaması olduğunu belirtir. Açıklama genellikle bir veya iki cümle olur.|
| `<remarks>`**_metinleri_**`</remarks>`           | *Metnin* program öğesiyle ilgili ek bilgileri içerdiğini belirtir.|
| `<param name="`**_ad_** `">` ** _Açıklama_**`</param>` | Bir işlev veya yöntem parametresi için ad ve açıklama belirtir.|
| `<typeparam name="`**_ad_** `">` ** _Açıklama_**`</typeparam>` | Bir tür parametresi için ad ve açıklama belirtir.|
| `<returns>`**_metinleri_**`</returns>`           | *Metnin* bir işlevin veya yöntemin dönüş değerini açıklamakta olduğunu belirtir.|
| `<exception cref="`**_tür_** `">` ** _Açıklama_**`</exception>` |Üretilene özel durum türünü ve bunun altında oluşturulduğu koşulları belirtir.|
| `<seealso cref="`**_başvurunun_**`"/>`      | Ayrıca bkz. başka bir tür için belgelere bağlantı bağlantısı. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. Ayrıca bkz. bağlantılar genellikle belge sayfasının alt kısmında görünür.|

Aşağıdaki tabloda, açıklama bölümlerinin içinde kullanım için Etiketler açıklanmaktadır:

| Etiket sözdizimi                                | Description |
|-------------------------------------------|-------------|
| `<para>`**_metinleri_**`</para>`               | Metnin paragrafını belirtir. Bu, **açıklamalar** etiketinin içindeki metni ayırmak için kullanılır.|
| `<code>`**_metinleri_**`</code>`               | *Metnin* birden çok kod satırı olduğunu belirtir. Bu etiket, kod için uygun bir yazı tipinde metin göstermek üzere belge üreticileri tarafından kullanılabilir.|
| `<paramref name="`**_ada_**`"/>`         | Aynı belge açıklamasında bir parametreye bir başvuru belirtir.|
| `<typeparamref name="`**_ada_**`"/>`     | Aynı belge açıklamasında bir tür parametresine bir başvuru belirtir.|
| `<c>`**_metinleri_**`</c>`                     | *Metnin* satır içi kod olduğunu belirtir. Bu etiket, kod için uygun bir yazı tipinde metin göstermek üzere belge üreticileri tarafından kullanılabilir.|
| `<see cref="`**_başvuru_** `">` ** _metin_**`</see>` | Başka bir program öğesinin satır içi bağlantısını belirtir. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. *Metin* , bağlantıda gösterilen metindir.|

### <a name="user-defined-tags"></a>Kullanıcı tanımlı Etiketler

Önceki Etiketler, F # derleyicisi ve tipik F # düzenleyici araçları tarafından tanınan olanları temsil eder. Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.
Fsdocs gibi araçlar, gibi ek Etiketler için destek getirir [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) .
Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.

## <a name="compile-time-checking"></a>Derleme zamanı denetimi

`--warnon:3390`Etkinleştirildiğinde, DERLEYICI XML sözdizimini ve içindeki ve etiketlerinde başvurulan parametreleri doğrular `<param>` `<paramref>` .

## <a name="documenting-f-constructs"></a>F # yapılarını belgeleme

Modüller, Üyeler, birleşim durumları ve kayıt alanları gibi F # yapıları, `///` bildirimlerinden hemen önce bir yorum tarafından belgelenmiştir.
Gerekirse, `///` bağımsız değişken listesinden önce bir yorum vererek sınıfların örtük oluşturucuları belgelenmiştir. Örneğin:

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a>Sınırlamalar

C# ve diğer .NET dillerinde XML belgelerinin bazı özellikleri C# ' de desteklenmez.

- F # ' da, çapraz başvuruların karşılık gelen sembolün tam XML imzasını kullanması gerekir, örneğin `cref="T:System.Console"` .
  Gibi basit C# stili çapraz başvurular `cref="Console"` ayrıntılı, tam XML imzalarına değildir ve bu öğeler F # derleyicisi tarafından denetlenmez. Bazı belge araçları, sonraki işleme bu çapraz başvuruların kullanılmasına izin verebilir, ancak tam imzaların kullanılması gerekir.
  
- Etiketler `<include>` , `<inheritdoc>` F # derleyicisi tarafından desteklenmez. Kullanıldıklarında hata verilmez, ancak oluşturulan belgeleri etkilemeden yalnızca oluşturulan belgeler dosyasına kopyalanırlar.

- Kullanıldığında bile, çapraz başvurular F # derleyicisi tarafından denetlenmez `-warnon:3390` .

- , Kullanıldığında bile, etiketlerinde kullanılan `<typeparam>` ve `<typeparamref>` F # derleyicisi tarafından işaretlenmemiş olan adlar `--warnon:3390` .

- Kullanıldığı zaman bile belgeler eksikse hiçbir uyarı verilmez `--warnon:3390` .

## <a name="recommendations"></a>Öneriler

Kodu belgeleme pek çok nedenden dolayı önerilir. Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve F # kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.

- `--warnon:3390`XML belgelerinin GEÇERLI XML olduğundan emin olmak için kodunuzda seçeneğini etkinleştirin.

- Uygulamanızdaki uzun XML belge açıklamalarını ayırmak için imza dosyaları eklemeyi düşünün.

- Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır. Bunu yapmanız gerekiyorsa, bunu yapın.

- En azından, modüller, türler ve üyeleri düz bir `///` yoruma veya etikete sahip olmalıdır `<summary>` . Bu, F # Editing araçlarında otomatik tamamlama araç ipucu penceresinde gösterilir.

- Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# XML belge açıklamaları &#40;C&#35; programlama kılavuzu&#41;](../../csharp/programming-guide/xmldoc/index.md).
- [F # dil başvurusu](index.md)
- [Derleyici seçenekleri](compiler-options.md)
