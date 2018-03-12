---
title: Demetler (F#)
description: "F # tanımlama hakkında farklı türlerde adlandırılmamış ancak sıralı değerler gruplandırması öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: 996566f2baaea8ab01e5c80e53caea82e9684714
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2018
---
# <a name="tuples"></a>Demetler

A *tanımlama grubu* farklı türlerde adlandırılmamış ancak sıralı değerler grubudur.  Tanımlama grubu ya da başvuru türleri veya yapılar olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>Açıklamalar
Her *öğesi* önceki sözdiziminde herhangi geçerli F # ifade olabilir.

## <a name="examples"></a>Örnekler
Diziler örnekleri çiftleri, Üçlü vb., aynı veya farklı türleri içerir. Bazı örnekler aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>Tek tek değerleri alma
Desen eşleştirme erişmek ve tanımlama grubu öğelerin adları atamak için aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Bir tanımlama grubu dışında desen eşleştirme aracılığıyla deconstruct bir `match` ifadesi aracılığıyla `let` bağlama:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Or deseni giriş olarak işlevleri tanımlama grupları üzerinde eşleşen:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Yalnızca tek bir öğe kayıt gerekiyorsa, joker karakter (alt çizgi) ihtiyacınız olmayan bir değer için yeni bir ad oluşturmamak için kullanılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Öğeleri bir başvuru tanımlama grubundan bir yapı tanımlama grubu kopyalama ayrıca basittir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

İşlevler `fst` ve `snd` (başvuru yalnızca başlıkları) ilk dönün ve bir tanımlama grubu öğeleri sırasıyla ikinci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Bir Üçlü üçüncü öğeyi döndürür hiçbir yerleşik işlevi yoktur, ancak, kolay bir şekilde yazabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Genellikle, tek tek başlığın öğeleri erişmek için desen eşleştirme kullanmak en iyisidir.

## <a name="using-tuples"></a>Tanımlama gruplarını kullanma
Diziler, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kolay bir yol sağlamak. Bu örnek tamsayı bölme gerçekleştirir ve işlem bir tanımlama grubu çifti ilk üye olarak ve geri kalan çift ikinci bir üyesi olarak yuvarlatılmış sonucunu döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Normal işlevi sözdizimi tarafından kapsanan işlev bağımsız değişkenleri örtülü currying engellemek istediğinizde diziler işlevi bağımsız değişken olarak da kullanılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

İşlev tanımlamak için normal sözdizimi `let sum a b = a + b` aşağıdaki kodda gösterildiği gibi kısmi uygulama işlevinin ilk bağımsız değişkenin bir işlev tanımlamanızı sağlar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Parametre olarak bir tanımlama grubu kullanarak currying devre dışı bırakır. Daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevler](functions/index.md).

## <a name="names-of-tuple-types"></a>Tuple türlerinin adlarını
Bir tanımlama grubu olan bir türü adını yazdığınızda, kullandığınız `*` öğeleri ayırmak için kullanılan simge. Oluşan bir tanımlama grubu için bir `int`, `float`ve bir `string`, gibi `(10, 10.0, "ten")`, türü şu şekilde yazılır.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# başlıkları ile birlikte çalışma

C# 7 Dil diziler kullanıma sunuldu.  C# diziler yapılar ve F # yapısı diziler eşdeğerdir.  C# ile çalışmanız gerekiyorsa, yapı dizilerini kullanmanız gerekir.

Bunu yapmak kolaydır.  Örneğin, C# sınıfına bir tanımlama grubu geçirmek ve aynı zamanda bir tanımlama grubu olan sonucunu kullanmak zorunda düşünün:

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

F # kodu, ardından yapısı tanımlama grubu parametre olarak geçirmek ve sonucu bir yapı tanımlama grubu olarak kullanabilir.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Başvuru başlıkları ve yapı diziler arasında dönüştürme

Başvuru başlıkları ve yapı diziler tamamen farklı bir temel alınan gösterimi olduğundan, bunlar örtük olarak dönüştürülebilir değildir.  Diğer bir deyişle, aşağıdaki gibi kod derleme olmaz:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Desen gereken diğer bağlı bölümlerle oluşturmak ve bir tanımlama grubu üzerinde eşleşmiyor.  Örneğin:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Başvuru başlık derlenmiş formu
Bu bölümde, derlenmiş zaman formun başlık açıklanmaktadır.  Burada yer alan bilgiler, .NET Framework 3.5 hedeflediğiniz sürece okumak gerekli veya alt değil.

Diziler birkaç genel türlerden birinde, tüm adlandırılmış nesnelerine derlenmiş `System.Tuple`, bu aşırı parametre sayısı veya türü parametre sayısı. Dizi türleri, bunları C# veya Visual Basic gibi başka bir dilden görüntülediğinizde veya F # yapılarını tanımaz bir aracı kullanırken bu formda görüntülenir. `Tuple` Türleri, .NET Framework 4'te sunulmuştu. .NET Framework'ün önceki bir sürümünü hedefliyorsanız, derleyici sürümlerini kullanan [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) F # Core kitaplık 2.0 sürümünden. Bu kitaplıktaki türleri 2.0, 3.0 ve .NET Framework 3.5 sürümlerini hedefleyen uygulamalar için kullanılır. Tür iletme, .NET Framework 2.0 ve .NET Framework 4 F # bileşenleri arasında ikili uyumluluğu sağlamak için kullanılır.

### <a name="compiled-form-of-struct-tuples"></a>Yapı başlık derlenmiş formu

Yapı diziler (örneğin, `struct (x, y)`), başvuru diziler temelde farklıdır.  İçine derlenmiş <xref:System.ValueTuple> parametre sayısı veya türü parametre sayısı aşırı türü.  Eşdeğer [C# 7 diziler](../../csharp/tuples.md) ve [Visual Basic 2017 diziler](../../visual-basic/programming-guide/language-features/data-types/tuples.md)ve çift yönlü onunla birlikte çalışamaz.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[F# Türleri](fsharp-types.md)
