---
title: Dizeleri alt dizelere ayır
description: String. Split, normal ifadeler ve String. SUBSTRING dahil olmak üzere bir dizenin parçalarını ayıklamaya yönelik farklı teknikler hakkında bilgi edinin.
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: 88947c4576b0496e4b4e45042d665e3ca5857c53
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403632"
---
# <a name="extract-substrings-from-a-string"></a>Dizeden alt dizeleri Ayıkla

Bu makalede bir dizenin parçalarını ayıklamanıza yönelik bazı farklı teknikler ele alınmaktadır.

- İstediğiniz alt dizeler bilinen bir sınırlandırma karakteriyle (veya karakterler) ayrıldığı sırada [split yöntemini](#stringsplit-method) kullanın.
- [Normal ifadeler](#regular-expressions) , dize sabit bir düzene uygun olduğunda faydalıdır.
- Bir dizedeki *Tüm* alt dizeleri ayıklamak Istemediğinizde, [IndexOf ve substring yöntemlerini](#stringindexof-and-stringsubstring-methods) birlikte kullanın.

## <a name="stringsplit-method"></a>String. Split yöntemi

<xref:System.String.Split%2A?displayProperty=nameWithType> belirlediğiniz bir veya daha fazla sınırlandırma karakteri temelinde bir dizeyi bir alt dizeler grubuna bölmek için yardımcı olmak üzere çok sayıda aşırı yükleme sağlar. Son sonuçdaki toplam alt dize sayısını sınırlayabilirsiniz, alt dizelerin boşluk karakterlerini kırpabilir veya boş alt dizeleri dışlayabilirsiniz.

Aşağıdaki örneklerde üç farklı aşırı yüklemesi gösterilmektedir `String.Split()` . İlk örnek, <xref:System.String.Split(System.Char[])> hiçbir ayırıcı karakter geçirmeden aşırı yüklemeyi çağırır. Herhangi bir sınırlandırma karakteri belirtmezseniz, `String.Split()` dizeyi ayırmak için boşluk karakterleri olan varsayılan sınırlayıcıları kullanır.

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

Gördüğünüz gibi, nokta karakterleri ( `.` ) alt dizelerin iki içine dahil edilir. Süre karakterlerini dışlamak istiyorsanız, Period karakterini ek sınırlandırma karakteri olarak ekleyebilirsiniz. Sonraki örnekte bunun nasıl yapılacağı gösterilmektedir.

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

Dönemler alt dizelerdeki çıktı, ancak artık iki ek boş alt dize eklenmiştir. Bu boş alt dize, sözcük ve onu izleyen nokta arasındaki alt dizeyi temsil eder. Sonuç dizisindeki boş alt dizeleri atlamak için, <xref:System.String.Split(System.Char[],System.StringSplitOptions)> aşırı yüklemeyi çağırabilir ve <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametresi için belirtebilirsiniz `options` .

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a>Normal ifadeler

Dizeniz sabit bir düzene uyuyorsa, öğelerini ayıklamak ve işlemek için normal bir ifade kullanabilirsiniz. Örneğin, dizeler " *Number* *Operand* *Number* " biçimini alıyorsa, dizenin öğelerini ayıklamak ve işlemek için [normal bir ifade](regular-expressions.md) kullanabilirsiniz. İşte bir örnek:

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

Normal ifade deseninin `(\d+)\s+([-+*/])\s+(\d+)` şöyle olduğu tanımlanır:

|Desen|Açıklama|
|-------------|-----------------|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ilk yakalama grubudur.|
|`\s+`|Bir veya daha fazla boşluk karakteri eşleştirin.|
|`([-+*/])`|Aritmetik işleç işaretiyle Eşleştir (+,-, *, veya/). Bu ikinci yakalama grubudur.|
|`\s+`|Bir veya daha fazla boşluk karakteri eşleştirin.|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|

Ayrıca, sabit bir karakter kümesi yerine bir düzene göre bir dizeden alt dizeleri ayıklamak için normal bir ifade kullanabilirsiniz. Bu koşullardan biri gerçekleştiğinde yaygın bir senaryodur:

- Sınırlayıcı karakterlerden biri veya birkaçı *her zaman* örnekteki sınırlayıcı olarak görev yapmaz <xref:System.String> .

- Sınırlayıcı karakterlerin sırası ve sayısı değişken veya bilinmiyor.

Örneğin, <xref:System.String.Split%2A> yöntemi aşağıdaki dizeyi ayırmak için kullanılamaz, çünkü `\n` (yeni satır) karakter değişken olduğundan ve her zaman sınırlayıcılar olarak kullanılmazlar.

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

Aşağıdaki örnekte gösterildiği gibi, normal bir ifade bu dizeyi kolayca bölebilir.

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

Normal ifade deseninin `\[([^\[\]]+)\]` şöyle olduğu tanımlanır:

|Desen|Açıklama|
|-------------|-----------------|
|`\[`|Açma köşeli ayracını eşleştirin.|
|`([^\[\]]+)`|Bir veya daha fazla kez açma veya kapatma ayracı olmayan herhangi bir karakterle eşleştirin. Bu ilk yakalama grubudur.|
|`\]`|Bir kapanış parantezini eşleştirin.|

<xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>Yöntemi <xref:System.String.Split%2A?displayProperty=nameWithType> , bir dizeyi sabit karakter kümesi yerine normal ifade düzenine göre bölünmeyeceği dışında, ile neredeyse aynıdır. Örneğin, aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> çeşitli tire ve diğer karakter birleşimleri ile ayrılmış alt dizeler içeren bir dizeyi ayırmak için yöntemini kullanır.

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

Normal ifade deseninin `\s-\s?[+*]?\s?-\s` şöyle olduğu tanımlanır:

|Desen|Açıklama|
|-------------|-----------------|
|`\s-`|Bir boşluk karakteri ve ardından bir tire ile eşleştirin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`[+*]?`|+ Ya da * karakterinin sıfır veya bir oluşumunu eşleştirin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`-\s`|Bir kısa çizgi karakteri ve ardından boşluk karakteri ile eşleştirin.|

## <a name="stringindexof-and-stringsubstring-methods"></a>String. IndexOf ve String. SUBSTRING yöntemleri

Bir dizedeki tüm alt dizeleri ilgilenmiyorsanız, eşleşmenin başladığı dizini döndüren dize karşılaştırma yöntemlerinden biriyle çalışmayı tercih edebilirsiniz. Daha sonra istediğiniz alt <xref:System.String.Substring%2A> dizeyi ayıklamak için yöntemini çağırabilirsiniz. Dize karşılaştırma yöntemleri şunları içerir:

- <xref:System.String.IndexOf%2A>, bir dize örneğindeki bir karakter veya dizenin ilk oluşumunun sıfır tabanlı dizinini döndürür.

- <xref:System.String.IndexOfAny%2A>, bir karakter dizisindeki herhangi bir karakterin geçerli dize örneğindeki sıfır tabanlı dizini döndürür.

- <xref:System.String.LastIndexOf%2A>, bir dize örneğindeki bir karakter veya dizenin son oluşumunun sıfır tabanlı dizinini döndürür.

- <xref:System.String.LastIndexOfAny%2A>, bir karakter dizisindeki herhangi bir karakterin geçerli dize örneğinde sıfır tabanlı bir dizin döndüren.

Aşağıdaki örnek, <xref:System.String.IndexOf%2A> bir dizedeki dönemleri bulmak için yöntemini kullanır. Ardından, <xref:System.String.Substring%2A> tam tümceler döndürmek için yöntemini kullanır.

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te temel dize işlemleri](basic-string-operations.md)
- [.NET normal ifadeleri](regular-expressions.md)
- [C 'de dize. Split kullanarak dizeleri ayrıştırma #](../../csharp/how-to/parse-strings-using-split.md)
