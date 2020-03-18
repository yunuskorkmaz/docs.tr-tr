---
title: .NET Düzenli İfadelerde Karakter Kaçışları
description: .NET düzenli ifadelerinde özel karakterler ve kaçan karakterler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
ms.openlocfilehash: 82e60b3cb5eb777d48219209550367642f78d8c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711434"
---
# <a name="character-escapes-in-regular-expressions"></a>Normal İfadelerdeki Karakter Çıkışları
Düzenli bir\\ifadedeki ters eğik çizgi ( ) aşağıdakilerden birini gösterir:  
  
- Aşağıdaki bölümde tabloda gösterildiği gibi, onu izleyen karakter özel bir karakterdir. Örneğin, `\b` normal bir ifade eşleşmesi bir sözcük sınırında `\t` başlaması gerektiğini belirten `\x020` bir çapa, bir sekmeyi temsil eder ve bir alanı temsil eder.  
  
- Aksi takdirde kaçmış olmayan bir dil yapısı olarak yorumlanacak bir karakter kelimenin tam anlamıyla yorumlanmalıdır. Örneğin, bir ayraç (`{`) bir niceleyici tanımını başlatır, ancak`\{`bir destek ( ) tarafından izlenen bir ters çizgi, normal ifade altyapısının ayraçla eşleşmesi gerektiğini gösterir. Benzer şekilde, tek bir ters eğik çizgi, kaçan bir dil`\\`yapısının başlangıcını işaretler, ancak iki ters eğik çizgi ( ) normal ifade altyapısının ters eğik çizgiyle eşleşmesi gerektiğini gösterir.  
  
> [!NOTE]
> Karakter kaçışları normal ifade desenlerinde tanınabilir, ancak değiştirme desenlerinde tanınmaz.  
  
## <a name="character-escapes-in-net"></a>.NET'te Karakter Kaçışları  
 Aşağıdaki tabloda .NET'te normal ifadelerle desteklenen karakter kaçışları listelenir.  
  
|Karakter veya dizi|Açıklama|  
|---------------------------|-----------------|  
|Aşağıdakiler dışında tüm karakterler:<br /><br /> . ^ ^ { [ &#124; ) * + ? \ |**Karakter veya dizi** sütununda listelenenler dışındaki karakterlerin normal ifadelerde özel bir anlamı yoktur; kendi kendilerine eşleşirler.<br /><br /> **Karakter veya sıra** sütununda yer alan karakterler özel normal ifade dili öğeleridir. Bunları normal bir ifadeyle eşleştirmek için, kaçmaları veya pozitif karakter [grubuna](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)dahil edilmeleri gerekir. Örneğin, normal ifade `\$\d+` `[$]\d+` veya "1200 $" eşleşir.|  
|`\a`|Bir çan (alarm) `\u0007`karakteriyle eşleşir.|  
|`\b`|`[` *character_group* karakter sınıfında, bir arka boşlukla eşleşir. `\u0008``]`  [(Bkz. Karakter Sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Karakter sınıfının `\b` dışında, sözcük sınırıyla eşleşen bir çapa dır. (Bkz. [Çapalar](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Bir sekmeyle eşleşir. `\u0009`|  
|`\r`|Bir araba dönüşüyle eşleşiyor. `\u000D` `\r` Yeni satır karakterine eşdeğer olmadığını `\n`unutmayın.|  
|`\v`|Dikey sekmeyle `\u000B`eşleşir.|  
|`\f`|Form akışıyla `\u000C`eşleşir, .|  
|`\n`|Yeni bir çizgiyle `\u000A`eşleşir.|  
|`\e`|Bir kaçışla `\u001B`eşleşiyor.|  
|`\`*nnnn*|*NNN'nin* sekizli karakter kodunu temsil eden iki veya üç basamaktan oluştuğu bir ASCII karakteriyle eşleşir. Örneğin, `\040` bir boşluk karakterini temsil eder. Bu yapı, yalnızca bir basamak (örneğin,) `\2`varsa veya bir yakalama grubunun sayısına karşılık gelen bir geri başvuru olarak yorumlanır. (Bkz. [Backreference Yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x`*nn*|*NN'nin* iki basamaklı bir hexadecimal karakter kodu olduğu bir ASCII karakteriyle eşleşir.|  
|`\c` *X*|X'in denetim karakterinin harfi olduğu bir ASCII denetim karakteriyle eşleşir. Örneğin, `\cC` CTRL-C'dir.|  
|`\u`*nnnnn*|Değeri *nnnn* hexadecimal olan bir UTF-16 kod birimiyle eşleşir. **Not:**  Unicode belirtmek için kullanılan Perl 5 karakter kaçış .NET tarafından desteklenmez. Perl 5 karakter kaçış `\x{` *####* `…}`formu *####* `…` vardır , nerede hexadecimal basamak bir dizi. Bunun yerine, `\u` *nnnn*kullanın.|  
|`\`|Kaçan bir karakter olarak tanınmayan bir karakter tarafından takip edildiğinde, bu karakter eşleşir. Örneğin, `\*` yıldız işaretiyle (*) eşleşir ve `\x2A`.'la aynıdır.|  
  
## <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnek, karakter kaçışlarının normal bir ifadede kullanımını göstermektedir. 2009 yılında dünyanın en büyük şehirlerinin ve popülasyonlarının adlarını içeren bir dize parses. Her şehir adı bir sekme (`\t`) veya dikey bir `\u007c`çubuk (&#124; veya) ile kendi nüfusundan ayrılır. Şehirler ve popülasyonları birbirlerinden bir at arabası dönüşü ve hat beslemesi ile ayrılır.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Normal ifade `\G(.+)[\t|\u007c](.+)\r?\n` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\G`|Son maçın bittiği maça başlayın.|  
|`(.+)`|Herhangi bir karakteri bir veya daha fazla kez eşleştirin. Bu ilk yakalama grubudur.|  
|`[\t\u007c]`|Bir sekmeyi`\t`( ) veya dikey çubuğu (&#124;) eşleştirin.|  
|`(.+)`|Herhangi bir karakteri bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|  
|`\r?\n`|Sıfır'ı veya bir satır dönüşünü niçin yeni bir satırla eşleştirin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
