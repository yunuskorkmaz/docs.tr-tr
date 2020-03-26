---
title: Güvenli ve verimli C# kodu yazın
description: C# dilinde yapılan son geliştirmeler, daha önce güvenli olmayan kodla ilişkili performansın doğrulanabilir güvenli kodu yazmanızı sağlar.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: bb53264f61192c042da469ba687da6c472e8c6d4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506989"
---
# <a name="write-safe-and-efficient-c-code"></a>Güvenli ve verimli C# kodu yazın

C#'daki yeni özellikler, daha iyi performansla doğrulanabilir güvenli kod yazmanızı sağlar. Bu teknikleri dikkatle uygularsanız, daha az senaryo güvenli olmayan kod gerektirir. Bu özellikler, yöntem bağımsız değişkenleri ve yöntem döndürür olarak değer türlerine başvuruları kullanmayı kolaylaştırır. Güvenli bir şekilde yapıldığında, bu teknikler kopyalama değer türlerini en aza indirir. Değer türlerini kullanarak, ayırma ve çöp toplama geçişlerinin sayısını en aza indirebilirsiniz.

Bu makaledeki örnek kodun çoğu C# 7.2'ye eklenen özellikleri kullanır. Bu özellikleri kullanmak için projenizi C# 7.2 veya daha sonra kullanacak şekilde yapılandırmanız gerekir. Dil sürümünü ayarlama hakkında daha fazla bilgi için [bkz.](language-reference/configure-language-version.md)

Bu makalede, verimli kaynak yönetimi teknikleri üzerinde duruluyor. Değer türlerini kullanmanın bir avantajı da genellikle yığın ayırmalarından kaçınmalarıdır. Dezavantajı, değere göre kopyalanmış olmalarıdır. Bu dengeleme, büyük miktarda veri üzerinde çalışan algoritmaları optimize etmeyi zorlaştırır. C# 7.2'deki yeni dil özellikleri, değer türlerine yapılan atıfları kullanarak güvenli verimli kod sağlayan mekanizmalar sağlar. Hem ayırmaları hem de kopyalama işlemlerini en aza indirmek için bu özellikleri akıllıca kullanın. Bu makalede, bu yeni özellikler inceletir.

Bu makalede, aşağıdaki kaynak yönetimi teknikleri üzerinde duruluyor:

- Bir [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) türün **değişmez** olduğunu ve derleyicinin parametreleri kullanırken [`in`](language-reference/keywords/in-parameter-modifier.md) kopyaları kaydetmesini sağladığını ifade etmek için a bildirin.
- Bir tür değişmez değilse, üyenin `struct` durumu `readonly` değiştirmediğini belirtmek için üye bildirin.
- İade [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) değeri daha `struct` <xref:System.IntPtr.Size?displayProperty=nameWithType> büyükse ve depolama ömrü değeri döndüren yöntemden daha büyükse bir iade kullanın.
- A `readonly struct` boyutu daha <xref:System.IntPtr.Size?displayProperty=nameWithType>büyükse, performans nedenleriyle `in` bir parametre olarak geçirmelisiniz.
- Değiştirici `struct` ile `in` beyan edilmedikçe veya yöntem yalnızca `readonly` yapı nın üyelerini çağırmadığı sürece asla bir parametre olarak geçmeyin. `readonly` Bu kılavuzun ihlal için de performansı olumsuz etkileyebilir ve belirsiz bir davranışa yol açabilir.
- Bir [`ref struct`](language-reference/keywords/ref.md#ref-struct-types)byte `readonly ref struct` dizisi <xref:System.Span%601> olarak <xref:System.ReadOnlySpan%601> bellekle çalışmak için bir veya benzeri bir şey kullanın.

Bu teknikler **referanslar** ve **değerler**açısından iki rakip hedefleri dengelemek için zorlar. [Başvuru türleri](programming-guide/types/index.md#reference-types) olan değişkenler bellekteki konuma bir başvuru tutar. [Değer türleri](programming-guide/types/index.md#value-types) olan değişkenler doğrudan değerlerini içerir. Bu farklılıklar, bellek kaynaklarını yönetmek için önemli olan temel farklılıkları vurgular. **Değer türleri** genellikle bir yönteme geçirildiğinde veya bir yöntemden döndürüldüğünde kopyalanır. Bu davranış, bir değer `this` türünün üyelerini ararken değerini kopyalamayı içerir. Kopyanın maliyeti, türün boyutuyla ilgilidir. **Başvuru türleri** yönetilen yığına ayrılır. Her yeni nesne yeni bir ayırma gerektirir ve daha sonra geri alınmalıdır. Bu iki işlem de zaman alır. Başvuru türü bir bağımsız değişken olarak bir yönteme geçirildiğinde veya bir yöntemden döndürüldüğünde başvuru kopyalanır.

Bu makalede, bu önerileri açıklamak için 3B noktası yapısının aşağıdaki örnek kavramını kullanır:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Farklı örnekler bu kavramın farklı uygulamalarını kullanır.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Değişmez değer türleri için yalnızca okunan structs'u bildirin

`struct` Değiştiricinin `readonly` kullanılmasını bildirmek derleyiciye amacınızın değişmez bir tür oluşturmak olduğunu bildirir. Derleyici bu tasarım kararını aşağıdaki kurallarla zorlar:

- Tüm saha üyeleri,`readonly`
- Otomatik olarak uygulanan özellikler de dahil olmak üzere tüm özellikler salt okunur olmalıdır.

Bu iki kural, hiçbir `readonly struct` üyenin o yapının durumunu dengelenmediğinden emin olmak için yeterlidir. Değişmez. `struct` Yapı, `Point3D` aşağıdaki örnekte gösterildiği gibi değişmez bir yapı olarak tanımlanabilir:

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

Tasarım amacınız değişmez bir değer türü oluşturmak olduğunda bu öneriyi uygulayın. Performans iyileştirmeleri ek bir avantajdır. Tasarım `readonly struct` amacınızı açıkça ifade eder.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Bir yapı değişmez olamaz zaman salt okunur üyeleri bildirin

C# 8.0 ve daha sonra, bir yapı türü mutasyona neden olmayan üyeleri beyan `readonly`etmeniz gerekir. 3B nokta yapısı gerektiren, ancak susturulabilirliği desteklemesi gereken farklı bir uygulama düşünün. 3B nokta yapısının aşağıdaki sürümü, değiştiriciyi `readonly` yalnızca yapıyı değiştirmeyen üyelere ekler. Tasarımınızın bazı üyeler tarafından yapıda yapılan değişiklikleri desteklemesi gerektiğinde, ancak yine de yalnızca bazı üyelere okunan zorlamanın avantajlarını istediğinizde bu örneği izleyin:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

Önceki örnek, `readonly` değiştiriciyi uygulayabileceğiniz birçok konumu gösterir: yöntemler, özellikler ve özellik erişimcileri. Otomatik olarak uygulanan özellikleri kullanıyorsanız, derleyici `readonly` okuma yazma `get` özellikleri için değiştiriciyi erişime ekler. Derleyici, yalnızca `readonly` `get` bir erişime sahip özellikler için otomatik olarak uygulanan özellik bildirimlerine değiştirici ekler.

`readonly` Durumu mutasyona uğratmaz üyelere değiştirici nin eklenmesi, ilgili iki avantaj sağlar. İlk olarak, derleyici niyetinizi zorlar. Bu üye yapının durumunu mutasyona uğratamaz ve aynı zamanda işaretlenmemiş `readonly`bir üyeye erişemez. İkinci olarak, derleyici bir `in` `readonly` üyeye erişirken parametrelerin savunma kopyalarını oluşturmaz. Derleyici, bir üye tarafından değiştirilmediğini garanti `struct` ettiği için bu `readonly` optimizasyonu güvenli bir şekilde yapabilir.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Mümkün `ref readonly return` olduğunda büyük yapılar için ifadeleri kullanma

Döndürülen değer dönen yönteme yerel olmadığında değerleri referans olarak döndürebilirsiniz. Başvuruyla döndürülme, yapının değil, yalnızca başvurunun kopyalanması anlamına gelir. Aşağıdaki örnekte, `Origin` döndürülen değer yerel `ref` bir değişken olduğundan özellik geri dönüş kullanamaz:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Ancak, döndürülen değer statik bir üye olduğundan, aşağıdaki özellik tanımı başvuru yla döndürülebilir:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Arayanların kaynağı değiştirmesini istemiyorsanız, değeri aşağıdakilere göre `ref readonly`döndürmeniz gerekir:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

İade, `ref readonly` daha büyük yapıların kopyalanmasını kaydetmenize ve dahili veri üyelerinizin değişmezliğini korumanızı sağlar.

Arama sitesinde, arayanlar `Origin` özelliği bir `ref readonly` değer olarak veya bir değer olarak kullanmayı tercih eder:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Önceki koddaki ilk atama, sabitin `Origin` bir kopyasını yapar ve bu kopyayı atar. İkinci bir referans atar. Değiştiricinin `readonly` değişkenin bildiriminin bir parçası olması gerektiğine dikkat edin. Başvuruda bulunduğu başvuru değiştirilemez. Bunu yapmaya çalışır derleme zamanı hatasına neden olabilir.

Değiştirici `readonly` nin beyanı üzerine `originReference`gereklidir.

Derleyici, arayanın başvuruyu değiştiremeyebileceğini zorlar. Değeri doğrudan derleme zamanı hatası oluşturmaya çalışır. Ancak derleyici, herhangi bir üye yönteminin yapının durumunu modicimi olduğunu bilemiyor.
Nesnenin değiştirilmediğinden emin olmak için derleyici bir kopya oluşturur ve bu kopyayı kullanarak üye başvurularını arar. Herhangi bir değişiklik bu savunma kopya vardır.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>`in` Değiştiriciyi daha `readonly struct` büyük parametrelere uygulayın`System.IntPtr.Size`

`in` Anahtar kelime, varolan `ref` `out` ve anahtar kelimeleri referansa göre bağımsız değişkenler geçirmek için tamamlar. `in` Anahtar kelime, bağımsız değişkeni başvuruyla geçeni belirtir, ancak çağrılan yöntem değeri değiştirmez.

Bu ek, tasarım amacınızı ifade etmek için tam bir kelime dağarcığı sağlar.
Yöntem imzasında aşağıdaki değiştiricilerden hiçbirini belirtmediğinizde, değer türleri çağrılan yönteme geçildiğinde kopyalanır. Bu değiştiricilerin her biri, kopyadan kaçınarak bir değişkenin başvuru yla geçirildiğini belirtir. Her değiştirici farklı bir amacı ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlayabilir.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini değiştirmez.

Bir `in` bağımsız değişkeni başvuruyla geçirmek için değiştiriciekleyin ve gereksiz kopyalamayı önlemek için tasarım amacınızı bağımsız değişkenleri referans olarak geçirmek üzere bildirin. Bu bağımsız değişken olarak kullanılan nesneyi değiştirmek niyetinde değilsiniz.

Bu uygulama genellikle <xref:System.IntPtr.Size?displayProperty=nameWithType>yalnızca daha büyük olan salt değer türleri için performansı artırır. Basit türleri`sbyte`için `byte` `short`(, `int` `uint`, `long` `ushort` `ulong`, `char` `float`, `double` `decimal` , `bool`, `enum` , , , ve türleri), herhangi bir potansiyel performans kazançları en azdır. Aslında, performans <xref:System.IntPtr.Size?displayProperty=nameWithType>daha küçük türleri için pass-by-reference kullanarak bozulabilir.

Aşağıdaki kod, 3B alanda iki nokta arasındaki mesafeyi hesaplayan bir yöntem örneği gösterir.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Bağımsız değişkenler, her biri üç çift içeren iki yapıdır. Bir çift 8 bayt, bu yüzden her argüman 24 bayt olduğunu. `in` Değiştirici belirterek, makinenin mimarisine bağlı olarak bu bağımsız değişkenlere 4 bayt veya 8 baytlık bir başvuru geçersiniz. Boyut farkı küçüktür, ancak uygulamanız bu yöntemi birçok farklı değer kullanarak sıkı bir döngü içinde aradığında birikir.

`in` Değiştirici tamamlar `out` ve `ref` diğer şekillerde de. Yalnızca `in`, `out`veya `ref`. Bu yeni kurallar, her zaman tanımlanmış `out` olan `ref` davranışı ve parametreleri genişletir. `out` Değiştiriciler `ref` ve değiştiriciler gibi, `in` değiştirici uygulandığından değer türleri kutulu değil.

Değiştirici `in` parametreleri alan herhangi bir üyeye uygulanabilir: yöntemler, temsilciler, lambdas, yerel fonksiyonlar, dizinleyiciler, işleçler.

Parametrelerin `in` bir diğer özelliği de, bağımsız değişken için bir `in` parametre için gerçek değerleri veya sabitleri kullanabilmektir. Ayrıca, bir `ref` `out` veya parametrenin aksine, `in` değiştiriciyi çağrı yerinde uygulamanız gerekmez. Aşağıdaki kod, `CalculateDistance` yöntemi arama iki örnek gösterir. İlk başvuru ile geçirilen iki yerel değişken kullanır. İkinci yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Derleyicinin bir `in` bağımsız değişkenin salt okunur doğasını zorladığı çeşitli yollar vardır.  Her şeyden önce, çağrılan yöntem doğrudan bir `in` parametre atamaz. Bu değer bir `in` `struct` tür olduğunda doğrudan bir parametrenin herhangi bir alanına atamaz. Buna ek olarak, bir `in` parametreyi `ref` veya `out` değiştiriyi kullanarak herhangi bir yönteme geçiremezsiniz.
Bu kurallar, alan bir `in` `struct` tür ve parametre de bir tür olması `struct` koşuluyla, bir parametrenin herhangi bir alan için geçerlidir. Aslında, bu kurallar üye erişim in her düzeyde türleri sağlanan üye `structs`erişim birden çok katman için geçerlidir.
Derleyici, bağımsız `struct` değişken olarak `in` geçirilen `struct` türleri zorlar ve diğer yöntemlere bağımsız değişken olarak kullanıldığında üyeleri salt okunur değişkenlerdir.

Parametrelerin `in` kullanımı kopya yapma olası performans maliyetlerini önleyebilirsiniz. Herhangi bir yöntem çağrısının anlambilimini değiştirmez. Bu nedenle, arama yerinde `in` değiştirici belirtmeniz gerekmez. Çağrı yerindeki `in` değiştiricinin atlanması derleyiciye, aşağıdaki nedenlerle bağımsız değişkenin bir kopyasını yapmasına izin verildiğini bildirir:

- Bağımsız değişken türünden parametre türüne bir kimlik dönüştürmesi yok.
- Bağımsız değişken bir ifadedir, ancak bilinen bir depolama değişkeni yoktur.
- Varlığına veya yokluğuna göre farklılık gösteren `in`aşırı yük vardır. Bu durumda, değer aşırı daha iyi bir maç.

Bu kurallar, salt okunur başvuru bağımsız değişkenlerini kullanmak üzere varolan kodu güncelleştirirken yararlıdır. Çağrılan yöntemin içinde, değer parametrelerine göre kullanan herhangi bir örnek yöntemi çağırabilirsiniz. Bu gibi durumlarda, parametrenin `in` bir kopyası oluşturulur. Derleyici herhangi `in` bir parametre için geçici bir değişken oluşturabileceğinden, `in` herhangi bir parametre için varsayılan değerleri de belirtebilirsiniz. Aşağıdaki kod, ikinci noktanın varsayılan değeri olarak kaynağı (0,0 noktası) belirtir:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Derleyiciyi başvuru yla salt okunur bağımsız değişkenleri `in` geçirmeye zorlamak için, aşağıdaki kodda gösterildiği gibi çağrı yerindeki bağımsız değişkenlerde değiştirici belirtin:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Bu davranış, performans kazançlarının mümkün olduğu büyük kod tabanlarında parametrelerin zaman içinde benimsenmesi `in` kolaylaştırır. Önce yöntem `in` imzalarına değiştirici ekleyin. Daha sonra, çağrı `in` sitelerinde değiştirici ekleyebilir `readonly struct` ve derleyicinin daha fazla konumda `in` parametrelerin savunma kopyalarını oluşturmamasını sağlamak için türler oluşturabilirsiniz.

`in` Parametre ataması, başvuru türleri veya sayısal değerlerle de kullanılabilir. Ancak, her iki durumda da yararları, varsa, en azdır.

## <a name="avoid-mutable-structs-as-an-in-argument"></a>`in` Bağımsız değişken olarak değişken structs kaçının

Yukarıda açıklanan teknikler, referansları döndürerek ve değerleri referansla geçirerek kopyalardan nasıl kaçınılanın açıklar. Bu teknikler, bağımsız değişken türleri `readonly struct` tür olarak bildirilirken en iyi şekilde çalışır. Aksi takdirde, derleyici, herhangi bir bağımsız değişkenin yalnızca okuma sını uygulamak için birçok durumda **savunma kopyaları** oluşturmalıdır. Bir 3B noktanın kaynaktan uzaklığı hesaplayan aşağıdaki örneği göz önünde bulundurun:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Yapı `Point3D` sadece okunan bir yapı *değildir.* Bu yöntemin gövdesinde altı farklı özellik erişim çağrıları vardır. İlk muayenede, bu erişimlerin güvenli olduğunu düşünmüş olabilirsiniz. Sonuçta, bir `get` erişimci nesnenin durumunu değiştirmemelidir. Ama bunu zorunlu kılacak bir dil kuralı yok. Bu sadece sıradan bir toplantı. Herhangi bir tür `get` iç durumu değiştiren bir erişimci uygulayabilir. Bazı dil garantisi olmadan, derleyici `readonly` değiştirici ile işaretlenmemiş herhangi bir üye çağırmadan önce bağımsız değişkenin geçici bir kopyasını oluşturması gerekir. Yığında geçici depolama oluşturulur, bağımsız değişkenin değerleri geçici depolama alanına kopyalanır ve değer `this` bağımsız değişken olarak her üye erişim için yığına kopyalanır. Çoğu durumda, bu kopyalar, bağımsız değişken türü bir `readonly struct` olmadığında ve yöntem işaretlenmemiş `readonly`üyeleri aradığında, geçiş değeri nin yalnızca okunan başvurudan daha hızlı olduğu performansa yeterince zarar verir. Yapı durumunu değiştirmeyen tüm yöntemleri `readonly`işaretlerseniz, derleyici yapı durumunun değiştirilmediğini ve savunma kopyasının gerekli olmadığını güvenli bir şekilde belirleyebilir.

Bunun yerine, mesafe hesaplaması değişmez yapıyı `ReadonlyPoint3D`kullanıyorsa, geçici nesnelergerekmez:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Derleyici, üye `readonly struct`yi çağırdığınızda daha verimli `this` kod oluşturur : Başvuru, alıcının bir `in` kopyası yerine, her zaman üye yöntemine atıfta bulunularak geçirilen bir parametredir. Bu optimizasyon, bir `readonly struct` `in` bağımsız değişken olarak kullandığınızda kopyalama kaydeder.

`in` Bağımsız değişken olarak geçersiz bir değer türünü geçmemelisin. Tür, <xref:System.Nullable%601> salt okunur yapı olarak bildirilmemiştir. Bu, derleyicinin parametre bildirimindeki `in` değiştiriciyi kullanarak bir yönteme geçirilen herhangi bir geçersiz değer türü bağımsız değişkeni için savunma kopyaları oluşturması gerektiği anlamına gelir.

GitHub'daki [örnek depomuzda](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) [BenchmarkDotNet'i](https://www.nuget.org/packages/BenchmarkDotNet/) kullanarak performans farklarını gösteren bir örnek program görebilirsiniz. Değişmez bir yapıyı değere ve referansa göre ve değere göre sabit bir yapıyla karşılaştırır. Değişmez yapının kullanımı ve referans la geçiş en hızlısi.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Tek `ref struct` bir yığın çerçeveüzerinde bloklarla veya bellekle çalışmak için türleri kullanma

İlişkili dil özelliği, tek bir yığın çerçevesiyle sınırlandırılması gereken bir değer türünü bildirme yeteneğidir. Bu kısıtlama derleyicinin birkaç optimizasyon yapmalarını sağlar. Bu özelliğin temel <xref:System.Span%601> motivasyonu ve ilgili yapılardır. Bu <xref:System.Span%601> geliştirmelerden, türünden yararlanan yeni ve güncelleştirilmiş .NET API'lerini kullanarak performans iyileştirmeleri elde eedeceksiniz.

Interop API'lerinden bellek [`stackalloc`](language-reference/operators/stackalloc.md) kullanırken veya kullanırken oluşturulan bellekle çalışan benzer gereksinimlere sahip olabilirsiniz. Bu ihtiyaçlar `ref struct` için kendi türlerinizi tanımlayabilirsiniz.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct`Türü

Bir yapıyı bir `readonly ref` yapı olarak bildirmek, `ref struct` beyannamelerin yararlarını ve `readonly struct` kısıtlamalarını birleştirir. Yalnızca okuma açıklığı tarafından kullanılan bellek tek bir yığın çerçevesiyle sınırlıdır ve yalnızca okunan yayılma alanı tarafından kullanılan bellek değiştirilemez.

## <a name="conclusions"></a>Sonuçlar

Değer türlerinin kullanılması ayırma işlemleri sayısını en aza indirir:

- Değer türleri için depolama yerel değişkenler ve yöntem bağımsız değişkenleri için ayrılmış yığın.
- Diğer nesnelerin üyesi olan değer türleri için depolama ayrı bir ayırma olarak değil, bu nesnenin bir parçası olarak ayrılır.
- Değer türü iade değerleri için depolama yığın ayrılır.

Bu aynı durumlarda başvuru türleri ile kontrast:

- Başvuru türleri için depolama, yerel değişkenler ve yöntem bağımsız değişkenleri için ayrılan yığındır. Başvuru yığınında depolanır.
- Diğer nesnelerin üyesi olan başvuru türleri için depolama ayrı ayrı yığın aayrılır. İçeren nesne başvuruyu depolar.
- Referans türü iade değerleri için depolama yığın ayrılır. Bu depolama başvurusu yığında depolanır.

Tahsisatları en aza indirmek, dengelemelerle birlikte gelir. Boyutu başvurunun boyutundan daha `struct` büyük olduğunda daha fazla bellek kopyalarsınız. Bir başvuru genellikle 64 bit veya 32 bittir ve hedef makine CPU'ya bağlıdır.

Bu tradeoffs genellikle en az performans etkisi vardır. Ancak, büyük strüktlar veya daha büyük koleksiyonlar için performans etkisi artar. Etkisi sıkı döngüler ve programlar için sıcak yollar büyük olabilir.

C# dilindeki bu geliştirmeler, bellek ayırmalarını en aza indirmenin gerekli performansı elde etmede önemli bir faktör olduğu performans açısından kritik algoritmalar için tasarlanmıştır. Yazdığınız kodda bu özellikleri sık sık kullanmadığınızı görebilirsiniz. Ancak, bu geliştirmeler .NET boyunca benimsenmiştir. Giderek daha fazla API bu özellikleri kullandıkça, uygulamalarınızın performansının iyileştiğini görürsünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar kelime](language-reference/keywords/ref.md)
- [Ref dönüşler ve ref yerel ayarlar](programming-guide/classes-and-structs/ref-returns.md)
