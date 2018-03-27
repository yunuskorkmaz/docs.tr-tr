---
title: Normal İfadelerdeki Karakter Çıkışları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a4ec10bfa332c8caafce57385791d8069a7231a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="character-escapes-in-regular-expressions"></a>Normal İfadelerdeki Karakter Çıkışları
Ters eğik çizgi (\\) normal ifadede aşağıdakilerden birini gösterir:  
  
-   Aşağıdaki bölümde yer alan tabloda gösterilen aynıdır, bunu izleyen karakterin bir özel karakter kullanır. Örneğin, `\b` bir normal ifade eşleştirmesi word sınırında başlayacağını belirtir bağlantıdır `\t` bir sekme temsil eder ve `\x020` bir alanı temsil eder.  
  
-   Atlanmayan dil yapısı tam anlamıyla yorumlanması gerektiğini gibi Aksi takdirde yorumlanacağını karakter. Örneğin, bir küme parantezi (`{`) bir nicelik, ancak eğik çizgi ve ayraç tarafından tanımını başlar (`\{`) normal ifade altyapısı parantezi eşleşmelidir gösterir. Benzer şekilde, tek bir ters eğik çizgi Atlanan dil yapısı, ancak iki ters eğik çizgi başlangıcını işaretleyen (`\\`) normal ifade altyapısı ters eğik çizgi eşleşmelidir gösterir.  
  
> [!NOTE]
>  Karakter çıkışları normal ifade desenleri ancak değiştirme desenleri tanınır.  
  
## <a name="character-escapes-in-net"></a>.NET karakter çıkışları  
 Aşağıdaki tabloda .NET normal ifadelerde tarafından desteklenen karakter çıkışları listeler.  
  
|Karakter ya da sırası|Açıklama|  
|---------------------------|-----------------|  
|Aşağıdakiler dışında tüm karakterler:<br /><br /> biçimindeki telefon numarasıdır. $ ^ { [ ( &#124; ) * + ? \|Listelenenler dışında karakterler **karakter ya da dizisi** sütun normal ifadelerde özel bir anlamı yoktur; bunların kendileri eşleşmesi.<br /><br /> İçindeki karakterleri **karakter ya da dizisi** sütun öğeleridir özel normal ifade dili. Normal ifadede eşleştirmek için bunlar kaçışlı veya gereken dahil bir [pozitif karakter grubu](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Örneğin, normal ifade `\$\d+` veya `[$]\d+` "$1200" ile eşleşir.|  
|`\a`|Zil (uyarı) bir karakterle eşleşir `\u0007`.|  
|`\b`|İçinde bir `[` *character_group* `]` karakter sınıfı, geri alma, bir eşleşme `\u0008`.  (Bkz [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Karakter sınıfı dışında `\b` word sınır eşleşen bir bağlantıdır. (Bkz [bağlayıcılarını](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Bir sekme eşleşen `\u0009`.|  
|`\r`|Bir satır başı, eşleşen `\u000D`. Unutmayın `\r` yeni satır karakteri için eşdeğer olmayan `\n`.|  
|`\v`|Dikey sekme eşleşen `\u000B`.|  
|`\f`|Form besleme, eşleşen `\u000C`.|  
|`\n`|Yeni bir satırla eşleşen `\u000A`.|  
|`\e`|Bir kaçış eşleşen `\u001B`.|  
|`\` *nnn*|ASCII karakter eşleşme nerede *nnn* sekizli karakter kodunu temsil eden iki veya üç basamak oluşur. Örneğin, `\040` bir boşluk karakteri temsil eder. Yalnızca bir basamak varsa, bu yapıyı yeniden başvuru yorumlanır (örneğin, `\2`) veya yakalamayla grup sayısı karşılık gelir. (Bkz [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|ASCII karakter eşleşme nerede *nn* iki basamaklı onaltılı karakter kodu.|  
|`\c` *X*|Denetim karakteri Harf X, ASCII denetim karakterle eşleşir. Örneğin, `\cC` CTRL-c|  
|`\u` *nnnn*|Değeri UTF-16 kod birimi eşleşen *nnnn* onaltılık. **Not:** Unicode belirtmek için kullanılan Perl 5 karakteri kaçış .NET tarafından desteklenmiyor. Perl 5 karakteri kaçış bir biçime sahip `\x{` *####* `…}`, burada *####* `…` onaltılık basamak dizisidir. Bunun yerine, kullanın `\u` *nnnn*.|  
|`\`|Kaçış karakterli bir karakter olarak tanınmıyor bir karakter ve ardından, bu karakterle eşleşir. Örneğin, `\*` bir yıldız işareti (*) ile eşleşen ve aynı `\x2A`.|  
  
## <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnek, normal ifadede karakter çıkışları kullanımını göstermektedir. 2009'dünyanın en büyük şehirler ve bunların ortalamaya adlarını içeren bir dize ayrıştırır. Her şehir adı kendi popülasyondan bir sekmeyle ayrılmış (`\t`) veya dikey çubuk (&#124; veya `\u007c`). Tek tek şehirler ve bunların ortalamaya birbirinden bir satır başı ve satır besleme tarafından ayrılır.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Normal ifade `\G(.+)[\t|\u007c](.+)\r?\n` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\G`|Burada son eşleşme sona erdi eşleşme başlayın.|  
|`(.+)`|Herhangi bir karakter, bir veya birden çok kez aynı. Bu ilk yakalama grubudur.|  
|`[\t\u007c]`|Sekme eşleşen (`\t`) veya dikey çubuk (&#124;).|  
|`(.+)`|Herhangi bir karakter, bir veya birden çok kez aynı. Bu ikinci yakalama grubudur.|  
|`\r?\n`|Ardından yeni bir satır başı sıfır veya bir örneğini Bul.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
