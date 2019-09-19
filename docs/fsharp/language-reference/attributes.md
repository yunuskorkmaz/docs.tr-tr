---
title: Öznitelikler
description: Özniteliklerin bir F# programlama yapısına nasıl uygulanacağını nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 08d50f7f57b6c0a81221e8f635f77f67750d0ff9
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082932"
---
# <a name="attributes"></a>Öznitelikler

Öznitelikler meta verilerin bir programlama yapısına uygulanmasını sağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *hedef* isteğe bağlıdır ve varsa, özniteliğin uygulandığı program varlığının türünü belirtir. *Target* için geçerli değerler, bu belgenin ilerleyen kısımlarında görüntülenen tabloda gösteriliyor.

*Öznitelik adı* , genellikle öznitelik türü adlarında kullanılan soneke `Attribute` sahip olan veya olmayan geçerli bir öznitelik türünün adı (ad alanları ile nitelenme) anlamına gelir. Örneğin, türü `ObsoleteAttribute` yalnızca `Obsolete` bu bağlamda kısaltılarak yapılabilir.

*Bağımsız değişkenler* öznitelik türü için oluşturucunun bağımsız değişkenidir. Bir özniteliğin varsayılan Oluşturucusu varsa, bağımsız değişken listesi ve parantezleri atlanabilir. Öznitelikler hem Konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri destekler. *Konumsal bağımsız değişkenler* göründükleri sırada kullanılan bağımsız değişkenlerdir. Adlandırılmış bağımsız değişkenler, özniteliğinde ortak özellikler varsa kullanılabilir. Bunları, bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.

```fsharp
property-name = property-value
```

Bu tür özellik başlatmaları herhangi bir sırada olabilir, ancak bunların herhangi bir Konumsal bağımsız değişkeni izlemesi gerekir. Aşağıda Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir özniteliğe örnek verilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Bu örnekte, özniteliği `DllImportAttribute`kısaltılmış biçimde kullanılır. İlk bağımsız değişken bir Konumsal parametredir ve ikincisi bir özelliktir.

Öznitelikler, bir *öznitelik* olarak bilinen bir nesnenin bir tür veya diğer program öğesiyle ilişkilendirilmesi için bir .NET programlama yapısıdır. Bir özniteliğin uygulandığı program öğesi *öznitelik hedefi*olarak bilinir. Özniteliği genellikle hedefi hakkında meta veriler içerir. Bu bağlamda meta veriler, alanları ve üyeleri dışındaki türle ilgili herhangi bir veri olabilir.

İçindeki F# öznitelikler şu programlama yapılarına uygulanabilir: işlevler, Yöntemler, derlemeler, modüller, türler (sınıflar, kayıtlar, yapılar, arabirimler, temsilciler, numaralandırmalar, birleşimler, vb.), oluşturucular, özellikler, alanlar, Parametreler, tür parametreleri ve dönüş değerleri. Sınıfların, ifadelerin veya iş `let` akışı ifadelerinin içindeki bağlamalarda özniteliklere izin verilmez.

Genellikle, öznitelik bildirimi doğrudan öznitelik hedefinin bildiriminden önce görünür. Birden çok öznitelik bildirimi, aşağıdaki şekilde birlikte kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET Reflection kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.

Bir önceki kod örneğinde olduğu gibi birden çok özniteliği tek tek bir dizi şekilde bildirebilirsiniz veya bağımsız öznitelikleri ve oluşturucuları ayırmak için noktalı virgül kullanırsanız, burada gösterildiği gibi bunları tek bir köşeli ayraç kümesinde bildirebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Tipik olarak, `Obsolete` öznitelik, güvenlik açısından dikkat edilecek öznitelikler, com desteği öznitelikleri, kod sahipliğiyle ilgili öznitelikler ve bir türün seri hale getirilebilir olup olmadığını belirten öznitelikler içerir. Aşağıdaki örnek, `Obsolete` özniteliğinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Öznitelik hedefleri `assembly` `module`için, özniteliklerini derlemenizin en üst düzey `do` bağlamaya uygularsınız. Word 'ü `assembly` veya `module` öznitelik bildirimine aşağıdaki gibi ekleyebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Bir `do` bağlamaya uygulanan bir özniteliğin öznitelik hedefini atlarsanız, F# derleyici bu öznitelik için anlamlı olan öznitelik hedefini saptamaya çalışır. Birçok öznitelik sınıfı, bu öznitelik için desteklenen `System.AttributeUsageAttribute` olası hedefler hakkında bilgi içeren türünde bir özniteliğe sahiptir. Eğer özniteliğinin işlevleri hedef olarak desteklediğini gösteriyorsa,öznitelikprogramınanagirişnoktasınauygulanacakşekildealınır.`System.AttributeUsageAttribute` Eğer özniteliğin derlemeleri hedef olarak desteklediğini gösteriyorsa,derleyiciözniteliğiderlemeyeuygulanacakşekildealır.`System.AttributeUsageAttribute` Çoğu öznitelik hem işlevler hem de derlemeler için geçerlidir, ancak oldukları durumlarda özniteliği programın ana işlevine uygulanacak şekilde alınır. Öznitelik hedefi açıkça belirtilirse, öznitelik belirtilen hedefe uygulanır.

Genellikle öznitelik hedefini açıkça belirtmeniz gerekmese de, bir öznitelikte *target* için geçerli değerler, kullanım örnekleri ile birlikte aşağıdaki tabloda gösterilmiştir.

<table>
  <tr>
    <th>Öznitelik hedefi</td>
    <th>Örnek</td> 
  </tr>
  <tr>
    <td>derleme</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td> 
  </tr>
  <tr>
    <td>alan</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td> 
  </tr>
  <tr>
    <td>özellik</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td> 
  </tr>
  <tr>
    <td>Larına</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td> 
  </tr>
  <tr>
    <td>türü</td>
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

- [F# Dili Başvurusu](index.md)
