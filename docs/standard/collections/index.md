---
title: Koleksiyonlar ve Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
  - grouping data in collections
  - 'objects [.NET Framework], grouping in collections'
  - 'Array class, grouping data in collections'
  - 'threading [.NET Framework], safety'
  - Collections classes
  - 'collections [.NET Framework]'
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
author: mairaw
ms.author: mairaw
---
# <a name="collections-and-data-structures"></a>Koleksiyonlar ve Veri Yapıları
Benzer veri genellikle daha verimli bir şekilde depolanır ve bir koleksiyonu olarak yönetilebilir işlenebilir. Kullanabileceğiniz <xref:System.Array?displayProperty=nameWithType> sınıf veya sınıflardan <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, eklemek, gt;System.Collections.Immutable ad alanlarını kaldırın ve ayrı ayrı öğeleri veya koleksiyondaki öğelerin bir aralığını değiştirin.  
  
 Koleksiyonların iki ana türü vardır; Genel koleksiyonlar ve genel olmayan koleksiyon. Genel koleksiyonlar .NET Framework 2.0 sürümünde eklenen ve tür kullanımı uyumlu koleksiyonlar sağlamak derleme zamanında. Bu nedenle, genel koleksiyonlar normalde daha iyi performans sunar. Genel koleksiyonlar oluşturulur ve ve ondan dönüştürme gerektirmeyen bir tür parametresini kabul <xref:System.Object> eklediğinizde veya öğeleri koleksiyondan Kaldır yazın.  Ayrıca, en genel koleksiyonlar desteklenen [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] uygulamalar. Genel olmayan koleksiyonları depolayabileceğiniz öğeleri olarak <xref:System.Object>atama gerektirir ve çoğu için desteklenmez [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] uygulama geliştirme. Ancak, eski kod içinde genel olmayan koleksiyon görebilirsiniz.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], koleksiyonlar <xref:System.Collections.Concurrent> ad alanı, koleksiyon öğelerine birden fazla iş parçacığından erişmek için verimli bir iş parçacığı açısından güvenli işlemler sağlar. Gt;System.Collections.Immutable ad alanındaki değişmez koleksiyon sınıfları ([NuGet paketini](https://www.nuget.org/packages/System.Collections.Immutable)) özgün koleksiyon ve özgün koleksiyon bir kopyası üzerinde gerçekleştirilen işlemler doğası gereği iş parçacığı açısından güvenli değildir değiştirilemez.  
  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Genel koleksiyon özellikleri  
 Tüm koleksiyonlar, ekleme, kaldırma veya koleksiyondaki öğeleri bulma yöntemleri sağlar. Ayrıca, tüm koleksiyonlar, doğrudan veya dolaylı olarak uygulamak <xref:System.Collections.ICollection> arabirimi veya <xref:System.Collections.Generic.ICollection%601> arabirimi paylaşmak bu özellikler:  
  
-   **Koleksiyon listeleme olanağı**  
  
     .NET framework koleksiyonları ya da uygulama <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> koleksiyonu aracılığıyla yinelenir etkinleştirmek için. Bir numaralandırıcı, koleksiyondaki her öğe için taşınabilir bir işaretçi olarak düşünülebilir. [Foreach içinde](../../csharp/language-reference/keywords/foreach-in.md) deyimi ve [her biri için... Sonraki deyimi](../../visual-basic/language-reference/statements/for-each-next-statement.md) tarafından kullanıma sunulan Numaralandırıcı kullanın <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi ve numaralandırıcıyı işlemek karmaşıklığı gizle. Ayrıca, herhangi bir koleksiyon uygulayan <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> değerlendirilir bir *sorgulanabilir tür* ve LINQ ile sorgulanabilir. LINQ sorguları, verilere erişmek için genel bir desen sağlar. Genellikle daha kısa süren ve okunabilir standart `foreach` döngüye girer ve filtreleme, sıralama ve Gruplama yetenekler sağlar. LINQ sorguları da performansı artırır. Daha fazla bilgi için [LINQ to Objects'in (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects'in (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [LINQ sorguları (giriş C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md), ve [temel sorgu işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
-   **Bir diziye koleksiyon içeriği kopyalama özelliği**  
  
     Tüm koleksiyonlar kullanarak bir dizi kopyalanabilir **CopyTo** yöntemi; ancak, yeni dizideki öğelerin sırasını içinde numaralandırıcıyı döndürür bunları sırasına dayanan. Sonuç dizisi her zaman sıfır alt sınırı ile boyutludur.  
  
 Ayrıca, çok sayıda koleksiyon sınıfları aşağıdaki özellikleri içerir:  
  
-   **Kapasite ve sayısı özellikleri**  
  
     Bir koleksiyonun kapasitesi içerebileceği öğe sayısıdır. Bir koleksiyon sayısı gerçekte içerdiği öğeleri sayısıdır. Kapasite sayısı veya her ikisi de bazı koleksiyonları gizleyin.  
  
     Geçerli kapasite üst sınırına ulaşıldığında çoğu koleksiyonları kapasitede otomatik olarak genişletin. Bellek yeniden ve öğeler için yeni bir tane eski koleksiyondan kopyalanır. Bu koleksiyon kullanmak için gereken kod miktarını azaltır; Ancak, koleksiyonun performans olumsuz etkilenebilir. Örneğin, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.List%601.Count%2A> olduğu küçüktür <xref:System.Collections.Generic.List%601.Capacity%2A>, bir öğe eklemek, bir o(1) olur. Yeni öğeye uyum sağlamak için artırılmış kapasite gerekiyorsa, burada n, bir o(n), bir öğe eklemeye olur <xref:System.Collections.Generic.List%601.Count%2A>. Birden çok yapıcıların tarafından nedeniyle düşük performans önlemek için en iyi yolu, koleksiyon tahmini boyutu için ilk kapasite ayarlamaktır.  
  
     A <xref:System.Collections.BitArray> bir özel durum kapasitesi sayımına aynıdır, uzunluğu ile aynıdır.  
  
-   **Tutarlı bir alt sınırı**  
  
     Bir koleksiyon alt sınırı, ilk öğenin dizinidir. Tümünü dizinlenmiş koleksiyonlarında <xref:System.Collections> ad sahip alt sınırı sıfır, 0-dizinli anlamına gelir. <xref:System.Array> Varsayılan olarak sıfır alt sınırı vardır, ancak bir örneğini oluştururken farklı alt sınırı tanımlanabilir **dizi** kullanarak <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Birden çok iş parçacığından erişimi için eşitleme** (<xref:System.Collections> yalnızca sınıfları).  
  
     Genel olmayan koleksiyon türlerini de <xref:System.Collections> ad ile eşitleme bazı iş parçacığı güvenliği sağlar; genellikle aracılığıyla kullanıma <xref:System.Collections.ICollection.SyncRoot%2A> ve <xref:System.Collections.ICollection.IsSynchronized%2A> üyeleri. Bu koleksiyonlara varsayılan iş parçacığı açısından güvenli değildir. Bir koleksiyona ölçeklenebilir ve etkili çok iş parçacıklı erişimi gerekiyorsa, sınıflarda birini kullanın <xref:System.Collections.Concurrent> ad alanı veya bir sabit koleksiyon kullanmayı düşünün. Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Bir koleksiyon seçme  
 Genel olarak, genel koleksiyonlar kullanmanız gerekir. Aşağıdaki tabloda, bazı yaygın toplama senaryoları ve bu senaryolar için kullanabileceğiniz koleksiyon sınıflarını açıklar. Genel koleksiyonlar için yeni başladıysanız, bu tabloda göreviniz için en uygun genel koleksiyona seçmenize yardımcı olur.  
 
|İstiyorum...|Genel koleksiyon seçenekleri|Genel olmayan koleksiyonu seçenekleri|İş parçacığı açısından güvenli veya sabit koleksiyon seçenekleri|  
|-|-|-|-|  
|Anahtara göre hızlı arama için anahtar/değer çiftleri olarak öğeleri Store|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Anahtarın karma koduna göre düzenlenen anahtar/değer çifti koleksiyonunu.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dizine göre öğelere erişme|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Kullanan öğeleri ilk-giren ilk çıkar (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Son giren ilk-çıkar (LIFO) verileri kullanın|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Erişim ardışık öğeleri|<xref:System.Collections.Generic.LinkedList%601>|Öneri yok|Öneri yok|  
|Öğeler kaldırıldı veya koleksiyona eklenmesini bozulma olduğunda bildirimler alabilir. (uygulayan <xref:System.ComponentModel.INotifyPropertyChanged> ve <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Öneri yok|Öneri yok|  
|Sıralanmış koleksiyon|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|A için matematiksel İşlevler|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Öneri yok|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyon Sınıfı Seçme](../../../docs/standard/collections/selecting-a-collection-class.md)|Farklı koleksiyonlarda açıklar ve bir senaryonuz için seçmenize yardımcı olur.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|Gibi yaygın olarak kullanılan jenerik ve jenerik olmayan koleksiyon türlerini açıklar <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türlerinin kullanımını açıklar.|  
|[Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Eşitlik karşılaştırma ve sıralama karşılaştırmaları koleksiyonlardaki kullanmayı açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Sıralanmış koleksiyon performans ve özelliklerini açıklar.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türleri özelliklerini açıklar.|  
|[İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)|Gibi koleksiyon türlerini açıklar <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> birden çok iş parçacığından güvenli ve verimli eş zamanlı erişimi destekler.|  
|Gt;System.Collections.Immutable|Değişmez koleksiyonları tanıtır ve koleksiyon türlerine bağlantılar sağlar.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
