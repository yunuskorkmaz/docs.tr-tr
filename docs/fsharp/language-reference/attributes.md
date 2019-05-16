---
title: Öznitelikler
description: Bilgi nasıl F# bir programlama yapısı için uygulanacak meta veri öznitelikleri etkinleştirin.
ms.date: 05/16/2016
ms.openlocfilehash: fed4c549b95d6d3701ab81cf5d62add411c16038
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642023"
---
# <a name="attributes"></a>Öznitelikler

Bir programlama yapısı için uygulanacak meta veri öznitelikleri etkinleştirin.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *hedef* isteğe bağlıdır ve varsa, öznitelik program varlık türünü belirtir. İçin geçerli değerler *hedef* bu belgenin sonraki bölümlerinde görüntülenen tabloda gösterilir.

*Öznitelik adı* geçerli öznitelik türü ile ya da soneki olmadan (büyük olasılıkla ad alanları ile tam) adını başvurduğu `Attribute` öznitelik türü adları genellikle kullanılır. Örneğin, türü `ObsoleteAttribute` yalnızca kısalttık `Obsolete` bu bağlamda.

*Bağımsız değişkenleri* oluşturucusu için bağımsız değişkenler için öznitelik türü. Öznitelik bir varsayılan oluşturucusu yoksa, bağımsız değişken listesi ve parantezler atlanmış olabilir. Konumsal bağımsız değişkenlere hem adlandırılmış bağımsız değişkenler öznitelikler destekler. *Konumsal bağımsız değişkenlere* göründükleri sırayla kullanılan bağımsız değişkenler. Genel Özellikler özniteliğine sahipse, adlandırılmış bağımsız değişkenler kullanılabilir. Bu bağımsız değişken listesinde aşağıdaki söz dizimini kullanarak ayarlayabilirsiniz.

```
*property-name* = *property-value*
```

Bu özellik başlatmalarının herhangi bir sırada olabilir, ancak herhangi bir konumsal bağımsız değişken izlemeniz gerekir. Konumsal bağımsız değişkenler ve özellik başlatmalarının kullanan bir öznitelik örneği aşağıda verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Bu örnekte, bir özniteliktir `DllImportAttribute`, burada kısaltılmış içinde kullanılan. İlk bağımsız değişken konumsal bir parametredir ve ikinci bir özelliktir.

Öznitelikleri karşılıklı olarak bilinen bir nesne sağlayan bir .NET programlama yapısı bir *özniteliği* bir türü veya başka bir program öğesi ile ilişkilendirilmiş. Özniteliğin uygulandığı bir program öğesi olarak bilinen *öznitelik hedefi*. Öznitelik, genellikle hedefine hakkındaki meta veriler içeriyor. Bu bağlamda herhangi bir veri üyeleri ve alanları dışındaki türü hakkında meta veriler olabilir.

Öznitelikleri F# aşağıdaki programlama yapıları için uygulanabilir: işlevleri, yöntemleri, derlemeler, modüller, türler (sınıflar, kayıtları, yapılar, arabirimler, temsilciler, numaralandırmalar, birleşimler ve benzeri), Oluşturucular, özellikleri, alanları, Parametreler, tür parametreleri ve dönüş değerleri. Öznitelikler üzerinde izin verilmez `let` sınıfları, ifadeler veya iş akışı ifadeler içinde bağlar.

Genellikle, öznitelik bildiriminin doğrudan özniteliği hedef bildiriminden önce görünür. Birden çok öznitelik bildirimleri kullanılabilir birlikte, aşağıdaki gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Öznitelikler, çalışma zamanında .NET yansıma kullanarak sorgulayabilirsiniz.

Önceki kod örneğinde olduğu gibi tek tek birden çok öznitelik bildirebilirsiniz veya burada gösterildiği gibi noktalı tek tek öznitelikler ve Oluşturucular, ayırmak için kullanıyorsanız bunları parantez kümesi içinde bildirebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Sık rastlanan öznitelikleri yer `Obsolete` öznitelik, öznitelikler için güvenlik konuları öznitelikleri COM desteği, kod sahipliği ilişkili öznitelikleri ve bir türü seri hale belirten öznitelikleri. Aşağıdaki örnek, kullanımını gösterir `Obsolete` özniteliği.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Öznitelik hedefleri için `assembly` ve `module`, öznitelik için bir en üst düzey uygulama `do` , derlemede bağlama. Word içerebilir `assembly` veya `module` gösterildiği gibi öznitelik bildirimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

İçin uygulanan bir öznitelik için öznitelik hedefi atlarsanız, bir `do` bağlamayı F# derleyici bu özniteliği için anlamlı öznitelik hedefi belirlemek dener. Çok sayıda öznitelik sınıfları bir öznitelik türü sahip `System.AttributeUsageAttribute` bu öznitelik için desteklenen olası hedefleri hakkında bilgi içerir. Varsa `System.AttributeUsageAttribute` gösterir öznitelik hedefleri olarak işlevleri destekler, öznitelik programının ana giriş noktasına uygulanacak alınır. Varsa `System.AttributeUsageAttribute` gösterir öznitelik hedefleri olarak derlemelerini destekler, derleyici derlemeye uygulanacak özniteliği alır. Çoğu öznitelikleri işlevleri ve derlemeler için geçerli değildir, ancak yaptıkları olduğu durumlarda, öznitelik için programın main işlevi uygulamak için alınır. Öznitelik, öznitelik hedefi açıkça belirtilmediği takdirde, belirtilen hedef uygulanır.

Genellikle belirtmek gerekmez, ancak öznitelik hedef açıkça için geçerli değerler *hedef* öznitelik içinde kullanım örneklerinin yanı sıra aşağıdaki tabloda gösterilmiştir.

<table>
  <tr>
    <th>Öznitelik hedefi</td>
    <th>Örnek</td> 
  </tr>
  <tr>
    <td>derleme</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td>alan</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td>özellik</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
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
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
