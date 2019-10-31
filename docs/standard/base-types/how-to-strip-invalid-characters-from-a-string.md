---
title: 'Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127646"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma
Aşağıdaki örnek, bir dizeden geçersiz karakterleri atmak için statik <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemini kullanır.  
  
## <a name="example"></a>Örnek  
 Kullanıcı girişini kabul eden bir metin alanına girilmiş olabilecek zararlı karakterleri birleştirmek için bu örnekte tanımlanan `CleanInput` yöntemini kullanabilirsiniz. Bu durumda, nokta (.), semboller (@) ve kısa çizgi (-) dışındaki tüm alfasayısal olmayan karakterleri `CleanInput` ve kalan dizeyi döndürür. Ancak, normal ifade deseninin bir giriş dizesine dahil olmaması gereken herhangi bir karakteri şeritleri için değişiklik yapabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade deseninin `[^\w\.@-]`, bir sözcük karakteri, nokta, @ simge veya kısa çizgi olmayan herhangi bir karakterle eşleşir. Bir sözcük karakteri, alt çizgi gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcıdır. Bu düzenle eşleşen herhangi bir karakter, değiştirme düzeniyle tanımlanan dize olan <xref:System.String.Empty?displayProperty=nameWithType>ile değiştirilmiştir. Kullanıcı girişinde ek karakterlere izin vermek için, bu karakterleri normal ifade deseninin karakter sınıfına ekleyin. Örneğin, normal ifade deseninin `[^\w\.@-\\%]` bir yüzde simgesine ve bir giriş dizesinde ters eğik çizgiye izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
