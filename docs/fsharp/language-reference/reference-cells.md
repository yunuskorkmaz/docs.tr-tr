---
title: Başvuru Hücreleri
description: Başvuru semantiğine sahip kesilebilir değerler oluşturmanıza olanak sağlayan depolama konumları olan başvuru hücrelerinin nasıl F# olduğunu öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216773"
---
# <a name="reference-cells"></a>Başvuru Hücreleri

*Başvuru hücreleri* , başvuru semantiğinin değişebilir değerler oluşturmanızı sağlayan depolama konumlarıdır.

## <a name="syntax"></a>Sözdizimi

```fsharp
ref expression
```

## <a name="remarks"></a>Açıklamalar

Değeri kapsülleyen yeni `ref` bir başvuru hücresi oluşturmak için bir değerden önce işlecini kullanırsınız. Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.

Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir. `ref` İşlecini kullanarak bir başvuru hücresi oluşturduğunuzda, temeldeki değerin bir kopyasını kapsüllenmiş kesilebilir değer olarak oluşturursunuz.

`!` (Bankg) işlecini kullanarak bir başvuru hücresine başvurabilirsiniz.

Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Çıktı `50`.

Başvuru hücreleri, aşağıdaki şekilde tanımlanan `Ref` genel kayıt türünün örnekleridir.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Tür `'a ref` için`Ref<'a>`bir eş anlamlı. Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.

`ref` İşleci yeni bir başvuru hücresi oluşturur. Aşağıdaki kod, `ref` işlecinin bildirimidir.

```fsharp
let ref x = { contents = x }
```

Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.

|İşleç, üye veya alan|Açıklama|Tür|Tanım|
|--------------------------|-----------|----|----------|
|`!`(başvuru işleci)|Temeldeki değeri döndürür.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=`(atama işleci)|Temeldeki değeri değiştirir.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref`işlecinde|Yeni bir başvuru hücresine bir değer kapsüller.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value`özelliði|Temeldeki değeri alır veya ayarlar.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents`(kayıt alanı)|Temeldeki değeri alır veya ayarlar.|`'a`|`let ref x = { contents = x }`|

Temeldeki değere erişmek için çeşitli yollar vardır. Başvuru işleci (`!`) tarafından döndürülen değer atanabilir bir değer değil. Bu nedenle, temel alınan değeri değiştiriyorsanız bunun yerine atama işlecini (`:=`) kullanmanız gerekir.

`Value` Hem özelliği `contents` hem de alanı atanabilir değerlerdir. Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Çıktı aşağıdaki gibidir:

```console
10
10
11
12
```

Alan `contents` , diğer ml sürümleriyle uyumluluk için sağlanır ve derleme sırasında bir uyarı oluşturur. Uyarıyı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneğini kullanın. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).

C#programcılar `ref` ' de C# ile aynı şeyi `ref` olmadığını bilmelidir. F# ' Deki F# eşdeğer yapılar, başvuru hücrelerinden farklı bir kavram olan [ByRef referanslardır](byrefs.md).

Olarak `mutable`işaretlenen değerler `'a ref` , bir kapanış tarafından yakalanarak otomatik olarak yükseltilebilir; [değerlere](./values/index.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)
- [Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)
- [Değerler](./values/index.md)
