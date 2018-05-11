---
title: Ad Alanları (F#)
description: 'F # ad alanı nasıl program öğeleri gruplandırması için bir ad eklemek sağlayarak ilgili işlevselliği alanlarına kodunu düzenlemenizi sağlar öğrenin.'
ms.date: 04/24/2017
ms.openlocfilehash: 151079864f18fff79dac108889b68b3acf1566a1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="namespaces"></a>Ad Alanları

Bir ad alanı, kod ilgili işlevselliği alanlarına program öğeleri gruplandırması için bir ad eklemek sağlayarak düzenlemenizi sağlar.


## <a name="syntax"></a>Sözdizimi

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Açıklamalar
Kod bir ad alanındaki put istiyorsanız, dosyayı ilk bildiriminde ad alanı bildirmeniz gerekir. Tüm dosya içeriğini sonra ad alanının parçası haline gelir.

Ad alanları doğrudan değerleri ve işlevler içeremez. Bunun yerine, değerler ve işlevleri modülleri eklenmelidir ve modülleri ad alanları eklenir. Ad alanları türleri, modüller içerebilir.

Ad alanları açıkça veya ad alanı anahtar sözcüğü ile örtük olarak bir modül bildirirken bildirilebilir. Bir ad alanını açıkça bildirmek için ad alanı adına göre ad alanı anahtar sözcüğünü kullanın. Aşağıdaki örnek, bir ad alanını bir türde ve bu ad alanına dahil bir modül pencere öğeleri bildiren bir kod dosyası gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Dosyanın tüm içeriğini bir modülde varsa, aynı zamanda ad alanları örtük olarak kullanarak bildirebilirsiniz `module` anahtar sözcüğü ve sağlayan yeni ad alanı adı tam modül adı. Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir `Widgets` ve bir modülü `WidgetsModule`, bir işlev içeriyor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Aşağıdaki kod, önceki kod eşdeğerdir, ancak bir yerel modül bildirimi modülüdür. Bu durumda, ad alanı, kendi satırında yer almalıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Bir veya daha fazla ad aynı dosyasında birden fazla modülü gerekirse, yerel modül bildirimleri kullanmanız gerekir. Yerel modül bildirimleri kullandığınızda, tam ad modülü bildirimlerinde kullanamazsınız. Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimleri sahip bir dosyayı gösterir. Bu durumda, modülleri doğrudan ad alanında yer alır; aynı ada sahip dosyayı olarak hiç örtük olarak oluşturulmuş bir modülü vardır. Diğer kod dosyasında gibi bir `do` modülü üye nitelemek gereken bağlama, ad alanı ancak iç modülleri olduğundan `widgetFunction` modül adı kullanarak.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Bu örnek çıktı aşağıdaki gibidir.

```fsharp
Module1 10 20
Module2 5 6
```

Daha fazla bilgi için bkz: [modülleri](modules.md).

## <a name="nested-namespaces"></a>İç içe geçmiş ad alanları
İç içe geçmiş bir ad alanı oluşturduğunuzda, tam olarak nitelemek gerekir. Aksi takdirde, yeni bir üst düzey ad alanı oluşturun. Girinti ad alanı bildirimleri göz ardı edilir.

Aşağıdaki örnek, iç içe geçmiş bir ad alanı bildirimini gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Dosyaları ve derlemeler için ad alanları
Ad alanları projenin ya da derleme birden çok dosya yayılabilir. Terim *ad parçasını* bir dosyada bulunan bir ad alanının parçası açıklar. Ad alanları, birden çok derleme da yayılabilir. Örneğin, `System` ad alanı, çok sayıda derlemeleri yayılan ve pek çok iç içe geçmiş ad alanları içeren tüm .NET Framework, içerir.


## <a name="global-namespace"></a>Genel Namespace
Önceden tanımlanmış ad alanını kullanmak `global` .NET en üst düzey ad alanında adları yerleştirilecek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Ayrıca genel kullanabileceğiniz üst düzey .NET ad alanı, örneğin başvurmak için diğer ad ile ad çakışmalarını çözmek için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Özyinelemeli ad alanları

F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan ad alanları kavramını sunmaktadır.  Bu aracılığıyla yapılır `namespace rec`.  Kullanımı `namespace rec` türleri ve modülleri arasında karşılıklı başvuru kod yazmaya yazdıramama içinde bazı sorunlar hafifletmek.  Bunun bir örneği verilmiştir:

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

Unutmayın özel `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.  Ayrıca, modül `BananaHelpers` ve sınıf `Banana` de birbirine bakın.  Bu kaldırdıysanız F # express kurulamaz `rec` anahtar sözcüğünün `MutualReferences` ad alanı.

Bu özellik ayrıca kullanılabilir en üst düzey [modülleri](modules.md) F # 4.1 veya daha yüksek.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Modüller](modules.md)

[F # RFC FS-1009 - birbirini başvuru türleri ve modülleri dosyaları büyük kapsamlarında üzerinden izin ver](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
