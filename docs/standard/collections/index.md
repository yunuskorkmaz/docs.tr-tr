---
title: "Koleksiyonlar ve Veri Yapıları"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: "36"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7760f30e8053b55c2f846c08ccb6a3d026089afb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="collections-and-data-structures"></a>Koleksiyonlar ve Veri Yapıları
Benzer veri genellikle daha verimli bir şekilde depolanır ve bir koleksiyon olarak yönetilebilir işlenebilir. Kullanabileceğiniz <xref:System.Array?displayProperty=nameWithType> sınıf veya sınıflarda <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, eklemek için System.Collections.Immutable ad alanlarını kaldırın ve ayrı ayrı öğeler veya bir koleksiyondaki öğelerin aralığını değiştirin.  
  
 Koleksiyonların iki ana tür vardır; Genel koleksiyonlar ve genel olmayan koleksiyonu. Genel koleksiyonlar .NET Framework 2. 0 ' eklendi ve tür kullanımı uyumlu koleksiyonlar sağlamak derleme zamanında. Bu nedenle, genel koleksiyonlar genellikle daha iyi performans sunar. Genel koleksiyonlar oluşturulur ve ve ondan dönüştürme gerektirmeyen bir tür parametresi kabul <xref:System.Object> eklediğinizde veya öğeleri koleksiyondan yazın.  Ayrıca, en genel koleksiyonlar desteklenen [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] uygulamalar. Genel olmayan koleksiyonları depolayabileceğiniz öğeleri olarak <xref:System.Object>atama gerektirir ve çoğu desteklenmemektedir [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] uygulama geliştirme. Ancak, eski kod genel olmayan koleksiyonlarda görebilirsiniz.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], koleksiyonlardaki <xref:System.Collections.Concurrent> ad alanı koleksiyon öğeleri birden çok iş parçacığından erişmek için etkin iş parçacığı açısından güvenli işlemler sağlar. System.Collections.Immutable ad alanında değişmez koleksiyon sınıfları ([NuGet paketi](https://www.nuget.org/packages/System.Collections.Immutable)) özgün koleksiyonu ve özgün koleksiyonu bir kopyası üzerinde gerçekleştirilen işlemler kendiliğinden iş parçacığı güvenli olduğu değiştirilemez.  
  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Genel koleksiyon özellikleri  
 Tüm koleksiyonlar ekleme, kaldırma veya koleksiyonda öğeleri bulma yöntemleri sağlar. Ayrıca, tüm koleksiyonlar da doğrudan veya dolaylı olarak uygulayan <xref:System.Collections.ICollection> arabirimi veya <xref:System.Collections.Generic.ICollection%601> arabirimi paylaşmak bu özellikleri:  
  
-   **Toplamasını olanağı**  
  
     .NET framework koleksiyonları ya da uygulama <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> koleksiyonu aracılığıyla yinelendiğinde etkinleştirilemedi. Bir numaralandırıcı, koleksiyondaki herhangi bir öğeye taşınabilir bir işaretçi olarak düşünülebilir. [Foreach,](~/docs/csharp/language-reference/keywords/foreach-in.md) deyimi ve [For Each... Sonraki deyim](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) tarafından sunulan Numaralandırıcı kullanmak <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi ve Gizle Numaralandırıcı düzenleme karmaşıklığını. Ayrıca, herhangi bir koleksiyonu uygulayan <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> olarak kabul edilir bir *sorgulanabilir türü* ve LINQ ile sorgulanabilir. LINQ sorgularını verilerine erişmek için genel bir desen sağlar. Genellikle daha kısa ve standart okunabilir `foreach` döngüye girer ve filtreleme, sıralama ve yetenekleri gruplandırma sağlar. LINQ sorguları da performansı artırabilir. Daha fazla bilgi için bkz: [nesnelere LINQ](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9), [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) ve [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   **Özelliği için bir dizi koleksiyon içeriğini kopyalayın**  
  
     Tüm koleksiyonlar kullanarak bir dizinin kopyalanabilir **CopyTo** yöntemi; ancak, yeni bir dizi öğelerin sırasını içine numaralandırıcısı döndürür bunları sırasına dayanan. Sonuçta elde edilen her zaman sıfır bir alt sınır tek boyutlu dizidir.  
  
 Ayrıca, birçok koleksiyon sınıfları aşağıdaki özellikleri içerir:  
  
-   **Kapasite ve sayısı özellikleri**  
  
     Bir koleksiyon kapasitesini oluşabilir öğeleri sayısıdır. Bir koleksiyon sayısı gerçekte içerdiği öğeler sayısıdır. Kapasite veya sayı ya da her ikisini de bazı koleksiyonları gizleyin.  
  
     Geçerli kapasitenin ulaşıldığında çoğu koleksiyonlarını otomatik olarak kapasite genişletin. Bellek bırakılan ve öğeleri için yeni bir eski koleksiyondan kopyalanır. Bu koleksiyon kullanmak için gereken kod azaltır; Ancak, koleksiyon performansını olumsuz yönde etkilenebilir. Örneğin, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.List%601.Count%2A> olan değerinden <xref:System.Collections.Generic.List%601.Capacity%2A>, O(1) işlemi olan bir öğe ekleme. Kapasite yeni öğe uyum sağlayacak şekilde artırılması gerekiyorsa, n, bir o(n), öğe ekleme hale <xref:System.Collections.Generic.List%601.Count%2A>. Birden çok adetle sınırla tarafından neden performansın önlemek için en iyi yolu, koleksiyon tahmini boyutunu olması için ilk kapasite ayarlamaktır.  
  
     A <xref:System.Collections.BitArray> özel bir durum; kapasitesi sayımına aynı uzunluğu ile aynıdır.  
  
-   **Tutarlı bir alt sınırı**  
  
     İlk alt öğenin dizini koleksiyonunun alt sınırdır. Tüm dizine koleksiyonlarda <xref:System.Collections> ad sahip alt sınırı sıfır, 0 dizinli anlamına gelir. <xref:System.Array>Varsayılan olarak sıfır alt sınırı vardır, ancak farklı bir alt sınır örneği oluşturulurken tanımlanan **dizi** kullanarak sınıfı <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Birden çok iş parçacığından erişimi için eşitleme** (<xref:System.Collections> yalnızca sınıfları).  
  
     Olmayan genel koleksiyon türleri <xref:System.Collections> ad alanı eşitlemede bazı iş parçacığı güvenliği sağlar; genellikle aracılığıyla kullanıma sunulan <xref:System.Collections.ICollection.SyncRoot%2A> ve <xref:System.Collections.ICollection.IsSynchronized%2A> üyeleri. Bu koleksiyonları varsayılan olarak iş parçacığı açısından güvenli değildir. Bir koleksiyon için ölçeklenebilir ve verimli çok iş parçacıklı erişimi gerekiyorsa sınıflarda birini kullanın <xref:System.Collections.Concurrent> ad alanı veya sabit bir koleksiyonu kullanmayı düşünün. Daha fazla bilgi için bkz: [iş parçacığı koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Bir koleksiyon seçme  
 Genel olarak, genel koleksiyonlar kullanmanız gerekir. Aşağıdaki tabloda bazı yaygın toplama senaryolar ve bu senaryolar için kullanabileceğiniz koleksiyon sınıfları açıklar. Genel koleksiyonlar için yeni başladıysanız, bu tablo göreviniz için en iyi şekilde çalışır genel koleksiyon seçmenize yardımcı olur.  
|İstiyorum...|Genel koleksiyon seçenekleri|Genel olmayan koleksiyonu seçenekleri|İş parçacığı veya değişmez koleksiyonunu seçenekleri|  
|-|-|-|-|  
|Öğeleri hızlı arama için anahtar/değer çiftleri olarak anahtarının depolar.|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Düzenleme olan anahtar/değer çiftleri koleksiyonu anahtarı karma kodunu temel.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dizine göre öğelere erişim|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Kullanmak öğeleri ilk-giren ilk çıkar (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Kullanım verileri son-giren ilk çıkar (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Erişim sırayla öğeleri|<xref:System.Collections.Generic.LinkedList%601>|Öneri yok|Öneri yok|  
|Öğeleri kaldırılmış veya koleksiyonuna eklenen olduğunda bildirim alırsınız. (uygulayan <xref:System.ComponentModel.INotifyPropertyChanged> ve <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Öneri yok|Öneri yok|  
|Sıralanmış koleksiyon|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Matematik işlevleri için ayarlanmış A|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Öneri yok|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyon Sınıfı Seçme](../../../docs/standard/collections/selecting-a-collection-class.md)|Farklı koleksiyonlarda açıklar ve senaryonuz için bir tane seçmenize yardımcı olur.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|Yaygın olarak kullanılan genel ve nongeneric koleksiyon türleri gibi açıklar <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türleri kullanmayı açıklar.|  
|[Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Eşitlik karşılaştırmaları ve koleksiyonlarda sıralama karşılaştırmaları kullanmayı açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Sıralanmış koleksiyon performans ve özelliklerini açıklar|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türleri özelliklerini açıklar.|  
|[İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)|Koleksiyon türleri gibi açıklar <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> birden çok iş parçacığı güvenli ve verimli eşzamanlı erişimden destekler.|  
|System.Collections.Immutable|Sabit koleksiyonlar tanıtır ve koleksiyon türleri için bağlantılar sağlar.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
