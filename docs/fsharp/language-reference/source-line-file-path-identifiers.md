---
title: "Kaynak Satırı, Dosya ve Yol Tanımlayıcıları (F#)"
description: "Kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik F # tanımlayıcı değerlerini kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a>Kaynak Satırı, Dosya ve Yol Tanımlayıcıları

Tanımlayıcılar `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__` kaynağı satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik değerlerdir.


## <a name="syntax"></a>Sözdizimi

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Açıklamalar
Bu değerlerin her birini türüne sahip `string`.

Kaynak satırı, dosya ve F #'da kullanılabilir yol tanımlayıcıları aşağıdaki tabloda özetlenmiştir. Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar derleyici tarafından tanınan yerleşik değerlerdir.

|Önceden tanımlanmış tanımlayıcısı|Açıklama|
|---------------------|-----------|
|`__LINE__`|Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_DIRECTORY__`|Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_FILE__`|Geçerli kaynak dosya adını ve yolunu değerlendirir dikkate `#line` yönergeleri.|
Hakkında daha fazla bilgi için `#line` yönerge, bkz: [derleyici yönergeleri](compiler-directives.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bu değerleri kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Çıktı:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Ayrıca Bkz.
[Derleyici yönergeleri](compiler-directives.md)

[F # dili başvurusu](index.md)
