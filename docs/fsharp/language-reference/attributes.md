---
title: Öznitelikler (F#)
description: 'Nasıl F # öznitelikleri bir programlama yapısı uygulanacak meta verilerini etkinleştir öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 107f5d9cbcce28c97fc5b738759ef27649fc45a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565431"
---
# <a name="attributes"></a>Öznitelikler

Öznitelikleri bir programlama yapısı uygulanacak meta verilerini etkinleştir.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *hedef* isteğe bağlıdır ve varsa, öznitelik uygulandığı program varlık türünü belirtir. İçin geçerli değerler *hedef* bu belgenin sonraki bölümlerinde görünür tabloda gösterilen.

*Öznitelik adı* geçerli öznitelik türü ile veya olmadan soneki (büyük olasılıkla ad alanları ile tam) adının başvurduğu `Attribute` öznitelik türü adları genellikle kullanılan. Örneğin, türü `ObsoleteAttribute` henüz için kısaltılmış `Obsolete` bu bağlamda.

*Bağımsız değişkenleri* oluşturucuya öznitelik türü bağımsız değişkenleri. Özniteliğin varsayılan bir oluşturucu varsa, bağımsız değişken listesi ve parantez atlanabilir. Öznitelikler konumsal bağımsız değişkenler ve adlandırılmış bağımsız değişkenler destekler. *Konumsal bağımsız değişkenleri* göründükleri sırada kullanılan bağımsız değişkenler. Adlandırılmış bağımsız değişkenler özniteliği ortak özellikleri varsa kullanılabilir. Bu bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.

```
*property-name* = *property-value*
```

Bu tür özelliği başlatmaları herhangi bir sırada olabilir, ancak konumsal herhangi bir bağımsız değişken izlemeniz gerekir. Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir öznitelik örneği verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Bu örnekte, bir özniteliktir `DllImportAttribute`, burada kısaltılmış formunda kullanılır. İlk bağımsız değişken konumsal bir parametre ve ikinci bir özelliktir.

Öznitelikleridir olarak bilinen bir nesne sağlayan bir .NET programlama yapısı bir *özniteliği* bir tür veya başka bir program öğesi ile ilişkili olmalıdır. Bir öznitelik uygulanan bir program öğesi olarak bilinen *özniteliği hedef*. Öznitelik, genellikle hedefine hakkındaki meta verileri içerir. Bu bağlamda herhangi bir veri alanları ve üyeleri dışında türü hakkında meta veri olabilir.

F # öznitelikleri aşağıdaki programlama yapıları için uygulanabilir: İşlevler, yöntemleri, derlemeleri, modüller, türleri (sınıfları, kayıtları, yapıları, arabirimler, temsilciler, listeleme, birleşimler vb.), Oluşturucular, özellikler, alanları, parametreleri Tür parametreleri ve dönüş değerleri. Öznitelikleri yapılamaz `let` bağlamaları sınıfları, ifadeler veya iş akışı ifadeler içinde.

Genellikle, doğrudan özniteliği hedef bildiriminden önce özniteliği bildirimi görüntülenir. Birden çok öznitelik bildirimleri kullanılabilir birlikte, aşağıdaki gibi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET yansıma kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.

Önceki kod örneğinde olduğu gibi tek tek, birden çok öznitelik bildirebilir veya aşağıda gösterildiği gibi bir noktalı virgül tek tek özniteliklerini ve Oluşturucular, ayırmak için kullanırsanız bunları köşeli bir dizi bildirebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Genelde karşılaşılan öznitelikleri yer `Obsolete` öznitelik, öznitelikler için güvenlik konuları öznitelikleri COM desteği, kod sahipliği ilgili öznitelikleri ve bir türü seri hale belirten öznitelikleri. Aşağıdaki örnek kullanımını gösteren `Obsolete` özniteliği.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Öznitelik hedefleri için `assembly` ve `module`, öznitelikler için üst düzey uygulama `do` bütünleştirilmiş kodunda bağlama. Word içerebilir `assembly` veya `module` şekilde öznitelik bildirimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Uygulanan bir öznitelik için öznitelik hedef atlarsanız, bir `do` bağlama, F # derleyici bu öznitelik için anlamlı özniteliği hedef belirlemeye çalışır. Çok sayıda öznitelik sınıfları türünde bir özniteliği bulunması `System.AttributeUsageAttribute` bu öznitelik için desteklenen olası hedefleri hakkında bilgiler içerir. Varsa `System.AttributeUsageAttribute` öznitelik hedefleri olarak işlevlerini destekleyen, öznitelik programının ana giriş noktası uygulamak için geçen gösterir. Varsa `System.AttributeUsageAttribute` belirten özniteliği derlemeleri hedefleri olarak destekler, derleyicinin derlemeye uygulamak için özniteliğini alır. Çoğu öznitelikleri işlevler ve derlemeler için geçerli değildir, ancak burada yaptıkları durumlarda, programın main işlevi uygulamak için öznitelik alınır. Öznitelik, öznitelik hedef açıkça belirtilmediği takdirde, belirtilen hedef uygulanır.

Genellikle belirtmeniz gerekmez ancak öznitelik hedef açıkça için geçerli değerler *hedef* bir öznitelikte aşağıdaki tabloda, kullanım örnekleri ile birlikte gösterilir.

<table>
  <tr>
    <th>Öznitelik hedef</td>
    <th>Örnek</td> 
  </tr>
  <tr>
    <td>derleme</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' function1 izin x: [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>alan</td>
    <td>' [<field: DefaultValue>] val değişebilir x: int'</td> 
  </tr>
  <tr>
    <td>özellik</td>
    <td>' [<property: Obsolete>] Bu. MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>' üye bu. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</td> 
  </tr>
  <tr>
    <td>türü</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] MyStruct yazın yapısı = x: byte y: int bitiş ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Ayrıca Bkz.

[F# Dili Başvurusu](index.md)
