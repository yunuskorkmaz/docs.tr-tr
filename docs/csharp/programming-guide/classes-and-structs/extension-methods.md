---
title: Uzatma Yöntemleri - C# Programlama Kılavuzu
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249226"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)

Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri statik yöntemlerdir, ancak genişletilmiş türdeki örnek yöntemleriymiş gibi adlandırılırlar. C#, F# ve Visual Basic ile yazılmış istemci kodu için, uzantı yöntemini çağırmakla bir türde tanımlanan yöntemler arasında belirgin bir fark yoktur.

En yaygın uzantı yöntemleri, varolan <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türleri sorgu işlevselliği eklemek LINQ standart sorgu işleçleridir. Standart sorgu işleçlerini kullanmak için, önce `using System.Linq` bunları bir yönergeyle kapsama getirin. <xref:System.Collections.Generic.IEnumerable%601> Sonra uygular herhangi bir tür <xref:System.Linq.Enumerable.GroupBy%2A>gibi örnek yöntemleri <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>var gibi görünür , , , ve benzeri. Bu ek yöntemleri IntelliSense deyiminin tamamlanmasında <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.List%601> <xref:System.Array>görebilirsiniz.

### <a name="orderby-example"></a>Sipariş Eki

Aşağıdaki örnek, bir arasyağı `OrderBy` dizisinde standart sorgu işleci yönteminin nasıl çağrılmasını gösterir. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleci lambda ifadelerini parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için [Lambda İfadeleri'ne](../statements-expressions-operators/lambda-expressions.md)bakın.

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametre, yöntemin hangi türde çalıştığını belirtir. Parametre [bu](../../language-reference/keywords/this.md) değiştirici tarafından önce gelir. Uzantı yöntemleri yalnızca bir `using` yönergeyle ad alanını kaynak kodunuza açıkça aktardığınızda kapsam içindedir.

Aşağıdaki örnek, sınıf için tanımlanan <xref:System.String?displayProperty=nameWithType> bir uzantı yöntemini gösterir. İç içe geçmiş olmayan, genel olmayan statik bir sınıf içinde tanımlanır:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

Uzatma `WordCount` yöntemi bu `using` yönerge ile kapsamına getirilebilir:

```csharp
using ExtensionMethods;
```

Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Örnek yöntemi sözdizimi ile kodunuzda uzantı yöntemini çağırırsınız. Derleyici tarafından oluşturulan ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya çevirir. Kapsülleme prensibi gerçekten ihlal edilemiyor. Uzantı yöntemleri, genişlettikleri türdeki özel değişkenlere erişemez.

Daha fazla bilgi için, [özel bir uzantı yöntemini nasıl uygulayacağı ve çağıracağı hakkında](./how-to-implement-and-call-a-custom-extension-method.md)bilgi.

Genel olarak, büyük olasılıkla kendi uygulama çok daha sık uzatma yöntemleri çağırıyor olacak. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için uzantı yöntemlerini etkinleştirmek için, yöntemlerin tanımlandığı ad alanı için bir `using` yönerge eklemeniz gereken bir yönerge eklemeniz gerek. Örneğin, standart sorgu işleçlerini kullanmak `using` için bu yönergeyi kodunuza ekleyin:

```csharp
using System.Linq;
```

(System.Core.dll adresine de bir başvuru eklemeniz gerekebilir.) Standart sorgu işleçlerinin artık IntelliSense'de çoğu <xref:System.Collections.Generic.IEnumerable%601> tür için kullanılabilir ek yöntemler olarak göründüğünü fark edeceksiniz.

## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama

Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Başka bir deyişle, bir tür `Process(int i)`de adlı bir yöntem varsa ve aynı imzaile bir uzantı yönteminiz varsa, derleyici her zaman örnek yönteme bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf, `Extensions` uygulayan herhangi bir tür `IMyInterface`için tanımlanan uzantı yöntemleri içerir. Sınıflar `A` `B`ve `C` tüm arabirimi uygulayın.

Ad `MethodB` ve imzası sınıflar tarafından zaten uygulanan yöntemlerle eşleştin, çünkü uzantı yöntemi asla çağrılmaz.

Derleyici eşleşen imzaiçeren bir örnek yöntemi bulamazsa, varsa eşleşen bir uzantı yöntemine bağlanır.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Ortak Kullanım Modelleri

### <a name="collection-functionality"></a>Koleksiyon İşlevselliği

Geçmişte, belirli bir tür için <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi uygulayan ve bu tür koleksiyonlarda hareket eden işlevler içeren "Koleksiyon Sınıfları" oluşturmak yaygındı. Bu tür bir koleksiyon nesnesi oluşturmada yanlış bir şey olmasa da, <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>aynı işlevsellik . Uzantılar, işlevselliğin bu tür de uygulanmış veya <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> bu türde <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> uygulanan herhangi bir koleksiyondan çağrılmasını sağlar. Bu int32 dizisi kullanarak bunun bir örneği [bu makalede daha önce](#orderby-example)bulunabilir.

### <a name="layer-specific-functionality"></a>Katmana Özel İşlevsellik

Soğan Mimarisi veya diğer katmanlı uygulama tasarımı kullanırken, uygulama sınırları arasında iletişim kurmak için kullanılabilecek bir etki alanı varlıkları kümesine veya Veri Aktarımı Nesnelerine sahip olmak yaygındır. Bu nesneler genellikle hiçbir işlevsellik veya uygulamanın tüm katmanları için geçerli dir en az işlevsellik içerir. Uzantı yöntemleri, nesneyi diğer katmanlarda gerekmeyen veya istenmeyen yöntemlerle yüklemeden her uygulama katmanına özgü işlevsellik eklemek için kullanılabilir.

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

### <a name="extending-predefined-types"></a>Önceden Tanımlanmış Türleri Genişletme

Yeniden kullanılabilir işlevselliğin oluşturulması gerektiğinde yeni nesneler oluşturmak yerine, genellikle .NET Framework veya CLR türü gibi varolan bir türü genişletebiliriz. Örnek olarak, uzantı yöntemlerini kullanmazsak, kodumuzdaki birden çok yerden çağrılabilecek bir SQL Sunucusu'nda sorgu yürütme işini yapmak için bir `Engine` veya `Query` sınıf oluşturabiliriz. Ancak bunun yerine <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> bir SQL Server bağlantısı olan her yerden bu sorguyu gerçekleştirmek için uzantı yöntemleri kullanarak sınıf genişletebilirsiniz. <xref:System.String?displayProperty=nameWithType> Diğer örnekler sınıfa ortak işlevsellik eklemek, belirli hata işleme <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> işlevselliği için <xref:System.Exception?displayProperty=nameWithType> nesnelerin ve nesnelerin veri işleme yeteneklerini genişletmek olabilir. Bu tür kullanım durumları sadece hayal gücünüzve sağduyunuzla sınırlıdır.

Değer tarafından yöntemlere geçirildiği `struct` için, önceden tanımlanmış türleri genişletmek türleri ile zor olabilir. Bu, yapının bir kopyasında yapılan herhangi bir değişiklik anlamına gelir. Uzatma yöntemi çıktıktan sonra bu değişiklikler görünmez. C# 7.2 ile başlayarak, `ref` bir uzantı yönteminin ilk bağımsız değişkenine değiştirici ekleyebilirsiniz. Değiştiricinin `ref` eklenmesi, ilk bağımsız değişkenin başvuru yla geçtiği anlamına gelir. Bu, uzatılan yapının durumunu değiştiren uzantı yöntemleri yazmanızı sağlar.

## <a name="general-guidelines"></a>Genel Yönergeler

Bir nesnenin kodunu değiştirerek veya bunu yapmak makul ve mümkün olduğunda yeni bir tür üreterek işlevsellik eklemek hala tercih edilebilir olarak kabul edilirken, uzantı yöntemleri .NET boyunca yeniden kullanılabilir işlevsellik oluşturmak için önemli bir seçenek haline gelmiştir Ekosistem. Özgün kaynağın denetimialtında olmadığı, türetilen bir nesnenin uygunsuz veya imkansız olduğu veya işlevselliğin geçerli kapsamının dışında açığa çıkmaması gereken durumlar için Uzantı yöntemleri mükemmel bir seçimdir.

Türetilen türler hakkında daha fazla bilgi için [Kalıtım'a](./inheritance.md)bakın.

Kaynak kodu denetiminde olmayan bir türü genişletmek için bir uzantı yöntemi kullanırken, türün uygulanmasındayapılacak bir değişikliğin uzantı yönteminizin kırılmasına neden olacağı riskini taşırsınız.

Belirli bir tür için uzantı yöntemleri uygularsanız, aşağıdaki noktaları unutmayın:

- Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.
- Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlandırılmış `Extensions`tek bir ad alanında uzantı yöntemleri içeren birden çok statik sınıfınvarsa, `using Extensions;` bunların tümü yönerge tarafından kapsamına getirilir.

Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için [Montaj Sürümü'ne](../../../standard/assembly/versioning.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Paralel Programlama Örnekleri (bunlar birçok örnek uzantı yöntemi içerir)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda İfadeler](../statements-expressions-operators/lambda-expressions.md)
- [Standart Sorgu İşleçlerine Genel Bakış](../concepts/linq/standard-query-operators-overview.md)
- [Örnek parametreleri ve etkileri için dönüşüm kuralları](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Uzantı yöntemleri Diller arasında birlikte çalışabilirlik](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Uzatma yöntemleri ve Curried Delegeler](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Uzatma yöntemi Bağlama ve Hata raporlama](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
