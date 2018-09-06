---
title: Normal İfadelerdeki Karakter Çıkışları
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f19cbf305165c2553d5a493f7011a6aea19fb23
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671323"
---
# <a name="character-escapes-in-regular-expressions"></a>Normal İfadelerdeki Karakter Çıkışları
Ters eğik çizgi (\\) normal bir ifadede aşağıdakilerden birini gösterir:  
  
-   Aşağıdaki bölümde yer alan tabloda gösterilen aynıdır, onu izleyen karakterin özel bir karakter kullanır. Örneğin, `\b` bir normal ifade eşleştirmesi bir sözcük sınırında başlayacağını belirtir bir tutturucudur `\t` bir sekme temsil eder ve `\x020` bir alanını temsil eder.  
  
-   Atlanmayan dil yapısı tam anlamıyla yorumlanması gerektiğini gibi yoksa yorumlanacağını bir karakter. Örneğin, bir küme ayracı (`{`) bir miktar belirleyiciyi, ancak eğik çizgi ve ayraç tarafından tanımını başlar (`\{`) gösterir ve normal ifade altyapısının küme ayracı eşleşmesi gerekir. Benzer şekilde, tek bir ters eğik çizgi kaçış dil yapısı, ancak iki ters eğik çizgi başlangıcını işaretleyen (`\\`) normal ifade altyapısı ters eğik çizgiyi eşleşmelidir gösterir.  
  
> [!NOTE]
>  Karakter çıkışları, normal ifade desenleri ancak değiştirme desenleri tanınır.  
  
## <a name="character-escapes-in-net"></a>.NET içinde karakter çıkışları  
 Aşağıdaki tablo, .NET içinde normal ifadeler tarafından desteklenen karakter çıkışları listeler.  
  
|Karakter veya dizisi|Açıklama|  
|---------------------------|-----------------|  
|Aşağıdakiler dışında tüm karakterleri:<br /><br /> biçimindeki telefon numarasıdır. $ ^ { [ ( &#124; ) * + ? \ |Listelenenler dışında karakterler **karakter veya dizisi** sütun normal ifadeler özel bir anlamı vardır; bunların kendileri eşleşmesi.<br /><br /> İçindeki karakterleri **karakter veya dizisi** sütun, özel normal ifade dil öğe. Normal bir ifadede ayarlarla eşleşecek şekilde bunlar kaçış karakterleri veya gereken dahil bir [pozitif karakter grubu](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Örneğin, normal ifade `\$\d+` veya `[$]\d+` "$1200" ile eşleşir.|  
|`\a`|Zil (alarm) bir karakterle eşleşir `\u0007`.|  
|`\b`|İçinde bir `[` *character_group* `]` karakter sınıfı, Geri Al, bir eşleşme `\u0008`.  (Bkz [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Bir karakter sınıfı dışında `\b` bir sözcük sınırı eşleşen bir tutturucudur. (Bkz [bağlayıcılarını](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Bir sekmeyle eşleşir, `\u0009`.|  
|`\r`|Bir satır başı, eşleşen `\u000D`. Unutmayın `\r` yeni satır karakteri eşdeğer değildir `\n`.|  
|`\v`|Bir dikey sekmeyle eşleşir, `\u000B`.|  
|`\f`|Bir form besleme, eşleşen `\u000C`.|  
|`\n`|Yeni bir satırla eşleşir `\u000A`.|  
|`\e`|Bir çıkışla eşleşir `\u001B`.|  
|`\` *nnn*|ASCII karakterleriyle eşleşir burada *nnn* sekizli karakter kodunu temsil eden iki veya üç basamak içerir. Örneğin, `\040` bir boşluk karakteri temsil eder. Yalnızca bir basamak varsa, bu yapı bir yeniden başvuru yorumlanır (örneğin, `\2`) veya bir yakalama grubu sayısı karşılık gelirse. (Bkz [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|ASCII karakterleriyle eşleşir burada *nn* iki basamaklı onaltılık karakter kodu.|  
|`\c` *X*|X'harfinin denetim karakteri olduğu bir ASCII denetim karakteriyle eşleşir. Örneğin, `\cC` CTRL-c|  
|`\u` *nnnn*|Eşleşen değeri olan bir UTF-16 kod birimini *nnnn* onaltılık. **Not:** Unicode belirtmek için kullanılan Perl 5 karakter kaçış .NET tarafından desteklenmez. Perl 5 karakter kaçış formundadır `\x{` *####* `…}`burada *####* `…` bir dizi onaltılık basamak. Bunun yerine, `\u` *nnnn*.|  
|`\`|Kaçış karakteri tanınmayan bir karakterle önce geldiğinde karakterle eşleşir. Örneğin, `\*` yıldız işareti (*) ile eşleşir ve aynı `\x2A`.|  
  
## <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnek, bir normal ifadede karakter çıkışları kullanımını gösterir. Bu, 2009'dan dünyanın en büyük şehirlerin ve bunların yerleştirme adlarını içeren bir dizeyi ayrıştırır. Her şehir adı, bir sekmeyle kendi popülasyondan ayrıldığı (`\t`) ya da dikey çubuk (&#124; veya `\u007c`). Tek tek Şehir ve bunların yerleştirme birbirinden bir satır başı ve satır besleme tarafından ayrılır.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Normal ifade `\G(.+)[\t|\u007c](.+)\r?\n` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\G`|Burada da son eşleşmenin sona erdiği eşleşmeye başla.|  
|`(.+)`|Herhangi bir karakter, bir veya daha fazla kez eşleştirin. Bu ilk yakalama grubudur.|  
|`[\t\u007c]`|Eşleşen bir sekme (`\t`) ya da dikey çubuk (&#124;).|  
|`(.+)`|Herhangi bir karakter, bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|  
|`\r?\n`|Bir yeni satırın izlediği bir satır başı sıfır veya bir oluşumunu eşleştirin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
