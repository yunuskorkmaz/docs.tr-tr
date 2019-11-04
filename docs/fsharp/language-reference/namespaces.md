---
title: Ad Alanları
description: Bir F# ad alanı, bir program öğeleri gruplandırmasına bir ad iliştirerek, ilgili işlevlerin bölümlerine kod düzenlemenize nasıl olanak sağladığını öğrenin.
ms.date: 12/08/2018
ms.openlocfilehash: a55da1592b04c64576b4c66de61b5ca137289a6f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425040"
---
# <a name="namespaces"></a>Ad Alanları

Bir ad alanı, F# program öğeleri gruplandırmasına bir ad iliştirmenizi sağlayarak kodu ilgili işlevlerin alanlarıyla düzenlemenizi sağlar. Ad alanları genellikle F# dosyalardaki en üst düzey öğelerdir.

## <a name="syntax"></a>Sözdizimi

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Açıklamalar

Bir ad alanına kod koymak istiyorsanız, dosyadaki ilk bildirim ad alanını bildirmelidir. Dosyanın tamamı daha sonra başka bir ad alanı bildirimi mevcut olmadığından, bu dosyanın içeriği ad alanının bir parçası haline gelir. Bu durumda, sonraki ad alanı bildirimi ilk ad alanı içinde olduğu Düşünülene kadar tüm kod yukarı.

Ad alanları doğrudan değer ve işlevleri içeremez. Bunun yerine, değerler ve işlevler modüllerde yer almalıdır ve modüller ad alanlarına dahil edilir. Ad alanlarında türler, modüller bulunabilir.

XML belge açıklamaları bir ad alanı üzerinde bildirilemez, ancak bunlar yok sayılır. Derleyici yönergeleri Ayrıca bir ad alanı üzerinde de belirtilebilir.

Ad alanları, ad alanı anahtar sözcüğüyle açıkça veya bir modül bildirilirken örtük olarak bildirilemez. Bir ad alanını açıkça bildirmek için, ad alanı adını izleyen namespace anahtar sözcüğünü kullanın. Aşağıdaki örnek, bir ad alanı `Widgets` bildiren bir kod dosyası ve bu ad alanına dahil olan bir modüldür.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Dosyanın tüm içeriği bir modülde ise, `module` anahtar sözcüğünü kullanarak ve tam modül adında yeni ad alanı adını sağlayarak ad alanlarını örtülü olarak da bildirebilirsiniz. Aşağıdaki örnek, bir işlevi içeren bir ad alanı `Widgets` ve bir modül `WidgetsModule`bildiren bir kod dosyası gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Aşağıdaki kod, önceki koda eşdeğerdir, ancak modül yerel bir modül bildirimidir. Bu durumda, ad alanı kendi satırında görünmelidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

Aynı dosyada bir veya daha fazla ad alanında birden fazla modül gerekliyse, yerel modül bildirimleri kullanmanız gerekir. Yerel modül bildirimleri kullandığınızda, modül bildirimlerinde nitelikli ad alanını kullanamazsınız. Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimi olan bir dosyayı gösterir. Bu durumda, modüller doğrudan ad alanında yer alır; dosya ile aynı ada sahip örtük olarak oluşturulmuş bir modül yoktur. Dosyadaki bir `do` bağlama gibi diğer tüm kodlar, ad alanında yer alan, iç modüllerde değil, modül üyesini `widgetFunction` modül adını kullanarak nitelemeniz gerekir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Bu örneğin çıktısı aşağıdaki gibidir.

```fsharp
Module1 10 20
Module2 5 6
```

Daha fazla bilgi için bkz. [modüller](modules.md).

## <a name="nested-namespaces"></a>İç içe geçmiş ad alanları

İç içe bir ad alanı oluşturduğunuzda, tam olarak nitelemeniz gerekir. Aksi takdirde, yeni bir üst düzey ad alanı oluşturursunuz. Ad alanı bildirimlerinde girintileme yok sayılır.

Aşağıdaki örnek, iç içe bir ad alanının nasıl bildirilemeyeceğini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Dosyalarda ve derlemelerde ad alanları

Ad alanları, tek bir projede veya derlemede birden çok dosyayı kapsayabilir. *Ad alanı parçası* , bir dosyada bulunan bir ad alanının parçasını açıklar. Ad alanları birden fazla derlemeye de yayılabilir. Örneğin, `System` ad uzayı birçok derlemeyi kapsayan ve birçok iç içe ad alanı içeren tüm .NET Framework içerir.

## <a name="global-namespace"></a>Genel ad alanı

.NET en üst düzey ad alanına ad koymak için `global` önceden tanımlanmış ad alanını kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Ayrıca, üst düzey .NET ad alanına başvurmak için genel ' i de kullanabilirsiniz. Örneğin, diğer ad alanları ile ad çakışmalarını çözmek için.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Özyinelemeli ad alanları

Ayrıca, içerilen tüm kodun birbirini karşılıklı olarak özyinelemeli olmasını sağlamak için ad alanları özyinelemeli olarak da bildirilemez.  Bu, `namespace rec`aracılığıyla yapılır. `namespace rec` kullanımı, bazı paıns 'leri türler ve modüller arasında karşılıklı başvuru kodu yazamayacak şekilde giderebiliyor. Aşağıda buna bir örnek verilmiştir:

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

Özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` her ikisi de birbirine başvurmadığını unutmayın.  Ayrıca, modül `BananaHelpers` ve sınıf `Banana` aynı zamanda birbirini da ifade eder. Bu, `MutualReferences` ad alanından `rec` anahtar F# sözcüğünü kaldırdıysanız, içinde ifade etmeniz mümkün değildir.

Bu özellik, üst düzey [modüller](modules.md)için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Modüller](modules.md)
- [F#RFC FS-1009-dosyalar içindeki daha büyük kapsamlar üzerinde karşılıklı başvuru türleri ve modülleri sağlar](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
