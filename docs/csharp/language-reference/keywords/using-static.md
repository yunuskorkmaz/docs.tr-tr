---
title: static yönergesini kullanma-C# başvurusu
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: bffbc026e8f7937db91d42b7a06a5b7bba3bc2f8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396149"
---
# <a name="using-static-directive-c-reference"></a>static yönergesini kullanma (C# Başvurusu)

`using static`Yönergesi statik üyeleri ve iç içe geçmiş türleri bir tür adı belirtmeden erişebileceğiniz bir türü belirler. Sözdizimi şöyledir:

```csharp
using static <fully-qualified-type-name>;
```

*tam nitelikli tür* adı, statik üyeleri ve iç içe türlerine bir tür adı belirtilmeden başvurulabilen türün adıdır. Tam nitelikli tür adı (tür adıyla birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "tür veya ad alanı adı ' Type/Namespace ' bulunamadı (bir using yönergesi veya derleme başvurunuz eksik olabilir mi?)".

`using static`Yönergesi, örnek üyelerine de sahip olsa bile statik üyelere (veya iç içe türler) sahip her tür için geçerlidir. Ancak, örnek üyeleri yalnızca tür örneği aracılığıyla çağrılabilir.

`using static`Yönerge C# 6 ' da tanıtılmıştı.

## <a name="remarks"></a>Açıklamalar

Genellikle, bir statik üye çağırdığınızda, tür adını üye adıyla birlikte sağlarsınız. Türün üyelerini çağırmak için aynı tür adının tekrar tekrar girilmesi, ayrıntılı ve belirsiz kod oluşmasına neden olabilir. Örneğin, bir sınıfın aşağıdaki tanımı, `Circle` sınıfının bir dizi üyesine başvurur <xref:System.Math> .

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<xref:System.Math>Bir üyeye her başvurulilişinde, bir sınıfa açık bir şekilde başvuruda bulunmak gereksinimini ortadan kaldırarak, `using static` yönerge çok daha Temizleyici kod üretir:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`yalnızca erişilebilir statik üyeleri ve belirtilen türde tanımlanmış iç içe geçmiş türleri içeri aktarır.  Devralınan Üyeler içeri aktarılmaz.  Visual Basic modüller dahil olmak üzere, bir using static yönergesi ile herhangi bir adlandırılmış türden içeri aktarabilirsiniz.  F # en üst düzey işlevleri meta verilerde adı geçerli bir C# tanımlayıcısı olan bir adlandırılmış türün statik üyeleri olarak görünürse, F # işlevleri içeri aktarılabilir.

 `using static`Uzantı yöntemi arama için belirtilen türde belirtilen uzantı yöntemlerini kullanılabilir yapar.  Ancak, uzantı yöntemlerinin adları kodda nitelenmemiş başvuru için kapsama aktarılmaz.

 Aynı ada sahip Yöntemler `using static` aynı derleme birimi veya ad alanı içinde farklı yönergelere göre farklı türlerden içeri aktarılmalıdır bir yöntem grubu.  Bu yöntem grupları içindeki aşırı yükleme çözümlemesi normal C# kurallarını izler.

## <a name="example"></a>Örnek

Aşağıdaki örnek `using static` <xref:System.Console> ,, ve sınıflarının statik üyelerini <xref:System.Math> <xref:System.String> tür adlarını belirtmeye gerek kalmadan kullanılabilir hale getirmek için yönergesini kullanır.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Örnekte, `using static` yönergesi türüne de uygulanmış olabilir <xref:System.Double> . Bu, <xref:System.Double.TryParse(System.String,System.Double@)> bir tür adı belirtmeden yöntemi çağırmak mümkün hale gelir. Ancak, bu, `using static` hangi sayısal tür yönteminin çağrıldığını belirleyen yönergeleri denetlemek için gerekli hale geldiği için, daha az okunabilir bir kod oluşturur `TryParse` .

## <a name="see-also"></a>Ayrıca bkz.

- [using yönergesi](using-directive.md)
- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Ad alanlarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
