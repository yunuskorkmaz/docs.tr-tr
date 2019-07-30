---
title: Modüller
description: Bir F# modülün bir F# F# programdaki değerler, türler ve işlev değerleri gibi bir kod gruplandırması olduğunu öğrenin.
ms.date: 04/24/2017
ms.openlocfilehash: 685ab638e7e1b6c8d47d1a316483abcc18e40199
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627431"
---
# <a name="modules"></a>Modüller

Dil bağlamında *Modül* , bir F# programdaki değerler, türler ve işlev değerleri gibi F# bir kod gruplandırmasıdır. F# Modüllerde kod gruplandırma, ilgili kodu birlikte tutmaya yardımcı olur ve programınızda ad çakışmalarını önlemeye yardımcı olur.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Açıklamalar

F# Modül; türler, değerler, F# işlev değerleri ve bağlamalardaki `do` kod gibi kod yapılarının bir gruplandırmasıdır. Yalnızca statik üyelere sahip ortak dil çalışma zamanı (CLR) sınıfı olarak uygulanır. Tüm dosyanın modüle dahil edilip edilmeyeceğini bağlı olarak iki tür modül bildirimi vardır: en üst düzey modül bildirimi ve yerel bir modül bildirimi. Üst düzey modül bildirimi, modülün tüm dosyasını içerir. En üst düzey modül bildirimi, yalnızca bir dosyadaki ilk bildirim olarak görünebilir.

Üst düzey modül bildiriminin sözdiziminde, isteğe bağlı *nitelikli ad alanı* , modülünü içeren iç içe ad alanı adlarının sırasıdır. Nitelenmiş ad alanının önceden bildirilmesine izin yoktur.

Üst düzey modüldeki bildirimleri girintilemek zorunda değilsiniz. Yerel modüllerdeki tüm bildirimlerin girintisini almanız gerekir. Yerel bir modül bildiriminde, yalnızca söz konusu modül bildiriminde girintili olan bildirimler modülün bir parçasıdır.

Bir kod dosyası en üst düzey modül bildirimiyle veya bir ad alanı bildirimiyle başlamamışsa, tüm yerel modüller dahil olmak üzere dosyanın tüm içerikleri, uzantısı olmadan dosya ile aynı ada sahip örtük olarak oluşturulmuş bir üst düzey modülün bir parçası haline gelir. ilk harfle büyük harfe dönüştürülür. Örneğin, aşağıdaki dosyayı göz önünde bulundurun.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Bu dosya bu şekilde yazılmış gibi derlenir:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Bir dosyada birden çok modülünüz varsa, her modül için yerel bir modül bildirimi kullanmanız gerekir. Kapsayan bir ad alanı bildirilirse, bu modüller kapsayan ad alanının bir parçasıdır. Kapsayan bir ad alanı bildirilmemiş ise, modüller örtük olarak oluşturulan en üst düzey modülün bir parçası haline gelir. Aşağıdaki kod örneği, birden çok modül içeren bir kod dosyası gösterir. Derleyici örtük olarak adlı `Multiplemodules` `MyModule1` `MyModule2` bir üst düzey modül oluşturur ve bu üst düzey modülde iç içe geçmiş.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Bir projede veya tek bir derlemede birden çok dosya varsa veya bir kitaplık oluşturuyorsanız, dosyanın üst kısmına bir ad alanı bildirimi veya modül bildirimi eklemeniz gerekir. F# Derleyici yalnızca bir proje veya derleme komut satırında yalnızca bir dosya olduğunda ve bir uygulama oluşturuyorsanız bir modül adını örtülü olarak belirler.

*Erişilebilirlik-değiştirici* aşağıdakilerden biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için bkz. [Access Control](access-control.md). Varsayılan değer geneldir.

## <a name="referencing-code-in-modules"></a>Modüllerde koda başvurma

Başka bir modülden işlevlere, türlere ve değerlere başvuru yaptığınızda tam adı kullanmanız veya modülünü açmanız gerekir. Nitelikli bir ad kullanırsanız, istediğiniz program öğesi için ad alanlarını, modülü ve tanımlayıcıyı belirtmeniz gerekir. Tam yolun her bölümünü aşağıdaki gibi bir nokta (.) ile ayırın.

`Namespace1.Namespace2.ModuleName.Identifier`

Kodu basitleştirmek için modülü veya bir veya daha fazla ad alanını açabilirsiniz. Ad alanlarını ve modülleri açma hakkında daha fazla bilgi için [bkz. içeri aktarma bildirimleri: `open` Anahtar sözcüğü](import-declarations-the-open-keyword.md).

Aşağıdaki kod örneğinde, dosyanın sonuna kadar olan tüm kodu içeren bir üst düzey modül gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Aynı projedeki başka bir dosyadan bu kodu kullanmak için, aşağıdaki örneklerde gösterildiği gibi, işlevleri kullanmadan önce nitelikli adları kullanırsınız veya modülü açarsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>İç içe modüller

Modüller iç içe olabilir. İç modüller, yeni modüller değil, iç modüller olduğunu göstermek için dış modül bildirimlerinin en çok olarak girintilenmelidir. Örneğin, aşağıdaki iki örneği karşılaştırın. Modül `Z` , aşağıdaki kodda yer aldığı bir iç modüldür.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Ancak modül `Z` aşağıdaki kodda bir eşdüzey modüldür `Y` .

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
Modül `Z` , modüldeki `Y`diğer bildirimlerde olduğu kadar girintili olmadığından, aşağıdaki kodda bir eşdüzey modüldür.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Son olarak, dış modülün bildirimi yoksa ve daha sonra başka bir modül bildirimi tarafından hemen ardından, yeni modül bildiriminin bir iç modül olduğu varsayılır, ancak ikinci modül tanımı adı.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Uyarıyı ortadan kaldırmak için, iç modülün girintisini artırın.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Bir dosyadaki tüm kodun tek bir dış modülde olmasını ve iç modüller olmasını istiyorsanız, dıştaki modül eşittir işaretine gerek yoktur ve dış modülün içindeki tüm iç modül bildirimleri de dahil olmak üzere, bu bildirimlerin girintileneceği bir girinti olması gerekmez. İç modül bildirimlerinin içindeki bildirimlerin girintili olması gerekir. Aşağıdaki kod bu durumu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Özyinelemeli modüller

F#4,1, içerilen tüm kodların birbirini karşılıklı olarak özyinelemeli olmasını sağlayan modül kavramını sunar.  Bu, aracılığıyla `module rec`yapılır.  Kullanımı, `module rec` ve modülleri arasında karşılıklı başvuru kodu yazamayacak bazı paıns 'leri hafifme edebilir.  Aşağıda buna bir örnek verilmiştir:

```fsharp
module rec RecursiveModule =
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

Özel durumun `DontSqueezeTheBananaException` ve sınıfın `Banana` her ikisi de birbirine başvurmadığını unutmayın.  Ayrıca, modülü `BananaHelpers` ve sınıfı `Banana` birbirini da ifade eder.  `rec` Anahtar F# sözcüğünü`RecursiveModule` modülden kaldırdıysanız, bu, ' ın içinde ifade edilebilir.

Bu özellik [ad alanlarında](namespaces.md) 4,1 ile F# de mümkündür.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Ad Alanları](namespaces.md)
- [F#RFC FS-1009-dosyalar içindeki daha büyük kapsamlar üzerinde karşılıklı başvuru türleri ve modülleri sağlar](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
