---
title: Koleksiyon Sınıfı Seçme
ms.date: 03/18/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
ms.openlocfilehash: fb03200c810290c970f7aa56a0e15d385aca7ca8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711356"
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme

Koleksiyon sınıfınızı dikkatle seçtiğinizden emin olun. Yanlış tür kullanımı, koleksiyonun kullanımını kısıtlayabilir.  

> [!IMPORTANT]
> <xref:System.Collections> ad alanındaki türleri kullanmaktan kaçının. Koleksiyonların genel ve eş zamanlı sürümleri, daha yüksek tür güvenliği ve diğer geliştirmeler nedeniyle önerilir.  

 Aşağıdaki soruları göz önünde bulundurun:  
  
- Öğenin genellikle değeri alındıktan sonra atıldığı sıralı bir liste gerekiyor mu?  
  
  - Yanıt Evet ise, ilk kez, ilk çıkar (FıFO) davranışına ihtiyacınız varsa <xref:System.Collections.Queue> sınıfını veya <xref:System.Collections.Generic.Queue%601> genel sınıfını kullanmayı düşünün. En son, ilk çıkar (LıFO) davranışına ihtiyacınız varsa <xref:System.Collections.Stack> sınıfını veya <xref:System.Collections.Generic.Stack%601> genel sınıfını kullanmayı düşünün. Birden çok iş parçacığından güvenli erişim için, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>eşzamanlı sürümlerini kullanın.  
  
  - Aksi takdirde, diğer koleksiyonları kullanmayı göz önünde bulundurun.  
  
- Öğelere FıFO, LıFO veya Random gibi belirli bir sırada erişmeniz gerekiyor mu?  
  
  - <xref:System.Collections.Queue> sınıfı ve <xref:System.Collections.Generic.Queue%601> veya <xref:System.Collections.Concurrent.ConcurrentQueue%601> genel sınıfı FıFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?  
  
  - <xref:System.Collections.Stack> sınıfı ve <xref:System.Collections.Generic.Stack%601> veya <xref:System.Collections.Concurrent.ConcurrentStack%601> genel sınıfı, LıFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?  
  
  - <xref:System.Collections.Generic.LinkedList%601> genel sınıfı, başa veya kuyruklu bir sıralı erişime izin verir.  
  
- Dizine göre her öğeye erişmeniz mi gerekiyor?  
  
  - <xref:System.Collections.ArrayList> ve <xref:System.Collections.Specialized.StringCollection> sınıfları ve <xref:System.Collections.Generic.List%601> genel sınıfı, öğesinin sıfır tabanlı diziniyle öğelerine erişim sağlar.  
  
  - <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>ve <xref:System.Collections.Specialized.StringDictionary> sınıfları ve <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları öğe anahtarına göre öğelerine erişim sağlar.  
  
  - <xref:System.Collections.Specialized.NameObjectCollectionBase> ve <xref:System.Collections.Specialized.NameValueCollection> sınıfları ve <xref:System.Collections.ObjectModel.KeyedCollection%602> ve <xref:System.Collections.Generic.SortedList%602> genel sınıflar öğelerine sıfır tabanlı dizin ya da öğenin anahtarı ile erişim sağlar.  
  
- Her öğe bir değer, bir anahtar ve bir değer birleşimi ya da bir anahtar ve birden çok değer birleşimi içerir mi?  
  
  - Bir değer: <xref:System.Collections.IList> arabirimini veya <xref:System.Collections.Generic.IList%601> genel arabirimini temel alan koleksiyonlardan birini kullanın.  
  
  - Bir anahtar ve bir değer: <xref:System.Collections.IDictionary> arabirimini veya <xref:System.Collections.Generic.IDictionary%602> genel arabirimini temel alan koleksiyonlardan birini kullanın.  
  
  - Gömülü anahtara sahip bir değer: <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıfını kullanın.  
  
  - Bir anahtar ve birden çok değer: <xref:System.Collections.Specialized.NameValueCollection> sınıfını kullanın.  
  
- Öğeleri girildiklerinde farklı şekilde sıralamak mı gerekiyor?  
  
  - <xref:System.Collections.Hashtable> sınıfı öğelerini karma kodlarına göre sıralar.  
  
  - <xref:System.Collections.SortedList> sınıfı ve <xref:System.Collections.Generic.SortedList%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları öğelerini anahtara göre sıralar. Sıralama düzeni, <xref:System.Collections.SortedList> sınıfı için <xref:System.Collections.IComparer> arabiriminin uygulamasına ve <xref:System.Collections.Generic.SortedList%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları için <xref:System.Collections.Generic.IComparer%601> genel arabiriminin uygulamasına göre yapılır. İki genel türün <xref:System.Collections.Generic.SortedDictionary%602>, <xref:System.Collections.Generic.SortedList%602> daha az bellek tüketirken <xref:System.Collections.Generic.SortedList%602>daha iyi performans sunar.  
  
  - <xref:System.Collections.ArrayList>, bir <xref:System.Collections.IComparer> uygulamasını parametre olarak alan bir <xref:System.Collections.ArrayList.Sort%2A> yöntemi sağlar. Genel karşılığına sahip olan <xref:System.Collections.Generic.List%601> genel karşılığı, parametre olarak <xref:System.Collections.Generic.IComparer%601> genel arabiriminin bir uygulamasını alan bir <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi sağlar.  
  
- Bilgilerin hızlı aramalarında ve alınmasına mi ihtiyacınız var?  
  
  - <xref:System.Collections.Specialized.ListDictionary> küçük koleksiyonlar için <xref:System.Collections.Hashtable> daha hızlıdır (10 öğe veya daha az). <xref:System.Collections.Generic.Dictionary%602> genel sınıfı, <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfından daha hızlı arama sağlar. Çoklu iş parçacıklı uygulama <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>, sıralanmamış veriler için hızlı çoklu iş parçacıklı ekleme sağlar. Çoklu iş parçacıklı türler hakkında daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?  
  
- Yalnızca dizeleri kabul eden koleksiyonlara mi ihtiyacınız var?  
  
  - <xref:System.Collections.Specialized.StringCollection> (<xref:System.Collections.IList>tabanlı) ve <xref:System.Collections.Specialized.StringDictionary> (<xref:System.Collections.IDictionary>göre) <xref:System.Collections.Specialized> ad alanıdır.  
  
  - Ayrıca, genel tür bağımsız değişkenleri için <xref:System.String> sınıfını belirterek, <xref:System.Collections.Generic> ad alanındaki genel koleksiyon sınıflarından herhangi birini, türü kesin belirlenmiş dize koleksiyonları olarak kullanabilirsiniz. Örneğin, [liste\<dize >](xref:System.Collections.Generic.List%601) veya [Sözlük < string, dize >](xref:System.Collections.Generic.Dictionary%602)olan bir değişken belirtebilirsiniz.
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects ve PLıNQ  
 LINQ to Objects, nesne türü <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>uyguladığı sürece geliştiricilerin, bellek içi nesnelere erişmek için LINQ sorguları kullanmasına olanak sağlar. LINQ sorguları verilere erişim için ortak bir model sağlar, genellikle standart `foreach` döngülerinden daha kısa ve okunabilir ve filtreleme, sıralama ve gruplama özellikleri sağlar. Daha fazla bilgi için bkz. [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) ve [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 PLıNQ, çok çekirdekli bilgisayarların kullanımını daha verimli bir şekilde kullanarak çok sayıda senaryoda daha hızlı sorgu yürütme sunabilme LINQ to Objects paralel bir uygulamasını sağlar. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)
