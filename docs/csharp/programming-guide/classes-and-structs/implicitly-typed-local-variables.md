---
title: Örtük olarak yazılan yerel değişkenler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 8c09ddc5a9db71a4e0bef0434d2fc14a4c088352
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635559"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtük olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)

Yerel değişkenler, açık bir tür vermeden bildirilebilir. `var` Başlatma ifadesinin sağ tarafındaki ifade değişkenin türünü çıkarsamak için derleyicinin anahtar sözcüğü bildirir. Çıkarsanan tür, yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework Sınıf Kitaplığı'nda tanımlı bir tür olabilir. Dizilerle başlatma hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).

Aşağıdaki örnekler, yerel değişkenleri bildirilebilir ile çeşitli şekillerde `var`:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Kavramak önemlidir `var` anahtar sözcüğü, "değişken" anlamına gelmez ve değişken gevşek olduğunu göstermez yazılabilir veya geç bağlama. Yalnızca derleyici belirler ve en uygun türde atar anlamına gelir.

`var` Anahtar sözcüğü aşağıdaki bağlamlarında kullanılabilir:

- Yerel değişkenlere (yöntemi kapsamında bildirilen değişkenler) önceki örnekte gösterildiği gibi.

- İçinde bir [için](../../language-reference/keywords/for.md) başlatma ifadesi.

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- İçinde bir [foreach](../../language-reference/keywords/foreach-in.md) başlatma ifadesi.

    ```csharp
    foreach(var item in list){...}
    ```

- İçinde bir [kullanarak](../../language-reference/keywords/using-statement.md) deyimi.

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Daha fazla bilgi için [nasıl yapılır: Kullanım türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri sorgu ifadesinde](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var ve anonim türler

Çoğu durumda kullanımını `var` isteğe bağlıdır ve yalnızca söz dizimsel kolaylık. Ancak, bir değişken içeren bir anonim tür başlatıldığında olarak değişkeni bildirilmelidir `var` daha sonraki bir noktada nesnenin özelliklerini erişmeniz gerekiyorsa. Bu ortak senaryoda olan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Daha fazla bilgi için [anonim türler](anonymous-types.md).

Kaynak kodunuzu açısından bakıldığında, anonim bir tür adı yok. Bu nedenle, bir sorgu değişkeni ile başlatılmışsa `var`, döndürülen dizi nesnelerin özelliklerine erişmek için tek yolu kullanmaktır sonra `var` yineleme değişkeni türü olarak `foreach` deyimi.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Açıklamalar

Türü örtük olarak belirlenmiş değişken bildirimleri için aşağıdaki kısıtlamalar uygulanır:

- `var` yerel bir değişken bildirildi ve aynı deyimde başlatıldı, yalnızca kullanılabilir; değişkeni, null ya da bir yöntem grubu ya da anonim bir işlevdir başlatılamaz.

- `var` sınıf kapsamı alanları kullanılamaz.

- Kullanılarak bildirilen değişkenler `var` başlatma ifadesinde kullanılamaz. Diğer bir deyişle, bu ifade yasal`: int i = (i = 20);` ancak bu ifade bir derleme zamanı hatası oluşturur: `var i = (i = 20);`

- Aynı deyimde birden fazla örtük olarak yazılan değişkenler başlatılamaz.

- Adlı bir tür ise `var` kapsam içinde olan sonra `var` anahtar sözcüğü bu tür adı için çözümler ve bir örtük olarak belirlenmiş yerel değişken bildirimi bir parçası olarak kabul edilmez.

İle örtülü yazma `var` anahtar sözcüğü yalnızca uygulanabilir yerel yöntemi kapsamda değişkenlere. Örtülü yazma sınıf alanlar için kullanılabilir değil C# derleyici kodu işlendi olarak mantıksal paradox karşılaştığınız: derleyici alanın türünü bilmeniz gerekir, ancak atama ifadesi analiz kadar türü belirlenemiyor ve ifade türü bilmeden değerlendirilemez. Aşağıdaki kodu göz önünde bulundurun:

```csharp
private var bookTitles;
```

`bookTitles` bir sınıf alanı türü verilen `var`. Hesaplanacak ifade yok alana sahip olduğundan, derleyicinin hangi türünün çıkarsanması mümkün değildir `bookTitles` olduğu varsayılır. Ayrıca, (için yerel bir değişken gibi), bir ifade için alan ekleme da yeterli değil:

```csharp
private var bookTitles = new List<string>();
```

Derleyici, alanlar, kod derleme sırasında karşılaştığında, ilişkili tüm ifadeleri işlenmeden önce her alanın türünü kaydeder. Derleyici ayrıştırmaya çalışırken aynı paradox karşılaştığında `bookTitles`: alan türünü bilmeniz gerekir, ancak derleyicinin normalde belirler `var`'s türe göre çözümleme ifade türü önceden bilmeden mümkün değildir.

İlginizi çekebilecek `var` da yararlı sorgu ifadeleri tam olarak yapılandırılmış sorgu değişkeni türünü olduğu saptamak zor olabilir. Bu gruplandırma ve sıralama işlemleri ile ortaya çıkabilir.

`var` Anahtar sözcüğü de yararlı olabilir değişkeni türünü yorucu bir süreç klavyede yazın veya açıktır veya kodun okunabilirliğini eklemez. Bir örnek burada `var` bu yararlıdır şekilde olan grubu işlemleri ile Kullanılanlar gibi iç içe geçmiş genel türler. Aşağıdaki sorguda, sorgu değişkeninin türü olduğu `IEnumerable<IGrouping<string, Student>>`. Siz ve kodunuzu korumalıdır başkalarının bunu anlamak sürece örtülü yazma convenience ve kısaltma için kullanma konusunda sorun yoktur.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Ancak, kullanımını `var` kodunuzu anlamak için diğer geliştiriciler daha zor hale getirmek için olası en az yok. Bu nedenle, genellikle C# belgeleri kullanan `var` yalnızca gerekli olduğunda.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [Örtük Olarak Yazılan Diziler](../arrays/implicitly-typed-arrays.md)
- [Nasıl yapılır: Kullanım yerel değişkenleri ve dizileri sorgu ifadesinde örtük](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonim Tipler](anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ Sorgu ifadeleri](../linq-query-expressions/index.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
