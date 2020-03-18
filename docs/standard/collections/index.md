---
title: Koleksiyonlar ve Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
ms.openlocfilehash: 3ca340e19d7340d7bea133fa62c6d8bbc3c0512a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160397"
---
# <a name="collections-and-data-structures"></a>Koleksiyonlar ve Veri Yapıları
Benzer veriler genellikle depolandığında ve koleksiyon olarak işlendiğinde daha verimli bir şekilde işlenebilir. <xref:System.Array?displayProperty=nameWithType> Sınıf veya sınıflar , <xref:System.Collections>, <xref:System.Collections.Generic> <xref:System.Collections.Concurrent>System.Collections.Değişmez ad alanları eklemek için kullanabilirsiniz, kaldırmak ve bir koleksiyonda öğeleri veya öğeleri bir dizi değiştirin.  
  
 Koleksiyonların iki ana türü vardır; genel koleksiyonlar ve genel olmayan koleksiyonlar. Genel koleksiyonlar .NET Framework 2.0'a eklendi ve derleme zamanında tür güvenli koleksiyonlar sağladı. Bu nedenle, genel koleksiyonlar genellikle daha iyi performans sunar. Genel koleksiyonlar oluşturulduklarında bir tür parametresini kabul eder ve öğeleri <xref:System.Object> koleksiyondan eklediğinizde veya kaldırdığınızda bu türe ve bu türden döküm yapmanıza gerek duymaz.  Ayrıca, çoğu genel koleksiyon Windows Mağazası uygulamalarında desteklenir. Genel olmayan koleksiyonlar öğeleri <xref:System.Object>, döküm gerektirir ve çoğu Windows Mağazası uygulaması geliştirme için desteklenmez olarak depolar. Ancak, eski kodda genel olmayan koleksiyonlar görebilirsiniz.  
  
 .NET Framework 4'ten başlayarak, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, birden çok iş parçacığından toplama öğelerine erişmek için verimli iş parçacığı güvenli işlemleri sağlar. System.Collections.Immutable namespace[(NuGet](https://www.nuget.org/packages/System.Collections.Immutable)paketi)'deki değişmez koleksiyon sınıfları, işlemler özgün koleksiyonun bir kopyasıüzerinde gerçekleştirildiğinden ve özgün koleksiyon değiştirilemediğinden doğal olarak iş parçacığı açısından güvenlidir.  

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>Ortak koleksiyon özellikleri  
 Tüm koleksiyonlar, koleksiyondaki öğeleri ekleme, kaldırma veya bulma yöntemleri sağlar. Ayrıca, <xref:System.Collections.ICollection> arabirimi veya <xref:System.Collections.Generic.ICollection%601> arabirimi doğrudan veya dolaylı olarak uygulayan tüm koleksiyonlar bu özellikleri paylaşır:  
  
- **Koleksiyonu sayısala bilme**  
  
     .NET Framework koleksiyonları, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> koleksiyonun yinelanmasını sağlamak için ya uygular ya da etkinleştirir. Bir sayıcı, koleksiyondaki herhangi bir öğeiçin hareketli bir işaretçi olarak düşünülebilir. [Foreach,](../../csharp/language-reference/keywords/foreach-in.md) ifade ve [Her biri için ... Sonraki İfade,](../../visual-basic/language-reference/statements/for-each-next-statement.md) <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemtarafından maruz kalan sayısalatörü kullanın ve sayısallaştırıcıyı manipüle etme karmaşıklığını gizler. Buna ek olarak, uygulayan <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> herhangi bir koleksiyon *sorgulanabilir* bir tür olarak kabul edilir ve LINQ ile sorgulanabilir. LINQ sorguları verilere erişmek için ortak bir desen sağlar. Genellikle standart `foreach` döngülere göre daha kısa ve okunabilirdirler ve filtreleme, sıralama ve gruplandırma özellikleri sağlarlar. LINQ sorguları da performansı artırabilir. Daha fazla bilgi için [linq to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [LINQ Sorgularına Giriş (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)ve [Temel Sorgu İşlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)adresine bakın.  
  
- **Koleksiyon içeriğini bir diziye kopyalama yeteneği**  
  
     Tüm koleksiyonlar **CopyTo** yöntemini kullanarak bir diziye kopyalanabilir; ancak, yeni dizideki öğelerin sırası, sayılayıcının bunları döndürdeği sırasına dayanır. Ortaya çıkan dizi her zaman sıfır ın alt sınırı ile tek boyutludur.  
  
 Buna ek olarak, birçok koleksiyon sınıfı aşağıdaki özellikleri içerir:  
  
- **Kapasite ve Sayma özellikleri**  
  
     Bir koleksiyonun kapasitesi, içerebileceği öğe sayısıdır. Bir koleksiyonun sayısı, gerçekte içerdiği öğe sayısıdır. Bazı koleksiyonlar kapasiteyi veya sayıyı veya her ikisini birden gizler.  
  
     Çoğu koleksiyon, geçerli kapasiteye ulaşıldığında kapasiteyi otomatik olarak genişletir. Bellek yeniden ayrılır ve öğeler eski koleksiyondan yenisine kopyalanır. Bu, koleksiyonu kullanmak için gereken kodu azaltır; ancak, koleksiyonun performansı olumsuz etkilenebilir. Örneğin, , <xref:System.Collections.Generic.List%601>Öğe <xref:System.Collections.Generic.List%601.Count%2A> eklemek <xref:System.Collections.Generic.List%601.Capacity%2A>O(1) işleminden daha azsa. Yeni öğeyi barındıracak kapasitenin artırılması gerekiyorsa, bir öğe eklemek n'nin bulunduğu <xref:System.Collections.Generic.List%601.Count%2A>bir O(n) işlemi olur. Birden çok gerçek değiştirmenin neden olduğu düşük performansı önlemenin en iyi yolu, ilk kapasiteyi koleksiyonun tahmini boyutu olarak ayarlamaktır.  
  
     A <xref:System.Collections.BitArray> özel bir durumdur; kapasitesi uzunluğu ile aynıdır, sayısı ile aynıdır.  
  
- **Tutarlı bir alt sınır**  
  
     Bir koleksiyonun alt sınırı, ilk öğenin dizinidir. Ad alanlarındaki <xref:System.Collections> tüm dizine eklenmiş koleksiyonların daha düşük bir sınırı sıfırdır, yani 0 dizine sahiptirler. <xref:System.Array>varsayılan olarak sıfır ın daha düşük bir sınırı vardır, ancak **dizi** sınıfının <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>bir örneğini oluştururken farklı bir alt sınır tanımlanabilir.  
  
- Birden çok iş parçacığı (yalnızca<xref:System.Collections> sınıflar) **erişim için eşitleme.**  
  
     <xref:System.Collections> Ad alanındaki genel olmayan toplama türleri eşitleme ile bazı iş parçacığı güvenliği sağlar; genellikle <xref:System.Collections.ICollection.SyncRoot%2A> ve <xref:System.Collections.ICollection.IsSynchronized%2A> üyeleri aracılığıyla maruz. Bu koleksiyonlar varsayılan olarak iş parçacığı güvenli değildir. Bir koleksiyona ölçeklenebilir ve verimli çok iş parçacığı erişimi ne gerekiyorsa, <xref:System.Collections.Concurrent> ad alanındaki sınıflardan birini kullanın veya değişmez bir koleksiyon kullanmayı düşünün. Daha fazla bilgi için [İş Parçacığı Güvenli Koleksiyonları'na](../../../docs/standard/collections/thread-safe/index.md)bakın.  
  
<a name="BKMK_Choosingacollection"></a>
## <a name="choosing-a-collection"></a>Koleksiyon seçme  
 Genel olarak, genel koleksiyonları kullanmanız gerekir. Aşağıdaki tabloda bazı ortak toplama senaryoları ve bu senaryolar için kullanabileceğiniz koleksiyon sınıfları açıklanmaktadır. Genel koleksiyonlarda yeniyseniz, bu tablo göreviniz için en iyi şekilde çalışan genel koleksiyonu seçmenize yardımcı olur.  

|İstiyorum...|Genel toplama seçenekleri|Genel olmayan toplama seçenekleri|İş parçacığı güvenli veya değişmez toplama seçenekleri|  
|-|-|-|-|  
|Anahtara göre hızlı arama için öğeleri anahtar/değer çiftleri olarak depolama|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Anahtarın karma koduna göre düzenlenen anahtar/değer çiftleri topluluğu.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Öğelere dizin le erişim|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Öğeleri ilk ilk çıkan öğeleri kullanma (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Verileri Son İlk Çıkış (LIFO) kullanma|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Öğelere sırayla erişin|<xref:System.Collections.Generic.LinkedList%601>|Öneri yok|Öneri yok|  
|Öğeler kaldırıldığında veya koleksiyona eklendiğinde bildirimleri alın. (uygular <xref:System.ComponentModel.INotifyPropertyChanged> ve <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Öneri yok|Öneri yok|  
|Sıralanmış bir koleksiyon|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Matematiksel fonksiyonlar için bir küme|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Öneri yok|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyon Sınıfı Seçme](../../../docs/standard/collections/selecting-a-collection-class.md)|Farklı koleksiyonları açıklar ve senaryonuz için bir tane seçmenize yardımcı olur.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|Yaygın olarak kullanılan genel ve genel <xref:System.Array?displayProperty=nameWithType>olmayan <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>toplama <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>türlerini açıklar, , , ve.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türlerinin kullanımını tartışır.|  
|[Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Eşitlik karşılaştırmalarının kullanımını ve koleksiyonlarda sıralama karşılaştırmalarını tartışır.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Sıralanmış koleksiyonların performansını ve özelliklerini açıklar|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|  
|[İş Parçacığı Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)|Birden çok iş <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> parçacığından güvenli ve verimli eşzamanlı erişimi destekleyen ve koleksiyon türlerini açıklar.|  
|System.Collections.Değişmez|Değişmez koleksiyonları tanıtır ve koleksiyon türlerine bağlantılar sağlar.|  
  
<a name="BKMK_Reference"></a>
## <a name="reference"></a>Başvuru  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
