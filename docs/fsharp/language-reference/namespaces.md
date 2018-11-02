---
title: Ad Alanları (F#)
description: 'F # ad alanı, program öğeleri gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemek nasıl olanak tanıdığını öğrenin.'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178266"
---
# <a name="namespaces"></a>Ad Alanları

Bir ad alanı program öğeleri gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Açıklamalar

Bir ad alanında kod koymak istiyorsanız, ilk bildirimi dosyasındaki ad alanı belirtmesi gerekir. Tüm dosya içeriğini, ardından ad alanı bir parçası haline gelir.

Ad alanları, doğrudan değerleri ve işlevler içeremez. Bunun yerine, değerleri ve işlevleri modüllerde eklenmelidir, ve modülleri ad alanlarında yer alır. Ad alanlarını, türleri, modülleri içerebilir.

Ad alanları açıkça ad alanı anahtar sözcüğüyle veya örtük olarak bir modül bildirirken bildirilebilir. Bir ad alanını açıkça bildirmek için ad alanı adından önce gelen ad alanı anahtar sözcüğünü kullanın. Aşağıdaki örnek, bir ad alanı pencere öğeleri ve o ad alanında bulunan bir modül türü ile bildirir. bir kod dosyası gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Dosyanın tüm içeriğini bir modülde varsa, ayrıca ad alanlarında örtülü olarak kullanarak bildirebilirsiniz `module` anahtar sözcüğü ve tam modül adı yeni ad alanı adı sağlar. Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir. `Widgets` ve modül `WidgetsModule`, bir işlev içerir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Aşağıdaki kod, önceki koda eşdeğerdir, ancak bir yerel modül bildirimi modülüdür. Bu durumda, ad alanı, kendi satırında yer almalıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Aynı dosyada bir veya daha fazla ad alanlarında birden fazla modülü gerekiyorsa, yerel modül bildirimlerinde kullanmanız gerekir. Yerel modül bildirimlerinde kullandığınızda, tam ad alanı, modül bildirimlerinde kullanılamaz. Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimi içeren bir dosya gösterir. Bu durumda, modülleri doğrudan ad alanında bulunan; dosyayla aynı ada sahip hiçbir örtük olarak oluşturulmuş modülü yoktur. Diğer kod dosyasında aşağıdaki gibi bir `do` modülü üye nitelemek gereken bağlama, ad alanında ancak iç modülleri olduğundan `widgetFunction` kullanarak modül adı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Bu örnek çıktısı aşağıdaki gibidir.

```fsharp
Module1 10 20
Module2 5 6
```

Daha fazla bilgi için [modülleri](modules.md).

## <a name="nested-namespaces"></a>İç içe geçmiş ad alanları

Bir iç içe geçmiş ad alanı oluşturduğunuzda, tam olarak nitelemek gerekir. Aksi takdirde, yeni bir üst düzey ad alanı oluşturun. Girinti ad alanı bildirimi göz ardı edilir.

Aşağıdaki örnek, bir iç içe geçmiş ad alanı bildirmek gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Dosyaları ve derlemeleri ad alanları

Ad alanları, birden çok dosyayı tek bir proje veya derleme yayılabilir. Terim *ad alanı parça* bir dosyada bulunan bir ad alanı parçası açıklar. Ad alanları, birden çok bütünleştirilmiş koda da yayılabilir. Örneğin, `System` çoğu derleme yayılan ve çoğu iç içe ad alanlarını içeren tüm .NET Framework, ad alanı içerir.

## <a name="global-namespace"></a>Genel Namespace

Önceden tanımlanmış ad alanını kullanacak `global` adları .NET en üst düzey ad alanında yerleştirmek için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Ayrıca genel kullanabileceğiniz üst düzey .NET ad alanı, örneğin başvurmak için diğer ad alanları ile ad çakışmalarını çözmek için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Özyinelemeli ad alanları

F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan ad alanları kavramını sunar.  Bu aracılığıyla yapılır `namespace rec`.  Kullanım `namespace rec` türler ve modüller arasında karşılıklı başvurusal kod yazmak boyutlandırılmamışsa, bazı sorunlar hafifletmek.  Bunun bir örneği verilmiştir:

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

Unutmayın özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.  Buna ek olarak, modül `BananaHelpers` ve sınıf `Banana` ayrıca birbirine bakın.  Bu F #'ta kaldırdıysanız express mümkün olmazdı `rec` from anahtar sözcüğü `MutualReferences` ad alanı.

Bu özellik için de kullanılabilir olan en üst düzey [modülleri](modules.md) F # 4.1 veya üzeri.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Modüller](modules.md)
- [F # RFC FS-1009 - karşılıklı başvurusal türler ve modüller daha büyük dosyaları kapsamlarda üzerinden izin ver](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
