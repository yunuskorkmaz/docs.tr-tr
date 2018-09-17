---
title: Girdi Noktası (F#)
description: 'Yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir F # programına giriş noktası kurmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 298500931d49c891a7a243295333df3a9f5d413e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698399"
---
# <a name="entry-point"></a>Girdi Noktası

Bu konuda, bir F # programına giriş noktası ayarlamak için kullandığınız yöntemin açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *let işlevi bağlaması* içinde bir işlev tanımı bir `let` bağlama.

Yürütme resmi olarak başladığı bir yürütülebilir dosya olduğu gibi derlenmiş bir programın giriş noktası. Uygulayarak bir F # uygulaması giriş noktası belirtme `EntryPoint` özniteliği programın `main` işlevi. Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenen dosyayı son işlev olmalıdır. Son derlenen son proje dosyasına veya komut satırına geçirilen dosyanın son dosyasıdır.

Giriş noktası işlevini türünde `string array -> int`. Komut satırında sağlanan bağımsız değişkenler geçirilen `main` işlevi bir dize dizisi. Dizinin ilk öğesi olmayan ilk bağımsız değişken; diğer dillerde olduğu gibi yürütülebilir dosyanın adını dizide dahil edilmez. Dönüş değeri çıkış kodu işlemi için kullanılır. Sıfır, genellikle başarılı gösterir; sıfır olmayan değerler, bir hata gösterir. Özel bir anlamı sıfır dönüş kodları için hiçbir kural yoktur; dönüş kodları anlamı, uygulamaya özgü olur.

Aşağıdaki örnekte basit bir `main` işlevi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Ne zaman bu kod yürütüldüğünde komut satırından `EntryPoint.exe 1 2 3`, çıktı aşağıdaki gibidir.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Örtük giriş noktası

Bir program, Hayır olduğunda **EntryPoint** giriş noktası, derlenecek dosyanın son en üst düzey bağlamaları açıkça belirten bir özniteliği, giriş noktası olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [let Bağlamaları](let-bindings.md)
