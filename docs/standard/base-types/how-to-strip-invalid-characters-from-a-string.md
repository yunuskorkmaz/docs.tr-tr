---
title: 'Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma'
description: Statik Regex. Replace metodunu kullanarak bir dizeden zararlı olabilecek karakterlerin nasıl sökülmesini gösteren bir örnek okuyun.
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: d6422556ab9c7d2100ea66e6b0dae1ee01e0e434
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683855"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma

Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> bir dizeden geçersiz karakterleri atmak için statik yöntemi kullanır.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Örnek  

 `CleanInput`Kullanıcı girişini kabul eden bir metin alanına girilmiş olabilecek zararlı karakterleri birleştirmek için bu örnekte tanımlanan yöntemi kullanabilirsiniz. Bu durumda, `CleanInput` noktalar (.), semboller (@) ve tire (-) dışındaki tüm alfasayısal olmayan karakterleri kaldırır ve kalan dizeyi döndürür. Ancak, normal ifade deseninin bir giriş dizesine dahil olmaması gereken herhangi bir karakteri şeritleri için değişiklik yapabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade stili, bir `[^\w\.@-]` sözcük karakteri, nokta, @ simge veya kısa çizgi olmayan herhangi bir karakterle eşleşir. Bir sözcük karakteri, alt çizgi gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcıdır. Bu düzenle eşleşen herhangi bir karakter <xref:System.String.Empty?displayProperty=nameWithType> , değiştirme düzeniyle tanımlanan dize olan ile değiştirilmiştir. Kullanıcı girişinde ek karakterlere izin vermek için, bu karakterleri normal ifade deseninin karakter sınıfına ekleyin. Örneğin, normal ifade deseninin de bir `[^\w\.@-\\%]` yüzde simgesine ve bir giriş dizesinde ters eğik çizgiye izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
