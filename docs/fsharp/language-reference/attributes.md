---
title: Öznitelikler
description: Özniteliklerin bir F# programlama yapısına nasıl uygulanacağını nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 17822891109b8e8eaa10044f82f0b872ce9d30b5
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736808"
---
# <a name="attributes"></a>Öznitelikler

Öznitelikler meta verilerin bir programlama yapısına uygulanmasını sağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *hedef* isteğe bağlıdır ve varsa, özniteliğin uygulandığı program varlığının türünü belirtir. *Target* için geçerli değerler, bu belgenin ilerleyen kısımlarında görüntülenen tabloda gösteriliyor.

*Öznitelik adı* , genellikle öznitelik türü adlarında kullanılan `Attribute` sonekine sahip veya olmadan geçerli bir öznitelik türünün adı (ad alanları ile nitelenme) anlamına gelir. Örneğin, `ObsoleteAttribute` türü bu bağlamda yalnızca `Obsolete` olarak kısaltılarak yapılabilir.

*Bağımsız değişkenler* öznitelik türü için oluşturucunun bağımsız değişkenidir. Bir özniteliğin parametresiz oluşturucusu varsa, bağımsız değişken listesi ve parantezleri atlanabilir. Öznitelikler hem Konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri destekler. *Konumsal bağımsız değişkenler* göründükleri sırada kullanılan bağımsız değişkenlerdir. Adlandırılmış bağımsız değişkenler, özniteliğinde ortak özellikler varsa kullanılabilir. Bunları, bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.

```fsharp
property-name = property-value
```

Bu tür özellik başlatmaları herhangi bir sırada olabilir, ancak bunların herhangi bir Konumsal bağımsız değişkeni izlemesi gerekir. Aşağıda Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir özniteliğe örnek verilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Bu örnekte, öznitelik `DllImportAttribute` ' dır ve kısaltılmış biçimde kullanılır. İlk bağımsız değişken bir Konumsal parametredir ve ikincisi bir özelliktir.

Öznitelikler, bir *öznitelik* olarak bilinen bir nesnenin bir tür veya diğer program öğesiyle ilişkilendirilmesi için bir .NET programlama yapısıdır. Bir özniteliğin uygulandığı program öğesi *öznitelik hedefi*olarak bilinir. Özniteliği genellikle hedefi hakkında meta veriler içerir. Bu bağlamda meta veriler, alanları ve üyeleri dışındaki türle ilgili herhangi bir veri olabilir.

İçindeki F# öznitelikler şu programlama yapılarına uygulanabilir: işlevler, Yöntemler, derlemeler, modüller, türler (sınıflar, kayıtlar, yapılar, arabirimler, temsilciler, numaralandırmalar, birleşimler, vb.), oluşturucular, özellikler, alanlar, Parametreler, tür parametreleri ve dönüş değerleri. Sınıfların, ifadelerin veya iş akışı ifadelerinin içindeki `let` bağlamalarda özniteliklere izin verilmez.

Genellikle, öznitelik bildirimi doğrudan öznitelik hedefinin bildiriminden önce görünür. Birden çok öznitelik bildirimi, aşağıdaki gibi birlikte kullanılabilir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET Reflection kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.

Bir önceki kod örneğinde olduğu gibi birden çok özniteliği ayrı ayrı bildirebilir veya bağımsız öznitelikleri ve oluşturucuları ayırmak için noktalı virgül kullanırsanız, bunları bir parantez kümesinde bildirebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Tipik olarak, `Obsolete` özniteliği, güvenlik konuları için öznitelikler, COM desteği öznitelikleri, kod sahipliğiyle ilgili öznitelikler ve bir türün seri hale getirilebilir olup olmadığını belirten öznitelikler bulunur. Aşağıdaki örnek `Obsolete` özniteliğinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

@No__t-0 ve `module` olan öznitelik hedefleri için, öznitelikleri derlemeinizdeki en üst düzey `do` bağlamaya uygularsınız. Öznitelik bildiriminde `assembly` veya `module` sözcüğünü aşağıdaki gibi ekleyebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

@No__t-0 bağlamaya uygulanan bir özniteliğin öznitelik hedefini atlarsanız, F# derleyici bu öznitelik için anlamlı olan öznitelik hedefini saptamaya çalışır. Birçok öznitelik sınıfı, bu öznitelik için desteklenen olası hedefler hakkında bilgi içeren `System.AttributeUsageAttribute` türünde bir özniteliğe sahiptir. @No__t-0, özniteliğin işlevleri hedef olarak desteklediğini gösteriyorsa, öznitelik programın ana giriş noktasına uygulanacak şekilde alınır. @No__t-0 özniteliğin derlemeleri hedef olarak desteklediğini gösteriyorsa, derleyici özniteliği derlemeye uygulanacak şekilde alır. Çoğu öznitelik hem işlevler hem de derlemeler için geçerlidir, ancak oldukları durumlarda özniteliği programın ana işlevine uygulanacak şekilde alınır. Öznitelik hedefi açıkça belirtilirse, öznitelik belirtilen hedefe uygulanır.

Genellikle öznitelik hedefini açıkça belirtmeniz gerekmese de, bir öznitelikte *target* için geçerli değerler, kullanım örnekleri ile birlikte aşağıdaki tabloda gösterilmiştir:

<table>
  <tr>
    <th>Öznitelik hedefi</td>
    <th>Örnek</td> 
  </tr>
  <tr>
    <td>Derleme</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td> 
  </tr>
  <tr>
    <td>döndürülmesini</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td> 
  </tr>
  <tr>
    <td>Alanla</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td> 
  </tr>
  <tr>
    <td>Özelliði</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td> 
  </tr>
  <tr>
    <td>Larına</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td> 
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;] 
type MyStruct = 
struct 
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Ayrıca bkz.

- [F#Dil başvurusu](index.md)
