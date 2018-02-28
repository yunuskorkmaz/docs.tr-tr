---
title: "Modüller (F#)"
description: "Nasıl bir F # modülün F # kodunda değerler, türleri ve F # programında işlevi değerleri gibi grubudur öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 46de2d18-da51-40fa-a262-92edecada79d
ms.openlocfilehash: 9b189903511f53d3ecceb30f3d056e189b00511d
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="modules"></a>Modüller

F # dili bağlamında bir *Modülü* F # kodunda değerler, türleri ve F # programında işlevi değerleri gibi bir gruplandırmasıdır. Modüllerinde kodu gruplandırma ilgili kod birlikte tutmaya yardımcı olur ve ad çakışmalarını programınızdaki önlemeye yardımcı olur.

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
F # modülün F # kod yapılarını türleri, değerleri, işlev değerlerini ve kodda gibi bir gruplandırmasıdır `do` bağlar. Yalnızca statik üyeleri olan bir ortak dil çalışma zamanı (CLR) sınıfı uygulanır. Modül bildirimleri, dosyanın tamamını modülünde olup olmadığı dahil bağlı olarak iki tür vardır: bir üst düzey modül bildirimi ve bir yerel modül bildirimi. Bir üst düzey modül bildirimi modülünde dosyanın tamamını içerir. Bir üst düzey modül bildirimi yalnızca bir dosya ilk bildirimde olarak yer alabilir.

İsteğe bağlı en üst düzey modülü bildiriminin sözdiziminde *nitelenmiş ad* modülü içeren iç içe geçmiş ad alanı adları sırasıdır. Daha önce bildirilmesi tam ad alanı yok.

Üst düzey bir modül bildirimlerinde girinti gerekmez. Tüm yerel modülleri bildirimlerinde girinti zorunda. Bir yerel modül bildiriminde yalnızca modülü bildirim altında girintili bildirimlerine modülü bir parçasıdır.

Bir kod dosyası bir en üst düzey modül bildiriminde ya da bir ad alanı bildirimi ile başlamıyorsa, herhangi bir yerel modül dahil olmak üzere dosyanın tüm içeriğini uzantısı olmadan dosya aynı ada sahip bir örtük olarak oluşturulmuş en üst düzey modülün parçası haline gelir, ilk harfi büyük harfe dönüştürülmüş. Örneğin, aşağıdaki dosya göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Bu şekilde yazılmışsa gibi bu dosyayı derlenmiş:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Birden fazla modülü bir dosyanız varsa, her modül için bir yerel modül bildirimi kullanmanız gerekir. Kapsayan bir ad alanı bildirilirse, bu modülleri kapsayan ad alanını bir parçasıdır. Kapsayan bir ad alanı bildirilmedi, modüller örtük olarak oluşturulmuş en üst düzey modülü parçası haline gelir. Aşağıdaki kod örneğinde birden fazla modülü içeren bir kod dosyası gösterir. Derleyici örtük olarak adlı en üst düzey bir modül oluşturur `Multiplemodules`, ve `MyModule1` ve `MyModule2` , üst düzey modülü iç içe geçmiş.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Birden çok proje veya tek bir derleme dosyalarınız varsa veya bir kitaplık oluşturuluyorsa, bir ad alanı bildirimini veya modül bildirimi dosyanın üst eklemeniz gerekir. F # Derleyici yalnızca modül adı örtük olarak bir proje veya derleme komut satırında yalnızca bir dosya olduğunda ve bir uygulama oluşturmaya belirler.

*Erişim değiştiricisi* şunlardan biri olabilir: `public`, `private`, `internal`. Daha fazla bilgi için bkz: [erişim denetimi](access-control.md). Ortak varsayılandır.


## <a name="referencing-code-in-modules"></a>Kod modülleri içinde başvurma
Başka bir modülden işlevleri, türleri ve değerleri başvuru yaptığınızda, bir tam ad kullanın veya modülü açmak gerekir. Bir tam ad kullanıyorsanız, ad alanları modülü ve istediğiniz program öğesi için tanımlayıcı belirtmeniz gerekir. Tam yolu her bir parçasını bir nokta (.), aşağıdaki gibi ayırır.

`Namespace1.Namespace2.ModuleName.Identifier`

Modül veya bir veya daha fazla kodu basitleştirmek için ad alanları açabilirsiniz. Açılış ad alanları ve modülleri hakkında daha fazla bilgi için bkz: [içeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md).

Aşağıdaki kod örneğinde dosyasının sonuna kadar olan tüm kodları içeren üst düzey bir modülü gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Bu kodu aynı projede başka bir dosyadan kullanmak için ya da nitelikli adlar kullanın veya İşlevler, kullanmadan önce Modülü aşağıdaki örneklerde gösterildiği gibi açın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>İç içe geçmiş modülleri
Modülleri içe olamaz. İç modülleri iç modülleri, değil yeni modüller olduğunu belirtmek için dış modülü bildirimleri durum girintili gerekir. Örneğin, aşağıdaki iki örnek karşılaştırın. Modül `Z` aşağıdaki kodda iç modülüdür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Ancak Modülü `Z` modülü bir eşdüzeyi olan `Y` aşağıdaki kodda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Modül `Z` modülü diğer bildirimlerinde durum girintili değil de bir eşdüzey Modülü aşağıdaki kodda, çünkü `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Son olarak, dış modülü hiçbir bildirimleri varsa ve başka bir modül bildirimi hemen ardından, yeni modül bildiriminde bir iç modül olarak kabul edilir, ancak derleyici ikinci modül tanım farther daha girintili değil durumunda uyaracak ilk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Uyarı ortadan kaldırmak için iç modül girinti.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Bir dosyanın tek bir dış modülünde olması için tüm kodda istiyorsanız ve iç modülleri istediğiniz dış modülü eşittir işaretinden gerektirmez ve dış modülünde gidecek tüm iç modül bildirimleri de dahil olmak üzere bu bildirimleri girintili gerekmez. Bildirimler iç modül bildirimleri içinde girintili olmak zorunda. Aşağıdaki kod bu durumda gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Özyinelemeli modülleri

F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan modüller kavramını sunmaktadır.  Bu aracılığıyla yapılır `module rec`.  Kullanımı `module rec` türleri ve modülleri arasında karşılıklı başvuru kod yazmaya yazdıramama içinde bazı sorunlar hafifletmek.  Bunun bir örneği verilmiştir:

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

    module private BananaHelpers =
        let peel (b : Banana) =
            let flip banana =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides banana =
                for side in banana.Sides do
                    if side = Unpeeled then
                        side <- Peeled

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

Unutmayın özel `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.  Ayrıca, modül `BananaHelpers` ve sınıf `Banana` de birbirine bakın.  Bu kaldırdıysanız F # express kurulamaz `rec` anahtar sözcüğünün `RecursiveModule` modülü.

Bu özellik ayrıca mümkündür [ad alanları](namespaces.md) F # 4.1 ile.

## <a name="see-also"></a>Ayrıca Bkz.

[F # dili başvurusu](index.md)
[ad alanları](namespaces.md)
[F # RFC FS-1009 - birbirini başvuru türleri ve modülleri dosyaları büyük kapsamlarında üzerinden izin ver](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
