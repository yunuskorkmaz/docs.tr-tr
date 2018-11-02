---
title: Başvuru Hücreleri (F#)
description: 'F # başvuru hücreleri başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak tanıyan depolama konumları nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44192284"
---
# <a name="reference-cells"></a>Başvuru Hücreleri

*Başvuru hücreleri* , başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak sağlayan depolama yerleridir.

## <a name="syntax"></a>Sözdizimi

```fsharp
ref expression
```

## <a name="remarks"></a>Açıklamalar

Kullandığınız `ref` değeri kapsülleyen yeni bir başvuru hücresi oluşturmak için bir değer önce işleci. Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.

Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir. Kullanarak bir başvuru hücresi oluşturduğunuzda `ref` işleci, kapsüllenmiş bir değişmez değer olarak temeldeki değerin bir kopyasını oluşturun.

Kullanarak bir başvuru hücresi başvuru `!` (bang) işlecini.

Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Çıktı `50`.

Başvuru hücreleri örnekleridir `Ref` genel kayıt türü, şu şekilde bildirilir.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Türü `'a ref` eşanlamlıdır `Ref<'a>`. Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.

`ref` İşleci yeni bir başvuru hücresi oluşturur. Aşağıdaki kod bildirimidir `ref` işleci.

```fsharp
let ref x = { contents = x }
```

Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.

|İşleç, üye veya alan|Açıklama|Tür|Tanım|
|--------------------------|-----------|----|----------|
|`!` (başvuru işleci)|Temeldeki değeri döndürür.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (atama işleci)|Temeldeki değeri değiştirir.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (işleç)|Yeni bir başvuru hücresine bir değer kapsüller.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (özelliği)|Temeldeki değeri alır veya ayarlar.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (kayıt alanı)|Temeldeki değeri alır veya ayarlar.|`'a`|`let ref x = { contents = x }`|
Temeldeki değere erişmek için çeşitli yollar vardır. Başvuru işleci tarafından döndürülen değer (`!`) atanabilir bir değer değil. Bu nedenle, temeldeki değeri değiştiriyorsanız, atama işlecini kullanmanız gerekir (`:=`) bunun yerine.

Her iki `Value` özelliği ve `contents` alanı atanabilir değerlerdir. Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Çıktı aşağıdaki gibidir:

```
10
10
11
12
```

Alan `contents` diğer ML sürümleriyle uyumluluk için sağlanır ve derleme sırasında bir uyarı üretecektir. Uyarı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).

C# programcıları, bilmeniz `ref` C# ile aynı şeydir değil `ref` F #. F #'de eşdeğer bir yapıdır [zkratka](byrefs.md), başvuru hücrelerinin'dan farklı bir kavram olan.

Değerleri olarak işaretlenmiş `mutable`için otomatik olarak yükseltilebilir `'a ref` kapanım; tarafından yakalanan olup [değerleri](values/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)
- [Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)
- [Değerler](values/index.md)
