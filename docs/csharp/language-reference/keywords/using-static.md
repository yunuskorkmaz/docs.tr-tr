---
title: using statik yönergesi (C# Başvurusu)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b7508c6e751f83fdc16a700ad68aa7de36e497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285141"
---
# <a name="using-static-directive-c-reference"></a>using statik yönergesi (C# Başvurusu)

`using static` Yönergesi statik üyeler türü adı belirtmeden erişmek için bir türü belirler. Sözdizimi aşağıdaki gibidir:

```csharp
using static <fully-qualified-type-name>
```

Burada *tam-etki-türü-adı* statik üyeleri bir tür adı belirtmeden başvurulabilir türünün adı. Tam olarak nitelenmiş tür adını (tür adı ile birlikte tam ad alanı adı) belirtmezseniz, C# Derleyici Hatası CS0246 oluşturur: "'< tür-adı >' türü veya ad alanı adı bulunamadı."

`using static` Yönergesi örnek üyelerin de sahip olsa bile statik üyeleri olan tüm türü için geçerlidir. Ancak, örnek üyeleri yalnızca türü örneği çağrılabilir.

`using static` Yönergesi, C# 6'sunulmuştur.

## <a name="remarks"></a>Açıklamalar
 
Normalde, statik bir üyenin çağırdığınızda, üye adı ile birlikte türü adını belirtin. Art arda türün üyeleri çağırmak için aynı tür adı girerek ayrıntılı, belirsiz kodda neden olabilir. Örneğin, aşağıdaki tanımı bir `Circle` sınıfı üyeleri sayısı başvuran <xref:System.Math> sınıfı.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Açıkça başvuru gereğini ortadan tarafından <xref:System.Math> sınıf üyesi başvurulur, her zaman `using static` yönergesi kadar temizleyici kod üretir:

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` yalnızca erişilebilir statik üyeleri ve iç içe geçmiş türler belirtilen türdeki bildirilen alır.  Devralınan üyeleri içeri aktarılmadı.  Her adlandırılmış tür kullanarak içeri aktarabilirsiniz Visual Basic modülleri dahil statik yönergesi.  F # en üst düzey işlevleri meta verilerinde geçerli bir C# tanımlayıcı adı olan adlandırılmış bir türün statik üyeleri görünüyorsa, F # işlevleri içeri aktarılabilir.  
  
 `using static` uzantısı yöntemi arama için kullanılabilen belirtilen türü içinde bildirilen genişletme yöntemleri sağlar.  Ancak, genişletme yöntemleri adlarını kodda nitelenmemiş başvurusu için kapsam içine içeri aktarılmadı.  
  
 Farklı türler farklı tarafından alınan aynı ada sahip yöntem `using static` yönergeleri aynı derleme birim veya ad alanı form yöntemi grubu.  Bu yöntem grupları içinde aşırı yükleme çözünürlüğü normal C# kurallara uygun olmalıdır.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek kullanır `using static` statik üyeleri yapmak için yönergesi <xref:System.Console>, <xref:System.Math>, ve <xref:System.String> sınıfları kendi türü adını belirtmek zorunda kalmadan kullanılabilir.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Örnekte, `using static` yönergesi ayrıca uygulandı için <xref:System.Double> türü. Bu çağrı mümkün yapılan <xref:System.Double.TryParse(System.String,System.Double@)> bir tür adı belirtmeden yöntemi. Ancak, bu daha az okunabilir kod oluşturur denetlemek gerekli hale beri `using static` hangi sayısal türün belirlemek için deyimleri `TryParse` yöntemi çağrılır.

## <a name="see-also"></a>Ayrıca bkz.

[using yönergesi](using-directive.md)   
[C# başvurusu](../../../csharp/language-reference/index.md)   
[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)   
[Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
[Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)   
[Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)   
