---
title: Örtük olarak yazılan yerel değişkenler-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 842f73b7af9671157495df961f5db22702ae897e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240713"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtük olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)

Yerel değişkenler açık bir tür vermeden bildirilebilecek. `var`Anahtar sözcüğü, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler. Çıkarsanan tür yerleşik bir tür, anonim tür, Kullanıcı tanımlı tür veya .NET sınıf kitaplığı 'nda tanımlanmış bir tür olabilir. İle dizileri başlatma hakkında daha fazla bilgi için `var` bkz. [örtülü olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).

Aşağıdaki örneklerde, yerel değişkenlerin ile bildirilebilecek çeşitli yollar gösterilmektedir `var` :

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

`var`Anahtar sözcüğünün "varyant" anlamına gelmeyeceğini ve değişkenin gevşek olarak yazılmış olduğunu veya geç bağlandığını belirtmeyeceğini anlamak önemlidir. Yalnızca derleyicinin en uygun türü belirlediği ve atayacağı anlamına gelir.

`var`Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:

- Yerel değişkenlerde (Yöntem kapsamında belirtilen değişkenler) önceki örnekte gösterildiği gibi.

- [For](../../language-reference/keywords/for.md) Initialization ifadesinde.

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- Bir [foreach](../../language-reference/keywords/foreach-in.md) başlatma bildiriminde.

    ```csharp
    foreach (var item in list) {...}
    ```

- Bir [using](../../language-reference/keywords/using-statement.md) ifadesinde.

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Daha fazla bilgi için bkz. [bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var ve anonim türler

Çoğu durumda, kullanımı `var` isteğe bağlıdır ve yalnızca sözdizimsel bir kolaylık vardır. Ancak, bir değişken anonim bir türle başlatıldığında, `var` nesnenin özelliklerine sonraki bir noktada erişmeniz gerekiyorsa değişkeni bildirmeniz gerekir. Bu, LINQ sorgu ifadelerinde yaygın bir senaryodur. Daha fazla bilgi için bkz. [anonim türler](anonymous-types.md).

Kaynak kodunuzun perspektifinden adsız bir türün adı yoktur. Bu nedenle, bir sorgu değişkeni ile başlatılmış ise `var` , nesne dizisinde döndürülen özelliklere erişmenin tek yolu, `var` deyimindeki yineleme değişkeninin türü olarak kullanmaktır `foreach` .

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kısıtlamalar, örtük olarak belirlenmiş değişken bildirimleri için geçerlidir:

- `var`yalnızca yerel bir değişken aynı deyimde bildirildiği ve başlatıldığı zaman kullanılabilir; değişken null veya bir yöntem grubuna veya anonim işleve başlatılamaz.

- `var`sınıf kapsamındaki alanlarda kullanılamaz.

- Kullanılarak belirtilen değişkenler `var` başlatma ifadesinde kullanılamaz. Diğer bir deyişle, bu ifade geçerlidir: `int i = (i = 20);` ancak bu ifade derleme zamanı hatası oluşturur:`var i = (i = 20);`

- Birden çok örtük olarak yazılmış değişkenler aynı ifadede başlatılamaz.

- Adlandırılmış bir tür `var` kapsamdadır, `var` anahtar sözcüğü bu tür adına çözümlenir ve örtük olarak yazılmış bir yerel değişken bildiriminin parçası olarak değerlendirilmez.

Anahtar sözcükle örtük yazma `var` yalnızca yerel Yöntem kapsamındaki değişkenlere uygulanabilir. C# derleyicisi kod işlendiği için bir mantıksal Paradox ile karşılaşacağından, sınıf alanları için örtük yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türü belirleyemez ve ifade türü bilmeden değerlendirilemiyor. Aşağıdaki kodu inceleyin:

```csharp
private var bookTitles;
```

`bookTitles`, türü verilen bir sınıf alanıdır `var` . Alanın değerlendirilecek bir ifadesi olmadığından, derleyicinin ne tür olması gerektiğini çıkarması olanaksızdır `bookTitles` . Ayrıca, alana bir ifade eklemek (yerel bir değişken gibi) de yeterli değildir:

```csharp
private var bookTitles = new List<string>();
```

Derleyici kod derleme sırasında alanlarla karşılaştığında, onunla ilişkili herhangi bir ifadeyi işlemeden önce her alanın türünü kaydeder. Derleyici ayrıştırmaya çalışan aynı Paradox ile karşılaştığında `bookTitles` : alanın türünü bilmesi gerekir, ancak derleyici, bu türü `var` önceden bilmeden ifadeyi analiz ederek normalde türünü tespit edecektir.

`var`Sorgu değişkeninin tam olarak oluşturulan türünün belirlenmesi zor olduğu sorgu ifadeleri ile de yararlı olabileceğini fark edebilirsiniz. Gruplandırma ve sıralama işlemlerinde bu durum oluşabilir.

`var`Anahtar sözcüğü, değişkenin belirli türü klavyede yazmak sıkıcı veya belirgin olduğunda ya da kodun okunabilirliğini eklememe olduğunda da yararlı olabilir. `var`Bu şekilde yararlı olduğu bir örnek, Grup işlemleriyle kullanılanlar gibi iç içe geçmiş genel türlerdir. Aşağıdaki sorguda, sorgu değişkeninin türü `IEnumerable<IGrouping<string, Student>>` . Siz ve kodunuzun bakımını yapmak zorunda olan başkaları bunu anlamış olduğu sürece, kolaylık ve kısaltma için örtük yazma kullanmayla ilgili bir sorun yoktur.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Kullanımı, `var` kodunuzun basitleştirilmesine yardımcı olur, ancak kullanımı gereken durumlarda veya kodunuzun daha kolay okunması durumunda kullanılması gerekir. Düzgün olarak ne zaman kullanılacağı hakkında daha fazla bilgi için `var` C# kodlama yönergeleri makalesindeki [örtülü olarak yazılan yerel değişkenler](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [Türü Örtük Olarak Belirlenmiş Diziler](../arrays/implicitly-typed-arrays.md)
- [Sorgu ifadesinde türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri kullanma](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonim Türler](anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
- [l](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/index.md)
- [:](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
