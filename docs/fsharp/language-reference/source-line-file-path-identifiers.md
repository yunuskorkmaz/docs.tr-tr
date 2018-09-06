---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları (F#)
description: 'Kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik F # tanımlayıcı değerlerini kullanma konusunda bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777435"
---
# <a name="source-line-file-and-path-identifiers"></a>Kaynak Satırı, Dosya ve Yol Tanımlayıcıları

Tanımlayıcıları `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__` kodunuzda kaynak satırı numarasını, dizin ve dosya adına erişmenize olanak tanıyan yerleşik değerler.

## <a name="syntax"></a>Sözdizimi

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Açıklamalar

Bu değerlerin her birini türünde `string`.

Aşağıdaki tabloda özetlenmiştir: kaynak satırı, dosya ve yol tanımlayıcıları, F #'ta da kullanılabilir. Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar, derleyici tarafından tanınan yerleşik değerlerdir.

|Önceden tanımlanmış tanımlayıcısı|Açıklama|
|---------------------|-----------|
|`__LINE__`|Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_DIRECTORY__`|Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_FILE__`|Geçerli kaynak dosya adını ve yolunu da değerlendirir dikkate `#line` yönergeleri.|
Hakkında daha fazla bilgi için `#line` yönergesine bakın [derleyici yönergeleri](compiler-directives.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bu değerlerin kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Çıktı:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleyici Yönergeleri](compiler-directives.md)
- [F# Dili Başvurusu](index.md)
