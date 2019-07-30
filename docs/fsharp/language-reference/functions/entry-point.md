---
title: Girdi Noktası
description: Yürütme resmi 'nin başladığı çalıştırılabilir dosya olarak derlenmiş bir F# programa giriş noktası ayarlamayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630526"
---
# <a name="entry-point"></a>Girdi Noktası

Bu konuda, giriş noktasını bir F# programa ayarlamak için kullandığınız yöntem açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *Let-işlev-bağlama* bir `let` bağlamadaki bir işlevin tanımıdır.

Yürütülebilir dosya olarak derlenen bir programa giriş noktası, yürütmenin resmi olarak başladığı yerdir. F# `EntryPoint` Programın işlevine`main` özniteliğini uygulayarak giriş noktasını bir uygulamaya belirlersiniz. Bu işlev (bir `let` bağlama kullanılarak oluşturulan), son derlenmiş dosyadaki son işlev olmalıdır. Son derlenen dosya, projedeki son dosya veya komut satırına geçirilen son dosyadır.

Giriş noktası işlevinde tür `string array -> int`vardır. Komut satırında verilen bağımsız değişkenler, dizeler dizisindeki `main` işleve geçirilir. Dizinin ilk öğesi ilk bağımsız değişkendir; yürütülebilir dosyanın adı, başka dillerde olduğu gibi diziye dahil değildir. Dönüş değeri, işlem için çıkış kodu olarak kullanılır. Sıfır genellikle başarıyı gösterir; sıfır olmayan değerler bir hatayı gösterir. Sıfır olmayan dönüş kodlarının belirli anlamı için bir kural yoktur; dönüş kodlarının anlamları uygulamaya özgüdür.

Aşağıdaki örnekte basit `main` bir işlev gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

Bu kod komut satırıyla `EntryPoint.exe 1 2 3`yürütüldüğünde, çıkış aşağıdaki gibidir.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Örtük giriş noktası

Bir programın giriş noktasını açıkça belirten bir **entryPoint** özniteliği olmadığında, Derlenecek son dosyadaki en üst düzey bağlamalar giriş noktası olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [let Bağlamaları](let-bindings.md)
