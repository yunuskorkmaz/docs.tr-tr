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
ms.openlocfilehash: 66fe5dd1da148e8afd07ae69cec960438b53536a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567360"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma
Aşağıdaki örnek, statik kullanır <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> bir dizeden geçersiz karakterleri Şerit yöntemi.  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz `CleanInput` Bu örnekte, kullanıcı girişi kabul eden bir metin alanına girilen zararlı olabilecek karakterleri Şerit tanımlanmış yöntemi. Bu durumda, `CleanInput` nokta (.) dışındaki tüm alfasayısal olmayan karakterler çıkışı konumundaki simgeleri kaldırır (@), tire (-) ve kalan dize döndürür. Ancak, böylece bir giriş dizesi içinde dahil edilmemesi gereken herhangi bir karakteri çıkışı şeritler normal ifade deseni değiştirebilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Normal ifade deseni `[^\w\.@-]` bir sözcük karakteriyle değil herhangi bir karakterle eşleşir bir nokta, bir simge veya tire @. Bir word herhangi harf, ondalık sayı veya alt çizgi gibi noktalama bağlayıcı karakterdir. Bu desenle eşleşen herhangi bir karakter ile değiştirilir <xref:System.String.Empty?displayProperty=nameWithType>, değiştirme düzeni tarafından tanımlanan bir dize değil. Uygulamasında kullanıcı girdisi ek karakterlerine izin vermek için bu karakterleri normal ifade deseni karakter sınıfında ekleyin. Örneğin, normal ifade deseni `[^\w\.@-\\%]` yüzdesi simge ve bir ters eğik çizgi bir giriş dizesi içinde de sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
