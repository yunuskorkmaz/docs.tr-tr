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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb231df9ed33b89fa15cde998379b2964cf32ff9
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204767"
---
# <a name="collections-and-data-structures"></a>Koleksiyonlar ve Veri Yapıları
Benzer veriler genellikle koleksiyon olarak depolandığında ve değiştirildiğinde daha verimli bir şekilde işlenebilir. Tek tek öğeleri veya bir koleksiyondaki öğe aralığını eklemek, kaldırmak ve değiştirmek için <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System. Collections. sabit ad alanlarındaki <xref:System.Array?displayProperty=nameWithType> sınıfını veya sınıfları kullanabilirsiniz.  
  
 İki ana koleksiyon türü vardır; Genel Koleksiyonlar ve genel olmayan Koleksiyonlar. Genel Koleksiyonlar .NET Framework 2,0 ' ye eklenmiştir ve derleme zamanında tür kullanımı uyumlu koleksiyonlar sağlar. Bu nedenle, genel Koleksiyonlar genellikle daha iyi performans sunar. Genel Koleksiyonlar, oluşturuldukları sırada bir tür parametresi kabul eder ve koleksiyondan öğe eklediğinizde veya kaldırdığınızda <xref:System.Object> türüne ve ' a dönüştürmeniz gerekmez.  Ayrıca, çoğu genel koleksiyon Windows Mağazası uygulamalarında desteklenir. Genel olmayan koleksiyonlar öğeleri <xref:System.Object>olarak depolar, atama gerektir ve en çoğu Windows Mağazası uygulaması geliştirme için desteklenmez. Ancak, daha eski bir kodda genel olmayan koleksiyonlar görebilirsiniz.  
  
 .NET Framework 4 ' ten başlayarak, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar birden çok iş parçacığından koleksiyon öğelerine erişmek için verimli iş parçacığı güvenli işlemleri sağlar. System. Collections. sabit ad alanındaki ([NuGet paketindeki](https://www.nuget.org/packages/System.Collections.Immutable)) sabit koleksiyon sınıfları, işlemler orijinal koleksiyonun bir kopyasında gerçekleştirildiğinden ve özgün koleksiyon değiştirilemediğinden, kendiliğinden iş parçacığı güvenlidir.  

<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Ortak koleksiyon özellikleri  
 Tüm Koleksiyonlar koleksiyondaki öğeleri eklemek, kaldırmak veya bulmak için yöntemler sağlar. Ayrıca, <xref:System.Collections.ICollection> arabirimini veya <xref:System.Collections.Generic.ICollection%601> arabirimini doğrudan veya dolaylı olarak uygulayan tüm koleksiyonlar bu özellikleri paylaşır:  
  
- **Koleksiyonu listeleme özelliği**  
  
     .NET Framework koleksiyonlar, koleksiyonun üzerinden tekrarlandırılmış olmasını sağlamak için <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> uygular. Numaralandırıcı, koleksiyondaki herhangi bir öğe için taşınabilir bir işaretçi olarak düşünülebilir. [Foreach, in](../../csharp/language-reference/keywords/foreach-in.md) Ifadesi ve [for each... Next Ifadesinde](../../visual-basic/language-reference/statements/for-each-next-statement.md) <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi tarafından sunulan Numaralandırıcı kullanılır ve Numaralandırıcının işlenmesinin karmaşıklığı gizlenir. Ayrıca, <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> uygulayan herhangi bir koleksiyon, *sorgulanabilir bir tür* olarak DEĞERLENDIRILIR ve LINQ ile sorgulanabilir. LINQ sorguları verilere erişmek için ortak bir model sağlar. Genellikle standart `foreach` döngülerinden daha kısa ve okunabilir ve filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [LINQ Sorgularına Giriş (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)ve [temel sorgu işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
- **Koleksiyon içeriğini bir diziye kopyalama özelliği**  
  
     Tüm koleksiyonlar, **CopyTo** yöntemi kullanılarak bir diziye kopyalanabilir; Ancak, yeni dizideki öğelerin sırası, Numaralandırıcı tarafından döndürülen diziye göre belirlenir. Elde edilen dizi her zaman bir sıfır alt sınırı olan bir boyutludur.  
  
 Ayrıca, birçok koleksiyon sınıfı aşağıdaki özellikleri içerir:  
  
- **Kapasite ve sayı özellikleri**  
  
     Bir koleksiyonun kapasitesi içerebileceği öğelerin sayısıdır. Bir koleksiyonun sayısı, gerçekten içerdiği öğelerin sayısıdır. Bazı koleksiyonlar kapasiteyi veya sayıyı veya her ikisini de gizler.  
  
     En fazla koleksiyon, geçerli kapasiteye ulaşıldığında kapasiteyi otomatik olarak genişletir. Bellek yeniden ayrılır ve öğeler eski koleksiyondan yeni bir koleksiyona kopyalanır. Bu, koleksiyonu kullanmak için gereken kodu azaltır; Ancak, koleksiyonun performansı olumsuz etkilenebilir. Örneğin, <xref:System.Collections.Generic.List%601>için <xref:System.Collections.Generic.List%601.Count%2A> <xref:System.Collections.Generic.List%601.Capacity%2A>'den küçükse bir öğe eklemek O (1) işlemidir. Kapasitenin yeni öğeye uyum sağlayacak şekilde artırılması gerekiyorsa, bir öğe eklendiğinde bir O (n) işlemi olur; burada n <xref:System.Collections.Generic.List%601.Count%2A>. Birden çok realkonum nedeniyle oluşan zayıf performansı önlemenin en iyi yolu, ilk kapasiteyi koleksiyonun tahmini boyutu olacak şekilde ayarlamamaktır.  
  
     <xref:System.Collections.BitArray> özel bir durumdur; kapasitesi, sayısı ile aynı olan uzunluktadır.  
  
- **Tutarlı bir alt sınır**  
  
     Bir koleksiyonun alt sınırı, ilk öğesinin dizinidir. <xref:System.Collections> ad alanlarındaki tüm dizini oluşturulmuş koleksiyonların alt sınırı sıfır, yani 0 dizinlenir. <xref:System.Array> varsayılan olarak sıfır alt öğesine sahiptir, ancak <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>kullanılarak **dizi** sınıfının bir örneği oluşturulurken farklı bir alt sınır tanımlanabilir.  
  
- **Birden çok iş parçacığından erişim Için eşitleme** (yalnızca<xref:System.Collections> sınıfları).  
  
     <xref:System.Collections> ad alanındaki genel olmayan koleksiyon türleri eşitlemeyle bazı iş parçacığı güvenliği sağlar; genellikle <xref:System.Collections.ICollection.SyncRoot%2A> ve <xref:System.Collections.ICollection.IsSynchronized%2A> üyeleri aracılığıyla sunulur. Bu koleksiyonlar varsayılan olarak iş parçacığı açısından güvenli değildir. Bir koleksiyona ölçeklenebilir ve verimli çok iş parçacıklı erişim istiyorsanız, <xref:System.Collections.Concurrent> ad alanındaki sınıflardan birini kullanın veya sabit bir koleksiyon kullanmayı deneyin. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Koleksiyon seçme  
 Genel olarak, genel Koleksiyonlar kullanmanız gerekir. Aşağıdaki tabloda bazı yaygın koleksiyon senaryoları ve bu senaryolar için kullanabileceğiniz koleksiyon sınıfları açıklanmaktadır. Genel koleksiyonlarınız için yeni olduğunuzda, bu tablo göreviniz için en iyi sonucu veren genel koleksiyonu seçmenize yardımcı olur.  
 
|İstiyorum...|Genel koleksiyon seçenekleri|Genel olmayan koleksiyon seçenekleri|İş parçacığı güvenli veya sabit koleksiyon seçenekleri|  
|-|-|-|-|  
|Öğeleri anahtara göre hızlı arama için anahtar/değer çiftleri olarak depola|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Anahtarın karma koduna göre düzenlenmiş anahtar/değer çiftleri koleksiyonu.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Öğelere dizine göre erişin|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|İlk kez çıkan öğeleri kullan (FıFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Ilk kez geçen verileri kullanma (LıFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Öğelere sırayla erişin|<xref:System.Collections.Generic.LinkedList%601>|Öneri yok|Öneri yok|  
|Öğeler kaldırıldığında veya koleksiyona eklendiğinde bildirim alın. (<xref:System.ComponentModel.INotifyPropertyChanged> ve <xref:System.Collections.Specialized.INotifyCollectionChanged>uygular)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Öneri yok|Öneri yok|  
|Sıralanmış bir koleksiyon|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Matematik işlevleri için bir küme|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Öneri yok|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyon Sınıfı Seçme](../../../docs/standard/collections/selecting-a-collection-class.md)|Farklı koleksiyonları açıklar ve senaryonuz için bir tane seçmenize yardımcı olur.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|<xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>gibi yaygın olarak kullanılan genel ve genel olmayan koleksiyon türlerini açıklar.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türlerinin kullanımını açıklar.|  
|[Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Koleksiyonlarda eşitlik karşılaştırmaları ve sıralama karşılaştırmalarının kullanımını açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Sıralanmış koleksiyon performansını ve özelliklerini açıklar|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|  
|[İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)|Birden çok iş parçacığından güvenli ve verimli eşzamanlı erişimi destekleyen <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> gibi koleksiyon türlerini açıklar.|  
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
