---
title: statik yönergeyi kullanarak - C# Referans
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712955"
---
# <a name="using-static-directive-c-reference"></a>statik yönergeyi kullanarak (C# Reference)

Yönerge, `using static` bir tür adı belirtmeden erişebileceğiniz statik üyeleri ve iç içe geçmiş türleri olan bir tür belirtir. Sözdizimi:

```csharp
using static <fully-qualified-type-name>;
```

*tam nitelikli tür adı* olan statik üyeleri ve iç içe türleri bir tür adı belirtilmeden başvurulabilir türün adıdır. Tam nitelikli bir tür adı (tür adı ile birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası [CS0246](../compiler-messages/cs0246.md)oluşturur : "Tür veya ad alanı adı 'type/namespace' bulunamadı (bir kullanma yönergesi veya derleme başvurusu eksik mi?)".

Yönerge, `using static` örnek üyeleri olsa bile statik üyeleri (veya iç içe geçmiş türleri) olan tüm türler için geçerlidir. Ancak, örnek üyeler yalnızca tür örneği aracılığıyla çağrılabilir.

Direktif `using static` C# 6'da tanıtıldı.

## <a name="remarks"></a>Açıklamalar

Normalde, statik bir üyeyi aradiğinizde, tür adını üye adı ile birlikte sağlarsınız. Türün üyelerini çağırmak için aynı tür adı tekrar tekrar girmek ayrıntılı, belirsiz kodla sonuçlanabilir. Örneğin, sınıfın `Circle` aşağıdaki tanımı sınıfın birkaç üyesine <xref:System.Math> başvurur.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Bir üyeye her başvuruda <xref:System.Math> bulunulan sınıfa açıkça başvurma `using static` gereksinimini ortadan kaldırarak, yönerge çok daha temiz bir kod üretir:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`yalnızca erişilebilir statik üyeleri ve belirtilen türde bildirilen iç içe geçmiş türleri içeri alır.  Devralınan üyeler alınmaz.  Visual Basic modülleri de dahil olmak üzere statik yönergekullanarak herhangi bir adlandırılmış türden içe aktarabilirsiniz.  F# üst düzey işlevler meta verilerde adı geçerli bir C# tanımlayıcısı olan bir adı taşıyan bir türün statik üyeleri olarak görünürse, F# işlevleri içe aktarılabilir.

 `using static`uzantı yöntemi araması için belirtilen türde bildirilen uzatma yöntemlerini yapar.  Ancak, uzantı yöntemlerinin adları kodda niteliksiz başvuru için kapsamına alınmaz.

 Aynı derleme biriminde veya ad `using static` alanında farklı yönergeler tarafından farklı türlerden alınan aynı ada sahip yöntemler bir yöntem grubu oluşturur.  Bu yöntem grupları içinde aşırı yükleme çözümü normal C# kurallarını izler.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `using static` tür adlarını belirtmek zorunda <xref:System.Console> <xref:System.Math>kalmadan, , ve <xref:System.String> sınıfların statik üyelerini kullanılabilir hale getirmek için yönergeyi kullanır.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Örnekte, `using static` yönerge <xref:System.Double> türüne de uygulanmış olabilir. Bu, bir tür adı <xref:System.Double.TryParse(System.String,System.Double@)> belirtmeden yöntemi çağırmayı mümkün kılardı. Ancak, sayısal türün `using static` `TryParse` yönteminin çağrıldığını belirlemek için ifadeleri denetlemek gerekli hale geldiğinden, bu daha az okunabilir kod oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [yönergeyi kullanarak](using-directive.md)
- [C# Referans](../index.md)
- [C# Anahtar Kelimeler](index.md)
- [Ad Alanlarını Kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
