---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları (F#)
description: 'Kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik F # tanımlayıcı değerlerini kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565223"
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
[Derleyici Yönergeleri](compiler-directives.md)

[F# Dili Başvurusu](index.md)
