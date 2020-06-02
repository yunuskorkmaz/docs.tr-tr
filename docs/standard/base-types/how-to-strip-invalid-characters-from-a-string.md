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
ms.openlocfilehash: 5f2a1e7a3202b14d32ed02c6808fe2411465d9b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290441"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma
Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> bir dizeden geçersiz karakterleri atmak için statik yöntemi kullanır.  
  
## <a name="example"></a>Örnek  
 `CleanInput`Kullanıcı girişini kabul eden bir metin alanına girilmiş olabilecek zararlı karakterleri birleştirmek için bu örnekte tanımlanan yöntemi kullanabilirsiniz. Bu durumda, `CleanInput` noktalar (.), semboller (@) ve tire (-) dışındaki tüm alfasayısal olmayan karakterleri kaldırır ve kalan dizeyi döndürür. Ancak, normal ifade deseninin bir giriş dizesine dahil olmaması gereken herhangi bir karakteri şeritleri için değişiklik yapabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade stili, bir `[^\w\.@-]` sözcük karakteri, nokta, @ simge veya kısa çizgi olmayan herhangi bir karakterle eşleşir. Bir sözcük karakteri, alt çizgi gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcıdır. Bu düzenle eşleşen herhangi bir karakter <xref:System.String.Empty?displayProperty=nameWithType> , değiştirme düzeniyle tanımlanan dize olan ile değiştirilmiştir. Kullanıcı girişinde ek karakterlere izin vermek için, bu karakterleri normal ifade deseninin karakter sınıfına ekleyin. Örneğin, normal ifade deseninin de bir `[^\w\.@-\\%]` yüzde simgesine ve bir giriş dizesinde ters eğik çizgiye izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
