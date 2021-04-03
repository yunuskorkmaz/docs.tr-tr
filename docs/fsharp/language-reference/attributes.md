---
title: Öznitelikler
description: 'F # özniteliklerinin bir programlama yapısına meta verilerin nasıl uygulanacağını nasıl etkinleştirtireceğinizi öğrenin.'
ms.date: 02/19/2020
ms.openlocfilehash: e61018dde832db6da3f3e6da05756f83e528eefc
ms.sourcegitcommit: 652f62fc8f3ab6a264681b6eb5211ac7539bd115
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105964812"
---
# <a name="attributes"></a>Öznitelikler

Öznitelikler meta verilerin bir programlama yapısına uygulanmasını sağlar.

## <a name="syntax"></a>Syntax

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *hedef* isteğe bağlıdır ve varsa, özniteliğin uygulandığı program varlığının türünü belirtir. *Target* için geçerli değerler, bu belgenin ilerleyen kısımlarında görüntülenen tabloda gösteriliyor.

*Öznitelik adı* , `Attribute` genellikle öznitelik türü adlarında kullanılan soneke sahip olan veya olmayan geçerli bir öznitelik türünün adı (ad alanları ile nitelenme) anlamına gelir. Örneğin, türü `ObsoleteAttribute` yalnızca bu bağlamda kısaltılarak yapılabilir `Obsolete` .

*Bağımsız değişkenler* öznitelik türü için oluşturucunun bağımsız değişkenidir. Bir özniteliğin parametresiz oluşturucusu varsa, bağımsız değişken listesi ve parantezleri atlanabilir. Öznitelikler hem Konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri destekler. *Konumsal bağımsız değişkenler* göründükleri sırada kullanılan bağımsız değişkenlerdir. Adlandırılmış bağımsız değişkenler, özniteliğinde ortak özellikler varsa kullanılabilir. Bunları, bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.

```fsharp
property-name = property-value
```

Bu tür özellik başlatmaları herhangi bir sırada olabilir, ancak bunların herhangi bir Konumsal bağımsız değişkeni izlemesi gerekir. Aşağıda Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir özniteliğe örnek verilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Bu örnekte, özniteliği `DllImportAttribute` kısaltılmış biçimde kullanılır. İlk bağımsız değişken bir Konumsal parametredir ve ikincisi bir özelliktir.

Öznitelikler, bir *öznitelik* olarak bilinen bir nesnenin bir tür veya diğer program öğesiyle ilişkilendirilmesi için bir .NET programlama yapısıdır. Bir özniteliğin uygulandığı program öğesi *öznitelik hedefi* olarak bilinir. Özniteliği genellikle hedefi hakkında meta veriler içerir. Bu bağlamda meta veriler, alanları ve üyeleri dışındaki türle ilgili herhangi bir veri olabilir.

F # içindeki öznitelikler şu programlama yapılarına uygulanabilir: işlevler, Yöntemler, derlemeler, modüller, türler (sınıflar, kayıtlar, yapılar, arabirimler, temsilciler, numaralandırmalar, birleşimler, vb.), oluşturucular, özellikler, alanlar, parametreler, tür parametreleri ve dönüş değerleri. `let`Sınıfların, ifadelerin veya iş akışı ifadelerinin içindeki bağlamalarda özniteliklere izin verilmez.

Genellikle, öznitelik bildirimi doğrudan öznitelik hedefinin bildiriminden önce görünür. Birden çok öznitelik bildirimi, aşağıdaki gibi birlikte kullanılabilir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET Reflection kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.

Bir önceki kod örneğinde olduğu gibi birden çok özniteliği ayrı ayrı bildirebilir veya bağımsız öznitelikleri ve oluşturucuları ayırmak için noktalı virgül kullanırsanız, bunları bir parantez kümesinde bildirebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Tipik `Obsolete` olarak, öznitelik, güvenlik açısından dikkat edilecek öznitelikler, com desteği öznitelikleri, kod sahipliğiyle ilgili öznitelikler ve bir türün seri hale getirilebilir olup olmadığını belirten öznitelikler içerir. Aşağıdaki örnek, özniteliğinin kullanımını gösterir `Obsolete` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Öznitelik hedefleri için `assembly` `module` , özniteliklerini derlemenizin en üst düzey `do` bağlamaya uygularsınız. Word 'ü `assembly` veya ``` ``module`` ``` öznitelik bildirimine aşağıdaki gibi ekleyebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Bir bağlamaya uygulanan bir özniteliğin öznitelik hedefini atlarsanız `do` , F # derleyicisi bu öznitelik için anlamlı olan öznitelik hedefini saptamaya çalışır. Birçok öznitelik sınıfı `System.AttributeUsageAttribute` , bu öznitelik için desteklenen olası hedefler hakkında bilgi içeren türünde bir özniteliğe sahiptir. Eğer `System.AttributeUsageAttribute` özniteliğinin işlevleri hedef olarak desteklediğini gösteriyorsa, öznitelik programın ana giriş noktasına uygulanacak şekilde alınır. Eğer `System.AttributeUsageAttribute` özniteliğin derlemeleri hedef olarak desteklediğini gösteriyorsa, derleyici özniteliği derlemeye uygulanacak şekilde alır. Çoğu öznitelik hem işlevler hem de derlemeler için geçerlidir, ancak oldukları durumlarda özniteliği programın ana işlevine uygulanacak şekilde alınır. Öznitelik hedefi açıkça belirtilirse, öznitelik belirtilen hedefe uygulanır.

Genellikle öznitelik hedefini açıkça belirtmeniz gerekmese de, bir öznitelikte *target* için geçerli değerler, kullanım örnekleri ile birlikte aşağıdaki tabloda gösterilmiştir:

<table>
  <tr>
    <th>Öznitelik hedefi</td>
    <th>Örnek</td>
  </tr>
  <tr>
    <td>derleme</td>
    <td><pre><code class="lang-fsharp">[&lt;assembly: AssemblyVersion("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>modül</td>
    <td><pre><code class="lang-fsharp">[&lt;``module``: MyCustomAttributeThatWorksOnModules&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre><code class="lang-fsharp">let function1 x : [&lt;return: MyCustomAttributeThatWorksOnReturns&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>alan</td>
    <td><pre><code class="lang-fsharp">[&lt;DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>özellik</td>
    <td><pre><code class="lang-fsharp">[&lt;Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>larına</td>
    <td><pre><code class="lang-fsharp">member this.MyMethod([&lt;Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>tür</td>
    <td>
        <pre><code class="lang-fsharp">
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
