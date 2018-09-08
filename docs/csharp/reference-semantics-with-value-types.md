---
title: Değer türleri ile başvuru semantiği
description: Kopyalama yapıları güvenli bir şekilde en aza dil özelliklerini anlama
ms.date: 11/10/2017
ms.custom: mvc
ms.openlocfilehash: f241219994d7a03192a4aea69b912bf1ac5ed29c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133746"
---
# <a name="reference-semantics-with-value-types"></a>Değer türleri ile başvuru semantiği

Değer türleri kullanmanın bir avantajı, bunlar genellikle yığın ayırmaları önlemek ' dir.
Olumsuz yönüyse, değere göre kopyalanır ' dir. Bu bir tradeoff, büyük miktarlarda veri çalışan algoritmalar iyileştirmek zorlaştırır. Yeni C# 7.2 dil özellikleri etkinleştiren değer türleri ile başvuru ile geçişi semantiği mekanizmaları sağlar. Bu özellikler hem ayırmaların en aza indirmek ve kopyalama işlemlerini akıllıca kullanın. Bu makalede, bu yeni özellikleri keşfediyor.

Bu makaledeki örnek kodun çoğu C# 7.2 eklenen özellikleri gösterir. Bu özellikleri kullanmak için projenizin C# 7.2 veya üzeri kullanmak için yapılandırmanız gerekir. Dil sürümü hakkında daha fazla bilgi için bkz. [dil sürümü yapılandırma](language-reference/configure-language-version.md).

## <a name="passing-arguments-by-readonly-reference"></a>Salt okunur başvuruya göre bağımsız değişkenleri geçirme

C# 7.2 ekler `in` varolan tamamlamak üzere anahtar sözcüğü `ref` ve `out` başvuruya göre bağımsız değişkenleri geçirmek için anahtar sözcükler. `in` Anahtar sözcüğü, bağımsız değişkenini başvuruya göre geçirme belirtir, ancak çağrılan yöntem değerini değiştirmez. 

Bu ayrıca, tasarım hedefi ifade etmek için tam bir kelime sağlar. Değer türleri Yöntem imzasında aşağıdaki değiştiriciler hiçbirini belirtmezseniz, çağrılan bir yönteme geçildiğinde kopyalanır. Bu değiştiriciler, her bir değer türü başvuruya göre kopyalama önleme geçirilen belirtir. Her değiştiricisi, farklı bir hedefi ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkenin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değerini ayarlayabilirsiniz.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değerini değiştirmez.

Ekleme `in` başvuruya göre bağımsız değişken geçirin ve gereksiz şekilde kopyalamama olanağı, başvuruya göre bağımsız değişkenleri geçirmek için tasarım amacınızla bildirmek üzere değiştiricisi. Bu bağımsız değişken olarak kullanılan nesneyi değiştirmek istemediğiniz. Aşağıdaki kod örneği, 3B alanda iki nokta arasındaki uzaklığı hesaplar bir yöntemin gösterir. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Her üç çiftten içeren iki yapıları bağımsız değişkenler. Bir çift 8 bayt olduğundan her bağımsız değişken 24 bayttır. Belirterek `in` makine mimarisine bağlı olarak bu bağımsız değişken bir 4 baytlık veya 8 bayt başvuru geçirdiğiniz değiştiricisi. Boyutu fark küçüktür, ancak uygulamanız bu yöntemi kullanarak birçok farklı değerler sıkı bir döngüde çağırdığında, hızlı bir şekilde toplanabilir.
 
`in` Değiştiricisi destekleyici `out` ve `ref` başka yöntemler de. Yalnızca içinde varken, farklı bir yöntem aşırı yüklemeleri oluşturulamıyor `in`, `out`, veya `ref`. Bu yeni kurallar her zaman için tanımlanmış aynı davranışı genişletmek `out` ve `ref` parametreleri.

`in` Değiştiricisi parametre almayan herhangi bir üyeye uygulanan: yöntemleri, temsilciler, lambda ifadeleri, yerel İşlevler, Dizinleyicileri, işleçleri.

Farklı `ref` ve `out` bağımsız değişkenler kullanabilirsiniz değişmez değerler veya sabitler bağımsız değişkeni için bir `in` parametresi. Ayrıca, farklı bir `ref` veya `out` parametresi, geçerli gerekmeyen `in` çağrı sitesinde değiştiricisi. Aşağıdaki kod çağırmanın iki örnek gösterir `CalculateDistance` yöntemi. İlk iki yerel değişkenini başvuruya göre geçirilen kullanır. İkinci yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Hangi derleyici sağlar, salt okunur yapısını birkaç şekilde bir `in` bağımsız değişken zorlanır.  İlk olarak çağrılan yöntem doğrudan atayamazsınız bir `in` parametresi. Herhangi bir alan için doğrudan atanamaz bir `in` değeri olduğunda parametresi bir `struct` türü. Ayrıca, geçirilemez bir `in` kullanarak herhangi bir yöntem için parametre `ref` veya `out` değiştiricisi.
Bu kurallar herhangi bir alan için geçerli bir `in` parametre, sağlanan alan bir `struct` türü ve parametre bir `struct` türü. Üye erişimi tüm düzeylerinde türleri birden çok üye erişimi katmanı sağlanan bu kurallar aslında uygulanmasını `structs`. Derleyici, zorlar `struct` türleri olarak geçirildi `in` bağımsız değişkenleri ve bunların `struct` üyesi olan diğer yöntemlerinin bağımsız değişkenleri olarak kullanılan salt okunur değişkenler.

Kullanımını `in` parametreleri kopyalarının olası performans maliyetini ortadan kaldırır. Herhangi bir yöntem çağrısının semantiği değiştirmez. Bu nedenle, belirtmeniz gerekmez `in` çağrı sitesinde değiştiricisi. Ancak, atlama `in` değiştiricisi çağrı sitesinde derleyici bağımsız değişkeni aşağıdaki nedenlerle bir kopyasını izni olduğunu bildirir:

- Örtük bir dönüştürme ancak olmayan bir kimlik dönüştürme bağımsız değişken türü parametre türü yoktur.
- Bağımsız değişken ifade ancak bilinen depolama değişkeni yok.
- Mevcut bir aşırı yükleme olan varlığı veya yokluğu ile farklı `in`. Bu durumda, değere göre aşırı daha iyi bir eşleşmedir.

Bu kurallar, mevcut kodu salt okunur başvuru bağımsız değişkenleri kullanın güncelleştirmelerden yararlıdır. Çağrılan yöntemde, değer parametreleri kullanan herhangi bir örnek yöntemi çağırabilirsiniz. Bu durumlarda, bir kopyasını `in` parametre oluşturulur. Derleyici için geçici değişken oluşturabildiğinden `in` parametresi varsayılan değerler için belirtebilirsiniz `in` parametresi. Aşağıdaki kod, ikinci noktası için varsayılan değer olarak (noktası 0,0) kaynak belirtir:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Yalnızca okuma bağımsız değişkenleri başvuruya göre geçiren zorlamak için bu seçeneği belirtin `in` modifer çağrı sitesinde aşağıdaki kodda gösterildiği gibi bağımsız değişkenlerde:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

Bu davranışı benimsemeye kolaylaştırır `in` parametreleri zaman içinde büyük kod tabanlarında nerede performans artışı mümkündür. Eklediğiniz `in` değiştirici yöntem imzaları için ilk. Daha sonra ekleyebilirsiniz `in` değiştiricisi callsites adresindeki oluşturup `readonly struct` savunma kopyası oluşturmaktan kaçınmak derleyicinin etkinleştirmek için türleri `in` daha fazla konumda parametreleri.

`in` Parametresi ataması, de başvuru türleri veya sayısal değerleri ile kullanılabilir. Ancak, varsa minimum avantajlarından her iki durumda değildir.

## <a name="ref-readonly-returns"></a>`ref readonly` döndürür

Bir değer türü başvuru ile döndürülen, ancak bu değeri değiştirmek gelen arayan engellemek isteyebilirsiniz. Kullanım `ref readonly` bu tasarım hedefi ifade etmek için değiştiricisi. Okuyucular, mevcut verileri bir başvuru döndürerek, ancak değiştirilmesine izin vermiyor olduğunu bildirir. 

Derleyici, çağırana başvurusu değiştirilemez zorlar. Denemeleri değeri doğrudan atamak için bir derleme zamanı hatası oluşturur. Ancak, derleyici, herhangi bir üye yöntemi yapı durumunu değiştirirse bilemezsiniz.
Nesne değiştirilmez emin olmak için derleyici bir kopyasını oluşturur ve bu kopyayı kullanarak başvuruları üye arar. Herhangi bir değişiklik için savunma kopyası var. 

Büyük olasılıkla bu kitaplığı kullanarak `Point3D` genellikle kaynak kod genelindeki kullanırsınız. Her örnek, yığın üzerinde yeni bir nesne oluşturur. Bir sabit oluşturmak ve başvuru ile döndürülen için yararlı olabilir. Ancak, iç depolama alanına bir başvuru döndürmeyi ise çağıranın başvurulan depolama değiştiremezsiniz zorlamak isteyebilirsiniz. Aşağıdaki kod döndüren bir salt okunur özelliği tanımlar. bir `readonly ref` için bir `Point3D` kaynağını belirtir.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Bir ref salt okunur bir kopyasını dönüş oluşturmak kolaydır: yalnızca bildirilen olmayan bir değişkene atayın `ref readonly` değiştiricisi. Derleyici, atama bir parçası olarak nesneyi kopyalamak için kod oluşturur. 

Bir değişkene atadığınızda bir `ref readonly return`, belirtebilirsiniz bir `ref readonly` değişkeni veya bir değere göre kopyalama salt okunur başvuru:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Önceki kodda ilk atama bir kopyasını oluşturur `Origin` sabit ve kopyalama atar. İkinci bir başvuru atar. Dikkat `readonly` değiştiricisi değişkenin bildirimi bir parçası olması gerekir. Başvurduğu başvurusu değiştirilemez. Bunu denediğinizde bir derleme zamanı hatasına neden.

## <a name="readonly-struct-type"></a>`readonly struct` Türü

Uygulama `ref readonly` yapı trafiği yüksek kullanımları için yeterli olabilir.
Diğer durumlarda, sabit bir yapı oluşturmak isteyebilirsiniz. Ardından, her zaman salt okunur başvuru ile geçirebilirsiniz. Yöntemleri olarak kullanılan bir yapının eriştiğinde uygulama savunma kaldırır meydana kopyalar bir `in` parametresi.

Oluşturarak bunu yapabilirsiniz bir `readonly struct` türü. Ekleyebileceğiniz `readonly` değiştiricisi için yapı bildirimi. Derleyici yapının tüm örnek üyeleri olduğunu zorlar `readonly`; `struct` sabit olmalıdır.

Diğer iyileştirmeler için vardır bir `readonly struct`. Kullanabileceğiniz `in` her konumda değiştiricisi burada bir `readonly struct` bir bağımsız değişken. Ayrıca, döndürebilir bir `readonly struct` olarak bir `ref return` ne zaman, döndürüyor bir nesne ömürlerinin genişletir nesnesi döndüren yöntem kapsamı dışındadır.

Son olarak, derleyici üyeleri çağırdığınızda daha verimli kod oluşturur bir `readonly struct`: `this` başvuru, alıcı bir kopyasını yerine, her zaman bir `in` parametresine geçirilen başvuruyla üye yöntemi. Bu iyileştirme kullanırken daha fazla kopyalama kaydeder bir `readonly struct`. `Point3D` Bu değişikliği için mükemmel bir adaydır. Aşağıdaki kod güncelleştirilmiş gösterir `ReadonlyPoint3D` yapısı:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Türü

İlgili dil özelliği başka bir yığın ayrılmış olması gereken bir değer türü bildirmek için yeteneğidir. Diğer bir deyişle, bu tür asla yığın üzerinde başka bir sınıf üyesi olarak oluşturulabilir. Bu özellik için birincil motivasyon olan <xref:System.Span%601> ve ilişkili yapıları. <xref:System.Span%601> yönetilen bir işaretçiyi kendi üyelerinden biri olarak diğer aralık uzunluğu olan içerebilir. C# güvenli olmayan bir bağlam dışında yönetilen bellek işaretçileri desteklemediği için biraz farklı şekilde uygulanır. İşaretçiyi ve uzunluğunu değiştiren herhangi bir yazma atomik olması gerekmez. Yani bir <xref:System.Span%601> , sınırlı değildir tek yığın çerçevesi için diğer tür güvenlik ihlallerini olan ya da yetersiz aralık hatalarında tabi olacaktır. Ayrıca, Yönetilen işaretçi GC yığınında genellikle koyarak JIT zaman kilitleniyor.

Kullanılarak oluşturulan bellek ile çalışmaya benzer gereksinimlerine sahip olabilir [ `stackalloc` ](language-reference/keywords/stackalloc.md) veya Interop API'leri bellekten kullanırken. Kendi tanımlayabilirsiniz `ref struct` türleri bu ihtiyaçları için. Bu makalede, gördüğünüz kullanan örnekler `Span<T>` kolaylık sağlamak için.

`ref struct` Bildirimi bildirir yığında bu tür bir yapı olmalıdır. Dil kuralları, bu tür güvenli kullanımı emin olun. Diğer türleri olarak bildirilen `ref struct` dahil <xref:System.ReadOnlySpan%601>. 

Amacı tutarken, bir `ref struct` yazın, tüm derleyici zorlayan çeşitli kurallar bir yığın ayırma değişken tanıtan `ref struct` türleri.

- Kutusunda edilemez bir `ref struct`. Atama yapılamaz bir `ref struct` türünde bir değişkene `object`, `dynamic`, veya herhangi bir arabirim türü.
- Bildirip bir `ref struct` bir sınıf veya normal yapı üyesi olarak.
- Yerel değişkenler bildiremezsiniz `ref struct` zaman uyumsuz yöntemlerde türleri. Döndüren zaman uyumlu yöntemleri bildirebilirsiniz `Task`, `Task<T>` veya görev benzeri türü.
- Bildirip `ref struct` yineleyiciler yerel değişkenler.
- Yakalama gerçekleştiremez `ref struct` değişkenleri lambda ifadeleri veya yerel işlevler.

Bu kısıtlamalar, yanlışlıkla kullanmayın emin olun. bir `ref struct` bir şekilde yönetilen yığınla Yükselt.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Türü

Bir yapı olarak bildirme `readonly ref` avantajları ve kısıtlamaları birleştirir `ref struct` ve `readonly struct` bildirimleri. 

Aşağıdaki örnek, bildirimi gösterir `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Sonuçları

Bu geliştirmeler C# diline burada bellek ayırmaları gerekli performansı elde etmek için kritik olabilir performans kritik algoritmalar için tasarlanmıştır. Yazdığınız kod bu özellikleri sık kullanmadığınız bulabilirsiniz. Ancak, bu geliştirmeler, .NET Framework'teki farklı konumlarda uyarlanmıştır. Giderek daha fazla API yaparken bu özelliklerini kullanmak, kendi uygulamalarınıza performansını artırma görürsünüz.
