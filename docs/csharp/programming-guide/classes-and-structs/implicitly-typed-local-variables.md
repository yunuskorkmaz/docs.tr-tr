---
title: Örtülü olarak yazılan yerel değişkenler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399828"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtülü olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)

Yerel değişkenler açık bir tür vermeden bildirilebilir. Anahtar `var` kelime, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler. Çıkarılan tür yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework sınıf kitaplığında tanımlanan bir tür olabilir. Dizileri `var`nasıl başharfe çevireceklerine ilişkin daha fazla bilgi için [bkz.](../arrays/implicitly-typed-arrays.md)

Aşağıdaki örnekler, yerel değişkenlerin aşağıdakilerle `var`bildirilebileceği çeşitli yolları göstermektedir:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Anahtar kelimenin `var` "varyant" anlamına gelmediğini ve değişkenin gevşek veya geç bağlı olduğunu göstermediğini anlamak önemlidir. Bu sadece derleyici belirler ve en uygun türü atar anlamına gelir.

Anahtar `var` kelime aşağıdaki bağlamlarda kullanılabilir:

- Önceki örnekte gösterildiği gibi yerel değişkenler (yöntem kapsamında bildirilen değişkenler) üzerinde.

- Başlangıç bildirimi [için.](../../language-reference/keywords/for.md)

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- [Foreach](../../language-reference/keywords/foreach-in.md) başlatma deyiminde.

    ```csharp
    foreach (var item in list) {...}
    ```

- Bir [açıklama kullanarak.](../../language-reference/keywords/using-statement.md)

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Daha fazla bilgi için, [sorgu ifadesinde örtülü olarak yazılan yerel değişkenleri ve dizileri nasıl kullanacağız'](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)a bakın.

## <a name="var-and-anonymous-types"></a>var ve anonim türleri

Birçok durumda kullanımı `var` isteğe bağlıdır ve sadece bir sözdizimsiz kolaylıktır. Ancak, bir değişken anonim bir türle başharfe `var` atıldığında, değişkeni daha sonraki bir noktada nesnenin özelliklerine erişmeniz gerekiyormuş gibi bildirmeniz gerekir. Bu, LINQ sorgu ifadelerinde sık karşılaşılan bir senaryodur. Daha fazla bilgi için [Bkz. Anonim Türler.](anonymous-types.md)

Kaynak kodunuz açısından, anonim bir türün adı yoktur. Bu nedenle, bir sorgu değişkeni `var`ile başharfe vurulmuşsa, nesnelerin döndürülen dizisindeki `var` özelliklere erişmenin tek yolu `foreach` deyimdeki yineleme değişkeninin türü olarak kullanmaktır.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kısıtlamalar örtülü olarak yazılan değişken bildirimleri için geçerlidir:

- `var`yalnızca yerel bir değişken aynı ifadede beyan edilip başharfe geçtiğinde kullanılabilir; değişken null veya bir yöntem grubu veya anonim bir işlev için başharf olamaz.

- `var`sınıf kapsamındaki alanlarda kullanılamaz.

- Initialization ifadesinde `var` kullanılarak bildirilen değişkenler kullanılamaz. Başka bir deyişle, bu `int i = (i = 20);` ifade yasaldır: ancak bu ifade derleme zamanı hatası üretir:`var i = (i = 20);`

- Aynı ifadede birden çok örtük olarak yazılan değişken ler baş harfe çevrilemez.

- Adlandırılmış `var` bir tür kapsamdaysa, `var` anahtar kelime bu tür adına çözülür ve örtülü olarak yazılan yerel değişken bildiriminin bir parçası olarak kabul edilmez.

`var` Anahtar kelimeile örtülü yazma yalnızca yerel yöntem kapsamındaki değişkenlere uygulanabilir. C# derleyicisi kodu işlediği için mantıksal bir paradoksla karşılaşacağı için sınıf alanları için örtük yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türünü belirleyemez ve ifade türünü bilmeden değerlendirilemez. Aşağıdaki kodu inceleyin:

```csharp
private var bookTitles;
```

`bookTitles`türü `var`verilen bir sınıf alanıdır. Alanın değerlendirilecek bir ifadesi olmadığından, derleyicinin ne tür `bookTitles` olması gerektiği hakkında bilgi alması mümkün değildir. Buna ek olarak, alana bir ifade eklemek (yerel bir değişken için yaptığınız gibi) da yetersizdir:

```csharp
private var bookTitles = new List<string>();
```

Derleyici kod derlemesi sırasında alanlarla karşılaştığında, onunla ilişkili ifadeleri işlemeden önce her alanın türünü kaydeder. Derleyici ayrıştırmaya çalışırken aynı paradoksla karşılaşır `bookTitles`: alanın türünü bilmesi gerekir, ancak derleyici `var`normalde ifadeyi analiz ederek 'ın türünü belirler, bu da önceden türünü bilmeden mümkün değildir.

Sorgu değişkeninin tam olarak oluşturulmuş türünü belirlemenin zor olduğu sorgu ifadeleri ile de yararlı `var` olabileceğini görebilirsiniz. Bu gruplandırma ve sıralama işlemleri ile oluşabilir.

Anahtar `var` kelime, değişkenin belirli türü klavyede yazmak için can sıkıcı olduğunda veya açık olduğunda veya kodun okunabilirliğine katkıda bulunmuyorsa da yararlı olabilir. Bu şekilde `var` yararlı olduğu bir örnek, grup işlemleriile kullanılanlar gibi iç içe genel türleri ile. Aşağıdaki sorguda, sorgu değişkeninin `IEnumerable<IGrouping<string, Student>>`türü . Siz ve kodunuzu korumanız gereken diğer kişiler bunu anladığınız sürece, kolaylık ve kısalık için örtülü yazıyazmakta bir sorun yoktur.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Kullanımı, `var` kodunuzu basitleştirmeye yardımcı olur, ancak kullanımı gerekli olduğu durumlarda veya kodunuzu okunmasını kolaylaştırdığında kısıtlanmalıdır. Ne zaman düzgün kullanılacağı `var` hakkında daha fazla bilgi için, C# Kodlama Yönergeleri makalesinde [Örtük olarak yazılan yerel değişkenler](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [Örtük Olarak Yazılan Diziler](../arrays/implicitly-typed-arrays.md)
- [Sorgu ifadesinde örtülü olarak yazılan yerel değişkenler ve diziler nasıl kullanılır?](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonim Türler](anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [LINQ (Dil-Entegre Sorgu)](../../linq/index.md)
- [Için](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [Ekstresi'ni kullanma](../../language-reference/keywords/using-statement.md)
