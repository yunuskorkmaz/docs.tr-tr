---
title: Başvuru Hücreleri (F#)
description: 'F # başvuru hücreleri başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak tanıyan depolama konumları nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892433"
---
# <a name="reference-cells"></a>Başvuru Hücreleri

*Başvuru hücreleri* , başvuru semantiğiyle değişebilir değerler oluşturmanıza olanak sağlayan depolama yerleridir.

## <a name="syntax"></a>Sözdizimi

```fsharp
ref expression
```

## <a name="remarks"></a>Açıklamalar

Kullandığınız `ref` değeri kapsülleyen yeni bir başvuru hücresi oluşturmak için bir değer önce işleci. Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.

Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir. Kullanarak bir başvuru hücresi oluşturduğunuzda `ref` işleci, kapsüllenmiş bir değişmez değer olarak temeldeki değerin bir kopyasını oluşturun.

Kullanarak bir başvuru hücresi başvuru `!` (bang) işlecini.

Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Çıktı `50`.

Başvuru hücreleri örnekleridir `Ref` genel kayıt türü, şu şekilde bildirilir.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Türü `'a ref` eşanlamlıdır `Ref<'a>`. Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.

`ref` İşleci yeni bir başvuru hücresi oluşturur. Aşağıdaki kod bildirimidir `ref` işleci.

```fsharp
let ref x = { contents = x }
```

Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.

|İşleç, üye veya alan|Açıklama|Tür|Tanım|
|--------------------------|-----------|----|----------|
|`!` (başvuru işleci)|Temeldeki değeri döndürür.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (atama işleci)|Temeldeki değeri değiştirir.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (işleç)|Yeni bir başvuru hücresine bir değer kapsüller.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (özelliği)|Temeldeki değeri alır veya ayarlar.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (kayıt alanı)|Temeldeki değeri alır veya ayarlar.|`'a`|`let ref x = { contents = x }`|
Temeldeki değere erişmek için çeşitli yollar vardır. Başvuru işleci tarafından döndürülen değer (`!`) atanabilir bir değer değil. Bu nedenle, temeldeki değeri değiştiriyorsanız, atama işlecini kullanmanız gerekir (`:=`) bunun yerine.

Her iki `Value` özelliği ve `contents` alanı atanabilir değerlerdir. Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Çıktı aşağıdaki gibidir:

```
10
10
11
12
```

Alan `contents` diğer ML sürümleriyle uyumluluk için sağlanır ve derleme sırasında bir uyarı üretecektir. Uyarı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).

Aşağıdaki kod, başvuru hücrelerinin parametre geçişlerinde kullanımını örneklendirmektedir. Byref parametre türü içeren bir parametre alan artışı yöntemi Incrementor türü vardır. Byref parametre türü, Arayanların bir başvuru hücresini veya belirtilen türün tipik değişkenin adresini bu büyük bir tamsayı geçmesi gerektiğini gösterir Geri kalan kod artırma hem de bu tür bağımsız değişkenleri ile çağırmak nasıl gösterir ve (ref myDelta1) başvuru hücresini oluşturmak için bir değişken başvuru işleci kullanımını gösterir. Ardından adres işlecini kullanımını gösterir (&amp;) uygun bir bağımsız değişken oluşturmak için. Son olarak, Increment yöntemi yeniden let bağlama kullanılarak bildirilen bir başvuru hücresi kullanılarak çağrılır. Son kod satırının kullanımını gösteren! yazdırma için başvuru hücresine başvuran işleci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Başvuruya göre hakkında daha fazla bilgi için bkz. [parametreler ve bağımsız değişkenler](parameters-and-arguments.md).

>[!NOTE]
C# programcıları, C# dilinde sağladığından, başvuru farklı F #'de çalışır bilmeniz gerekir. C# içinde çalıştığı gibi örneğin, bir bağımsız değişken geçirdiğinizde ref kullanımını aynı etkiyi F #'ta yok.

>[!NOTE]
`mutable` değişkenleri otomatik olarak yükseltilerek için `'a ref` kapanım; tarafından yakalanan olup [değerleri](values/index.md).

## <a name="consuming-c-ref-returns"></a>C# tüketme `ref` döndürür

F # 4.1 ile başlayarak, raporlarını kullanabilirsiniz `ref` oluşturulan C# dilinde döndürür.  Böyle bir çağrının sonucu bir `byref<_>` işaretçi.

Aşağıdaki C# yöntemi:

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

Şeffaf bir şekilde F # tarafından hiçbir özel sözdizimi ile çağrılabilir:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Ayrıca sürebilir işlevleri bildirebilirsiniz bir `ref` giriş olarak örneğin döndürür:

```fsharp
let f (x: byref<int>) = &x
```

Şu anda oluşturma olanağı, bir `ref` dönüş F #'de, C# ' de kullanılabilecek.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)
- [Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)
- [Değerler](values/index.md)
