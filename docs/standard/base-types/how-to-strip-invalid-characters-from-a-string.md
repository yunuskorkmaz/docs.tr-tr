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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698074"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma
Aşağıdaki örnek, statik kullanır <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi bir dizeden geçersiz karakterleri kaldırın.  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz `CleanInput` kullanıcı girişi kabul eden bir metin alanına girilen zararlı karakter Kendiyle Bu örnekte tanımlanan yöntemi. Bu durumda, `CleanInput` nokta (.) dışındaki tüm alfasayısal olmayan karakterleri çıkış sembol kaldırır. (@), tire (-) ve kalan dize döndürür. Ancak, bir giriş dizesinde dahil edilmemesi gereken herhangi bir karakter çıkış kaldırır, böylece normal ifade deseni değiştirebilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade deseni `[^\w\.@-]` bir sözcük karakteri olmayan herhangi bir karakterle eşleşen bir süresi, bir sembol veya tire @. Bir sözcük karakteri, herhangi bir harf, ondalık basamak veya alt çizgi gibi noktalama Bağlayıcısı ' dir. Bu desenle eşleşen herhangi bir karakterle değiştirilir <xref:System.String.Empty?displayProperty=nameWithType>, değiştirme deseni tarafından tanımlanan bir dize olduğu. Uygulamasında kullanıcı girdisi ek karakterler izin vermek için bu karakterler normal ifade deseninde karakter sınıfı ekleyin. Örneğin, normal ifade deseni `[^\w\.@-\\%]` bir giriş dizesindeki bir yüzde sembolü ve ters eğik çizgi de sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
