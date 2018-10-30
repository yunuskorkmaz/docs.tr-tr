---
title: Güvenli ve verimli yazma C# kod
description: Son geliştirmeler C# dil performansını daha önce güvenli olmayan kod ile ilişkili doğrulanabilir bir güvenli kod yazmak etkinleştirin.
ms.date: 10/23/2018
ms.custom: mvc
ms.openlocfilehash: 8e58a7f870c742f1c0a90a7b5507ac1e5d8074ea
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201591"
---
# <a name="write-safe-and-efficient-c-code"></a>Güvenli ve verimli yazma C# kod #

Yeni Özellikler C# daha iyi performans ile doğrulanabilir güvenli kod yazmanızı sağlar. Bu teknikler özenle uygularsanız, daha az senaryoları güvenli olmayan kod gerektirir. Bu özellikler başvuruları değer türleri için yöntem bağımsız değişkenleri ve yöntemi olarak kullanmak üzere kolaylaştırır. Güvenli bir şekilde işiniz bittiğinde, bu teknikler kopyalama türlerin en aza indirin. Değer türleri kullanarak ayırmaları ve çöp toplama geçişleri sayısını en aza indirebilirsiniz.

Bu makaledeki örnek kodun çoğu eklenen özellikler kullanıyor C# 7.2. Bu özellikleri kullanmak için projenizi kullanmak üzere yapılandırma C# 7.2 veya üzeri. Dil sürümü hakkında daha fazla bilgi için bkz. [dil sürümü yapılandırma](language-reference/configure-language-version.md).

Bu makalede, verimli kaynak yönetimi teknikleri odaklanır. Bunlar genellikle yığın ayırmaları önlemek değer türleri kullanmanın avantajlarından biri. Olumsuz yönüyse, değere göre kopyalanana ' dir. Bu bir tradeoff, büyük miktarlarda veri çalışan algoritmalar iyileştirmek zorlaştırır. Yeni dil özellikleri C# 7.2 başvuruları değer türleri kullanarak güvenli verimli kod etkinleştirme mekanizmaları sağlar. Bu özellikler hem ayırmaların en aza indirmek ve kopyalama işlemlerini akıllıca kullanın. Bu makalede, bu yeni özellikleri keşfediyor.

Bu makalede, aşağıdaki kaynak yönetimi teknikleri üzerinde odaklanır:

- Bildirme bir [ `readonly struct` ](language-reference/keywords/readonly.md#readonly-struct-example) tür olduğunu ifade **değişmez** ve kopya kullanırken kaydetmek için derleyiciyi etkinleştirir [ `in` ](language-reference/keywords/in-parameter-modifier.md) parametreleri.
- Kullanım bir [ `ref readonly` ](language-reference/keywords/ref.md#reference-return-values) dönüş değeri, dönüş bir `struct` büyük <xref:System.IntPtr.Size?displayProperty=nameWithType> ve depolama yaşam süresi değerini döndüren yöntemi büyüktür.
- Zaman boyutu bir `readonly struct` daha büyük <xref:System.IntPtr.Size?displayProperty=nameWithType>, olarak geçmelidir bir `in` Performans nedeniyle parametresi.
- Hiçbir zaman geçmesi bir `struct` olarak bir `in` parametresi ile bildirildiği sürece `readonly` değiştiricisi performansını olumsuz etkileyebilir ve belirsiz bir davranışa neden.
- Kullanım bir [ `ref struct` ](language-reference/keywords/ref.md#ref-struct-types), veya bir `readonly ref struct` gibi <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> bayt dizisi olarak bellek ile çalışmak için.

Bu teknikler, iki rakip hedefleri ile dengelemek için zorlama **başvuruları** ve **değerleri**. Değişkenler [başvuru türleri](programming-guide/types/index.md#reference-types) bellekteki konumu başvuru tutun. Değişkenler [değer türleri](programming-guide/types/index.md#value-types) doğrudan değerleri içerir. Bu farklılıklar, bellek kaynakları yönetmek için önemli olan temel farklılıklar vurgulayın. **Değer türleri** genellikle bir yönteme geçildiğinde kopyaladığınız veya bir yöntemin döndürdüğü. Değerini kopyalayarak bu davranışı içerir `this` bir değer türünün üyesi çağırırken. Kopyanın maliyet türü boyutunu ilişkilidir. **Başvuru türleri** yönetilen yığında ayrılır. Her yeni nesne ayırma gerektirir ve daha sonra yeniden gerekir. Bu işlemler uzun sürer. Bir başvuru türü bağımsız değişken olarak bir yönteme ya da bir yönteminden döndürülen başvuru kopyalanır.

Bu makalede, bu önerileri açıklayan 3B poınt yapısı aşağıdaki örnek kavramını kullanır:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Bu kavram, farklı uygulamalar farklı örnekleri kullanın.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Salt okunur yapılar için değişmez değer türleri bildirme

Bildirme bir `struct` kullanarak `readonly` değiştiricisi derleyici amacınızla sabit bir tür oluşturmak üzere olduğunu bildirir. Derleyici, aşağıdaki kurallar ile tasarım kararı uygular:

- Tüm alanı üyeleri olmalıdır `readonly`
- Tüm özellikler, otomatik uygulanan özellikler dahil olmak üzere salt okunur olmalıdır.

Bu iki kuralın hiçbir üye emin olmak yeterli bir `readonly struct` bu yapı durumunu değiştirir. `struct` Sabittir. `Point3D` Yapısı aşağıdaki örnekte gösterildiği gibi bir sabit yapısı açıklanabilir:

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

Bu öneri, bir değişmez değer türü oluşturmak için tasarım amacınızla olduğunda izleyin. Herhangi bir performans artışıyla avantaj ' dir. `readonly struct` Tasarım amacınızla açıkça ifade eder.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Kullanım `ref readonly return` mümkün olduğunda büyük yapıları için deyimleri

Döndürülen değer döndüren yöntemin yerel değilken, başvuruya göre değerler döndürmesine. Başvuruya göre döndüren anlamına gelir yalnızca başvurunun kopyalandığı yapısı. Aşağıdaki örnekte, `Origin` özelliğini kullanamaz bir `ref` döndürülen değer yerel bir değişken olduğundan döndürür:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Ancak, döndürülen değer, bir statik üye olduğundan aşağıdaki özellik tanımı başvuruya göre döndürülebilir:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Çağıranlar değeri döndürmelidir. Bu nedenle kaynağı değiştirmek istemediğiniz `readonly ref`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Döndüren `ref readonly` daha büyük yapılar kopyalama kaydedin ve değiştirilemezlik, iç veri üyeleri koruma sağlar.

Çağıran sitede, Arayanların kullanma seçimi yapın `Origin` özelliği olarak bir `readonly ref` ya da bir değer olarak:

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Önceki kodda ilk atama bir kopyasını oluşturur `Origin` sabit ve kopyalama atar. İkinci bir başvuru atar. Dikkat `readonly` değiştiricisi değişkenin bildirimi bir parçası olması gerekir. Başvurduğu başvurusu değiştirilemez. Bunu denediğinizde bir derleme zamanı hatasına neden.

`readonly` Değiştiricisi beyanı gerekli `originReference`.

Derleyici, çağırana başvurusu değiştirilemez zorlar. Denemeleri değeri doğrudan atamak için bir derleme zamanı hatası oluşturur. Ancak, derleyici, herhangi bir üye yöntemi yapı durumunu değiştirirse bilemezsiniz.
Nesne değişiklik olmadığından emin olmak için derleyici bir kopyasını oluşturur ve bu kopyayı kullanarak başvuruları üye arar. Herhangi bir değişiklik için savunma kopyası var.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Uygulama `in` değiştiriciyi `readonly struct` parametreleri büyük `System.IntPtr.Size`

`in` Anahtar sözcüğü tamamlar varolan `ref` ve `out` başvuruya göre bağımsız değişkenleri geçirmek için anahtar sözcükler. `in` Anahtar sözcüğü, bağımsız değişkenini başvuruya göre geçirme belirtir, ancak çağrılan yöntem değerini değiştirmez.

Bu ayrıca, tasarım hedefi ifade etmek için tam bir kelime sağlar.
Değer türleri Yöntem imzasında aşağıdaki değiştiriciler hiçbirini belirtmezseniz, çağrılan bir yönteme geçildiğinde kopyalanır. Bu değiştiriciler, her bir değişken kopyalama önleme başvuruyla geçirilir belirtir. Her değiştiricisi, farklı bir hedefi ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değerini ayarlayabilirsiniz.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değerini değiştirmez.

Ekleme `in` başvuruya göre bağımsız değişken geçirin ve gereksiz şekilde kopyalamama olanağı, başvuruya göre bağımsız değişkenleri geçirmek için tasarım amacınızla bildirmek üzere değiştiricisi. Bu bağımsız değişken olarak kullanılan nesneyi değiştirmek istemediğiniz.

Bu yöntem genellikle daha büyük bir salt okunur değer türleri için performansı geliştirir <xref:System.IntPtr.Size?displayProperty=nameWithType>. Basit türleri için (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ve `bool`, ve `enum` türleri), tüm olası performans artışı minimial. Aslında, performans geçişi tarafından başvuru türleri için küçük kullanarak düşebilir <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Aşağıdaki kod örneği, 3B alanda iki nokta arasındaki uzaklığı hesaplar bir yöntemin gösterir.

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Her üç çiftten içeren iki yapıları bağımsız değişkenler. Bir çift 8 bayt olduğundan her bağımsız değişken 24 bayttır. Belirterek `in` değiştiricisi, geçirdiğiniz bir 4 baytlık veya o bağımsız değişkenlerle 8 baytlık başvuru makine mimarisine bağlı olarak. Boyutu fark küçüktür, ancak uygulamanız bu yöntemi kullanarak birçok farklı değerler sıkı bir döngüde çağırdığında toplar.

`in` Değiştiricisi destekleyici `out` ve `ref` başka yöntemler de. Yalnızca içinde varken, farklı bir yöntem aşırı yüklemeleri oluşturulamıyor `in`, `out`, veya `ref`. Bu yeni kurallar her zaman için tanımlanmış aynı davranışı genişletmek `out` ve `ref` parametreleri. Gibi `out` ve `ref` değiştiriciler, değer türleri değildir çünkü Kutulu `in` değiştiricisi uygulanır.

`in` Değiştiricisi parametre almayan herhangi bir üyeye uygulanan: yöntemleri, temsilciler, lambda ifadeleri, yerel İşlevler, Dizinleyicileri, işleçleri.

Başka bir özelliği `in` parametreleri olduğundan, değişmez değerler veya sabit bağımsız değişkeni için kullanabilir, bir `in` parametresi. Ayrıca, farklı bir `ref` veya `out` parametresi, geçerli gerekmeyen `in` çağrı sitesinde değiştiricisi. Aşağıdaki kod çağırmanın iki örnek gösterir `CalculateDistance` yöntemi. İlk iki yerel değişkenini başvuruya göre geçirilen kullanır. İkinci yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir.

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Derleyici salt okunur doğasını zorlar birkaç şekilde bir `in` bağımsız değişken.  İlk olarak çağrılan yöntem doğrudan atayamazsınız bir `in` parametresi. Herhangi bir alan için doğrudan atanamaz bir `in` değeri olduğunda parametresi bir `struct` türü. Ayrıca, geçirilemez bir `in` kullanarak herhangi bir yöntem için parametre `ref` veya `out` değiştiricisi.
Bu kurallar herhangi bir alan için geçerli bir `in` parametre, sağlanan alan bir `struct` türü ve parametre bir `struct` türü. Üye erişimi tüm düzeylerinde türleri birden çok üye erişimi katmanı sağlanan bu kurallar aslında uygulanmasını `structs`.
Derleyici, zorlar `struct` türleri olarak geçirildi `in` bağımsız değişkenleri ve bunların `struct` üyesi olan diğer yöntemlerinin bağımsız değişkenleri olarak kullanılan salt okunur değişkenler.

Kullanımını `in` parametrelerinden olası performans maliyetini kopyalarının kaçının. Bu, herhangi bir yöntem çağrısının semantiği değiştirmez. Bu nedenle, belirtmeniz gerekmez `in` çağrı sitesinde değiştiricisi. Atlama `in` değiştiricisi çağrı sitesinde bildirir derleyici bağımsız değişkeni aşağıdaki nedenlerle bir kopyasını yapma izni:

- Örtük bir dönüştürme ancak olmayan bir kimlik dönüştürme bağımsız değişken türü parametre türü vardır.
- Bağımsız değişken ifade ancak bilinen depolama değişkeni yok.
- Mevcut bir aşırı yükleme olan varlığı veya yokluğu ile farklı `in`. Bu durumda, değere göre aşırı daha iyi bir eşleşmedir.

Bu kurallar, mevcut kodu salt okunur başvuru bağımsız değişkenleri kullanın güncelleştirmelerden yararlıdır. Çağrılan yöntemde, değer parametreleri kullanan herhangi bir örnek yöntemi çağırabilirsiniz. Bu durumlarda, bir kopyasını `in` parametre oluşturulur. Derleyici için geçici değişken oluşturabilir çünkü `in` parametresi varsayılan değerler için belirtebilirsiniz `in` parametresi. Aşağıdaki kod, ikinci noktası için varsayılan değer olarak (noktası 0,0) kaynak belirtir:

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Salt okunur bağımsız değişkenleri başvuruya göre geçiren zorlamak için bu seçeneği belirtin `in` çağrı sitesinde aşağıdaki kodda gösterildiği gibi bağımsız değişkenlerde değiştiricisi:

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Bu davranışı benimsemeye kolaylaştırır `in` parametreleri zaman içinde büyük kod tabanlarında nerede performans artışı mümkündür. Eklediğiniz `in` değiştirici yöntem imzaları için ilk. Daha sonra ekleyebilirsiniz `in` değiştiricisi, çağrı siteleri ve oluşturma `readonly struct` savunma kopyası oluşturmaktan kaçınmak derleyicinin etkinleştirmek için türleri `in` daha fazla konumda parametreleri.

`in` Parametresi ataması, de başvuru türleri veya sayısal değerleri ile kullanılabilir. Ancak, varsa minimum avantajlarından her iki durumda değildir.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Mutable yapılar gibi kullanmamanız `in` bağımsız değişken

Yukarıda açıklanan teknikleri, başvurular döndüren ve başvuruya göre değerler geçirerek kopyaları önlemek açıklanmaktadır. Bağımsız değişken türü olarak bildirilmemişse, bu teknikler en iyi şekilde çalıştığı `readonly struct` türleri. Aksi halde, derleyici oluşturmalısınız **savunma kopyası** herhangi bir bağımsız değişken salt okunur durumunu uygulamak, birçok durumda. 3B bir başlangıç noktasından uzaklığı hesaplar aşağıdaki örneği göz önünde bulundurun:

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D` Yapısıdır *değil* salt okunur yapı. Bu yöntemin gövdesinde altı farklı özellik erişim çağrıları vardır. İlk incelemesi üzerinde bu erişimi güvenli olduğunu düşündük. Sonuçta bir `get` erişimci nesne durumunu değiştirme olmamalıdır. Ancak, zorlayan dil kural yoktur. Bu genel bir kural olur. Her türlü uygulayabileceğine bir `get` iç durumu değiştirildiğinde erişimcisi. Bazı dil garanti derleyici herhangi bir üyenin çağırmadan önce bağımsız değişkenin bir geçici kopya oluşturmanız gerekir. Geçici depolama yığında oluşturulur, bağımsız değişken değerlerini geçici depolama alanına kopyalanır ve değer her üye erişimi yığını kopyalanır `this` bağımsız değişken. Çoğu durumda, bu kopya yeterince bu geçişi değere göre daha hızlı geçişi tarafından salt okunur başvuru bağımsız değişken türü olmadığı durumlarda performans zarar bir `readonly struct`.

Bunun yerine, uzaklık hesaplama sabit yapısı kullanıyorsa `ReadonlyPoint3D`, geçici nesneler gerekmiyor:

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Üyeleri çağırdığınızda derleyici, daha verimli kod oluşturur. bir `readonly struct`: `this` başvuru, alıcı bir kopyasını yerine, her zaman bir `in` parametresine geçirilen başvuruyla üye yöntemi. Bu iyileştirme kaydeder kullandığınızda kopyalama bir `readonly struct` olarak bir `in` bağımsız değişken.

Kullanarak performans farklarını gösteren bir örnek program gördüğünüz [Benchmark.net](https://www.nuget.org/packages/BenchmarkDotNet/) de bizim [örnekleri depomuzdan](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) GitHub üzerinde. Değere ve başvuruya göre değişmez bir yapı geçirme ile değere ve başvuruya göre değişebilir yapı geçirme ile karşılaştırır. Hızlı Başvuru ile geçişi ve sabit yapı kullanılır.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Kullanım `ref struct` blokları veya bellek ile tek bir yığın çerçevesi üzerinde çalışmak için türleri

Tek yığın çerçevesi için kısıtlı bir değer türünün bildirimi olanağı ilgili dil özelliğidir. Bu kısıtlama, çeşitli iyileştirmeler yapmak için derleyici sağlar. Bu özellik için birincil motivasyon olan <xref:System.Span%601> ve ilişkili yapıları. Bu geliştirmeler performans iyileştirmeleri yeni kullanarak elde edersiniz ve güncelleştirilmiş .NET API kullanımını <xref:System.Span%601> türü.

Kullanılarak oluşturulan bellek ile çalışmaya benzer gereksinimlerine sahip olabilir [ `stackalloc` ](language-reference/keywords/stackalloc.md) veya Interop API'leri bellekten kullanırken. Kendi tanımlayabilirsiniz `ref struct` türleri bu ihtiyaçları için.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Türü

Bir yapı olarak bildirme `readonly ref` avantajları ve kısıtlamaları birleştirir `ref struct` ve `readonly struct` bildirimleri. Tek yığın çerçevesi için salt okunur aralık tarafından kullanılan bellek sınırlıdır ve salt okunur aralık tarafından kullanılan bellek değiştirilemez.

## <a name="conclusions"></a>Sonuçları

Değer türleri kullanarak ayırma işlemlerinin sayısını en aza indirir:

- Değer türleri için depolama, yerel değişkenleri ve yöntem bağımsız değişkenleri için ayrılan yığınıdır.
- Depolama alanı diğer nesne üyeleri değer türleri için ayrı bir ayırma olarak değil o nesnenin bir parçası olarak ayrılır.
- Değer türü için depolama dönüş değeri ayrılan yığın.

Başvuru türleri aynı bu durumlarda ile karşılaştırın.

- Yığın yerel değişkenleri ve yöntem bağımsız değişkenleri için ayrılan depolama başvuru türleri için var. Yığında başvuru depolanır.
- Diğer nesne üyeleri başvuru türleri için depolama ayrı olarak yığında ayrılır. Başvuru içeren bir nesne depolar.
- Değer türü için depolama dönüş değeri ayrılan yığın. Yığında başvuru depolama depolanır.

Ayırmaları en aza ödünler. Daha fazla bellek kopyalama zaman boyutu `struct` başvuru boyutundan büyük. Başvuru, genellikle 64 bit veya 32 bit olduğundan ve hedef makine CPU üzerinde bağlıdır.

Bu bileşim genellikle en az düzeyde performans etkisi olur. Ancak, büyük yapılar veya daha büyük koleksiyonlar için performans etkisini artar. Etkisi sıkı döngüler ve programlar için etkin yolları büyük olabilir.

Bu geliştirmeler C# dil performans kritik algoritmaları burada bellek ayırmaları en aza indirmek için gerekli performansı ulaşmada önemli bir etken tasarlanmıştır. Yazdığınız kod bu özellikleri sık kullanmadığınız bulabilirsiniz. Ancak, bu geliştirmeler, .NET uyarlanmıştır. Giderek daha fazla API yaparken bu özelliklerini kullanmak, uygulamalarınızın performansını artırma görürsünüz.
