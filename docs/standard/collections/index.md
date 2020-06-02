---
title: Koleksiyonlar ve Veri Yapıları
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
ms.openlocfilehash: 0b87121a4a2003d3f85cf58f6d93f156fc121e54
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287958"
---
# <a name="collections-and-data-structures"></a>Koleksiyonlar ve Veri Yapıları

Benzer veriler genellikle koleksiyon olarak depolandığında ve değiştirildiğinde daha verimli bir şekilde işlenebilir. <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections> <xref:System.Collections.Generic> <xref:System.Collections.Concurrent> <xref:System.Collections.Immutable> Bir koleksiyondaki öğeleri veya öğe aralığını eklemek, kaldırmak ve değiştirmek için,, ve ad alanlarındaki sınıfı veya sınıfları kullanabilirsiniz.

İki ana koleksiyon türü vardır; Genel Koleksiyonlar ve genel olmayan Koleksiyonlar. Genel Koleksiyonlar .NET Framework 2,0 ' ye eklenmiştir ve derleme zamanında tür kullanımı uyumlu koleksiyonlar sağlar. Bu nedenle, genel Koleksiyonlar genellikle daha iyi performans sunar. Genel Koleksiyonlar, oluşturuldukları sırada bir tür parametresi kabul eder ve <xref:System.Object> koleksiyondan öğe eklediğinizde veya kaldırdığınızda türe ve türüne dönüştürme yapılmasını gerektirmez.  Ayrıca, çoğu genel koleksiyon Windows Mağazası uygulamalarında desteklenir. Genel olmayan koleksiyonlar öğeleri olarak depolar <xref:System.Object> , atama gerektir ve çoğu Windows Mağazası uygulaması geliştirme için desteklenmez. Ancak, daha eski bir kodda genel olmayan koleksiyonlar görebilirsiniz.

.NET Framework 4 ' ten başlayarak, ad alanındaki koleksiyonlar, <xref:System.Collections.Concurrent> koleksiyon öğelerine birden çok iş parçacığından erişmek için verimli iş parçacığı güvenli işlemleri sağlar. <xref:System.Collections.Immutable>Ad alanındaki ([NuGet paketi](https://www.nuget.org/packages/System.Collections.Immutable)) sabit koleksiyon sınıfları, işlemler orijinal koleksiyonun bir kopyasında yapıldığından ve özgün koleksiyon değiştirilemediğinden, doğal olarak iş parçacığı açısından güvenlidir.

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>Ortak koleksiyon özellikleri

Tüm Koleksiyonlar koleksiyondaki öğeleri eklemek, kaldırmak veya bulmak için yöntemler sağlar. Ayrıca, arabirimi veya arabirimi doğrudan veya dolaylı olarak uygulayan tüm koleksiyonlar <xref:System.Collections.ICollection> <xref:System.Collections.Generic.ICollection%601> Bu özellikleri paylaşır:

- **Koleksiyonu listeleme özelliği**

    .NET Framework koleksiyonlar <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> , koleksiyonun üzerinden tekrarlandırılmış olmasını sağlar veya uygular. Numaralandırıcı, koleksiyondaki herhangi bir öğe için taşınabilir bir işaretçi olarak düşünülebilir. [Foreach, in](../../csharp/language-reference/keywords/foreach-in.md) Ifadesi ve [for each... Next Ifadesinde](../../visual-basic/language-reference/statements/for-each-next-statement.md) yöntemi tarafından sunulan Numaralandırıcı kullanılır <xref:System.Collections.IEnumerable.GetEnumerator%2A> ve Numaralandırıcının işlenmesinin karmaşıklığı gizlenir. Ayrıca, uygulayan herhangi <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> bir koleksiyon *sorgulanabilir bir tür* olarak değerlendirilir ve LINQ ile sorgulanabilir. LINQ sorguları verilere erişmek için ortak bir model sağlar. Genellikle standart döngülerden daha kısa ve okunabilir `foreach` ve filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), [LINQ Sorgularına Giriş (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)ve [temel sorgu işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

- **Koleksiyon içeriğini bir diziye kopyalama özelliği**

    Tüm koleksiyonlar, **CopyTo** yöntemi kullanılarak bir diziye kopyalanabilir; Ancak, yeni dizideki öğelerin sırası, Numaralandırıcı tarafından döndürülen diziye göre belirlenir. Elde edilen dizi her zaman bir sıfır alt sınırı olan bir boyutludur.

Ayrıca, birçok koleksiyon sınıfı aşağıdaki özellikleri içerir:

- **Kapasite ve sayı özellikleri**

    Bir koleksiyonun kapasitesi içerebileceği öğelerin sayısıdır. Bir koleksiyonun sayısı, gerçekten içerdiği öğelerin sayısıdır. Bazı koleksiyonlar kapasiteyi veya sayıyı veya her ikisini de gizler.

    En fazla koleksiyon, geçerli kapasiteye ulaşıldığında kapasiteyi otomatik olarak genişletir. Bellek yeniden ayrılır ve öğeler eski koleksiyondan yeni bir koleksiyona kopyalanır. Bu, koleksiyonu kullanmak için gereken kodu azaltır; Ancak, koleksiyonun performansı olumsuz etkilenebilir. Örneğin, için ' <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601.Count%2A> den küçükse, <xref:System.Collections.Generic.List%601.Capacity%2A> bir öğe eklemek bir O (1) işlemidir. Kapasitenin yeni öğeye uyum sağlayacak şekilde artırılması gerekiyorsa, bir öğe eklendiğinde bir O ( `n` ) işlemi olur `n` <xref:System.Collections.Generic.List%601.Count%2A> . Birden çok realkonum nedeniyle oluşan zayıf performansı önlemenin en iyi yolu, ilk kapasiteyi koleksiyonun tahmini boyutu olacak şekilde ayarlamamaktır.

    <xref:System.Collections.BitArray>Özel bir durumdur; kapasitesi, sayısı ile aynı olan uzunluktadır.

- **Tutarlı bir alt sınır**

    Bir koleksiyonun alt sınırı, ilk öğesinin dizinidir. Ad alanlarındaki tüm dizini oluşturulmuş koleksiyonların <xref:System.Collections> alt sınırı sıfır, yani 0 dizinlenir. <xref:System.Array>Varsayılan olarak sıfır alt öğesine sahiptir, ancak kullanılarak **dizi** sınıfının bir örneği oluşturulurken farklı bir alt sınır tanımlanabilir <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> .

- **Birden çok iş parçacığından erişim Için eşitleme** ( <xref:System.Collections> Yalnızca sınıflar).

    Ad alanındaki genel olmayan koleksiyon türleri <xref:System.Collections> eşitlemeyle bazı iş parçacığı güvenliği sağlar; genellikle <xref:System.Collections.ICollection.SyncRoot%2A> ve üyeleri aracılığıyla gösterilir <xref:System.Collections.ICollection.IsSynchronized%2A> . Bu koleksiyonlar varsayılan olarak iş parçacığı açısından güvenli değildir. Bir koleksiyona ölçeklenebilir ve verimli bir çok iş parçacıklı erişim gerekiyorsa, ad alanındaki sınıflardan birini kullanın <xref:System.Collections.Concurrent> veya sabit bir koleksiyon kullanmayı deneyin. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](thread-safe/index.md).

<a name="BKMK_Choosingacollection"></a>
## <a name="choose-a-collection"></a>Bir koleksiyon seçin

Genel olarak, genel Koleksiyonlar kullanmanız gerekir. Aşağıdaki tabloda bazı yaygın koleksiyon senaryoları ve bu senaryolar için kullanabileceğiniz koleksiyon sınıfları açıklanmaktadır. Genel koleksiyonlarınız için yeni olduğunuzda, bu tablo göreviniz için en iyi sonucu veren genel koleksiyonu seçmenize yardımcı olur.

|İstiyorum...|Genel koleksiyon seçenekleri|Genel olmayan koleksiyon seçenekleri|İş parçacığı güvenli veya sabit koleksiyon seçenekleri|
|-|-|-|-|
|Öğeleri anahtara göre hızlı arama için anahtar/değer çiftleri olarak depola|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Anahtarın karma koduna göre düzenlenmiş anahtar/değer çiftleri koleksiyonu.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|
|Öğelere dizine göre erişin|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|
|İlk kez çıkan öğeleri kullan (FıFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|
|Ilk kez geçen verileri kullanma (LıFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|
|Öğelere sırayla erişin|<xref:System.Collections.Generic.LinkedList%601>|Öneri yok|Öneri yok|
|Öğeler kaldırıldığında veya koleksiyona eklendiğinde bildirim alın. ( <xref:System.ComponentModel.INotifyPropertyChanged> ve uygular <xref:System.Collections.Specialized.INotifyCollectionChanged> )|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Öneri yok|Öneri yok|
|Sıralanmış bir koleksiyon|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|
|Matematik işlevleri için bir küme|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Öneri yok|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|

### <a name="algorithmic-complexity-of-collections"></a>Koleksiyonların algoritmik karmaşıklığı

Bir [koleksiyon sınıfı](selecting-a-collection-class.md)seçerken, performans üzerindeki olası avantajları göz önünde bulundurmayı tercih edilir. Farklı kesilebilir koleksiyon türlerinin algoritmik karmaşıklığını karşılık gelen sabit karşılıklarıyla nasıl karşılaştırılacağını başvurmak için aşağıdaki tabloyu kullanın. Genellikle değişmez koleksiyon türleri daha az performansız olmakla kalmaz, genellikle geçerli bir karşılaştırmalı kullanım avantajıdır.

| Değiştirilebilir                   | Amorti edilmiş  | En kötü durum                | Değişmez                          | Karmaşıklık |
|---------------------------|------------|---------------------------|------------------------------------|------------|
| `Stack<T>.Push`           | O (1)       | O ( `n` )                    | `ImmutableStack<T>.Push`           | O (1)       |
| `Queue<T>.Enqueue`        | O (1)       | O ( `n` )                    | `ImmutableQueue<T>.Enqueue`        | O (1)       |
| `List<T>.Add`             | O (1)       | O ( `n` )                    | `ImmutableList<T>.Add`             | O (günlük `n` ) |
| `List<T>.Item[Int32]`     | O (1)       | O (1)                      | `ImmutableList<T>.Item[Int32]`     | O (günlük `n` ) |
| `List<T>.Enumerator`      | O ( `n` )     | O ( `n` )                    | `ImmutableList<T>.Enumerator`      | O ( `n` )     |
| `HashSet<T>.Add`, arama  | O (1)       | O ( `n` )                    | `ImmutableHashSet<T>.Add`          | O (günlük `n` ) |
| `SortedSet<T>.Add`        | O (günlük `n` ) | O ( `n` )                    | `ImmutableSortedSet<T>.Add`        | O (günlük `n` ) |
| `Dictionary<T>.Add`       | O (1)       | O ( `n` )                    | `ImmutableDictionary<T>.Add`       | O (günlük `n` ) |
| `Dictionary<T>`Ma    | O (1)       | O (1) – veya kesinlikle O ( `n` ) | `ImmutableDictionary<T>`Ma    | O (günlük `n` ) |
| `SortedDictionary<T>.Add` | O (günlük `n` ) | O ( `n` günlük `n` )            | `ImmutableSortedDictionary<T>.Add` | O (günlük `n` ) |

Bir `List<T>` döngü veya döngü kullanılarak etkili bir şekilde numaralandırılabilir `for` `foreach` . `ImmutableList<T>`Ancak, bir döngü içinde, `for` dizin oluşturucunun O (günlük) zamanı nedeniyle kötü bir iş yapar `n` . Bir `ImmutableList<T>` döngüyü kullanarak numaralandırma `foreach` etkilidir çünkü `ImmutableList<T>` , kullanımları gibi basit bir dizi yerine verilerini depolamak için bir ikili ağaç kullanır `List<T>` . Dizi, istenen dizine sahip düğüm bulunana kadar bir ikili ağacın aşağı doğru bir şekilde dizine alınması gerekir.

Ayrıca, `SortedSet<T>` ile aynı karmaşıklığa sahiptir `ImmutableSortedSet<T>` . Çünkü her ikisi de ikili ağaçlar kullanır. Kuşkusuz önemli fark, `ImmutableSortedSet<T>` değişmez bir ikili ağaç kullanır. `ImmutableSortedSet<T>`Ayrıca <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder?displayProperty=nameWithType> , mutasyona izin veren bir sınıf sağladığından, hem dengesslik hem de performans sağlayabilirsiniz.

<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Koleksiyon Sınıfı Seçme](selecting-a-collection-class.md)|Farklı koleksiyonları açıklar ve senaryonuz için bir tane seçmenize yardımcı olur.|
|[Yaygın olarak kullanılan koleksiyon türleri](commonly-used-collection-types.md)|, Ve gibi yaygın olarak kullanılan genel ve genel olmayan koleksiyon türlerini açıklar <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> .|
|[Genel Koleksiyonlar ne zaman kullanılır?](when-to-use-generic-collections.md)|Genel koleksiyon türlerinin kullanımını açıklar.|
|[Koleksiyonlar Içinde karşılaştırmalar ve sıralamalar](comparisons-and-sorts-within-collections.md)|Koleksiyonlarda eşitlik karşılaştırmaları ve sıralama karşılaştırmalarının kullanımını açıklar.|
|[Sıralanmış koleksiyon türleri](sorted-collection-types.md)|Sıralanmış koleksiyon performansını ve özelliklerini açıklar|
|[Hashtable ve Sözlük Koleksiyon Türleri](hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|
|[İş parçacığı güvenli Koleksiyonlar](thread-safe/index.md)|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Ve gibi <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> birçok iş parçacığından güvenli ve verimli eşzamanlı erişimi destekleyen koleksiyon türlerini açıklar.|
|System. Collections. sabit|Değişmez koleksiyonları tanıtır ve koleksiyon türlerine bağlantılar sağlar.|

<a name="BKMK_Reference"></a>
## <a name="reference"></a>Başvuru
<xref:System.Array?displayProperty=nameWithType>
<xref:System.Collections?displayProperty=nameWithType>
<xref:System.Collections.Concurrent?displayProperty=nameWithType>
<xref:System.Collections.Generic?displayProperty=nameWithType>
<xref:System.Collections.Specialized?displayProperty=nameWithType>
<xref:System.Linq?displayProperty=nameWithType>
<xref:System.Collections.Immutable>
