---
title: Güvenli ve verimli C# kod yazma
description: C# Dilde en son geliştirmeler, daha önce güvenli olmayan kodla ilişkili olan doğrulanabilir güvenli kod yazmanızı sağlar.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: d4a7916b80e15c7f00fa0a7da213ed0593e0959d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239982"
---
# <a name="write-safe-and-efficient-c-code"></a>Güvenli ve verimli C# kod yazma

' Deki C# yeni özellikler daha iyi performansa sahip doğrulanabilir güvenli kod yazmanızı sağlar. Bu teknikleri dikkatle uygularsanız, daha az senaryo güvenli olmayan kod gerektirir. Bu özellikler, yöntem bağımsız değişkenleri olarak değer türlerine yapılan başvuruların kullanımını kolaylaştırır ve yöntemi döndürür. Güvenli bir şekilde bitince, bu teknikler kopyalama değer türlerini en aza indirir. Değer türlerini kullanarak, ayırma sayısını ve çöp toplama geçişlerini en aza indirmiş olursunuz.

Bu makaledeki örnek kodun çoğu 7,2 ' de C# eklenen özellikleri kullanır. Bu özellikleri kullanmak için, projenizi 7,2 veya sonraki bir sürümü kullanacak C# şekilde yapılandırmanız gerekir. Dil sürümünü ayarlama hakkında daha fazla bilgi için bkz. [dil sürümünü yapılandırma](language-reference/configure-language-version.md).

Bu makalede, verimli kaynak yönetimine yönelik teknikler ele alınmaktadır. Değer türlerini kullanmanın bir avantajı genellikle yığın ayırmaların önlerinden kaçınmaktır. Dezavantajı, değere göre kopyalanmasıdır. Bu zorunluluğunu getirir, büyük miktarlarda veri üzerinde çalışan algoritmaların iyileştirmesini zorlaştırır. C# 7,2 sürümündeki yeni dil özellikleri, değer türlerine başvurular kullanarak güvenli verimli kod etkinleştiren mekanizmalar sağlar. Her iki ayırma ve kopyalama işlemini en aza indirmek için bu özellikleri daha seyrek kullanın. Bu makalede bu yeni özellikler incelenmektedir.

Bu makalede aşağıdaki kaynak yönetimi teknikleri ele alınmaktadır:

- Bir türün **sabit** olduğunu ifade etmek için bir [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) bildirin ve [`in`](language-reference/keywords/in-parameter-modifier.md) parametreleri kullanılırken derleyicinin kopyaları kaydetmesine olanak sağlar.
- Bir tür sabit olamaz, üyenin durumu değiştirmediğini göstermek için `struct` üyeleri `readonly` bildirin.
- Dönüş değeri <xref:System.IntPtr.Size?displayProperty=nameWithType> daha büyük bir `struct` olduğunda ve depolama ömrü değeri döndüren yöntemden daha büyük olduğunda bir [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) dönüşü kullanın.
- `readonly struct` boyutu <xref:System.IntPtr.Size?displayProperty=nameWithType>daha büyük olduğunda, performans nedenleriyle bunu bir `in` parametresi olarak geçirmeniz gerekir.
- `readonly` değiştiricisi ile bildirilemediği veya yöntem yalnızca yapının `readonly` üyelerini çağırdığı sürece bir `struct` `in` parametresi olarak geçirmeyin. Bu kılavuzun ihlal olması, performansı olumsuz etkileyebilir ve bu da belirsiz bir davranışa yol açabilir.
- Bellekle bir bayt dizisi olarak çalışmak için [`ref struct`](language-reference/keywords/ref.md#ref-struct-types)veya <xref:System.Span%601> ya da <xref:System.ReadOnlySpan%601> gibi bir `readonly ref struct` kullanın.

Bu teknikler, **başvuru** ve **değer**açısından birbiriyle rekabet eden iki hedefi dengelemenize zorlar. [Başvuru türleri](programming-guide/types/index.md#reference-types) olan değişkenler bellekteki konuma bir başvuru tutar. [Değer türleri](programming-guide/types/index.md#value-types) olan değişkenler doğrudan değerlerini içerir. Bu farklılıklar, bellek kaynaklarını yönetmek için önemli olan önemli farklılıkları vurgulamaktadır. **Değer türleri** genellikle bir yönteme geçirildiğinde veya bir yöntemden döndürüldüğünde kopyalanır. Bu davranış, bir değer türünün üyelerini çağırırken `this` değerini kopyalamayı içerir. Kopyanın maliyeti, türün boyutuyla ilgilidir. **Başvuru türleri** yönetilen yığında ayrılır. Her yeni bir nesne için yeni bir ayırma gerekir ve ardından geri kazanılır. Bu işlemlerin her ikisi de zaman alır. Başvuru, bir yönteme bir bağımsız değişken olarak geçirildiğinde veya bir yöntemden döndürüldüğünde kopyalanır.

Bu makalede, bu önerileri açıklamak için 3B nokta yapısının aşağıdaki örnek kavramı kullanılmaktadır:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Farklı örnekler bu kavramın farklı uygulamalarını kullanır.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Değişmez değer türleri için salt okunur yapılar bildirme

`readonly` değiştiricisini kullanarak bir `struct` bildirmek, derleyiciye sabit bir tür oluşturmak için olduğunu bildirir. Derleyici, aşağıdaki kurallarla bu tasarım kararı uygular:

- Tüm alan üyeleri `readonly` olmalıdır
- Otomatik uygulanan özellikler dahil olmak üzere tüm özellikler salt okunabilir olmalıdır.

Bu iki kural, bir `readonly struct` üyesinin bu yapının durumunu değiştirmemesini sağlamak için yeterlidir. `struct` sabittir. `Point3D` yapısı, aşağıdaki örnekte gösterildiği gibi sabit bir yapı olarak tanımlanabilir:

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

Tasarım amacınızda sabit değer türü oluşturmak her seferinde bu öneriyi izleyin. Tüm performans geliştirmeleri, ek bir avantajdır. `readonly struct` tasarım amacınızı açıkça ifade eder.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Bir yapı sabit olamaz, salt okunur Üyeler bildirin

C# 8,0 ve sonraki sürümlerde, bir struct türü değişebilir olduğunda, `readonly`bir şekilde olmasına neden olmayan Üyeler bildirmeniz gerekir. Örneğin, aşağıda 3B nokta yapısının değişebilir bir çeşitlemesi verilmiştir:

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

Yukarıdaki örnek, `readonly` değiştiricisini uygulayabileceğiniz konumların çoğunu gösterir: Yöntemler, Özellikler ve özellik erişimcileri. Otomatik uygulanan özellikler kullanırsanız, derleyici, okuma-yazma özellikleri için `get` erişimcisine `readonly` değiştiricisini ekler. Derleyici, `readonly` değiştiricisini yalnızca bir `get` erişimcisi olan özellikler için otomatik uygulanan özellik bildirimlerine ekler.

`readonly` değiştiricisini bulunmamalıdır olmayan üyelere eklemek, iki ilgili avantaj sağlar. İlk olarak, derleyici amacınızı zorluyor. Bu üye yapının durumunu veya `readonly`de işaretlenmemiş bir üyeye erişim sağlayabilir. İkincisi, derleyici bir `readonly` üyesine erişirken `in` parametrelerinin savunma kopyalarını oluşturmaz. Derleyici, `struct` bir `readonly` üyesi tarafından değiştirilmediğini garanti ettiğinden, bu iyileştirmesi güvenli hale getirir.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Mümkün olduğunda büyük yapılar için `ref readonly return` deyimlerini kullanın

Döndürülmekte olan değer döndürülen yönteme yerel olmadığında, değerleri başvuruya göre döndürebilirsiniz. Başvuruya göre döndürme, yapıyı değil yalnızca başvurunun kopyalandığı anlamına gelir. Aşağıdaki örnekte, döndürülen değer yerel bir değişken olduğundan, `Origin` özelliği bir `ref` dönüşü kullanamaz:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Ancak, döndürülen değer statik bir üye olduğu için aşağıdaki özellik tanımı başvuru ile döndürülebilir:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Çağıranların kaynağı değiştirmesini istemezsiniz, bu yüzden değeri `ref readonly`döndürmelidir:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

`ref readonly` döndürmek, daha büyük yapıları kopyalamayı ve iç veri üyelerinizin dengeszlik durumunu korumanızı sağlar.

Çağıran sitede, arayanlar `Origin` özelliğini `ref readonly` veya bir değer olarak kullanma seçeneğini yapar:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Yukarıdaki koddaki ilk atama `Origin` sabitinin bir kopyasını oluşturur ve bu kopyayı atar. İkincisi bir başvuru atar. `readonly` değiştiricinin, değişkenin bildiriminin bir parçası olması gerektiğini unutmayın. Başvurduğu başvuru değiştirilemez. Bunun için denemeler, derleme zamanı hatasına neden olacak.

`readonly` değiştiricisi `originReference`bildiriminde gereklidir.

Derleyici, çağıranın başvuruyu değiştiremiyorum. Değer atama denemeleri doğrudan derleme zamanı hatası oluşturur. Ancak derleyici, herhangi bir üye yönteminin yapının durumunu değiştirmediğini bilmez.
Nesnenin değiştirilmediğinden emin olmak için, derleyici bir kopya oluşturur ve bu kopyayı kullanarak üye başvuruları çağırır. Tüm değişiklikler, savunma kopyasına göre yapılır.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>`in` değiştiricisini `System.IntPtr.Size` daha büyük `readonly struct` parametrelere uygulayın

`in` anahtar sözcüğü, değişkenleri başvuruya göre geçirmek için mevcut `ref` ve `out` anahtar sözcüklerini tamamlar. `in` anahtar sözcüğü, bağımsız değişkeni başvuruya göre geçirmeyi belirtir, ancak çağrılan yöntem değeri değiştirmez.

Bu ek, tasarım amacınızı ifade etmek için tam bir sözlük sağlar.
Değer türleri, yöntem imzasında Aşağıdaki değiştiricilerin hiçbirini belirtmezseniz, çağrılan bir yönteme geçirildiğinde kopyalanır. Bu değiştiricilerin her biri, bir değişkenin başvuruya göre geçtiğini belirtir ve kopyalama önlenir. Her değiştirici farklı bir amacı ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlayabilir.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini değiştirmez.

Bir bağımsız değişkeni başvuruya göre geçirmek için `in` değiştiricisini ekleyin ve gereksiz kopyalama olmaması için bağımsız değişkenleri başvuruya göre iletmek üzere tasarım amacınızı bildirin. Bu bağımsız değişken olarak kullanılan nesneyi değiştirmeyi düşünmüyorsanız.

Bu uygulama genellikle <xref:System.IntPtr.Size?displayProperty=nameWithType>daha büyük salt okunur değer türleri için performansı geliştirir. Basit türler (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ve `bool`ve `enum` türleri) için olası performans kazançları en düşük düzeydedir. Aslında, <xref:System.IntPtr.Size?displayProperty=nameWithType>' den küçük türler için doğrudan başvuru aracılığıyla performans düşebilir.

Aşağıdaki kod, 3B alanda iki işaret arasındaki mesafeyi hesaplayan bir yöntem örneği gösterir.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Bağımsız değişkenler, her biri üç Double içeren iki yapıya sahiptir. Çift 8 bayttır, bu nedenle her bağımsız değişken 24 bayttır. `in` değiştiricisini belirterek, makinenin mimarisine bağlı olarak bu bağımsız değişkenlere 4 baytlık veya 8 baytlık bir başvuru geçirirsiniz. Boyut farkı küçüktür, ancak uygulamanız bu yöntemi birçok farklı değer kullanarak sıkı bir döngüde çağırdığında ekler.

`in` değiştirici `out` ve `ref` başka yollarla da tamamlar. Yalnızca `in`, `out`veya `ref`varlığı farklı olan bir yöntemin aşırı yüklerini oluşturamazsınız. Bu yeni kurallar, `out` ve `ref` parametreleri için her zaman tanımlanan davranışı genişletir. `out` ve `ref` değiştiricilerine benzer şekilde, `in` değiştiricisi uygulandığından değer türleri paketlenmez.

`in` değiştiricisi Parametreler alan herhangi bir üyeye uygulanabilir: Yöntemler, temsilciler, Lambdalar, yerel işlevler, Dizin oluşturucular, işleçler.

`in` parametrelerinin başka bir özelliği, bir `in` parametresine bağımsız değişken için değişmez değer veya sabitler kullanbiliriz. Ayrıca, bir `ref` veya `out` parametresinden farklı olarak, çağrı sitesinde `in` değiştiricisini uygulamanız gerekmez. Aşağıdaki kod, `CalculateDistance` yöntemini çağırmanın iki örneğini göstermektedir. İlki, başvuruya göre geçirilen iki yerel değişkeni kullanır. İkincisi, yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Derleyicinin `in` bağımsız değişkeninin salt okunurdur yapısını zorladığı çeşitli yollar vardır.  İlki, çağrılan yöntem bir `in` parametresine doğrudan atanamaz. Bu değer `struct` bir tür olduğunda, `in` parametresinin hiçbir alanına doğrudan atanamaz. Ayrıca, `ref` veya `out` değiştiricisini kullanarak herhangi bir yönteme `in` parametresi geçirilemez.
Bu kurallar, `in` parametresinin herhangi bir alanı için geçerlidir, alan bir `struct` türü ve parametresi de bir `struct` türüdür. Aslında, bu kurallar birçok üye erişimi katmanı için geçerlidir, tüm üye erişimi düzeylerindeki türler `structs`.
Derleyici, `in` bağımsız değişken olarak geçirilen `struct` türlerini ve `struct` üyelerini diğer yöntemlere bağımsız değişkenler olarak kullanıldığında salt okunurdur.

`in` parametrelerinin kullanımı, kopya yapmanın olası performans maliyetlerinden kaçınabilir. Herhangi bir yöntem çağrısının semantiğini değiştirmez. Bu nedenle, çağrı sitesinde `in` değiştiricisini belirtmeniz gerekmez. Çağrı sitesindeki `in` değiştiricinin atlanması derleyicinin aşağıdaki nedenlerden dolayı bağımsız değişkenin bir kopyasını yapmasına izin verildiğini bildirir:

- Bağımsız değişken türünden parametre türüne bir kimlik dönüştürmesi değil, örtük bir dönüştürme var.
- Bağımsız değişken bir ifadedir ancak bilinen bir depolama değişkenine sahip değildir.
- `in`varlığı veya yokluğuna göre farklı bir aşırı yükleme var. Bu durumda, değer olarak aşırı yüklemesi daha iyi bir eşleşmedir.

Bu kurallar, var olan kodu salt okuma başvuru bağımsız değişkenlerini kullanacak şekilde güncelleştirdiğinizde yararlıdır. Çağrılan yöntemin içinde, değer parametrelerine göre kullanan herhangi bir örnek yöntemini çağırabilirsiniz. Bu örneklerde `in` parametresinin bir kopyası oluşturulur. Derleyici herhangi bir `in` parametresi için geçici bir değişken oluşturabileceğinden, herhangi bir `in` parametresi için varsayılan değerleri de belirtebilirsiniz. Aşağıdaki kod, kaynak (nokta 0, 0) ikinci nokta için varsayılan değer olarak belirtir:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Derleyiciye başvuruya göre salt okuma bağımsız değişkenlerini geçirmeye zorlamak için, aşağıdaki kodda gösterildiği gibi, çağrı sitesindeki bağımsız değişkenlerde `in` değiştiricisini belirtin:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Bu davranış, performans kazançlarının mümkün olduğu büyük kod tabanlarında zaman içinde `in` parametrelerinin benimsenmesini kolaylaştırır. `in` değiştiricisini öncelikle Yöntem imzalarına eklersiniz. Ardından, çağrı sitelerine `in` değiştiricisini ekleyebilir ve derleyicinin daha fazla konumda `in` parametrelerinin savunma kopyalarını oluşturmaktan kaçınmasını sağlamak için `readonly struct` türleri oluşturabilirsiniz.

`in` parametresi ataması, başvuru türleri veya sayısal değerlerle de kullanılabilir. Ancak, her iki durumda da avantajlar, varsa en az düzeydedir.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>`in` bağımsız değişkeni olarak hiçbir şekilde kesilebilir yapılar kullanmayın

Yukarıda açıklanan teknikler, başvuruları döndürerek ve değerlere başvuruya göre geçirerek kopyaların nasıl önleneceğini açıklamaktadır. Bu teknikler, bağımsız değişken türleri `readonly struct` türleri olarak bildirildiğinde en iyi şekilde çalışır. Aksi takdirde, derleyicinin herhangi bir bağımsız değişken için salt okunur hale getirilmesi zorunlu kılmak için birçok durumda **savunma kopyaları** oluşturması gerekir. Bir 3B noktanın kaynaktan uzaklığını hesaplayan aşağıdaki örneği göz önünde bulundurun:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D` yapısı ReadOnly bir struct *değil* . Bu yöntemin gövdesinde altı farklı özellik erişim çağrısı vardır. İlk inceleme durumunda bu erişimlerin güvenli olduğunu düşündük. Tüm `get` erişimci nesnenin durumunu değiştirmez. Ancak bunu zorlayan bir dil kuralı yoktur. Yalnızca ortak bir kuraldır. Herhangi bir tür, iç durumu değiştiren bir `get` erişimcisi uygulayabilir. Bazı dil garantisi olmadan, derleyicinin herhangi bir üyeyi çağırmadan önce bağımsız değişkenin geçici bir kopyasını oluşturması gerekir. Geçici depolama, yığında oluşturulur, bağımsız değişkenin değerleri geçici depolamaya kopyalanır ve değer `this` bağımsız değişkeni olarak her üye erişiminde yığına kopyalanır. Birçok durumda, bu kopyalar, bağımsız değişken türü `readonly struct`olmadığında, bu kopya, değere göre geçiş, salt okunur başvuruya göre daha hızlıdır.

Bunun yerine, uzaklık hesaplaması değişmez yapıyı kullanıyorsa `ReadonlyPoint3D`geçici nesneler gerekmez:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

`readonly struct`üyelerini çağırdığınızda derleyici daha verimli kod üretir: alıcının bir kopyası yerine `this` başvurusu, her zaman üye yöntemine başvuru ile geçirilen bir `in` parametresidir. Bu iyileştirme, bir `readonly struct` `in` bağımsız değişkeni olarak kullandığınızda kopyalamayı kaydeder.

Null yapılabilir bir değer türünü `in` bağımsız değişken olarak geçirmemelisiniz. <xref:System.Nullable%601> türü salt okunurdur struct olarak bildirilmemiş. Bu, derleyicinin parametre bildiriminde `in` değiştiricisini kullanarak bir yönteme geçirilen herhangi bir Nullable değer türü bağımsız değişkeni için savunma kopyaları oluşturması gerektiği anlamına gelir.

GitHub 'daki [örnek depolarımızda](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) , [benchmarkdotnet](https://www.nuget.org/packages/BenchmarkDotNet/) kullanarak performans farklarını gösteren bir örnek program görebilirsiniz. Değere ve başvuruya göre değişmez bir struct geçirilerek başvuruya göre kesilebilir bir yapının geçirilmesini karşılaştırır. Değişmez yapının kullanımı ve başvuruya göre Pass en hızlı.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Tek bir yığın çerçevesinde bloklarla veya bellekle çalışmak için `ref struct` türlerini kullanın

İlgili dil özelliği, tek bir yığın çerçevesiyle sınırlandırılmak zorunda olması gereken bir değer türü bildirebilmesidir. Bu kısıtlama derleyicinin birkaç iyileştirme yapmasına olanak sağlar. Bu özellik için birincil mosyon <xref:System.Span%601> ve ilgili yapılarıdır. <xref:System.Span%601> türünü kullanan yeni ve güncelleştirilmiş .NET API 'Leri kullanarak bu geliştirmelerden performans iyileştirmeleri elde edersiniz.

[`stackalloc`](language-reference/operators/stackalloc.md) kullanılarak oluşturulan ve birlikte çalışma API 'lerinden bellek kullanırken benzer gereksinimlerle çalışıyor olabilirsiniz. Bu gereksinimler için kendi `ref struct` türlerinizi tanımlayabilirsiniz.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` türü

Bir yapının `readonly ref` olarak bildirilmesi, `ref struct` ve `readonly struct` bildirimlerinin avantajlarını ve kısıtlamalarını birleştirir. Salt okunur yayılma alanı tarafından kullanılan bellek tek bir yığın çerçevesiyle kısıtlıdır ve salt okunur olarak kullanılan bellek değiştirilemez.

## <a name="conclusions"></a>Sonuçlar

Değer türlerini kullanmak, ayırma işlemlerinin sayısını en aza indirir:

- Değer türleri için depolama, yerel değişkenler ve Yöntem bağımsız değişkenleri için ayrılmış yığındır.
- Diğer nesnelerin üyesi olan değer türleri için depolama alanı, ayrı bir ayırma olarak değil, bu nesnenin bir parçası olarak ayrılır.
- Değer türü dönüş değerleri için depolama, yığın olarak ayrıldı.

Aynı durumlarda başvuru türleri ile karşıtlık:

- Başvuru türleri için depolama, yerel değişkenler ve Yöntem bağımsız değişkenleri için ayrılır. Başvuru yığın üzerinde depolanır.
- Diğer nesnelerin üyesi olan başvuru türleri için depolama, yığın üzerinde ayrı olarak ayrılır. İçerilen nesne başvuruyu depolar.
- Başvuru türü dönüş değerleri için depolama, yığın olarak ayrıldı. Bu depolamanın başvurusu yığında depolanır.

En aza indirme ayırmaları, dengelerle gelir. `struct` boyutu bir başvurunun boyutundan daha büyükse daha fazla bellek kopyalayabilirsiniz. Başvuru genellikle 64 bit veya 32 bittir ve hedef makine CPU 'suna bağlıdır.

Bu dengeler genellikle en düşük performans etkisine sahiptir. Ancak, büyük yapılar veya daha büyük koleksiyonlar için performans etkisi artar. Etki, sıkı Döngülerde ve programlar için etkin yollarda büyük olabilir.

Bu C# dilde geliştirmeler, bellek ayırmalarının en aza indirmek için gerekli performansı elde etmek için önemli bir faktör olan performans açısından kritik algoritmalarda tasarlanmıştır. Bu özellikleri genellikle yazdığınız kodda kullanmacağınızı fark edebilirsiniz. Ancak, bu geliştirmeler .NET genelinde benimsenmiştir. Daha fazla API bu özellikleri kullanırken, uygulamalarınızın performansının iyileştireyi görürsünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar sözcüğü](language-reference/keywords/ref.md)
- [Ref dönüşler ve ref yerel ayarlar](programming-guide/classes-and-structs/ref-returns.md)
