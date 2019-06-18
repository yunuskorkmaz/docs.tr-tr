---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları
description: Yerleşik kullanmayı öğrenin F# kaynağına erişmek etkinleştirdiğiniz tanımlayıcı değerlerini, sayı, dizin ve dosya adı, kodunuzda satır.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152060"
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

Kullanılabilir kaynak satırı, dosya ve yol tanımlayıcıları aşağıdaki tabloda özetlenmiştir F#. Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar, derleyici tarafından tanınan yerleşik değerlerdir.

|Önceden tanımlanmış tanımlayıcısı|Açıklama|
|---------------------|-----------|
|`__LINE__`|Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_DIRECTORY__`|Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.|
|`__SOURCE_FILE__`|Yol olmadan geçerli kaynak dosya adı olarak değerlendirilen dikkate `#line` yönergeleri.|

Hakkında daha fazla bilgi için `#line` yönergesine bakın [derleyici yönergeleri](compiler-directives.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bu değerlerin kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Çıktı:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleyici Yönergeleri](compiler-directives.md)
- [F# Dili Başvurusu](index.md)
