---
title: Uzantı yöntemleri-C# Programlama Kılavuzu
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: fc816123134995b753beda0a6f281133d6ddd691
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506825"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)

Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri statik yöntemlerdir, ancak genişletilmiş türdeki örnek yöntemler gibi olarak adlandırılırlar. C#, F # ve Visual Basic yazılmış istemci kodu için, genişletme yöntemi ve bir tür içinde tanımlanan yöntemleri çağırma arasında görünür bir fark yoktur.

En yaygın genişletme yöntemleri, var <xref:System.Collections.IEnumerable?displayProperty=nameWithType> olan ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> TÜRLERINE sorgu işlevselliği ekleyen LINQ standart sorgu işleçleridir. Standart sorgu işleçlerini kullanmak için, önce bunları bir `using System.Linq` yönergeyle kapsama taşıyın. Ardından <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.Enumerable.GroupBy%2A>, uygulayan herhangi bir tür, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>,, vb. gibi örnek yöntemlere sahip olacak şekilde görünür. Ya da gibi bir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Array>türün örneğinden sonra "nokta" yazdığınızda, bu ek yöntemleri IntelliSense deyimin tamamlanmasına <xref:System.Collections.Generic.List%601> bakabilirsiniz.

### <a name="orderby-example"></a>OrderBy örneği

Aşağıdaki örnek, bir tamsayı dizisinde standart sorgu işleci `OrderBy` yönteminin nasıl çağrılacağını gösterir. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleci Lambda ifadelerini parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametresi, yöntemin hangi tür üzerinde çalıştığını belirtir. Parametresi öncesinde [Bu](../../language-reference/keywords/this.md) değiştirici gelir. Uzantı yöntemleri yalnızca bir `using` yönergeyle ad alanını kaynak kodunuza açıkça aktardığınızda kapsam içinde bulunur.

Aşağıdaki örnek, <xref:System.String?displayProperty=nameWithType> sınıfı için tanımlanmış bir uzantı yöntemini gösterir. İç içe olmayan, genel olmayan bir statik sınıf içinde tanımlanmıştır:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

`WordCount` Genişletme yöntemi bu `using` yönergeyle kapsama getirilebilir:

```csharp
using ExtensionMethods;
```

Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Kodunuzda, örnek yöntemi sözdizimi ile genişletme yöntemi çağırılır. Derleyici tarafından oluşturulan ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Kapsülleme ilkesi gerçekten ihlal edilmez. Genişletme yöntemleri genişledikleri türdeki özel değişkenlere erişemez.

Daha fazla bilgi için bkz. [özel bir genişletme yöntemi uygulama ve çağırma](./how-to-implement-and-call-a-custom-extension-method.md).

Genel olarak, büyük olasılıkla kendi uygulamanızı uygulamaktan çok daha sık genişletme yöntemleri çağrılıyor. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için uzantı yöntemlerini etkinleştirmek için, yöntemlerin tanımlandığı ad `using` alanı için bir yönerge eklemeniz yeterlidir. Örneğin, standart sorgu işleçlerini kullanmak için bu `using` yönergeyi kodunuza ekleyin:

```csharp
using System.Linq;
```

(System. Core. dll dosyasına da bir başvuru eklemeniz gerekebilir.) Standart sorgu işleçlerinin artık, çoğu <xref:System.Collections.Generic.IEnumerable%601> tür için kullanılabilen ek yöntemler olarak IntelliSense 'de göründüğünü fark edeceksiniz.

## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama

Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Diğer bir deyişle, bir türün adlı `Process(int i)`bir yöntemi varsa ve aynı imzaya sahip bir uzantı yönteminiz varsa, derleyici her zaman örnek yöntemine bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf `Extensions` , uygulayan `IMyInterface`her tür için tanımlanmış genişletme yöntemleri içerir. Sınıfları `A`, `B`ve `C` All arabirimini uygular.

Ad `MethodB` ve imza, sınıflar tarafından zaten uygulanmış yöntemlerle tam olarak eşleştiğinden, genişletme yöntemi hiçbir şekilde çağrılmaz.

Derleyici eşleşen imzaya sahip bir örnek yöntemi bulamadığında, varsa eşleşen bir uzantı yöntemine bağlanır.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Ortak kullanım desenleri

### <a name="collection-functionality"></a>Koleksiyon Işlevselliği

Geçmişte, belirli bir tür için <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi uygulayan ve bu türdeki koleksiyonlar üzerinde işlem yapan işlevselliği Içeren "koleksiyon sınıfları" oluşturmak yaygın bir şekilde oluşturulmuştur. Bu tür koleksiyon nesnesini oluştururken bir sorun olmadığından, üzerinde bir uzantı kullanılarak aynı işlevsellik elde edilebilir <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Uzantılar, işlevin bu tür üzerinde uygulayan <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> bir veya gibi herhangi bir koleksiyondan çağrılmasına izin vermenin avantajlarından yararlanır. Bu [makalede daha önce](#orderby-example), bir Int32 dizisi kullanılarak buna bir örnek bulabilirsiniz.

### <a name="layer-specific-functionality"></a>Katmana özgü Işlevsellik

Çoklu kare mimarisi veya diğer katmanlı uygulama tasarımı kullanırken, bir dizi etki alanı varlığı veya uygulama sınırları genelinde iletişim kurmak için kullanılabilecek nesneleri Veri Aktarımı. Bu nesneler genellikle hiçbir işlevsellik içermez veya yalnızca uygulamanın tüm katmanları için geçerli olan minimum işlevleri içerir. Uzantı yöntemleri, nesneleri gerekli olmayan yöntemlerle yüklemeden veya diğer katmanlarda istemeden, her uygulama katmanına özgü işlevselliği eklemek için kullanılabilir.

```aspx-csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>Önceden tanımlanmış türleri genişletme

Yeniden kullanılabilir işlevlerin oluşturulması gerektiğinde yeni nesneler oluşturmak yerine, genellikle .NET Framework veya CLR türü gibi varolan bir türü genişletebiliriz. Örnek olarak, genişletme yöntemlerini kullanmıyorsanız, kodumuza ait birden çok konumdan `Engine` çağrılabilen `Query` bir SQL Server sorgu yürütme işini yapmak için bir veya sınıfı oluşturarız. Ancak, bir SQL Server bağlantısı olan <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> her yerden bu sorguyu gerçekleştirmek için uzantı yöntemlerini kullanarak sınıfı genişletebilirsiniz. <xref:System.String?displayProperty=nameWithType> Diğer örnekler, sınıfa ortak işlevsellik eklemek <xref:System.IO.File?displayProperty=nameWithType> , ve <xref:System.IO.Stream?displayProperty=nameWithType> nesnelerinin veri işleme yeteneklerini ve belirli hata işleme işlevselliği için <xref:System.Exception?displayProperty=nameWithType> nesneleri genişletmek olabilir. Bu tür kullanım örnekleri yalnızca hayal ve iyi bir fikir ile sınırlıdır.

Önceden tanımlanmış türleri genişletme, değerler ile `struct` metotlara geçirdikleri için türlerle zor olabilir. Diğer bir deyişle, yapı üzerinde yapılan tüm değişiklikler yapının bir kopyasına yapılır. Uzantı yöntemi çıktıktan sonra bu değişiklikler görünür değildir. C# 7,2 ile başlayarak, bir genişletme yönteminin ilk `ref` bağımsız değişkenine değiştirici ekleyebilirsiniz. `ref` Değiştirici eklemek, ilk bağımsız değişkenin başvuruya göre geçirildiği anlamına gelir. Bu, genişletilmekte olan yapının durumunu değiştiren uzantı yöntemleri yazmanızı sağlar.

## <a name="general-guidelines"></a>Genel Yönergeler

Bir nesnenin kodunu değiştirerek veya makul ve mümkün olduğunda yeni bir tür türeterek işlevsellik eklemek tercih edilir ancak, uzantı yöntemleri .NET ekosistemi boyunca yeniden kullanılabilir işlevsellik oluşturmak için önemli bir seçenek haline gelir. Özgün kaynak denetiminiz altında olmadığında, türetilmiş bir nesne uygunsuz veya imkansız olduğunda ya da işlevselliğin uygun kapsamın ötesinde sunulmaması durumunda, uzantı yöntemleri mükemmel bir seçimdir.

Türetilmiş türler hakkında daha fazla bilgi için bkz. [Devralma](./inheritance.md).

Kaynak kodunu denetiminde olmayan bir türü genişletmek için bir genişletme yöntemi kullanırken, türün uygulamasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olacağı riski çalıştırırsınız.

Belirli bir tür için uzantı yöntemleri uygularsanız, aşağıdaki noktaları hatırlayın:

- Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.
- Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlı `Extensions`tek bir ad alanında uzantı yöntemlerini içeren birden fazla statik sınıfınız varsa, bunların hepsi `using Extensions;` yönergeyle kapsam haline getirilir.

Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Paralel programlama örnekleri (bunlar birçok örnek genişletme yöntemi içerir)](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
- [Lambda Ifadeleri](../statements-expressions-operators/lambda-expressions.md)
- [Standart Sorgu İşleçlerine Genel Bakış](../concepts/linq/standard-query-operators-overview.md)
- [Örnek parametreleri ve bunların etkileri için dönüştürme kuralları](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Diller arasında uzantı yöntemleri birlikte çalışabilirliği](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Uzantı yöntemleri ve curried temsilciler](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Uzantı yöntemi bağlama ve hata raporlama](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
