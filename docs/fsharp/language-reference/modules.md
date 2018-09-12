---
title: Modüller (F#)
description: 'Bir F # modül değerleri, türleri ve işlev değerleri olarak F # programında gibi F # kodu, bir gruplandırma nasıl olduğunu öğrenin.'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514361"
---
# <a name="modules"></a>Modüller

F # dili, bağlamında bir *Modülü* F # kodu, değerleri, türleri ve işlev değerleri olarak F # programında gibi bir gruplandırmasıdır. Kod modüllerinde gruplandırma ilgili kod bir arada tutmaya yardımcı olur ve programınızdaki ad çakışmalarını önlemek yardımcı olur.

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

Bir F # modül türleri, değerleri, işlev değerleri ve kodda gibi kod yapıları F # gruplandırmasıdır `do` bağlar. Bu, yalnızca statik üyeleri olan ortak dil çalışma zamanı (CLR) sınıfı uygulanır. Modül bildirimlerinde'olup tüm dosya modülüne dahil edilen bağlı olarak, iki tür vardır: üst düzey modül bildirimi ve bir yerel modül bildirimi. Üst düzey modül bildirimi modülünde dosyanın tamamını içerir. Üst düzey modül bildirimi yalnızca bir dosyadaki ilk bildirimi olarak görünebilir.

İsteğe bağlı üst düzey modül bildirimi için sözdiziminde *nitelenmiş ad* modülü içeren iç içe geçmiş ad alanı adları dizisidir. Daha önce belirtilecek tam ad alanı yok.

Üst düzey bir modül bildirimlerinde Girintile gerekmez. Tüm yerel modülleri bildirimlerinde Girintile gerekir. Bir yerel modül bildirimine yalnızca bu modül bildirimi altında girintili bildirimleri modülü bir parçasıdır.

Bir kod dosyası, bir üst düzey modül bildirimi ya da bir ad alanı bildirimi başlamazsa, yerel modüllerin de dahil olmak üzere dosyanın tüm içeriğini uzantısı olmadan bir dosyayla aynı ada sahip bir örtük olarak oluşturulan üst düzey modülü bir parçası olur, ilk harfi büyük harfe dönüştürülür. Örneğin, aşağıdaki dosya göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Bu dosya bu şekilde yazılmışlar gibi derlenmesi:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Birden çok modül bir dosya varsa, her modül için bir yerel modül bildirimi kullanmanız gerekir. Bir kapsayan ad uzayı bildirirse, bu modülleri kapsayan ad uzayı bir parçasıdır. Modüller, kapsayan bir ad alanında bildirilmedi, örtük olarak oluşturulan üst düzey modülü bir parçası haline gelir. Aşağıdaki kod örneği, birden çok modül içeren bir kod dosyası gösterir. Derleyici örtük olarak adlı en üst düzey bir modül oluşturur `Multiplemodules`, ve `MyModule1` ve `MyModule2` , üst düzey modülü iç içe geçmiş.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Birden çok dosya bir proje veya tek bir derleme varsa veya bir kitaplık oluşturuyorsanız, ad alanı bildirimini veya modül bildirimi dosyasının üst eklemeniz gerekir. F # derleyicisi yalnızca bir modül adı örtük olarak bir proje veya derleme komut satırı yalnızca bir dosya olduğunda ve bir uygulama oluşturuyorsanız belirler.

*Erişilebilirlik değiştiricisi* aşağıdakilerden biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için [erişim denetimi](access-control.md). Genel varsayılandır.

## <a name="referencing-code-in-modules"></a>Kod modüllerinde başvurma

İşlevleri, türleri ve değerleri başka bir modülden başvuruda bulunduğunuzda bir tam adı kullanın veya modül açmak gerekir. Bir tam adı kullanırsanız, ad alanları modülü ve istediğiniz program öğesi için tanımlayıcı belirtmeniz gerekir. Tam yolun her bölümü bir nokta (.), aşağıdaki gibi ayırır.

`Namespace1.Namespace2.ModuleName.Identifier`

Modülün veya bir veya daha fazla ad alanları kodu basitleştirmek için açabilirsiniz. Açılış ad alanları ve modüller hakkında daha fazla bilgi için bkz. [içeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md).

Aşağıdaki kod örneği, dosyanın sonuna kadar tüm kodu içeren bir üst düzey modülü gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Aynı projede başka bir dosyadan bu kodu kullanmak için ya da nitelikli adlar kullanın veya İşlevler, kullanmadan önce modül aşağıdaki örneklerde gösterildiği gibi açın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>İç içe geçmiş modülleri

Modülleri içe olabilir. İç modülleri iç modülleri değil yeni modüller olduğunu belirtmek için dış modül bildirimlerinde sunulan ürünün kendinde girintili gerekir. Örneğin, aşağıdaki iki örnek ile karşılaştırın. Modül `Z` aşağıdaki kodda iç bir modüldür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Ancak Modülü `Z` modülü eşdüzeye olduğu `Y` aşağıdaki kodda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Modül `Z` diğer modül bildirimlerinde sunulan ürünün kendinde girintili değil de bir eşdüzey Modülü aşağıdaki kodda, çünkü `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Son olarak, dış modül yok bildirimler içeriyor ve başka bir modül bildirimi tarafından hemen ardından, yeni modül bildirimi bir iç modül olarak kabul edilir, ancak derleyici ikinci modül tanımı farther daha girintili değil durumunda uyaracak ilk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Uyarıyı ortadan kaldırmak için iç modül girinti.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Tüm kodu dosyasında tek bir dış modülde olmasını istiyorsanız ve iç modülleri istediğiniz dış modül eşittir işareti gerektirmez ve dış modüle gidecek herhangi bir iç modül bildirimlerinde de dahil olmak üzere, bildirimleri girintili gerekmez. Bildirimi içinde iç modül bildirimlerinde girintili olmanız gerekir. Aşağıdaki kod, bu durumda gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Özyinelemeli modülleri

F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu tanıyan modülleri kavramını sunar.  Bu aracılığıyla yapılır `module rec`.  Kullanım `module rec` türler ve modüller arasında karşılıklı başvurusal kod yazmak boyutlandırılmamışsa, bazı sorunlar hafifletmek.  Bunun bir örneği verilmiştir:

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

Unutmayın özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.  Buna ek olarak, modül `BananaHelpers` ve sınıf `Banana` ayrıca birbirine bakın.  Bu F #'ta kaldırdıysanız express mümkün olmazdı `rec` from anahtar sözcüğü `RecursiveModule` modülü.

Bu özellik ayrıca mümkün [ad alanları](namespaces.md) ile F # 4.1.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)  
- [Ad Alanları](namespaces.md)  
- [F # RFC FS-1009 - karşılıklı başvurusal türler ve modüller daha büyük dosyaları kapsamlarda üzerinden izin ver](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
