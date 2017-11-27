---
title: "Koleksiyon Sınıfı Seçme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64b50839a5500b671a4bd5dd92eec2f0db9787a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme
Koleksiyon sınıfı dikkatli seçtiğinizden emin olun. Yanlış türde kullanarak koleksiyon kullanımınız kısıtlayabilirsiniz. Genel olarak, türlerinde kullanmaktan kaçının <xref:System.Collections> ad alanı .NET Framework sürüm 1.1 özellikle hedeflediğiniz sürece. Koleksiyonları genel ve eşzamanlı sürümleri kendi büyük tür güvenliği ve diğer geliştirmeler nedeniyle tercih edilen olacak.  
  
 Aşağıdaki soruları göz önünde bulundurun:  
  
-   Değerini alındıktan sonra burada öğesi genellikle atılır sıralı bir liste gerekiyor mu?  
  
    -   Yanıt Evet ise, kullanmayı <xref:System.Collections.Queue> sınıfı veya <xref:System.Collections.Generic.Queue%601> ilk gerekiyorsa genel bir sınıf, çıkar (FIFO) davranışı. Kullanmayı <xref:System.Collections.Stack> sınıfı veya <xref:System.Collections.Generic.Stack%601> son giren ilk çıkar (LIFO) davranışı gerekiyorsa genel bir sınıf. Birden çok iş parçacığı güvenli erişimden için eş zamanlı sürümlerini kullanan <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Aksi durumda, başka koleksiyonlar kullanmayı düşünün.  
  
-   FIFO, LIFO gibi belirli bir sipariş öğeleri erişmek zorunda veya rastgele?  
  
    -   <xref:System.Collections.Queue> Sınıfı ve <xref:System.Collections.Generic.Queue%601> veya <xref:System.Collections.Concurrent.ConcurrentQueue%601> genel sınıfı FIFO erişim sunar. Daha fazla bilgi için bkz: [bir iş parçacığı koleksiyonunun ne zaman kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Sınıfı ve <xref:System.Collections.Generic.Stack%601> veya <xref:System.Collections.Concurrent.ConcurrentStack%601> genel sınıfı LIFO erişim sunar. Daha fazla bilgi için bkz: [bir iş parçacığı koleksiyonunun ne zaman kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Genel sınıfı kuyruğunu için head veya head için kuyruk sıralı erişim sağlar.  
  
-   Her öğe dizini tarafından erişim sağlamaları gerekiyor mu?  
  
    -   <xref:System.Collections.ArrayList> Ve <xref:System.Collections.Specialized.StringCollection> sınıfları ve <xref:System.Collections.Generic.List%601> genel sınıfı öğenin sıfır tabanlı dizini tarafından kendi öğelere erişim sunar.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, Ve <xref:System.Collections.Specialized.StringDictionary> sınıfları ve <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları, öğenin anahtarı tarafından kendi öğelere erişim sağlar.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> Ve <xref:System.Collections.Specialized.NameValueCollection> sınıfları ve <xref:System.Collections.ObjectModel.KeyedCollection%602> ve <xref:System.Collections.Generic.SortedList%602> genel sınıflarını sunmak kendi öğelere erişim ya da sıfır tabanlı dizini veya öğenin anahtarı.  
  
-   Her öğe bir değer, bir anahtar ve bir değer, bir bileşimini veya tek bir tuş bileşimini ve birden çok değer içerir?  
  
    -   Tek değer: göre koleksiyonlar birini kullanın <xref:System.Collections.IList> arabirimi veya <xref:System.Collections.Generic.IList%601> genel arabirim.  
  
    -   Bir anahtar ve bir değer: göre koleksiyonlar birini kullanın <xref:System.Collections.IDictionary> arabirimi veya <xref:System.Collections.Generic.IDictionary%602> genel arabirim.  
  
    -   Katıştırılmış anahtara sahip bir değer: kullanım <xref:System.Collections.ObjectModel.KeyedCollection%602> genel bir sınıf.  
  
    -   Bir anahtar ve birden çok değer: kullanım <xref:System.Collections.Specialized.NameValueCollection> sınıfı.  
  
-   Girilen nasıl ayarından farklı bir şekilde öğeleri sıralama gerekiyor mu?  
  
    -   <xref:System.Collections.Hashtable> Sınıfı tarafından karma kodlarını öğeleri sıralar.  
  
    -   <xref:System.Collections.SortedList> Sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602> ve <xref:System.Collections.Generic.SortedList%602> Genel sınıflar anahtarı ile öğeleri sıralama uygulamaları üzerinde temel <xref:System.Collections.IComparer> arabirimi ve <xref:System.Collections.Generic.IComparer%601> genel arabirim.  
  
    -   <xref:System.Collections.ArrayList>sağlayan bir <xref:System.Collections.ArrayList.Sort%2A> yönteminin alan bir <xref:System.Collections.IComparer> bir parametre olarak uygulama. Genel kendisine karşılık gelen <xref:System.Collections.Generic.List%601> genel bir sınıf sağlayan bir <xref:System.Collections.Generic.List%601.Sort%2A> uygulaması gereken yöntemi <xref:System.Collections.Generic.IComparer%601> bir parametre olarak genel arabirim.  
  
-   Hızlı arama ve bilgi alınması gerekiyor mu?  
  
    -   <xref:System.Collections.Specialized.ListDictionary>hızlıdır <xref:System.Collections.Hashtable> küçük koleksiyonları (10 öğe veya daha az). <xref:System.Collections.Generic.Dictionary%602> Genel SAX daha hızlı arama <xref:System.Collections.Generic.SortedDictionary%602> genel bir sınıf. Çok iş parçacıklı uygulamasıdır <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>sırasız veriler için hızlı çok iş parçacıklı ekleme sağlar. İki çok iş parçacıklı türleri hakkında daha fazla bilgi için bkz: [bir iş parçacığı koleksiyonunun ne zaman kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Yalnızca dizelere kabul koleksiyonları gerekiyor mu?  
  
    -   <xref:System.Collections.Specialized.StringCollection>(temel <xref:System.Collections.IList>) ve <xref:System.Collections.Specialized.StringDictionary> (temel <xref:System.Collections.IDictionary>) bulunan <xref:System.Collections.Specialized> ad alanı.  
  
    -   Ayrıca, herhangi bir genel koleksiyon sınıfı kullanabilirsiniz <xref:System.Collections.Generic> ad alanı türü olarak belirterek dize koleksiyonlarını belirlenmiş <xref:System.String> kendi genel tür bağımsız değişkenleri için sınıf.  
  
## <a name="linq-to-objects-and-plinq"></a>Nesneleri ve PLINQ LINQ  
 Nesnelere LINQ etkinleştirir LINQ sorgularını nesne türü uygulayan sürece bellek içi nesnelere erişmek için kullanılacak geliştiriciler <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. LINQ sorgularını verilerine erişmek için genel bir desen sağlamak için genellikle daha kısa ve standart okunabilir `foreach` döngüye girer ve filtreleme, sıralama ve yetenekleri gruplandırma sağlar. Daha fazla bilgi için bkz: [nesnelere LINQ](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ çok çekirdekli bilgisayardaki daha verimli şekilde kullanılmasına aracılığıyla Çoğu senaryoda daha hızlı sorgu yürütme sunabileceğiniz nesnelere LINQ paralel bir uygulamasını sağlar. Daha fazla bilgi için bkz: [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections>  
 <xref:System.Collections.Specialized>  
 <xref:System.Collections.Generic>  
 [İş parçacığı koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)
