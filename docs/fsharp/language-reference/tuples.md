---
title: Demetler
description: Hakkında bilgi edinin F# tanımlama grubu, farklı türlerde adlandırılmamış ancak sıralı değerleri gruplandırmasıdır.
ms.date: 05/16/2016
ms.openlocfilehash: a1fc31d4dc97c0921545e53b91dcde0547002006
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611054"
---
# <a name="tuples"></a>Demetler

A *demet* farklı türlerde adlandırılmamış ancak sıralı değerleri bir gruplandırmasıdır.  Diziler, başvuru türleri veya yapıları ya da olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Açıklamalar

Her *öğesi* önceki sözdiziminde herhangi bir geçerli olabilir F# ifade.

## <a name="examples"></a>Örnekler

Çiftler, Üçlü ve benzeri, aynı veya farklı tür diziler örnekleridir. Bazı örnekler, aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Tek değer alma

Desen eşleştirme erişmek ve demet öğelerin adlarını atamak için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Ayrıca dışında desen eşleştirme aracılığıyla bir demet ayrıştırma bir `match` ifadesi ile `let` bağlama:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Veya desen giriş olarak işlevleri demetleri eşleşen:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Yalnızca bir demet öğesi gerekiyorsa, joker karakter (alt çizgi), ihtiyacınız olmayan bir değer için yeni bir ad oluşturmaktan kaçınmak için kullanılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Öğeleri bir başvuru tanımlama grubundan bir yapı tanımlama grubu kopyalama ayrıca basittir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

İşlevleri `fst` ve `snd` (başvuru yalnızca başlıkları) ilk geri dönün ve bir dizi öğelerini sırasıyla ikinci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Üçüncü bir Üçlü öğesine döndürür hiçbir yerleşik işlevi yoktur, ancak, kolay bir şekilde yazabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Genellikle, tek bir demet öğelere erişmek için desen eşleştirme kullanmak en iyisidir.

## <a name="using-tuples"></a>Demetlerin kullanılmasını sağlayan

Diziler, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kullanışlı bir yol sağlar. Bu örnek, Tamsayı bölme gerçekleştirir ve işlem olarak bir dizi çifti ilk üyesi ve kalanı çifti ikinci bir üyesi olarak yuvarlatılmış sonucunu döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Normal işlev sözdizimi tarafından örtük işlev bağımsız değişkenlerinin örtülü currying önlemek istediğinizde diziler de işlev bağımsız değişkenleri kullanılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

İşlevi tanımlayan normal söz dizimi `let sum a b = a + b` kısmi uygulama işlevinin ilk bağımsız değişkenin bir işlev aşağıdaki kodda gösterildiği gibi tanımlamanızı sağlar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Parametre olarak bir tanımlama grubu kullanımı currying devre dışı bırakır. Daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevleri](functions/index.md).

## <a name="names-of-tuple-types"></a>Demet türü adları

Bir demet türü adını yazdığınızda, kullandığınız `*` öğeleri ayırmak için kullanılan simge. Oluşan bir demet için bir `int`, `float`ve `string`, gibi `(10, 10.0, "ten")`, türü şu şekilde yazılır.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# demetleri ile birlikte çalışma

C# 7.0 diziler dili kullanıma sunuldu.  ' De tanımlama gruplarına C# birimleridir ve yapı demetleri içinde eşdeğer F#.  C# ile çalışmak ihtiyacınız varsa, yapı demetleri kullanmanız gerekir.

Bunu yapmak kolay bir işlemdir.  Örneğin, C# sınıfı için bir demet geçirin ve ardından bir tanımlama grubu olan sonucunu kullanmak sahip olduğunuz düşünün:

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

İçinde F# kod, bir yapı demet parametre olarak geçiriyoruz ve sonucu bir yapı tanımlama grubu olarak kullanma.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Yapı demetleri başvuru diziler arasında dönüştürme

Başvuru diziler ve yapı demetleri tamamen farklı bir temel alınan gösterimine sahip olduğundan, bunlar örtük olarak dönüştürülebilir değildir.  Kod aşağıdaki gibi diğer bir deyişle, derlenemeyecektir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Desen gerekir üzerinde bir dizi eşleşmesi ve diğer bağlı bileşenlerini oluşturun.  Örneğin:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Derlenmiş Form başvuru tanımlama grubu

Bu bölümde, bunlar derlendikleri zaman formun başlık açıklanmaktadır.  Burada yer alan bilgiler .NET Framework 3.5 hedefleniyorsa sürece okumak gerekli ya da düşük değildir.

Diziler, birkaç genel türler, tüm adlandırılmış birinin nesnelerini derlenen `System.Tuple`, parametre sayısı veya türü parametre sayısı aşırı yüklenmiştir. Tanımlama grubu türleri, bunları başka bir dilden gibi görüntülediğinizde bu formda görünen C# veya Visual Basic veya farkında değil bir aracı kullanırken F# oluşturur. `Tuple` Türleri, .NET Framework 4'te sunulmuştur. .NET Framework'ün önceki bir sürümü hedefliyorsanız, derleyici sürümleri kullanan [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) 2.0 sürümünden F# çekirdek kitaplığı. Bu kitaplıktaki türleri, 2.0, 3.0 ve .NET Framework 3.5 sürümlerini hedefleyen uygulamalar için kullanılır. .NET Framework 2.0 ve .NET Framework 4 ikili uyumluluğu sağlamak için kullanılan tür iletme F# bileşenleri.

### <a name="compiled-form-of-struct-tuples"></a>Yapı demetleri derlenmiş biçimi

Yapı demetleri (örneğin, `struct (x, y)`), temelde başvuru diziler farklıdır.  İçine derlenmiş <xref:System.ValueTuple> parametre sayısı veya türü parametre sayısı aşırı türü.  Eşdeğer oldukları [C# 7.0 diziler](../../csharp/tuples.md) ve [Visual Basic 2017 diziler](../../visual-basic/programming-guide/language-features/data-types/tuples.md)ve çift yönlü çalışmak.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [F# Türleri](fsharp-types.md)