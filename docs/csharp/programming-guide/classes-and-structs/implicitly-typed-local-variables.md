---
title: Örtük olarak yazılan yerel değişkenler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241006"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtük olarak yazılan yerel değişkenlerC# (Programlama Kılavuzu)

Yerel değişkenler açık bir tür vermeden bildirilebilecek. `var` anahtar sözcüğü, derleyiciye, başlatma deyiminin sağ tarafındaki ifadeden değişkenin türünü çıkarmasını söyler. Çıkarsanan tür bir yerleşik tür, anonim tür, Kullanıcı tanımlı tür veya .NET Framework sınıf kitaplığında tanımlanmış bir tür olabilir. Dizileri `var`ile başlatma hakkında daha fazla bilgi için, bkz. [örtülü olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).

Aşağıdaki örneklerde, yerel değişkenlerin `var`ile bildirilebilecek çeşitli yolları gösterilmektedir:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

`var` anahtar sözcüğünün "değişken" anlamına gelmeyeceğini ve değişkenin gevşek olarak yazılmış olduğunu veya geç bağlandığını belirtmeyeceğini anlamak önemlidir. Yalnızca derleyicinin en uygun türü belirlediği ve atayacağı anlamına gelir.

`var` anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:

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

Çoğu durumda `var` kullanımı isteğe bağlıdır ve yalnızca sözdizimsel bir kolaylık vardır. Ancak, bir değişken anonim bir türle başlatıldığında, nesnenin özelliklerine sonraki bir noktada erişmeniz gerekiyorsa değişkeni `var` olarak bildirmeniz gerekir. Bu, LINQ sorgu ifadelerinde yaygın bir senaryodur. Daha fazla bilgi için bkz. [anonim türler](anonymous-types.md).

Kaynak kodunuzun perspektifinden adsız bir türün adı yoktur. Bu nedenle, bir sorgu değişkeni `var`ile başlatılmışsa, nesne dizisinde döndürülen özelliklere erişmenin tek yolu, `foreach` deyimindeki yineleme değişkeninin türü olarak `var` kullanmaktır.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Açıklamalar

Aşağıdaki kısıtlamalar, örtük olarak belirlenmiş değişken bildirimleri için geçerlidir:

- `var`, yalnızca yerel bir değişken aynı deyimde bildirildiği ve başlatıldığı zaman kullanılabilir; değişken null veya bir yöntem grubuna veya anonim işleve başlatılamaz.

- `var` sınıf kapsamındaki alanlarda kullanılamaz.

- `var` kullanılarak belirtilen değişkenler başlatma ifadesinde kullanılamaz. Diğer bir deyişle, bu ifade geçerli: `int i = (i = 20);` ancak bu ifade derleme zamanı hatası veriyor: `var i = (i = 20);`

- Birden çok örtük olarak yazılmış değişkenler aynı ifadede başlatılamaz.

- `var` adlı bir tür kapsamdadır, `var` anahtar sözcüğü bu tür adına çözümlenir ve örtük olarak yazılmış bir yerel değişken bildiriminin parçası olarak değerlendirilmez.

`var` anahtar sözcüğüyle örtük yazma, yalnızca yerel Yöntem kapsamındaki değişkenlere uygulanabilir. C# Derleyici, kodu işlediği bir mantıksal Paradox ile karşılaşacağından, sınıf alanları için örtülü yazma kullanılamaz: derleyicinin alanın türünü bilmesi gerekir, ancak atama ifadesi çözümlenene kadar türü belirleyemez ve ifade türü bilmeden değerlendirilemiyor. Aşağıdaki kodu göz önünde bulundurun:

```csharp
private var bookTitles;
```

`bookTitles`, `var`türü verilen bir sınıf alanıdır. Alan değerlendirilecek bir ifadeye sahip olmadığı için derleyicinin ne tür `bookTitles` olması gerektiğini çıkarması olanaksızdır. Ayrıca, alana bir ifade eklemek (yerel bir değişken gibi) de yeterli değildir:

```csharp
private var bookTitles = new List<string>();
```

Derleyici kod derleme sırasında alanlarla karşılaştığında, onunla ilişkili herhangi bir ifadeyi işlemeden önce her alanın türünü kaydeder. Derleyici, `bookTitles`ayrıştırmaya çalışan aynı Paradox ile karşılaştığında: alanın türünü bilmesi gerekir, ancak derleyici, daha önce türü bilmeden mümkün olmayan ifadeyi analiz ederek normalde `var`türünü saptayabilir.

`var`, sorgu değişkeninin tam olarak oluşturulan türünün belirlenmesi zor olduğu sorgu ifadeleri ile de yararlı olabileceğini fark edebilirsiniz. Gruplandırma ve sıralama işlemlerinde bu durum oluşabilir.

`var` anahtar sözcüğü, değişkenin belirli türü klavyede yazmak sıkıcı veya belirgin olduğunda ya da kodun okunabilirliğini eklememe olduğunda da yararlı olabilir. Bu şekilde `var` yararlı olduğu bir örnek, Grup işlemleriyle kullanılanlar gibi iç içe geçmiş genel türlerdir. Aşağıdaki sorguda, sorgu değişkeninin türü `IEnumerable<IGrouping<string, Student>>`. Siz ve kodunuzun bakımını yapmak zorunda olan başkaları bunu anlamış olduğu sürece, kolaylık ve kısaltma için örtük yazma kullanmayla ilgili bir sorun yoktur.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

`var` kullanımı, kodunuzun basitleştirilmesine yardımcı olur, ancak kullanımı gereken durumlarda veya kodunuzun daha kolay okunması durumunda kullanılması gerekir. `var` düzgün şekilde kullanılacağı hakkında daha fazla bilgi için, C# kodlama yönergeleri makalesindeki [örtük olarak yazılan yerel değişkenler](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [Örtük Olarak Yazılan Diziler](../arrays/implicitly-typed-arrays.md)
- [Sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonim Tipler](anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
