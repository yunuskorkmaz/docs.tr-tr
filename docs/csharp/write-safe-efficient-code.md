---
title: Güvenli ve verimli C# kodu yazma
description: C# dilinde yapılan son geliştirmeler, daha önce güvenli olmayan kodla ilişkili olan doğrulanabilir güvenli kod yazmanızı sağlar.
ms.date: 03/17/2020
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 4728ff279d0a14adf239c1e177f7f840ea208e6e
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872489"
---
# <a name="write-safe-and-efficient-c-code"></a>Güvenli ve verimli C# kodu yazma

C# ' deki yeni özellikler daha iyi performansa sahip doğrulanabilir güvenli kod yazmanızı sağlar. Bu teknikleri dikkatle uygularsanız, daha az senaryo güvenli olmayan kod gerektirir. Bu özellikler, yöntem bağımsız değişkenleri olarak değer türlerine yapılan başvuruların kullanımını kolaylaştırır ve yöntemi döndürür. Güvenli bir şekilde bitince, bu teknikler kopyalama değer türlerini en aza indirir. Değer türlerini kullanarak, ayırma sayısını ve çöp toplama geçişlerini en aza indirmiş olursunuz.

Bu makaledeki örnek kodun çoğu C# 7,2 ' de eklenen özellikleri kullanır. Bu özellikleri kullanmak için, projenizi C# 7,2 veya sonraki bir sürümünü kullanacak şekilde yapılandırmanız gerekir. Dil sürümünü ayarlama hakkında daha fazla bilgi için bkz. [dil sürümünü yapılandırma](language-reference/configure-language-version.md).

Bu makalede, verimli kaynak yönetimine yönelik teknikler ele alınmaktadır. Değer türlerini kullanmanın bir avantajı genellikle yığın ayırmaların önlerinden kaçınmaktır. Dezavantajı, değere göre kopyalanmasıdır. Bu ticaret, büyük miktarlarda veri üzerinde çalışan algoritmaların iyileştirmesini zorlaştırır. C# 7,2 ' deki yeni dil özellikleri, değer türlerine başvurular kullanarak güvenli verimli kod etkinleştiren mekanizmalar sağlar. Her iki ayırma ve kopyalama işlemini en aza indirmek için bu özellikleri daha seyrek kullanın. Bu makalede bu yeni özellikler incelenmektedir.

Bu makalede aşağıdaki kaynak yönetimi teknikleri ele alınmaktadır:

- Bir [`readonly struct`](language-reference/builtin-types/struct.md#readonly-struct) türün **sabit** olduğunu bir Express 'e bildirin. Bu, derleyicinin parametreleri kullanırken savunma kopyalarının kaydedilmesini sağlar [`in`](language-reference/keywords/in-parameter-modifier.md) .
- Bir tür sabit olamaz, `struct` [`readonly`](language-reference/builtin-types/struct.md#readonly-instance-members) üyenin durumu değiştirmediğini göstermek için üye bildirin.
- [`ref readonly`](language-reference/keywords/ref.md#reference-return-values)Dönüş değeri `struct` şundan büyük olduğunda <xref:System.IntPtr.Size?displayProperty=nameWithType> ve depolama ömrü değeri döndüren yöntemden büyük olduğunda bir dönüş kullanın.
- Bir a 'nın boyutu daha büyükse `readonly struct` <xref:System.IntPtr.Size?displayProperty=nameWithType> , performans nedenleriyle bu parametreyi bir parametre olarak geçirmeniz gerekir `in` .
- `struct` `in` Değiştirici ile bildirilmemiş `readonly` ya da yöntemi yalnızca yapının üyelerini çağırdığı sürece bir parametre olarak hiçbir şekilde geçirilemez `readonly` . Bu kılavuzun ihlal olması, performansı olumsuz etkileyebilir ve bu da belirsiz bir davranışa yol açabilir.
- Bir [`ref struct`](language-reference/builtin-types/struct.md#ref-struct) `readonly ref struct` <xref:System.Span%601> <xref:System.ReadOnlySpan%601> bayt dizisi olarak bellekle çalışmak için veya gibi bir kullanın.

Bu teknikler, **başvuru** ve **değer** açısından birbiriyle rekabet eden iki hedefi dengelemenize zorlar. [Başvuru türleri](programming-guide/types/index.md#reference-types) olan değişkenler bellekteki konuma bir başvuru tutar. [Değer türleri](programming-guide/types/index.md#value-types) olan değişkenler doğrudan değerlerini içerir. Bu farklılıklar, bellek kaynaklarını yönetmek için önemli olan önemli farklılıkları vurgulamaktadır. **Değer türleri** genellikle bir yönteme geçirildiğinde veya bir yöntemden döndürüldüğünde kopyalanır. Bu davranış, `this` bir değer türünün üyelerini çağırırken değerini kopyalamayı içerir. Kopyanın maliyeti, türün boyutuyla ilgilidir. **Başvuru türleri** yönetilen yığında ayrılır. Her yeni bir nesne için yeni bir ayırma gerekir ve ardından geri kazanılır. Bu işlemlerin her ikisi de zaman alır. Başvuru, bir yönteme bir bağımsız değişken olarak geçirildiğinde veya bir yöntemden döndürüldüğünde kopyalanır.

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

Değiştirici kullanarak bir bildirmek, `struct` `readonly` derleyicinin, sabit bir tür oluşturmak için olduğunu bildirir. Derleyici, aşağıdaki kurallarla bu tasarım kararı uygular:

- Tüm alan üyeleri olmalıdır `readonly`
- Otomatik uygulanan özellikler dahil olmak üzere tüm özellikler salt okunabilir olmalıdır.

Bu iki kural, hiçbir üyenin `readonly struct` Bu yapının durumunu değiştirmemesini sağlamak için yeterlidir. `struct`Sabittir. `Point3D`Yapı, aşağıdaki örnekte gösterildiği gibi değişmez bir yapı olarak tanımlanabilir:

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

Tasarım amacınızda sabit değer türü oluşturmak her seferinde bu öneriyi izleyin. Tüm performans geliştirmeleri, ek bir avantajdır. `readonly struct`Tasarım amacınızı açıkça ifade eder.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Bir yapı sabit olamaz, salt okunur Üyeler bildirin

C# 8,0 ve üzeri sürümlerde, bir struct türü değişebilir olduğunda, bir yapının olmasına neden olmayan Üyeler bildirmeniz gerekir `readonly` . 3B nokta yapısına ihtiyacı olan, ancak değişikliğe neden olması gereken farklı bir uygulama düşünün. Aşağıdaki 3B nokta yapısının sürümü, `readonly` değiştiricisini yalnızca yapıyı değiştirolmayan üyelere ekler. Tasarımınızın bazı üyeler tarafından yapı üzerinde yapılan değişiklikleri desteklemesi gerektiğinde bu örneği izleyin, ancak yine de bazı Üyeler üzerinde ReadOnly 'i zorunlu tutmanın avantajlarının olmasını isteyebilirsiniz:

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

Yukarıdaki örnekte, `readonly` değiştirici, Özellikler ve özellik erişimcileri uygulayabileceğiniz konumların birçoğu gösterilmektedir. Otomatik uygulanan özellikler kullanırsanız, derleyici, `readonly` `get` okuma-yazma özellikleri için değiştiriciyi değiştirici ekler. Derleyici, `readonly` yalnızca bir erişimciyle özellikler için otomatik uygulanan özellik bildirimlerine değiştirici ekler `get` .

`readonly`Bulunmamalıdır durumu olmayan üyelere değiştiricisini eklemek, iki ilgili avantaj sağlar. İlk olarak, derleyici amacınızı zorluyor. Bu üye yapının durumunu mukutamıyorum. İkincisi, derleyici `in` bir üyeye erişirken parametrelerin savunma kopyalarını oluşturmaz `readonly` . Derleyici, `struct` bir üye tarafından değiştirilmediğini garanti ettiğinden, bu iyileştirmeyi güvenli hale getirir `readonly` .

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>`ref readonly return`Mümkün olduğunda büyük yapılar için deyimleri kullanın

Döndürülmekte olan değer döndürülen yönteme yerel olmadığında, değerleri başvuruya göre döndürebilirsiniz. Başvuruya göre döndürme, yapıyı değil yalnızca başvurunun kopyalandığı anlamına gelir. Aşağıdaki örnekte, `Origin` `ref` döndürülen değer yerel bir değişken olduğundan, özellik bir return kullanamaz:

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

Çağıranların kaynağı değiştirmesini istemezsiniz, bu nedenle değeri şu şekilde döndürmelisiniz `ref readonly` :

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Döndürme `ref readonly` , daha büyük yapıları kaydetmenizi ve iç veri üyelerinizin dengeszlik durumunu korumanızı sağlar.

Çağıran sitede, arayıcılar `Origin` özelliği bir veya değeri olarak kullanma seçeneğini yapar `ref readonly` :

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Önceki koddaki ilk atama, sabitin bir kopyasını oluşturur `Origin` ve bu kopyayı atar. İkincisi bir başvuru atar. `readonly`Değiştiricinin, değişkenin bildiriminin bir parçası olması gerektiğini unutmayın. Başvurduğu başvuru değiştirilemez. Bunun için denemeler, derleme zamanı hatasına neden olacak.

`readonly`' İn bildiriminde değiştirici gereklidir `originReference` .

Derleyici, çağıranın başvuruyu değiştiremiyorum. Değer atama denemeleri doğrudan derleme zamanı hatası oluşturur. Diğer durumlarda derleyici, salt okunur başvuruyu güvenli bir şekilde kullanmadığı takdirde bir savunma kopyası ayırır. Statik analiz kuralları yapının değiştirilip değiştirilemeyeceğini belirlenir. Derleyici, yapı bir öğesi olduğunda `readonly struct` veya üye yapının bir üyesiyse bir savunma kopyası oluşturmaz `readonly` . Bir bağımsız değişken olarak yapının iletilmesi için savunma kopyalarının gerekli değildir `in` .

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>`in`Değiştiricisini `readonly struct` şundan büyük parametrelere Uygula`System.IntPtr.Size`

`in`Anahtar sözcüğü, `ref` `out` bağımsız değişkenleri başvuruya göre geçirmek için var olan ve anahtar kelimeleri tamamlar. `in`Anahtar sözcüğü, bağımsız değişkeni başvuruya göre geçirmeyi belirtir, ancak çağrılan yöntem değeri değiştirmez.

Bu ek, tasarım amacınızı ifade etmek için tam bir sözlük sağlar.
Değer türleri, yöntem imzasında Aşağıdaki değiştiricilerin hiçbirini belirtmezseniz, çağrılan bir yönteme geçirildiğinde kopyalanır. Bu değiştiricilerin her biri, bir değişkenin başvuruya göre geçtiğini belirtir ve kopyalama önlenir. Her değiştirici farklı bir amacı ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlayabilir.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini değiştirmez.

`in`Bir bağımsız değişkeni başvuruya göre geçirme değiştiricisini ekleyin ve gereksiz kopyalama olmaması için bağımsız değişkenleri başvuruya göre iletmek üzere tasarım amacınızı bildirin. Bu bağımsız değişken olarak kullanılan nesneyi değiştirmeyi düşünmüyorsanız.

Bu uygulama genellikle öğesinden daha büyük salt okunur değer türleri için performansı geliştirir <xref:System.IntPtr.Size?displayProperty=nameWithType> . Basit türler (,,,,,,, `sbyte` ,, `byte` ,, `short` ve ve `ushort` `int` `uint` `long` `ulong` `char` `float` `double` `decimal` `bool` `enum` türleri) için olası performans kazançları en az düzeydedir. Aslında, daha küçük türler için başvuruyla geçir kullanılarak performans düşebilir <xref:System.IntPtr.Size?displayProperty=nameWithType> .

Aşağıdaki kod, 3B alanda iki işaret arasındaki mesafeyi hesaplayan bir yöntem örneği gösterir.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Bağımsız değişkenler, her biri üç Double içeren iki yapıya sahiptir. Çift 8 bayttır, bu nedenle her bağımsız değişken 24 bayttır. `in`Değiştiricisini belirterek, makinenin mimarisine bağlı olarak bu bağımsız değişkenlere 4 baytlık veya 8 baytlık bir başvuru geçirirsiniz. Boyut farkı küçüktür, ancak uygulamanız bu yöntemi birçok farklı değer kullanarak sıkı bir döngüde çağırdığında ekler.

`in`Değiştirici, `out` `ref` diğer yollarla da tamamlar. Yalnızca, veya varlığının farklı olduğu bir yöntemin aşırı yüklerini oluşturamazsınız `in` `out` `ref` . Bu yeni kurallar, ve parametreleri için her zaman tanımlanan davranışı genişletir `out` `ref` . `out`Ve değiştiricileri gibi `ref` , değiştirici uygulandığından değer türleri kutulanmış değildir `in` .

`in`Değiştirici parametre alan herhangi bir üyeye uygulanabilir: Yöntemler, temsilciler, Lambdalar, yerel işlevler, Dizin oluşturucular, işleçler.

Parametrelerin başka bir özelliği, `in` bir parametreye bağımsız değişken için değişmez değer veya sabitler kullanmanıza olanak sağlar `in` . Ayrıca, `ref` veya parametresinden farklı olarak `out` , `in` çağırma sitesinde değiştiriciyi uygulamanız gerekmez. Aşağıdaki kod, yöntemi çağırmanın iki örneğini göstermektedir `CalculateDistance` . İlki, başvuruya göre geçirilen iki yerel değişkeni kullanır. İkincisi, yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Derleyicinin bir bağımsız değişkenin salt okunurdur yapısını zorladığı çeşitli yollar vardır `in` .  İlki, çağrılan yöntem bir parametreye doğrudan atanamaz `in` . `in`Bu değer bir tür olduğunda, parametrenin hiçbir alanına doğrudan atayamaz `struct` . Ayrıca, `in` veya değiştiricisini kullanarak herhangi bir yönteme bir parametre geçiremezsiniz `ref` `out` .
Bu kurallar, bir parametrenin her alanı için geçerlidir `in` , ancak alan bir `struct` tür ve parametre de bir `struct` tür. Aslında, tüm üye erişimi düzeylerindeki türler sağlanmış olan bu kurallar birden çok üye erişimi katmanı için geçerlidir `structs` .
Derleyici, `struct` bağımsız değişken olarak geçirilen türleri  `in` ve `struct` üyeleri diğer yöntemlere bağımsız değişkenler olarak kullanıldığında salt okuma değişkenleridir.

Parametrelerin kullanımı, `in` kopya yapmanın olası performans maliyetlerinden kaçınabilir. Herhangi bir yöntem çağrısının semantiğini değiştirmez. Bu nedenle, `in` Çağrı sitesinde değiştiricisini belirtmeniz gerekmez. `in`Çağrı sitesinde değiştiricinin atlanması derleyicinin aşağıdaki nedenlerden dolayı bağımsız değişkenin bir kopyasını yapmasına izin verildiğini bildirir:

- Bağımsız değişken türünden parametre türüne bir kimlik dönüştürmesi değil, örtük bir dönüştürme var.
- Bağımsız değişken bir ifadedir ancak bilinen bir depolama değişkenine sahip değildir.
- Varlığı veya yokluğuna göre farklı bir aşırı yükleme var `in` . Bu durumda, değer olarak aşırı yüklemesi daha iyi bir eşleşmedir.

Bu kurallar, var olan kodu salt okuma başvuru bağımsız değişkenlerini kullanacak şekilde güncelleştirdiğinizde yararlıdır. Çağrılan yöntemin içinde, değer parametrelerine göre kullanan herhangi bir örnek yöntemini çağırabilirsiniz. Bu örneklerde, parametresinin bir kopyası `in` oluşturulur. Derleyici herhangi bir parametre için geçici bir değişken oluşturabileceğinden `in` , herhangi bir parametre için varsayılan değerleri de belirtebilirsiniz `in` . Aşağıdaki kod, kaynak (nokta 0, 0) ikinci nokta için varsayılan değer olarak belirtir:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Derleyiciye başvuruya göre salt okuma bağımsız değişkenlerini geçirmeye zorlamak için, `in` aşağıdaki kodda gösterildiği gibi, çağrı sitesindeki bağımsız değişkenlerde değiştirici belirtin:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Bu davranış `in` , performans kazançlarının mümkün olduğu büyük kod tabanlarında zaman içindeki parametreleri benimsemeyi kolaylaştırır. `in`Önce Yöntem imzalarına değiştiricisini eklersiniz. Daha sonra, `in` `readonly struct` `in` daha fazla konumda parametrelerin savunma kopyalarının oluşturulmasını önlemek için, derleyiciyi çağıran sitelere ve oluşturma türlerine ekleme değiştiricisini ekleyebilirsiniz.

`in`Parametre ataması ayrıca başvuru türleri veya sayısal değerlerle birlikte kullanılabilir. Ancak, her iki durumda da avantajlar, varsa en az düzeydedir.

## <a name="avoid-mutable-structs-as-an-in-argument"></a>Bağımsız değişken olarak değişebilir yapıların önüne kaçının `in`

Yukarıda açıklanan teknikler, başvuruları döndürerek ve değerlere başvuruya göre geçirerek kopyaların nasıl önleneceğini açıklamaktadır. Bağımsız değişken türleri tür olarak bildirildiğinde bu teknikler en iyi şekilde çalışır `readonly struct` . Aksi takdirde, derleyicinin herhangi bir bağımsız değişken için salt okunur hale getirilmesi zorunlu kılmak için birçok durumda **savunma kopyaları** oluşturması gerekir. Bir 3B noktanın kaynaktan uzaklığını hesaplayan aşağıdaki örneği göz önünde bulundurun:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D`Yapı ReadOnly bir struct *değil* . Bu yöntemin gövdesinde altı farklı özellik erişim çağrısı vardır. İlk inceleme durumunda bu erişimlerin güvenli olduğunu düşündük. Bütün olarak, `get` erişimci nesnenin durumunu değiştirmez. Ancak bunu zorlayan bir dil kuralı yoktur. Yalnızca ortak bir kuraldır. Herhangi bir tür `get` , iç durumu değiştiren bir erişimci uygulayabilir. Bazı dil garantisi olmadan, değiştiriciyle işaretlenmemiş bir üyeyi çağırmadan önce derleyicinin bağımsız değişkenin geçici bir kopyasını oluşturması gerekir `readonly` . Geçici depolama, yığında oluşturulur, bağımsız değişkenin değerleri geçici depolamaya kopyalanır ve değer bağımsız değişken olarak her üye erişimi için yığına kopyalanır `this` . Birçok durumda, bu, bağımsız değişken türü bir olmadığında `readonly struct` ve yöntemi işaretlenmeyen üyeleri çağırdığında, bu kopya değere göre geçiş-salt okunur başvuruya göre daha hızlı bir şekilde bir performans sağlar `readonly` . Yapı durumunu değiştirmeyin tüm yöntemleri olarak işaretlerseniz `readonly` , derleyici yapı durumunun değiştirilmediğini güvenli bir şekilde belirleyebilir ve savunma kopyası gerekli değildir.

Bunun yerine, uzaklık hesaplaması değişmez yapıyı kullanıyorsa `ReadonlyPoint3D` geçici nesneler gerekmez:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Bir öğesinin üyelerini çağırdığınızda derleyici daha verimli kod üretir `readonly struct` : `this` başvurunun bir kopyası yerine, her zaman `in` üye metoduna başvuru tarafından geçirilen bir parametre. Bu iyileştirme, bir `readonly struct` bağımsız değişken olarak kullandığınızda kopyalamayı kaydeder `in` .

Null yapılabilir bir değer türünü bağımsız değişken olarak geçirmemelisiniz `in` . <xref:System.Nullable%601>Tür salt okunurdur struct olarak bildirilmemiş. Bu, derleyicinin parametre bildiriminde değiştirici kullanılarak bir yönteme geçirilen herhangi bir Nullable değer türü bağımsız değişkeni için savunma kopyaları oluşturması gerektiği anlamına gelir `in` .

GitHub 'daki [örnek depolarımızda](https://github.com/dotnet/samples/tree/main/csharp/safe-efficient-code/benchmark) , [benchmarkdotnet](https://www.nuget.org/packages/BenchmarkDotNet/) kullanarak performans farklarını gösteren bir örnek program görebilirsiniz. Değere ve başvuruya göre değişmez bir struct geçirilerek başvuruya göre kesilebilir bir yapının geçirilmesini karşılaştırır. Değişmez yapının kullanımı ve başvuruya göre Pass en hızlı.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>`ref struct`Tek bir yığın çerçevesinde bloklarla veya bellekle çalışmak için türleri kullanma

İlgili dil özelliği, tek bir yığın çerçevesiyle sınırlandırılmak zorunda olması gereken bir değer türü bildirebilmesidir. Bu kısıtlama derleyicinin birkaç iyileştirme yapmasına olanak sağlar. Bu özellik için birincil mosyon <xref:System.Span%601> ve ilgili yapılar. Bu geliştirmelerden, türü kullanan yeni ve güncelleştirilmiş .NET API 'Leri kullanarak performans iyileştirmeleri elde edersiniz <xref:System.Span%601> .

[`stackalloc`](language-reference/operators/stackalloc.md)Birlikte çalışma API 'lerinden bellek kullanılırken veya kullanılarak oluşturulmuş bellekle çalışan benzer gereksinimleriniz olabilir. `ref struct`Bu gereksinimler için kendi türlerinizi tanımlayabilirsiniz.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` türüyle

Bir yapının `readonly ref` , ve bildirimlerinin avantajları ve kısıtlamalarını birleştiren şekilde `ref struct` Bildirme `readonly struct` . Salt okunur yayılma alanı tarafından kullanılan bellek tek bir yığın çerçevesiyle kısıtlıdır ve salt okunur olarak kullanılan bellek değiştirilemez.

## <a name="conclusions"></a>Sonuçlar

Değer türlerini kullanmak, ayırma işlemlerinin sayısını en aza indirir:

- Değer türleri için depolama, yerel değişkenler ve Yöntem bağımsız değişkenleri için ayrılmış yığındır.
- Diğer nesnelerin üyesi olan değer türleri için depolama alanı, ayrı bir ayırma olarak değil, bu nesnenin bir parçası olarak ayrılır.
- Değer türü dönüş değerleri için depolama, yığın olarak ayrıldı.

Aynı durumlarda başvuru türleri ile karşıtlık:

- Başvuru türleri için depolama, yerel değişkenler ve Yöntem bağımsız değişkenleri için ayrılır. Başvuru yığın üzerinde depolanır.
- Diğer nesnelerin üyesi olan başvuru türleri için depolama, yığın üzerinde ayrı olarak ayrılır. İçerilen nesne başvuruyu depolar.
- Başvuru türü dönüş değerleri için depolama, yığın olarak ayrıldı. Bu depolamanın başvurusu yığında depolanır.

En aza indirme ayırmaları, dengelerle gelir. Boyutu bir başvurunun boyutundan daha büyükse daha fazla bellek kopyalayabilirsiniz `struct` . Başvuru genellikle 64 bit veya 32 bittir ve hedef makine CPU 'suna bağlıdır.

Bu dengeler genellikle en düşük performans etkisine sahiptir. Ancak, büyük yapılar veya daha büyük koleksiyonlar için performans etkisi artar. Etki, sıkı Döngülerde ve programlar için etkin yollarda büyük olabilir.

C# dilinde yapılan bu geliştirmeler, bellek ayırmalarının en aza indirmek için gerekli performansı elde etmek için önemli bir faktör olan performans açısından kritik algoritmalarda tasarlanmıştır. Bu özellikleri genellikle yazdığınız kodda kullanmacağınızı fark edebilirsiniz. Ancak, bu geliştirmeler .NET genelinde benimsenmiştir. Daha fazla API bu özellikleri kullanırken, uygulamalarınızın performansının iyileştireyi görürsünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar sözcüğü](language-reference/keywords/ref.md)
- [Ref dönüşler ve ref yerel ayarlar](programming-guide/classes-and-structs/ref-returns.md)
