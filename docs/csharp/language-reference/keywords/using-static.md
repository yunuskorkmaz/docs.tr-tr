---
title: using static yönergesi - C# başvurusu
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c17f74fc16e8c9774086c5270a66e9e9d7cc425b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237785"
---
# <a name="using-static-directive-c-reference"></a>using static yönergesi (C# Başvurusu)

`using static` Yönergesi, statik üyeleri ve iç içe geçmiş türler erişebileceğiniz bir tür adı belirtmeden bir tür belirler. Kendi sözdizimi aşağıdaki gibidir:

```csharp
using static <fully-qualified-type-name>;
```

Burada *tam olarak nitelenmiş-tür adı* türün statik üyeleri adıdır ve iç içe geçmiş türler, tür adı belirtmeden başvurulabilir. Tam nitelikli tür adı (tür adıyla birlikte tam ad alanı adı), sağlamaz, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "' Türü/ad alanı' tür veya ad alanı adı bulunamadı (bir using eksik yönergeniz veya derleme başvurunuz?)".

`using static` Yönergesi Ayrıca örnek üyeleri sahip olsa bile statik üyeler (veya iç içe geçmiş türler) olan herhangi bir türü için geçerlidir. Ancak, örnek üyeleri yalnızca tür örneği çağrılabilir.

`using static` Yönergesi, C# 6'da sunulmuştur.

## <a name="remarks"></a>Açıklamalar
 
Normalde, bir statik üye çağırdığınızda, üye adıyla birlikte tür adı sağlayın. Art arda türün üyeleri çağırmak için aynı tür adı girerek, ayrıntılı, belirsiz kodu neden olabilir. Örneğin, aşağıdaki tanımını bir `Circle` sınıfına başvuran bir dizi üyeleri <xref:System.Math> sınıfı.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Açıkça başvuru gereksinimini ortadan kaldıran tarafından <xref:System.Math> sınıf üyesi başvuruluyor, her zaman `using static` yönergesi çok daha temiz bir kod üretir:

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` yalnızca erişilebilir statik üyeleri ve belirtilen türde bildirilen iç içe geçmiş türleri içeri aktarır.  Devralınan üyeleri içeri aktarılmaz.  Kullanarak herhangi bir adlandırılmış tür içeri aktarabileceğiniz static yönergesi, Visual Basic modülleri dahil.  Varsa F# adı, geçerli bir adlandırılmış bir türün statik üyeleri en üst düzey işlevler görünür meta verilerde C# tanımlayıcısı, ardından F# işlevleri alınabilir.  
  
 `using static` Uzantı yöntemi araması için kullanılabilen belirtilen türde bildirilen genişletme yöntemleri sağlar.  Ancak, genişletme yöntemleri adlarını nitelenmemiş bir başvuru kod kapsama içeri aktarılmaz.  
  
 Farklı türlerden farklı tarafından alınan aynı ada sahip yöntem `using static` yönergeleri aynı derleme biriminde veya ad alanı bir yöntem grubu oluşturur.  Bu yöntem grupları aşırı yükleme çözünürlüğüne normal C# kurallara uygun olmalıdır.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnekte `using static` statik üyelerinden birini yapmak için yönergesi <xref:System.Console>, <xref:System.Math>, ve <xref:System.String> sınıflarının kendi tür adını belirtmenize gerek kalmadan kullanılabilir.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Örnekte, `using static` yönergesi ayrıca uygulanıp uygulanmadığını için <xref:System.Double> türü. Bu, çağrılabilir alacağımızdı <xref:System.Double.TryParse(System.String,System.Double@)> türü adı belirtilmeden yöntemi. Ancak, bu daha okunabilir bir kod oluşturur denetlemek gerekli hale beri `using static` hangi sayısal türün belirlemek için ifadeleri `TryParse` yöntemi çağrılır.

## <a name="see-also"></a>Ayrıca bkz.

- [using yönergesi](using-directive.md)
- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Ad Alanlarını Kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)
