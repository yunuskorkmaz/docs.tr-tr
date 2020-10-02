---
title: C# 9,0 ' deki yenilikler-C# Kılavuzu
description: C# 9,0 ' de bulunan yeni özelliklere genel bakış alın.
ms.date: 09/04/2020
ms.openlocfilehash: c165ca764d93b74aac21028ed3e55e80f2a23ee0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654913"
---
# <a name="whats-new-in-c-90"></a>C# 9.0 sürümündeki yenilikler

C# 9,0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:

- [Kayıtlar](#record-types)
- [Yalnızca init ayarlayıcılar](#init-only-setters)
- [Üst düzey deyimler](#top-level-statements)
- [Desen eşleştirme geliştirmeleri](#pattern-matching-enhancements)
- Yerel boyutlu tamsayılar
- İşlev işaretçileri
- Yaymayı localsinit bayrağını gösterme
- Hedef türü belirtilmiş yeni ifadeler
- statik anonim işlevler
- Hedef türü belirlenmiş Koşullu ifadeler
- Birlikte değişken dönüş türleri
- `GetEnumerator`Döngüler için uzantı desteği `foreach`
- Lambda atma parametreleri
- Yerel işlevlerlerde öznitelikler
- Modül başlatıcılar
- Kısmi yöntemlere yönelik yeni özellikler

C# 9,0, **.NET 5**' te desteklenir. Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../language-reference/configure-language-version.md).

## <a name="record-types"></a>Kayıt türleri

C# 9,0, eşitlik için değer semantiğini sağlamak üzere birleştirilmiş Yöntemler sağlayan bir başvuru türü olan ***kayıt türlerini***tanıtır. Kayıtlar varsayılan olarak sabittir.

Kayıt türleri, .NET 'te değişmez başvuru türleri oluşturmayı kolaylaştırır. Geçmişte, .NET türleri büyük ölçüde başvuru türleri olarak sınıflandırılır (sınıflar ve anonim türler dahil) ve değer türleri (yapılar ve tanımlama birimleri dahil). Değişmez değer türleri önerilirken, değişebilir değer türleri genellikle hata sunmaz. Değer tür değişkenleri değerleri tutar, böylece değer türleri yöntemlere geçirildiğinde orijinal verilerin bir kopyasına değişiklikler yapılır.

Değişmez başvuru türleri için de birçok avantaj vardır. Bu avantajlar, paylaşılan verilerle eşzamanlı programlarda daha fazla yer sunar. Ne yazık ki C#, sabit başvuru türleri oluşturmak için size çok sayıda ek kod yazmanızı zordu. Kayıtlar, eşitlik için değer semantiğini kullanan sabit bir başvuru türü için bir tür bildirimi sağlar. Eşitlik ve karma kodları için birleştirilmiş Yöntemler, özelliklerinin hepsi eşit olduğunda iki kaydı kabul ettir. Bu tanımı göz önünde bulundurun:

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordDefinition":::

Kayıt tanımı `Person` iki ReadOnly özelliği içeren bir tür oluşturur: `FirstName` ve `LastName` . `Person`Tür bir başvuru türüdür. Il 'ye bakdıysanız, bu bir sınıftır. Özelliklerden hiçbirinin, oluşturulduktan sonra değiştirilemediği için bu sabittir. Bir kayıt türü tanımladığınızda, derleyici sizin için birkaç başka yöntem de birleştirir:

- Değer tabanlı eşitlik karşılaştırmaları için Yöntemler
- Geçersiz kıl <xref:System.Object.GetHashCode>
- Üyeleri Kopyala ve Kopyala
- `PrintMembers` ve <xref:System.Object.ToString>

Kayıtları devralmayı destekler. Öğesinden türetilmiş yeni bir kaydı `Person` aşağıdaki gibi bildirebilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="InheritedRecord":::

Ayrıca, daha fazla türetmeyi engellemek için kayıtları mühürleyebilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="SealedRecord":::

Derleyici Yukarıdaki yöntemlerin farklı sürümlerini birleştirir. Yöntem imzaları, kayıt türü korumalı ise ve doğrudan temel sınıf nesne ise öğesine bağlıdır. Kayıtlar aşağıdaki yeteneklere sahip olmalıdır:

- Eşitlik değer tabanlıdır ve türlerin eşleşip eşleşeceğini bir denetim içerir. Örneğin, `Student` `Person` iki kayıt aynı adı paylaşsa bile, a 'ya eşit olamaz.
- Kayıtlar sizin için oluşturulmuş tutarlı bir dize gösterimine sahiptir.
- Kayıtlar kopyalama oluşturmayı destekler. Doğru kopya oluşturma, devralma hiyerarşilerini ve geliştiriciler tarafından eklenen özellikleri içermelidir.
- Kayıtlar değiştirilmek üzere kopyalanabilir. Bu kopyalama ve değiştirme işlemleri, bozucu olmayan mutasyon 'yi destekler.

, Ve tanıdık aşırı yüklemelerin yanı sıra, `Equals` `operator ==` `operator !=` derleyici yeni bir özelliği birleştirir `EqualityContract` . Özelliği, `Type` kaydın türüyle eşleşen bir nesne döndürür. Temel tür ise, `object` özelliği olur `virtual` . Temel tür başka bir kayıt türü ise, özelliği bir olur `override` . Kayıt türü ise, `sealed` özelliği olur `sealed` . `GetHashCode` `GetHashCode` Sentezte, temel türde ve kayıt türünde belirtilen tüm özellikleri ve alanları kullanır. Bu birleştirilmiş Yöntemler, devralma hiyerarşisi boyunca değer tabanlı eşitlik uygular. Diğer bir deyişle `Student` , hiçbir şekilde `Person` aynı ada sahip bir ile eşit kabul edilmez. İki kaydın türleri aynı ve aynı zamanda eşit olan kayıt türleri arasında paylaşılan tüm özellikler eşleşmelidir.

Kayıtlar Ayrıca, kopya oluşturmak için birleştirilmiş bir oluşturucuya ve bir "Clone" yöntemine sahiptir. Sentezlenmiş oluşturucunun, kayıt türünde bir bağımsız değişkeni vardır. Kaydın tüm özellikleri için aynı değerlere sahip yeni bir kayıt oluşturur. Bu Oluşturucu, kayıt mühürlense, aksi takdirde korunmuşsa özel olur. Sentezlenmiş "kopya" yöntemi, kayıt hiyerarşileri için kopyalama oluşturmayı destekler. Gerçek ad derleyici tarafından oluşturulduğundan "kopya" terimi tırnak içine alınmış. Kayıt türünde adlı bir yöntem oluşturamazsınız `Clone` . Sentezlenmiş "kopya" yöntemi, sanal dağıtım kullanılarak Kopyalanmakta olan kaydın türünü döndürür. Derleyici, "Kopyala" yöntemi için, içindeki erişim değiştiricilerine bağlı olarak farklı değiştiriciler ekler `record` :

- Kayıt türü ise `abstract` , "Clone" yöntemi de vardır `abstract` . Temel tür değilse `object` , yöntemi de olur `override` .
- `abstract`Temel tür şu olduğunda olmayan kayıt türleri için `object` :
  - Kayıt ise `sealed` , "kopya" yöntemine ek değiştiriciler eklenmez (anlamı yoktur `virtual` ).
  - Kayıt değilse `sealed` , "Clone" yöntemi olur `virtual` .
- Temel tür olmadığında olmayan kayıt türleri için `abstract` `object` :
  - Kayıt ise `sealed` , "Clone" yöntemi de vardır `sealed` .
  - Kayıt değilse `sealed` , "Clone" yöntemi olur `override` .

Bu kuralların sonucu, eşitlik her türlü kayıt türü hiyerarşisinde tutarlı bir şekilde uygulanır. Aşağıdaki örnekte gösterildiği gibi, özellikleri eşitse iki kayıt birbirlerine eşittir ve türleri aynıdır:

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordsEquality":::

Derleyici, yazdırılan çıktıyı destekleyen iki yöntemi birleştirir: bir <xref:System.Object.ToString> geçersiz kılma ve `PrintMembers` . , `PrintMembers` <xref:System.Text.StringBuilder?displayProperty=nameWithType> Bağımsız değişkeni olarak bir alır. Kayıt türündeki tüm özellikler için özellik adlarının ve değerlerinin virgülle ayrılmış bir listesini ekler. `PrintMembers` diğer kayıtlardan türetilmiş tüm kayıtlar için temel uygulamayı çağırır. <xref:System.Object.ToString>Geçersiz kılma tarafından üretilen `PrintMembers` , ve ile çevrili dizeyi `{` döndürür `}` . Örneğin, <xref:System.Object.ToString> için yöntemi `Student` `string` Aşağıdaki kod gibi döndürür:

```csharp
"Student { LastName = Wagner, FirstName = Bill, Level = 11 }"
```

Şu ana kadar gösterilen örnekler, özellikleri bildirmek için Geleneksel söz dizimini kullanır. ***Konumsal kayıtlar***adlı daha kısa bir form vardır.  Daha önce konumsal kayıtlar olarak tanımlanan üç kayıt türü şunlardır:

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="PositionalRecords":::

Bu bildirimler, önceki sürümle aynı işlevleri oluşturur (aşağıdaki bölümde ele alınan birkaç ek özellik ile). Bu kayıtlar başka yöntemler eklemediğinden, bu bildirimler köşeli ayraç yerine noktalı virgül ile biter. Bir gövde ekleyebilir ve başka yöntemler de ekleyebilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="RecordsWithMethods":::

Derleyici `Deconstruct` konumsal kayıtlar için bir yöntem oluşturur. `Deconstruct`Yönteminde, kayıt türündeki tüm ortak özelliklerin adlarıyla eşleşen parametreler bulunur. `Deconstruct`Yöntemi, kayıt bileşenin özelliklerine göre oluşturmak için kullanılabilir:

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="DeconstructRecord":::

Son olarak, ***-deyimlerle***destek kaydeder. ***WITH ifadesi*** , derleyiciye bir kaydın kopyasını oluşturmasını söyler *, ancak belirtilen* özelliklerle değiştirilmiştir:

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="Wither":::

Yukarıdaki satır, `Person` `LastName` özelliğin bir kopyası olduğu `person` ve `FirstName` "Paul" olduğu yeni bir kayıt oluşturur. Bir WITH ifadesi içinde istediğiniz sayıda özelliği ayarlayabilirsiniz.  "Clone" yöntemi dışındaki birleştirilmiş üyelerin herhangi biri sizin tarafınızdan yazılabilir. Bir kayıt türünün herhangi bir sentezlenmiş yöntemin imzasıyla eşleşen bir yöntemi varsa, derleyici bu yöntemi birleştirmez. Önceki `Dog` kayıt örneği örnek olarak bir el kodlu <xref:System.String.ToString> yöntem içerir.

## <a name="init-only-setters"></a>Yalnızca init ayarlayıcılar

***Init Only Setter*** bir nesnenin üyelerini başlatmak için tutarlı sözdizimi sağlar. Özellik başlatıcıları, hangi değerin hangi özelliğin ayarlanmasını temizlesin. Downsıde, bu özelliklerin ayarlanabilir olması gerekir. C# 9,0 ' den başlayarak, `init` `set` Özellikler ve Dizin oluşturucular için erişimciler yerine erişimciler oluşturabilirsiniz. Çağıranlar, oluşturma ifadelerinde bu değerleri ayarlamak için özellik başlatıcısı sözdizimini kullanabilir, ancak oluşturma işlemi tamamlandıktan sonra bu özellikler salt okunur yapılır. Init Only ayarlayıcıları, durumu değiştirecek bir pencere sağlar. Bu pencere, oluşturma aşaması sona erdiğinde kapanır. Özellik başlatıcıları ve WITH ifadeleri dahil olmak üzere, oluşturma aşaması, tüm başlatma sonrasında etkili bir şekilde sona erer.

Konumsal kayıtlar için yukarıdaki örnek, WITH ifadesi kullanarak bir özelliği ayarlamak için bir init ayarlayıcı kullanmayı gösterir. Yazdığınız herhangi bir tür için yalnızca init ayarlayıcıları bildirebilirsiniz. Örneğin, aşağıdaki yapı bir hava durumu izleme yapısını tanımlar:

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="DeclareWeatherObservation":::

Çağıranlar, değerleri ayarlamak için özellik başlatıcısı sözdizimini kullanabilir, ancak yine de dengesizin kullanılabilirliği korunur:

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="UseWeatherObservation":::

Ancak başlatma sonrasında bir gözlemyi değiştirmek, başlatma dışında yalnızca bir init özelliğine atanarak bir hatadır:

```csharp
// Error! CS8852.
now.TemperatureInCelsius = 18;
```

Yalnızca Init ayarlayıcıları, türetilmiş sınıflardan temel sınıf özellikleri ayarlamak için yararlı olabilir. Ayrıca, bir temel sınıftaki yardımcılar aracılığıyla türetilmiş özellikleri de ayarlayabilir. Konumsal kayıtlar yalnızca init ayarlayıcıları kullanarak özellikleri bildirir. Bu ayarlayıcılar,-ifadelerinde kullanılır. Her türlü veya tanımladığınız için init Only ayarlayıcıları bildirebilirsiniz `class` `struct` .

## <a name="top-level-statements"></a>Üst düzey deyimler

***Üst düzey deyimler*** pek çok uygulamadan gereksiz seremonony 'yi kaldırır. "Merhaba Dünya!" kurallı öğesini düşünün programda

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Her şeyi yapan tek bir kod satırı vardır. En üst düzey deyimlerle, tüm bu demirbaş `using` ve iş yapan tek satır ile değiştirebilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/Program.cs" ID="TopLevelStatements":::

Tek satırlık bir program istediyseniz, `using` yönergeyi kaldırabilir ve tam nitelikli tür adını kullanabilirsiniz:

```csharp
System.Console.WriteLine("Hello World!");
```

Uygulamanızdaki yalnızca bir dosya en üst düzey deyimleri kullanabilir. Derleyici birden çok kaynak dosyasında en üst düzey deyimler bulursa, bu bir hatadır. En üst düzey deyimleri, genellikle bir yöntemi olan, belirtilen bir program giriş noktası yöntemiyle birleştirirseniz de bir hatadır `Main` . Bir anlamda, bir dosyanın normalde bir sınıf yönteminde olacak deyimleri içerdiğini düşünebilirsiniz `Main` `Program` .  

Bu özellik için en yaygın kullanımdan biri eğitim malzemeleri oluşturuyor. Başlangıç C# geliştiricileri kurallı "Merhaba Dünya!" yazabilir kodda bir veya iki satırda. Ek sertifika gerekmez. Bununla birlikte, deneyimli geliştiriciler bu özellik için birçok kullanım de bulacaktır. En üst düzey deyimler, Jupneter Not defterlerinin sağladığı deneme için bir komut dosyası benzeri deneyim sağlar. En üst düzey deyimler, küçük konsol programları ve yardımcı programlar için harika. Azure işlevleri, en üst düzey deyimler için ideal bir kullanım durumdur.

En önemlisi, üst düzey deyimler uygulamanızın kapsamını veya karmaşıklığını sınırlamaz. Bu deyimler, herhangi bir .NET sınıfına erişebilir veya kullanabilir. Ayrıca, komut satırı bağımsız değişkenlerinin veya dönüş değerlerinin kullanımını sınırlamaz. Üst düzey deyimler, args adlı dizeler dizisine erişebilir. En üst düzey deyimler bir tamsayı değeri döndürirse, bu değer sentezlenmiş bir yöntemden tamsayı dönüş kodu olur `Main` . En üst düzey deyimler zaman uyumsuz ifadeler içerebilir. Bu durumda, birleştirilmiş giriş noktası bir `Task` veya döndürür `Task<int>` .

## <a name="pattern-matching-enhancements"></a>Desen eşleştirme geliştirmeleri

C# 9, yeni bir model eşleşme geliştirmeleri içerir:

- ***Tür desenleri*** bir değişkenle eşleşiyor tür
- ***Parantez Içine alınmış desenler*** , desen birleşimlerinin önceliğini uygular veya vurgular
- ***Ayırt edici `and` desenler*** , her iki desen de eşleşmesini gerektirir
- Ayırt edici *** `or` desenler*** eşleşmesi gereken her iki model
- ***Değillenmiş `not` desenler*** bir düzenin eşleşmemesi gerekir
- ***İlişkisel desenler*** , girişin küçüktür, büyüktür, küçüktür veya eşittir veya belirtilen bir sabitten büyük veya eşit olması gerekir.

Bu desenler, desenlerin sözdizimini zenginleştirin. Aşağıdaki örnekleri göz önünde bulundurun:

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterPattern":::

Alternatif olarak, `and` daha yüksek önceliğe sahip olması için isteğe bağlı parantezle `or` :

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterOrSeparatorPattern":::

En yaygın kullanımdan biri null denetimi için yeni bir sözdizimidir:

```csharp
if (e is not null)
{
    // ...
}
```

Bu desenlerden herhangi biri desenleri izin verilen herhangi bir bağlamda kullanılabilir: `is` desen ifadeleri, `switch` ifadeler, iç içe desenler ve bir `switch` deyimin `case` etiketinin deseni.

## <a name="performance-and-interop"></a>Performans ve birlikte çalışma

Üç yeni özellik, yüksek performans gerektiren yerel birlikte çalışma ve alt düzey kitaplıklar desteğini geliştirir: yerel boyutlu tamsayılar, işlev işaretçileri ve `localsinit` bayrağı atlama.

Yerel boyutlu tamsayılar `nint` ve `nuint` , tamsayı türleridir. Bunlar, temel alınan türler ve ile ifade edilir <xref:System.IntPtr?displayProperty=nameWithType> <xref:System.UIntPtr?displayProperty=nameWithType> . Derleyici, bu türler için ek dönüştürmeler ve işlemleri yerel olarak gösterir. Yerel boyutlu tamsayılar veya özelliklerini tanımlar `MaxValue` `MinValue` . Bu değerler, Hedef makinedeki bir tamsayının yerel boyutuna bağlı olduğundan, derleme zamanı sabitleri olarak ifade edilemez. Çalışma zamanında bu değerler salt okunur. `nint`[.. Aralığında için sabit değerler kullanabilirsiniz. `int.MinValue` `int.MaxValue`]. `nuint`[.. Aralığında için sabit değerler kullanabilirsiniz. `uint.MinValue` `uint.MaxValue`]. Derleyici ve türlerini kullanarak tüm birli ve ikili işleçler için sabit katlama gerçekleştirir <xref:System.Int32?displayProperty=nameWithType> <xref:System.UInt32?displayProperty=nameWithType> . Sonuç 32 bite sığmazsa, işlem çalışma zamanında yürütülür ve bir sabit kabul edilmez. Yerel boyutlu tamsayılar, tamsayı matematiğinin yaygın olarak kullanıldığı ve en yüksek performansa sahip olması gereken senaryolarda performansı artırabilir.

İşlev işaretçileri, Il işlem kodları ve ' a erişmek için kolay bir sözdizimi sağlar `ldftn` `calli` . Yeni sözdizimini kullanarak işlev işaretçileri bildirebilirsiniz `delegate*` . `delegate*`Tür bir işaretçi türüdür. Yöntemi, `delegate*` yöntemini kullanan `calli` bir temsilcinin aksine, türünü çağırır `callvirt` `Invoke()` . Sözdizimi, çağırma aynıdır. İşlev işaretçisi çağrısı, `managed` çağırma kuralını kullanır. `unmanaged` `delegate*` Çağırma kuralına istediğinizi bildirmek için sözdiziminden sonra anahtar sözcüğünü eklersiniz `unmanaged` . Diğer çağırma kuralları, bildirimde öznitelikler kullanılarak belirtilebilir `delegate*` .

Son olarak, <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute?displayProperty=nameWithType> derleyicinin bayrağı yaymamasını sağlamak için öğesini ekleyebilirsiniz `localsinit` . Bu bayrak, CLR 'ye tüm yerel değişkenleri sıfıra başlatmasını söyler. `localsinit`Bayrak, 1,0 sonrasındaki C# için varsayılan davranıştır. Ancak, ek sıfır başlatma bazı senaryolarda ölçülebilir performans etkisine sahip olabilir. Özellikle, kullandığınızda `stackalloc` . Bu gibi durumlarda, ekleyebilirsiniz <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> . Tek bir yönteme veya özelliğe veya bir `class` ,, `struct` `interface` veya hatta bir modüle ekleyebilirsiniz. Bu öznitelik yöntemleri etkilemez `abstract` ; uygulama için oluşturulan kodu etkiler.

Bu özellikler, bazı senaryolarda performansı iyileştirebilir. Bunlar yalnızca, benimseme öncesinde ve sonrasında eklendikten sonra kullanılmalıdır. Yerel boyutlu tamsayılar içeren kodun, farklı tamsayı boyutlarına sahip birden çok hedef platformda test olması gerekir. Diğer özellikler güvenli olmayan kod gerektirir.

## <a name="fit-and-finish-features"></a>Sığdırma ve son özellikler

Diğer özelliklerin çoğu, daha verimli bir şekilde kod yazmanıza yardımcı olur. C# 9,0 ' de, oluşturulan nesnenin türü zaten biliniyorsa bir [ `new` ifadede](../language-reference/operators/new-operator.md) türü atlayabilirsiniz. En yaygın kullanım, alan bildirimlerinde bulunur:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="WeatherStationField":::

`new`Bir yönteme bağımsız değişken olarak geçirmek için yeni bir nesne oluşturmanız gerektiğinde, target türü de kullanılabilir. `ForecastFor()`Aşağıdaki imzaya sahip bir yöntem düşünün:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="ForecastSignature":::

Bunu şu şekilde çağırabilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="TargetTypeNewArgument":::

Bu özellik için bir diğer iyi kullanım, yeni bir nesneyi başlatmak için yalnızca init özellikleriyle birlikte birleştirilmenize yöneliktir:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="InitWeatherStation":::

Bir ifadesini kullanarak varsayılan Oluşturucu tarafından oluşturulan bir örnek döndürebilirsiniz `return new();` .

Benzer bir özellik, [koşullu ifadelerin](../language-reference/operators/conditional-operator.md)hedef tür çözümlemesini geliştirir. Bu değişiklik ile, iki ifadenin bir öğesinden diğerine örtük dönüştürmesi gerekmez, ancak her ikisi de hedef tür için örtük Dönüştürmelere sahip olabilir. Büyük olasılıkla bu değişikliği fark edeceksiniz. Ne fark edeceksiniz, daha önce gerekli olan veya derlenmeyen bazı Koşullu ifadeler artık çalışır.

C# 9,0 ' den başlayarak `static` [lambda ifadelerine](../language-reference/operators/lambda-expressions.md) veya [anonim yöntemlere](../language-reference/operators/delegate-operator.md)değiştiricisini ekleyebilirsiniz. Statik lambda ifadeleri `static` Yerel işlevlere benzerdir: statik lambda veya anonim yöntem yerel değişkenleri veya örnek durumunu yakalayabilir. `static`Değiştirici yanlışlıkla diğer değişkenleri yakalamaya engel olur.

Covaryant dönüş türleri, geçersiz kılınan işlevlerin dönüş türleri için esneklik sağlar. Geçersiz kılınan bir sanal işlev, temel sınıf yönteminde belirtilen dönüş türünden türetilmiş bir tür döndürebilir. Bu, kayıtlar için ve sanal kopya ya da fabrika yöntemlerini destekleyen diğer türler için yararlı olabilir.

Buna ek olarak, [ `foreach` döngü](../language-reference/keywords/foreach-in.md) , başka bir şekilde onu karşılayan bir genişletme yöntemi tanır ve kullanır `GetEnumerator` `foreach` . Bu değişiklik, `foreach` zaman uyumsuz model ve model tabanlı ayrıştırma gibi diğer model tabanlı kurulumlarını ile tutarlıdır. Uygulamada, bu değişiklik `foreach` herhangi bir türe destek ekleyebileceğiniz anlamına gelir. Bir nesne Numaralandırırken tasarımınızda anlamlı hale geldiğinde kullanımını sınırlamanız gerekir.

Sonra, Lambda ifadelerinde parametre olarak atar ' i kullanabilirsiniz. Bu kolaylık, bağımsız değişkeni adlandırmayı önlemenize olanak sağlar ve derleyici bunu kullanmaktan kaçınabilir. `_`Herhangi bir bağımsız değişken için öğesini kullanırsınız. Daha fazla bilgi için [lambda ifadeleri](../language-reference/operators/lambda-expressions.md) makalesinin [lambda ifadesinin giriş parametreleri](../language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) bölümüne bakın.

Son olarak, artık yerel işlevlere öznitelikler uygulayabilirsiniz. Örneğin, yerel işlevlere null yapılabilir öznitelik ek açıklamaları uygulayabilirsiniz.

## <a name="support-for-code-generators"></a>Kod oluşturucuları için destek

İki son özellik C# kod üreteçleri destekler. C# kod oluşturucuları, bir Roslyn çözümleyicisine veya kod düzeltmesine benzer şekilde yazabileceğiniz bir bileşendir. Fark, kod oluşturucuların kodu çözümlemelerine ve derleme sürecinin bir parçası olarak yeni kaynak kodu dosyaları yazmanızdır. Tipik bir kod üreticisi öznitelikleri veya diğer kuralları arar.

Bir kod Oluşturucu, Roslyn analiz API 'Lerini kullanarak öznitelikleri veya diğer kod öğelerini okur. Bu bilgilerden, derlemeye yeni kod ekler. Kaynak oluşturucuları yalnızca kod ekleyebilir; Bu kişiler, derlemede var olan herhangi bir kodu değiştirmesine izin verilmez.

Kod üreticileri için eklenen iki özellik, ***kısmi Yöntem sözdizimi***ve ***Modül başlatıcıları***için uzantılardır. Birincisi, kısmi metotlarda yapılan değişiklikler. C# 9,0 öncesi, kısmi Yöntemler, bir `private` erişim değiştiricisi `void` belirtmemelidir, geri dönemeyebilir ve parametrelere sahip olamaz `out` . Bu kısıtlamalar, hiçbir yöntem uygulama sağlanmazsa, derleyicinin kısmi yönteme yapılan tüm çağrıları kaldırmasının anlamına gelir. C# 9,0 bu kısıtlamaları ortadan kaldırır, ancak kısmi Yöntem bildirimlerinin bir uygulamaya sahip olmasını gerektirir. Kod oluşturucuları, bu uygulamayı sağlayabilir. Yeni bir değişiklik yapmaktan kaçınmak için, derleyici eski kuralları takip etmek üzere bir erişim değiştiricisi olmadan herhangi bir kısmi yöntemi dikkate alır. Kısmi Yöntem `private` erişim değiştiricisini içeriyorsa, yeni kurallar bu kısmi yöntemi yönetir.

Kod üreticileri için ikinci yeni özellik ***Modül başlatıcılarına***yöneliktir. Modül başlatıcıları, <xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> kendisine eklenmiş özniteliği olan yöntemlerdir. Bu yöntemler, derleme yüklendiğinde çalışma zamanı tarafından çağırılır. Modül başlatıcısı yöntemi:

- Statik olmalıdır
- Parametresiz olmalıdır
- Void döndürmelidir
- Genel bir yöntem olmamalıdır
- Genel bir sınıfta içerilmemelidir
- Kapsayan modülden erişilebilir olmalıdır

Bu son madde işareti noktası, yöntemin ve kapsayan sınıfın iç veya genel olması gerektiği anlamına gelir. Yöntem yerel bir işlev olamaz.
