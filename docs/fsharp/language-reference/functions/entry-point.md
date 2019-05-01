---
title: Girdi Noktası
description: Giriş noktası kümesine öğrenin bir F# yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir program.
ms.date: 05/16/2016
ms.openlocfilehash: 915ab17b9a4fc7fd4d0ae344cb273b1d348a02f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996833"
---
# <a name="entry-point"></a>Girdi Noktası

Bu konu, giriş noktası ayarlamak için kullandığınız yöntemin açıklar bir F# program.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *let işlevi bağlaması* içinde bir işlev tanımı bir `let` bağlama.

Yürütme resmi olarak başladığı bir yürütülebilir dosya olduğu gibi derlenmiş bir programın giriş noktası. Belirttiğiniz giriş noktası bir F# uygulayarak uygulama `EntryPoint` özniteliği programın `main` işlevi. Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenen dosyayı son işlev olmalıdır. Son derlenen son proje dosyasına veya komut satırına geçirilen dosyanın son dosyasıdır.

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