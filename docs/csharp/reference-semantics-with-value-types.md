---
title: Başvuru semantiği ile değer türleri
description: Kopyalama yapıları güvenle en aza dil özellikleri anlama
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 8a0cfe83200d50eefa9b01ab51591a5fe0703ec0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="reference-semantics-with-value-types"></a>Başvuru semantiği ile değer türleri

Değer türleri kullanmanın bir avantajı, bunlar genellikle yığın ayırmaları kaçının ' dir.
Karşılık gelen dezavantajı, değeriyle kopyalanırlar ' dir. Bu kolaylığını büyük miktarlarda verinin çalışması algoritmaları iyileştirmek daha zor hale getirir. C# 7.2 içindeki yeni dil özellikleri pass-by-reference semantiği değer türleri ile etkinleştirmek mekanizmaları sağlar. Bu özellikler akıllıca kullanırsanız, her iki ayırma en aza indirmek ve işlemleri kopyalayın. Bu makalede, bu yeni özellikleri açıklar.

Bu makaledeki örnek kod çoğunu C# 7.2 eklenen özellikler gösterir. Bu özellikleri kullanmak için projenizin C# 7,2 veya üzeri projenizde kullanacak şekilde yapılandırmanız gerekir. Visual Studio seçmek için kullanabilirsiniz. Her proje için seçin **proje** menüsünde, ardından **özellikleri**. Seçin **yapı** sekmesinde **Gelişmiş**. Buradan, dil sürümü yapılandırabilirsiniz. "7.2" veya "en son" seçin.  Veya düzenleyebilirsiniz *csproj* dosya ve aşağıdaki düğüm ekleyin:

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

"7,2" veya "en son" değerini kullanabilirsiniz.

## <a name="specifying-in-parameters"></a>Belirtme `in` parametreleri

C# 7.2 ekler `in` varolan tamamlamak üzere anahtar sözcük `ref` ve `out` bağımsız değişkenleri başvuruya göre geçirir bir yöntem yazdığınızda anahtar sözcükler. `in` Anahtar sözcüğü parametresi başvuruya göre geçirme ve çağrılan yöntem kendisine geçirilen değer değiştirmez belirtir. 

Bu ek tasarım hedefi ifade etmek için tam bir sözlüğünü sağlar. Değer türleri aşağıdaki değiştiricileri hiçbirini belirtmeyin olduğunda çağrılan yönteme geçirildiğinde kopyalanır. Bu değiştiricileri her bir değer türü başvurusu tarafından kopya önleme geçirilen belirtin. Her değiştiricisi farklı bir hedefi ifade eder:

- `out`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değerini ayarlar.
- `ref`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değeri ayarlayabilir.
- `in`: Bu yöntem, bu parametre olarak kullanılan bağımsız değişkeninin değeri değiştirmez.

Eklediğinizde `in` değiştiricisi başvuruya göre bağımsız değişken geçirmek için tasarım hedefi olan gereksiz kopyalama önlemek için başvuruya göre bağımsız değişken geçirmek için bildirin. Bu bağımsız değişken olarak kullanılan nesne değiştirmek istiyorsanız değil. Aşağıdaki kod örneği 3B uzaydaki iki nokta arasındaki uzaklığı hesaplar bir yöntemin gösterir. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Her üç çiftleri içeren iki yapıları bağımsız değişkenler. Bir çift 8 bayt olduğundan, her bir bağımsız değişkeni 24 bayttır. Belirterek `in` değiştiricisi, geçirdiğiniz bu bağımsız değişkenlerden 4-bayt veya 8-bayt başvuru makine mimarisi bağlı olarak. Boyutu fark küçüktür, ancak uygulamanız bu yöntem birçok farklı değerleri kullanarak sıkı bir döngüde çağırdığında, hızlı bir şekilde ekleyebilirsiniz.
 
`in` Değiştiricisi hazırlandı `out` ve `ref` başka yöntemler de. Yalnızca içinde varken, farklı bir yöntem aşırı oluşturulamıyor `in`, `out`, veya `ref`. Bu yeni kurallar her zaman için tanımlanmış aynı davranışı genişletmek `out` ve `ref` parametreleri.

`in` Değiştiricisi parametreler isteyen herhangi bir üyesi için uygulanan: yöntemler, temsilciler, Lambda'lar, yerel İşlevler, dizin oluşturucular, işleçler.

Farklı `ref` ve `out` bağımsız değişken kullandığınız değişmez değerler veya sabitleri bağımsız değişkeni için bir `in` parametresi. Ayrıca, farklı bir `ref` veya `out` parametre, geçerli gerekmeyen `in` çağrısı sitede değiştiricisi. Aşağıdaki kod iki örnek çağırma gösterir `CalculateDistance` yöntemi. İlk iki yerel değişkenleri başvuruya göre geçirilen kullanır. İkinci yöntem çağrısının bir parçası olarak oluşturulan geçici bir değişken içerir. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

İçinde derleyici sağlar, salt okunur yapısına birkaç yolu vardır bir `in` bağımsız değişkeni zorlanır.  Öncelikle, çağrılan yöntemin doğrudan atayamazsınız bir `in` parametresi. Herhangi bir alan için doğrudan atayamazsınız bir `in` parametresi. Ayrıca, geçiremezsiniz bir `in` yöntemi yoğun parametresini `ref` veya `out` değiştiricisi.
Derleyici zorlar `in` olmayan bir salt okunur değişken bağımsız değişken. Geçişi değerli semantiği kullanan herhangi bir örnek yöntemini çağırabilirsiniz. Bu durumlarda, bir kopyasını `in` parametresi oluşturulur. Derleyici herhangi için geçici bir değişken oluşturmak için `in` parametresi, ayrıca varsayılan değerleri için belirtebilirsiniz `in` parametresi. İzleme kodu, ikinci noktası için varsayılan değer olarak kaynak (noktası 0,0) belirlemek için kullanır:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

`in` Parametresi atamasını Ayrıca başvuru türleriyle kullanılan veya sayısal değerleri oluşturulmuş. Bununla birlikte, her iki durumda da avantajları en az, varsa.

## <a name="ref-readonly-returns"></a>`ref readonly` döndürür

Başvuruya göre dönüş değeri türü, ancak bu değeri değiştirmeden gelen arayan engellemek isteyebilirsiniz. Kullanım `ref readonly` bu tasarım hedefi express değiştiricisi. Okuyucular, var olan verilere bir başvuru döndürüyor, ancak değişiklik sağlanmıyor olduğunu bildirir. 

Derleyici çağıran başvurusu değiştirilemez zorlar. Deneme değerine doğrudan atamak için bir derleme zamanı hatası oluşturur. Ancak, derleyici herhangi bir üye yöntemini yapısı durumunu değiştirir olmadığını bilemezsiniz.
Nesne değiştirilmeyen emin olmak için derleyici bir kopyasını oluşturur ve bu kopyayı kullanarak başvurular üye çağırır. Herhangi bir değişiklik savunma bu kopyaya ' dir. 

Büyük olasılıkla, kitaplığını kullanarak `Point3D` genellikle kaynak kod genelindeki kullanırsınız. Her örneği yığında yeni bir nesne oluşturur. Bir sabit oluşturup başvuruya göre dönmek için yararlı olabilir. Ancak, iç depolama başvuru döndürürse, çağıran başvurulan depolama değiştirilemiyor zorlamak isteyebilirsiniz. Aşağıdaki kod döndüren bir salt okunur özelliği tanımlayan bir `readonly ref` için bir `Point3D` kaynağını belirtir.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Ref salt okunur bir kopyasını dönüş oluşturmak kolaydır: yalnızca ile bildirilmemiş bir değişkene atayın `ref readonly` değiştiricisi. Derleyici nesneyi atama bir parçası olarak kopyalamak için kod oluşturur. 

Bir değişkene atadığınızda bir `ref readonly return`, ya da belirtebilirsiniz bir `ref readonly` değişkeni veya salt okunur başvuru değeri tarafından kopyasını:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

İlk atama önceki kodda bir kopyasını oluşturur `Origin` sabiti ve kopyalama atar. İkinci bir başvuru atar. Dikkat `readonly` değiştiricisi değişken bildirimi parçası olması gerekir. Başvurduğu başvurusu değiştirilemez. Bunu yapmak için deneme, bir derleme zamanı hatasına neden.

## <a name="readonly-struct-type"></a>`readonly struct` Türü

Uygulama `ref readonly` yapı yüksek trafik kullanımlar için yeterli olabilir.
Diğer durumlarda, sabit bir yapı oluşturmak isteyebilirsiniz. Ardından readonly başvuruya göre geçirebilirsiniz. Alıştırma savunma kaldırır meydana yöntemleri olarak kullanılan bir yapı eriştiğinizde kopyalar bir `in` parametresi.

Bunu oluşturarak yapabilirsiniz bir `readonly struct` türü. Ekleyebileceğiniz `readonly` yapısı bildirimine değiştiricisi. Tüm örnek yapı üyesi olmalarını derleyici zorlar `readonly`; `struct` sabit olması gerekir.

Diğer en iyi duruma getirme vardır bir `readonly struct`. Kullanabileceğiniz `in` her konumda değiştiricisi burada bir `readonly struct` bir bağımsız değişken. Ayrıca, döndürebilir bir `readonly struct` olarak bir `ref return` zaman iade nesneyi, yaşam süresi genişletir nesnesi döndüren yöntemi kapsamı dışındadır.

Son olarak, üyeleri çağırdığınızda derleyici daha verimli kodunu oluşturur bir `readonly struct`: `this` alıcı kopyasını yerine başvurusunun olduğundan her zaman bir `in` parametresine geçirilen üye yöntemi başvuru. Bu iyileştirme kullanırken daha fazla kopyalama kaydeder bir `readonly struct`. `Point3D` Bu değişikliği mükemmel bir adaydır. Aşağıdaki kod güncelleştirilmiş gösterir `ReadonlyPoint3D` yapısı:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Türü

Başka bir ilgili dil yığını ayrılmış olması gereken değer türünü bildirmesine olanağı özelliğidir. Diğer bir deyişle, bu tür hiçbir zaman öbek üzerinde başka bir sınıf üyesi olarak oluşturulabilir. Bu özellik için birincil motivasyon oluştu <xref:System.Span%601> ve ilgili yapıları. <xref:System.Span%601> yönetilen bir işaretçi bir grubun üyeleri ve diğeri aralık uzunluğu olan içerebilir. C# güvenli olmayan bir bağlam dışında yönetilen bellek işaretçiler desteklemediğinden, aslında biraz farklı uygulanır. İşaretçinin ve uzunluk değişiklikleri yazma atomik değil. Yani bir <xref:System.Span%601> aralığı hataları dışında tabi olacaktır veya diğer tür güvenlik ihlallerini onu değil kısıtlı bir tek yığın çerçevesi olan. Ayrıca, yönetilen bir işaretçi GC yığınında genellikle koyma JIT zamanında çöküyor.

Kullanılarak oluşturulan bellekle çalışma benzer gereksinimleri olabilir [ `stackalloc` ](language-reference/keywords/stackalloc.md) veya birlikte çalışma API'leri bellekten kullanılırken. Kendi tanımlayabilirsiniz `ref struct` türleri bu ihtiyaçları için. Bu makalede, gördüğünüz kullanan örnekler `Span<T>` basitleştirmek için.

`ref struct` Bildirimi bildirir bu tür bir yapı yığında olmalıdır. Dil kuralları bu türlerinin güvenli kullanımını emin olun. Diğer türleri olarak bildirilen `ref struct` dahil <xref:System.ReadOnlySpan%601>. 

Tutma amacı bir `ref struct` yazın yığın ayırma değişkeni derleyici tüm zorlar çeşitli kurallar tanıtır gibi `ref struct` türleri.

- Kutu olamaz bir `ref struct`. Nesnesine atanamaz bir `ref struct` türünde bir değişkene `object`, `dynamic`, veya herhangi bir arabirim türü.
- Bildiremezsiniz bir `ref struct` bir sınıf veya normal yapı üyesi olarak.
- Yerel değişkenler bildiremezsiniz `ref struct` zaman uyumsuz yöntemleri türlerinde. Döndüren zaman uyumlu yöntemleri bildirebilir `Task`, `Task<T>` veya görev-like türleri.
- Bildiremezsiniz `ref struct` yineleyiciler yerel değişkenler.
- Yakalama yapılamaz `ref struct` lambda ifadeleri veya yerel işlevler değişkenlerinin.

Bu kısıtlamalar değil yanlışlıkla kullandığınızdan emin olun bir `ref struct` Yönetilen yığın Yükselt bir şekilde.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Türü

Yapı olarak bildirme `readonly ref` yararları ve kısıtlamaları birleştirir `ref struct` ve `readonly struct` delcarations. 

Aşağıdaki örnek, bildirimi gösterir `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Sonuçları

C# dili Bu geliştirmeler, burada bellek ayırmaları gerekli performansını elde için kritik olabilir performans kritik algoritmaları için tasarlanmıştır. Yazdığınız kodu bu özellikleri sık kullanmadığınız bulabilirsiniz. Ancak, bu geliştirmeler, .NET Framework'teki birçok konumdaki uyarlanmıştır. Daha da fazla API'leri yaparken bu özellikleri kullanan, kendi uygulamaların performansını artırmak görürsünüz.
