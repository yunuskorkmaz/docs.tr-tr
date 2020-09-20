---
title: Demetler
description: 'Farklı türlerde olabilecek adlandırılmamış ancak sıralı değerler gruplandırması olan F # Tuple hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6f4adf7e10e22d8b7a8cf697baee15962adf3630
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720367"
---
# <a name="tuples"></a>Demetler

*Kayıt düzeni* , farklı türlerde olabilecek adlandırılmamış ancak sıralanmış değerlerin bir gruplandırmasıdır.  Tanımlama grupları başvuru türleri ya da yapılar olabilir.

## <a name="syntax"></a>Syntax

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Açıklamalar

Önceki söz diziminde her *öğe* geçerli bir F # ifadesi olabilir.

## <a name="examples"></a>Örnekler

Tanımlama gruplarına örnek olarak, aynı veya farklı türlerde çiftler, Üçlü, vb. dahildir. Bazı örnekler aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Ayrı değerler alma

Aşağıdaki kodda gösterildiği gibi, kayıt düzeni öğelerine erişmek ve adları atamak için model eşleştirmeyi kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Ayrıca bağlama yoluyla bir ifadenin dışındaki bir düzeni kullanarak bir tanımlama grubu oluşturabilirsiniz `match`  `let` .

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Ya da, diziler üzerinde farklı işlevlere giriş olarak de kalıp eşleştirebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Kayıt düzeninin yalnızca bir öğesine ihtiyacınız varsa, ihtiyacınız olmayan bir değer için yeni bir ad oluşturmaktan kaçınmak için joker karakter (alt çizgi) kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Bir başvuru kayıt kümesinden yapı grubu içine öğe kopyalamak de basittir:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

İşlevler `fst` ve `snd` (yalnızca başvuru tanımlama grupları), bir başlığın sırasıyla ilk ve ikinci öğelerini döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Üçlü öğesinin üçüncü öğesini döndüren yerleşik bir işlev yoktur, ancak aşağıdaki gibi kolayca bir tane yazabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Genellikle, tek tek demet öğelerine erişmek için model eşleştirmeyi kullanmak daha iyidir.

## <a name="using-tuples"></a>Tanımlama gruplarını kullanma

Tanımlama grupları, aşağıdaki örnekte gösterildiği gibi bir işlevden birden çok değer döndürmek için kullanışlı bir yol sağlar. Bu örnek, tam sayı bölümü gerçekleştirir ve bir demet çiftinin ilk üyesi olarak işlemin yuvarlanmış sonucunu ve çiftinin ikinci bir üyesi olarak geri kalanını döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Ayrıca, normal işlev sözdizimi tarafından kapsanan işlev bağımsız değişkenlerinin örtük olarak oluşmasını önlemek istediğinizde, diziler işlev bağımsız değişkeni olarak kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

İşlevi tanımlamaya yönelik olağan sözdizimi, `let sum a b = a + b` aşağıdaki kodda gösterildiği gibi, işlevin ilk bağımsız değişkeninin kısmi uygulaması olan bir işlev tanımlamanızı sağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Parametre olarak bir tanımlama grubu kullanmak, currying 'i devre dışı bırakır. Daha fazla bilgi için, bkz. [işlevlerde](./functions/index.md)"bağımsız değişkenlerin kısmi uygulaması".

## <a name="names-of-tuple-types"></a>Demet türlerinin adları

Tanımlama grubu olan bir türün adını yazdığınızda, `*` öğeleri ayırmak için simgesini kullanın. , Gibi bir,, ve içeren bir tanımlama grubu için, `int` `float` `string` `(10, 10.0, "ten")` tür şöyle yazılır.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# tanımlama grupları ile birlikte çalışma

C# 7,0, tanımlama gruplarını dile sunmuştur.  C# ' deki diziler yapılar ve F # ' daki yapı tanımlama grupları ile eşdeğerdir.  C# ile birlikte çalışmanız gerekiyorsa struct tanımlama gruplarını kullanmanız gerekir.

Bu kolay bir işlemdir.  Örneğin, bir tanımlama grubunu C# sınıfına geçirmeniz ve sonra da bir tanımlama grubu olan sonucunu tüketmeniz gerektiğini düşünün:

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

F # kodunuzda, bir yapı tanımlama grubunu parametre olarak geçirebilir ve sonucu bir struct demet olarak kullanabilirsiniz.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Başvuru tanımlama grupları ve yapı tanımlama grupları arasında dönüştürme

Başvuru başlıkları ve yapı tanımlama gruplarının tamamen farklı bir temel temsili olduğundan, bunlar örtülü olarak dönüştürülebilir değildir.  Diğer bir deyişle, aşağıdaki gibi bir kod derlenmez:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Tek bir kayıt düzeninde kalıp eşleşmesi gerekir ve diğer bileşenleri oluşturan parçalar ile oluşturun.  Örneğin:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Başvuru tanımlama gruplarının derlenmiş formu

Bu bölüm, derlendikleri zaman başlıkların biçimini açıklar.  .NET Framework 3,5 veya daha düşük bir sürüm hedeflenmediğiniz müddetçe buradaki bilgiler okunmanıza gerek yoktur.

Tanımlama grupları, birden fazla genel türden biri olan, `System.Tuple` parametre sayısı üzerinde aşırı yüklenmiş olan tüm adlandırılmış nesneler veya tür parametrelerinin sayısıyla derlenir. Bu formda, C# veya Visual Basic gibi başka bir dilde görüntülediğinizde ya da F # yapıları farkında olmayan bir araç kullanırken demet türleri görüntülenir. `Tuple`Türler .NET Framework 4 ' te tanıtılmıştı. .NET Framework önceki bir sürümünü hedefliyorsanız, derleyici `System.Tuple` F # Çekirdek kitaplığının 2,0 sürümündeki sürümlerini kullanır. Bu kitaplıktaki türler yalnızca .NET Framework 2,0, 3,0 ve 3,5 sürümlerini hedefleyen uygulamalar için kullanılır. Tür iletme, .NET Framework 2,0 ve .NET Framework 4 F # bileşenleri arasında ikili uyumluluk sağlamak için kullanılır.

### <a name="compiled-form-of-struct-tuples"></a>Yapı tanımlama gruplarının derlenmiş formu

Yapı tanımlama grupları (örneğin, `struct (x, y)` ), başvuru dizklarından temelde farklıdır.  Bunlar <xref:System.ValueTuple> türü, parametre sayısına göre aşırı yüklendi veya tür parametrelerinin sayısı olarak derlenir.  [C# 7,0 tanımlama](../../csharp/language-reference/builtin-types/value-tuples.md) gruplarına ve [Visual Basic 2017 tanımlama](../../visual-basic/programming-guide/language-features/data-types/tuples.md)gruplarına eşdeğerdir ve birlikte çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [F# Türleri](fsharp-types.md)
