---
title: statik yönerge kullanma- C# başvuru
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 1a0e26d8b0a14e0c77b724fc492588e08762e47f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099993"
---
# <a name="using-static-directive-c-reference"></a>static yönergesini kullanma (C# başvuru)

`using static` yönergesi statik üyeleri ve iç içe geçmiş türleri bir tür adı belirtmeden erişebileceğiniz bir türü belirler. Sözdizimi şöyledir:

```csharp
using static <fully-qualified-type-name>;
```

*tam nitelikli tür* adı, statik üyeleri ve iç içe türlerine bir tür adı belirtilmeden başvurulabilen türün adıdır. Tam nitelikli tür adı (tür adıyla birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "tür veya ad alanı adı ' Type/Namespace ' bulunamadı (bir using yönergeniz veya bir bütünleştirilmiş kod eksik olabilir başvuru?) ".

`using static` yönergesi, örnek üyelerine de sahip olsa bile statik üyelere (veya iç içe türler) sahip her tür için geçerlidir. Ancak, örnek üyeleri yalnızca tür örneği aracılığıyla çağrılabilir.

`using static` yönergesi 6 ' da C# sunulmuştur.

## <a name="remarks"></a>Açıklamalar

Genellikle, bir statik üye çağırdığınızda, tür adını üye adıyla birlikte sağlarsınız. Türün üyelerini çağırmak için aynı tür adının tekrar tekrar girilmesi, ayrıntılı ve belirsiz kod oluşmasına neden olabilir. Örneğin, bir `Circle` sınıfının aşağıdaki tanımı <xref:System.Math> sınıfının bir dizi üyesine başvurur.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Bir üyeye her başvurulilişinde <xref:System.Math> sınıfına açıkça başvuru ihtiyacını ortadan kaldırarak `using static` yönergesi çok Temizleyici kod üretir:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`, yalnızca erişilebilir statik üyeleri ve belirtilen türde tanımlanan iç içe geçmiş türleri içeri aktarır.  Devralınan Üyeler içeri aktarılmaz.  Visual Basic modüller dahil olmak üzere, bir using static yönergesi ile herhangi bir adlandırılmış türden içeri aktarabilirsiniz.  F# Üst düzey işlevler, adı geçerli C# bir tanımlayıcı olan adlandırılmış türün statik üyeleri olarak meta verilerde görünürse, F# işlevler içeri aktarılabilir.

 `using static`, belirtilen türde tanımlanan uzantı yöntemlerinin genişletme yöntemi araması için kullanılabilir olmasını sağlar.  Ancak, uzantı yöntemlerinin adları kodda nitelenmemiş başvuru için kapsama aktarılmaz.

 Aynı ada sahip Yöntemler aynı derleme birimi veya ad alanı içinde farklı `using static` yönergeleri tarafından bir yöntem grubu oluşturur.  Bu yöntem grupları içindeki aşırı yükleme çözümlemesi normal C# kuralları izler.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Console>, <xref:System.Math>ve <xref:System.String> sınıflarının statik üyelerini tür adlarını belirtmek zorunda kalmadan kullanılabilir hale getirmek için `using static` yönergesini kullanır.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Örnekte, `using static` yönergesi <xref:System.Double> türüne de uygulanmış olabilir. Bu, bir tür adı belirtmeden <xref:System.Double.TryParse(System.String,System.Double@)> yöntemini çağırmak mümkün hale gelir. Ancak, bu, hangi sayısal tür `TryParse` yönteminin çağrıldığını belirleyen `using static` deyimlerini denetlemek için gerekli hale geldiği için, daha az okunabilir bir kod oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [using yönergesi](using-directive.md)
- [C#Başvurunun](../index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Ad Alanlarını Kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [Ad alanları](../../programming-guide/namespaces/index.md)
