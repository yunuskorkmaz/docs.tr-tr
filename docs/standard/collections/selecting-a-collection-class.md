---
title: Koleksiyon Sınıfı Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 049976c1e63d04c495a38b39531313adc1d12c5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620090"
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme
Koleksiyon sınıfınıza seçmeye emin olun. Yanlış türde kullanarak koleksiyon kullanımını kısıtlayabilirsiniz. Genel olarak, türlerini kullanmaktan <xref:System.Collections> ad alanı .NET Framework sürüm 1.1 özellikle hedeflediğiniz sürece. Genel ve eş zamanlı koleksiyonlar, büyük tür güvenliği ve diğer iyileştirmeler nedeniyle tercih edilen olarak sürümleridir.  
  
 Aşağıdaki soruları göz önünde bulundurun:  
  
-   Sıralı liste değeri alındıktan sonra nerede öğe genellikle atılır gerekiyor mu?  
  
    -   Yanıt Evet ise, kullanmayı <xref:System.Collections.Queue> sınıfı veya <xref:System.Collections.Generic.Queue%601> ilk gerekiyorsa genel bir sınıf, ilk çıkar (FIFO) davranışı. Kullanmayı <xref:System.Collections.Stack> sınıfı veya <xref:System.Collections.Generic.Stack%601> son giren ilk çıkar (LIFO) davranışı gerekiyorsa genel bir sınıf. Birden çok iş parçacığından güvenli erişim için eş zamanlı sürümlerle <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Aksi durumda, diğer koleksiyonları kullanmayı düşünün.  
  
-   FIFO, LIFO gibi belirli bir sırada öğelere erişmek zorunda veya rastgele?  
  
    -   <xref:System.Collections.Queue> Sınıfı ve <xref:System.Collections.Generic.Queue%601> veya <xref:System.Collections.Concurrent.ConcurrentQueue%601> genel sınıf FIFO erişim sunar. Daha fazla bilgi için [bir iş parçacığı güvenli koleksiyonu ne zaman](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Sınıfı ve <xref:System.Collections.Generic.Stack%601> veya <xref:System.Collections.Concurrent.ConcurrentStack%601> genel sınıf LIFO erişim sunar. Daha fazla bilgi için [bir iş parçacığı güvenli koleksiyonu ne zaman](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Genel sınıf kuyruğunu'ne gidin veya kuyruk karşılaştırması sıralı erişim sağlar.  
  
-   Dizine göre her bir öğesine erişmek gerekiyor mu?  
  
    -   <xref:System.Collections.ArrayList> Ve <xref:System.Collections.Specialized.StringCollection> sınıfları ve <xref:System.Collections.Generic.List%601> genel sınıf öğeleri öğenin sıfır tabanlı dizini tarafından erişim sunar.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, Ve <xref:System.Collections.Specialized.StringDictionary> sınıfları ve <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları, öğenin anahtarı tarafından kendi öğelere erişim sağlar.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> Ve <xref:System.Collections.Specialized.NameValueCollection> sınıfları ve <xref:System.Collections.ObjectModel.KeyedCollection%602> ve <xref:System.Collections.Generic.SortedList%602> genel sınıfları sağlar, bu öğelere erişimi ya da sıfır tabanlı dizini veya öğenin anahtarı.  
  
-   Her öğe bir değer, bir anahtar ve bir değer veya bir birleşimini bir anahtar ve birden çok değer içerir?  
  
    -   Tek değer: Temel koleksiyonları dilediğinizi <xref:System.Collections.IList> arabirimi veya <xref:System.Collections.Generic.IList%601> genel arabirim.  
  
    -   Bir anahtarı ve tek bir değer: Temel koleksiyonları dilediğinizi <xref:System.Collections.IDictionary> arabirimi veya <xref:System.Collections.Generic.IDictionary%602> genel arabirim.  
  
    -   Katıştırılmış bir anahtara sahip bir değer: Kullanım <xref:System.Collections.ObjectModel.KeyedCollection%602> genel bir sınıf.  
  
    -   Bir anahtar ve birden çok değer: Kullanım <xref:System.Collections.Specialized.NameValueCollection> sınıfı.  
  
-   Girilen nasıl öğesinden farklı öğeleri sıralama gerekiyor mu?  
  
    -   <xref:System.Collections.Hashtable> Sınıfı karma kodlarına göre öğeleri sıralar.  
  
    -   <xref:System.Collections.SortedList> Sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602> ve <xref:System.Collections.Generic.SortedList%602> Genel sınıflar anahtara göre öğeleri sıralama uygulamalarına göre <xref:System.Collections.IComparer> arabirimi ve <xref:System.Collections.Generic.IComparer%601> genel arabirim.  
  
    -   <xref:System.Collections.ArrayList> sağlar bir <xref:System.Collections.ArrayList.Sort%2A> gereken yöntemini bir <xref:System.Collections.IComparer> bir parametre olarak bir uygulama. Genel çözümlemesiyle <xref:System.Collections.Generic.List%601> genel bir sınıf sağlar bir <xref:System.Collections.Generic.List%601.Sort%2A> uygulaması gereken yöntemini <xref:System.Collections.Generic.IComparer%601> genel arabirim bir parametre olarak.  
  
-   Hızlı arama ve bilgi alınması gerekiyor mu?  
  
    -   <xref:System.Collections.Specialized.ListDictionary> hızlıdır <xref:System.Collections.Hashtable> küçük koleksiyonları (10 öğe veya daha az). <xref:System.Collections.Generic.Dictionary%602> Genel bir sınıf daha hızlı arama sağlayan <xref:System.Collections.Generic.SortedDictionary%602> genel bir sınıf. Çok iş parçacıklı uygulamasıdır <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> sırasız veriler için hızlı çok iş parçacıklı ekleme sağlar. İki çok iş parçacıklı türleri hakkında daha fazla bilgi için bkz. [bir iş parçacığı güvenli koleksiyonu ne zaman](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Yalnızca dizelere kabul koleksiyonları gerekiyor mu?  
  
    -   <xref:System.Collections.Specialized.StringCollection> (temel <xref:System.Collections.IList>) ve <xref:System.Collections.Specialized.StringDictionary> (temel <xref:System.Collections.IDictionary>) bulunan <xref:System.Collections.Specialized> ad alanı.  
  
    -   Ayrıca, genel koleksiyon sınıflarını dilediğinizi kullanabilirsiniz <xref:System.Collections.Generic> ad alanı türü kesin olarak belirterek dize koleksiyonlarını belirtilmiş <xref:System.String> , genel tür bağımsız değişkenleri için sınıf.  
  
## <a name="linq-to-objects-and-plinq"></a>Nesneleri ve PLINQ LINQ  
 LINQ to Objects'in bellek içi nesneler nesne türünün uyguladığı sürece erişmek için LINQ sorguları kullanmak geliştiricilerin sağlar <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. LINQ sorguları verilere erişmek için genel bir desen sağlar, genellikle daha kısa süren ve okunabilir standart `foreach` döngüye girer ve filtreleme, sıralama ve Gruplama yetenekler sağlar. Daha fazla bilgi için [LINQ to Objects'in](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ, çok çekirdekli bilgisayarlara daha verimli kullanımı aracılığıyla birçok senaryoda daha hızlı sorgu yürütme sunduğu nesnelere LINQ paralel bir uygulaması sağlar. Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)
