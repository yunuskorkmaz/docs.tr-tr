---
title: Girdi Noktası (F#)
description: 'Giriş noktası yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir F # programına öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 42e5fe7f85285f990ef92e9791ed5bdfacb85059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="entry-point"></a>Girdi Noktası

Bu konuda bir F # programı için giriş noktası ayarlamak için kullandığınız yöntem açıklanmaktadır.


## <a name="syntax"></a>Sözdizimi

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde *olanak sağlayan işlev bağlama* bir işlev tanımı bir `let` bağlama.

Yürütülebilir bir dosyanın yürütme resmi olarak başladığı olarak derlenmiş bir program için giriş noktası. Uygulayarak bir F # uygulama giriş noktasını belirtmek `EntryPoint` özniteliği programın `main` işlevi. Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenmiş dosyasındaki son işlevi olması gerekir. Son derlenmiş projesinde son dosya veya komut satırı geçirilen son dosya dosyasıdır.

Giriş noktası işlevi türüne sahip `string array -> int`. Komut satırında sağlanan bağımsız değişkenler geçirilecek `main` işlevinde bir dizeler dizisi. Dizinin ilk öğesi ilk bağımsız değişkeni olan; diğer bazı dillerde olduğu gibi yürütülebilir dosyanın adını dizisinde dahil edilmez. Dönüş değeri çıkış kodu işlemi için kullanılır. Sıfır genellikle başarılı olduğunu gösterir; sıfır olmayan değerler bir hata gösterir. Belirli bir anlamı, sıfır olmayan dönüş kodları için hiçbir kuralı yoktur; dönüş kodları anlamları uygulamaya özgü.

Aşağıdaki örnekte basit bir gösterilmektedir `main` işlevi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Ne zaman bu kodu yürütüldüğünde komut satırıyla `EntryPoint.exe 1 2 3`, çıktı aşağıdaki gibidir.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Örtük giriş noktası
Bir program yok olduğunda **EntryPoint** derlenecek son dosyanın üst düzey bağlamaları giriş noktası açıkça belirten özniteliği giriş noktası olarak kullanılır.


## <a name="see-also"></a>Ayrıca Bkz.
[İşlevler](index.md)

[let Bağlamaları](let-bindings.md)
