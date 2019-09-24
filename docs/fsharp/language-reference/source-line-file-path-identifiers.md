---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları
description: Kodunuzda kaynak satır numarası, dizin ve F# dosya adına erişmenizi sağlayan yerleşik tanımlayıcı değerlerini nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216752"
---
# <a name="source-line-file-and-path-identifiers"></a>Kaynak Satırı, Dosya ve Yol Tanımlayıcıları

`__LINE__`, Vekodunuzda`__SOURCE_FILE__` kaynak satır numarası, dizin ve dosya adına erişmenizi sağlayan yerleşik değerlerdir. `__SOURCE_DIRECTORY__`

## <a name="syntax"></a>Sözdizimi

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Açıklamalar

Bu değerlerin her birinin türü `string`vardır.

Aşağıdaki tabloda, ' de F#bulunan kaynak satırı, dosya ve yol tanımlayıcıları özetlenmektedir. Bu tanımlayıcılar Önişlemci makroları değildir; derleyici tarafından tanınan yerleşik değerlerdir.

|Önceden tanımlanmış tanımlayıcı|Açıklama|
|---------------------|-----------|
|`__LINE__`|, Yönergeleri dikkate alarak `#line` geçerli satır numarasını değerlendirir.|
|`__SOURCE_DIRECTORY__`|Kaynak dizinin geçerli tam yolu olarak değerlendirilir ve yönergeleri göz önünde `#line` bulundurur.|
|`__SOURCE_FILE__`|Yolu ve yönergeleri dikkate `#line` almadan geçerli kaynak dosya adı olarak değerlendirilir.|

`#line` Yönergesi hakkında daha fazla bilgi için bkz. [derleyici yönergeleri](compiler-directives.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bu değerlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Çıktı:

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleyici Yönergeleri](compiler-directives.md)
- [F# Dili Başvurusu](index.md)
