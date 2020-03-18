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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127646"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma
Aşağıdaki örnek, geçersiz <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> karakterleri bir dizeden sökmek için statik yöntemi kullanır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `CleanInput` tanımlanan yöntemi, kullanıcı girişini kabul eden bir metin alanına girilmiş zararlı olabilecek karakterleri şeritlemek için kullanabilirsiniz. Bu durumda, `CleanInput` dönemler (.), semboller (@) ve tireler (-) dışındaki tüm alfasayısal olmayan karakterleri şeritler ve kalan dizeyi döndürür. Ancak, giriş dizesinde yer almaması gereken karakterleri silecek şekilde normal ifade deseni değiştirebilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade `[^\w\.@-]` deseni, sözcük karakteri, dönem, bir @ sembolü veya tire olmayan herhangi bir karakterle eşleşir. Sözcük karakteri, alt puan gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcısıdır. Bu deseneşleşen herhangi bir karakter, değiştirme deseni tarafından tanımlanan dize ile değiştirilir. <xref:System.String.Empty?displayProperty=nameWithType> Kullanıcı girişindeki ek karakterlere izin vermek için, bu karakterleri normal ifade desenindeki karakter sınıfına ekleyin. Örneğin, normal ifade `[^\w\.@-\\%]` deseni de bir yüzde sembolü ve bir giriş dizesi bir ters çizgi sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
