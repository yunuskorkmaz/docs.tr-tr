---
title: Başvuru Hücreleri (F#)
description: 'F # başvuru hücreleri değişebilir değerleri başvuru semantiği ile oluşturmanıza olanak sağlaması depolama konumları ne olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: d68726619bdfce5a9ed9bd94d6434427644cd9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reference-cells"></a>Başvuru Hücreleri

*Başvuru hücreleri* değişebilir değerleri başvuru semantiği ile oluşturmanıza olanak sağlaması depolama konumlarının.

## <a name="syntax"></a>Sözdizimi

```fsharp
ref expression
```

## <a name="remarks"></a>Açıklamalar
Kullandığınız `ref` değeri yalıtan yeni bir başvuru hücre oluşturmak için işlecinden önce bir değer. Ardından, temeldeki değer değişebilir olduğundan değiştirebilirsiniz.

Başvuru hücresi gerçek bir değer taşır; yalnızca adres değildir. Kullanarak bir başvuru hücresi oluşturduğunuzda `ref` işleci, temel alınan değeri kapsüllenmiş değişmez değer olarak bir kopyasını oluşturun.

Kullanarak bir başvuru hücresine başvurur `!` (performansı) işleci.

Aşağıdaki kod örneği başvuru hücrelerinin bildirim ve kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Çıktı `50`.

Başvuru hücreleri örnekleridir `Ref` gibi bildirilmiş genel kayıt türü.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Türü `'a ref` eşanlamlısı olduğu `Ref<'a>`. Derleyici ve IDE içindeki IntelliSense, bu tür için ilkini görüntüler fakat temeldeki tanım ikincisidir.

`ref` İşleci yeni bir başvuru hücresi oluşturur. Aşağıdaki kodu bildirimi: `ref` işleci.

```fsharp
let ref x = { contents = x }
```

Aşağıdaki tablo başvuru hücresindeki mevcut özellikleri göstermektedir.

|İşleç, üye veya alan|Açıklama|Tür|Tanım|
|--------------------------|-----------|----|----------|
|`!` (işleci başvuru)|Temeldeki değeri döndürür.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (atama işleci)|Temeldeki değeri değiştirir.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (işleç)|Yeni bir başvuru hücresine bir değer kapsüller.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (özellik)|Temeldeki değeri alır veya ayarlar.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (kayıt alanı)|Temeldeki değeri alır veya ayarlar.|`'a`|`let ref x = { contents = x }`|
Temeldeki değere erişmek için çeşitli yollar vardır. Başvuru işleci tarafından döndürülen değer (`!`) atanabilen bir değer değil. Bu nedenle, temeldeki değer değiştiriyorsanız atama işleci kullanmanız gerekir (`:=`) yerine.

Her iki `Value` özelliği ve `contents` alan atanabilir değerleri şunlardır. Bu nedenle, bunları temeldeki değere ulaşmak ya da onu değiştirmek için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Çıktı aşağıdaki gibidir:

```
10
10
11
12
```

Alan `contents` diğer ML sürümleri ile uyumluluk için sağlanır ve derleme sırasında bir uyarı oluşturur. Uyarıyı devre dışı bırakmak için `--mlcompatibility` derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).

Aşağıdaki kod, başvuru hücrelerinin parametre geçişlerinde kullanımını örneklendirmektedir. Artırıcı türü bir yöntem byref parametre türü içeren bir parametre alan artışı sahiptir. Parametre türü byref arayanlar başvuru hücre veya belirtilen türün tipik değişkenin adresini bu büyük tamsayı geçmesi gerektiğini gösterir Kalan kod artırma hem de bu tür bağımsız değişkenleri ile çağırmak nasıl gösterir ve başvuru hücre (ref myDelta1) oluşturmak için bir değişken ref işleci kullanımını gösterir. Address-of işleci kullanımını ardından gösterir (&amp;) uygun bir bağımsız değişken oluşturmak için. Son olarak, Increment yöntemi yeniden let bağlama kullanarak bildirilmiş bir başvuru hücresi kullanılarak çağrılır. Kodu son satırının kullanımını gösteren! yazdırma için başvuru hücresi başvurulacak işleci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](parameters-and-arguments.md).

>[!NOTE]
C# programcıları C# ' ta göründüğünden bu ref farklı F # içinde çalıştığını bilmeniz. C# ' ta aksine Örneğin, bir bağımsız değişken geçirdiğinizde ref kullanımını aynı etkiye F #'ta yok.

## <a name="consuming-c-ref-returns"></a>C# tüketme `ref` döndürür

F # 4.1 ile başlayarak, size tüketebileceği `ref` C# ' de oluşturulan döndürür.  Bu tür bir çağrının sonucu olan bir `byref<_>` işaretçi.

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

Saydam F # kullanarak özel bir sözdizimi ile çağrılabilir:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Ele geçirebilir işlevlerini de bildirebilirsiniz bir `ref` giriş olarak örneğin döndürür:

```fsharp
let f (x: byref<int>) = &x
```

Şu anda oluşturmak için bir yolu yoktur bir `ref` F, C# dilinde kullanılabilecek # dönüş.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)

[Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)
