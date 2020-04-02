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
ms.openlocfilehash: 621d64183c1cacc14c2d432e4eef43f4d3ba5474
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588322"
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme

Toplama sınıfınızı dikkatle seçtiğinizden emin olun. Yanlış türü kullanmak koleksiyonu kullanımınızı kısıtlayabilir.  

> [!IMPORTANT]
> <xref:System.Collections> Ad alanında türleri kullanmaktan kaçının. Koleksiyonların genel ve eşzamanlı sürümleri, daha büyük tür güvenliği ve diğer iyileştirmeler nedeniyle önerilir.  

 Aşağıdaki soruları göz önünde bulundurun:  
  
- Öğenin değeri alındıktan sonra genellikle atıldığı sıralı bir listeye mi ihtiyacınız var?  
  
  - Evet ise, ilk,ilk çıkan (FIFO) davranışa ihtiyacınız varsa <xref:System.Collections.Queue> sınıfı veya <xref:System.Collections.Generic.Queue%601> genel sınıfı kullanmayı düşünün. Son, <xref:System.Collections.Stack> ilk çıkan <xref:System.Collections.Generic.Stack%601> (LIFO) davranışa ihtiyacınız varsa sınıfı veya genel sınıfı kullanmayı düşünün. Birden çok iş parçacığından güvenli erişim için <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>eşzamanlı sürümleri kullanın ve.  
  
  - Değilse, diğer koleksiyonları kullanmayı düşünün.  
  
- FIFO, LIFO veya rasgele gibi belirli bir sırada öğelere erişmeniz gerekiyor mu?  
  
  - Sınıf <xref:System.Collections.Queue> ve <xref:System.Collections.Generic.Queue%601> genel <xref:System.Collections.Concurrent.ConcurrentQueue%601> sınıf FIFO erişimi sunar. Daha fazla bilgi için, [İş Parçacığı Güvenli Koleksiyonu'nun Ne Zaman Kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)konusuna bakın.  
  
  - Sınıf <xref:System.Collections.Stack> ve <xref:System.Collections.Generic.Stack%601> genel <xref:System.Collections.Concurrent.ConcurrentStack%601> sınıf LIFO erişimi sunar. Daha fazla bilgi için, [İş Parçacığı Güvenli Koleksiyonu'nun Ne Zaman Kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)konusuna bakın.  
  
  - Genel <xref:System.Collections.Generic.LinkedList%601> sınıf, kafadan kuyrağa veya kuyruktan başa sıralı erişim sağlar.  
  
- Her öğeyi dizin olarak erişmeniz mi gerekiyor?  
  
  - Ve <xref:System.Collections.ArrayList> <xref:System.Collections.Specialized.StringCollection> sınıflar ve <xref:System.Collections.Generic.List%601> genel sınıf öğenin sıfır tabanlı dizini tarafından öğelerine erişim sağlar.  
  
  - , <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, <xref:System.Collections.Specialized.StringDictionary> , ve <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedDictionary%602> sınıflar ve genel sınıflar öğenin anahtarı ile kendi öğelerine erişim sağlar.  
  
  - Ve <xref:System.Collections.Specialized.NameObjectCollectionBase> <xref:System.Collections.Specialized.NameValueCollection> sınıflar ve <xref:System.Collections.ObjectModel.KeyedCollection%602> genel <xref:System.Collections.Generic.SortedList%602> sınıflar, öğelerine sıfır tabanlı dizin veya öğenin anahtarı yla erişim sağlar.  
  
- Her öğe bir değer, bir anahtar ve bir değerin birleşimi mi, yoksa bir anahtar ve birden çok değerin birleşimini mi içerecek?  
  
  - Bir değer: <xref:System.Collections.IList> Arabirim veya <xref:System.Collections.Generic.IList%601> genel arabirimi temel alan koleksiyonlardan herhangi birini kullanın.  
  
  - Bir anahtar ve tek değer: <xref:System.Collections.IDictionary> Arayüze veya <xref:System.Collections.Generic.IDictionary%602> genel arabirime dayalı koleksiyonlardan herhangi birini kullanın.  
  
  - Katıştılmış anahtarla <xref:System.Collections.ObjectModel.KeyedCollection%602> bir değer: Genel sınıfı kullanın.  
  
  - Bir anahtar ve birden <xref:System.Collections.Specialized.NameValueCollection> çok değer: Sınıfı kullanın.  
  
- Öğeleri girilen şekilden farklı sıralamanız gerekiyor mu?  
  
  - Sınıf, <xref:System.Collections.Hashtable> öğelerini karma kodlarına göre sıralar.  
  
  - Sınıf <xref:System.Collections.SortedList> ve <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> genel sınıflar öğelerini anahtara göre sıralar. <xref:System.Collections.IComparer> Sıralama sırası, <xref:System.Collections.SortedList> sınıf için arabirimin uygulanmasına ve genel <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> sınıflar için genel arabirimin uygulanmasına dayanır. İki genel tür, <xref:System.Collections.Generic.SortedDictionary%602> daha iyi <xref:System.Collections.Generic.SortedList%602>performans <xref:System.Collections.Generic.SortedList%602> sunar , daha az bellek tüketir iken.  
  
  - <xref:System.Collections.ArrayList>bir <xref:System.Collections.ArrayList.Sort%2A> <xref:System.Collections.IComparer> uygulamayı parametre olarak alan bir yöntem sağlar. Genel muadili, <xref:System.Collections.Generic.List%601> genel sınıf, bir parametre olarak <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.IComparer%601> genel arabirimin bir uygulama alır bir yöntem sağlar.  
  
- Hızlı arama ve bilgi alma gerekiyor mu?  
  
  - <xref:System.Collections.Specialized.ListDictionary>küçük koleksiyonlardan (10 öğe veya daha az) daha <xref:System.Collections.Hashtable> hızlıdır. Genel <xref:System.Collections.Generic.Dictionary%602> sınıf, genel sınıftan <xref:System.Collections.Generic.SortedDictionary%602> daha hızlı arama sağlar. Çok iş parçacığı uygulaması <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>sıralanmamış veriler için hızlı çok iş parçacığı ekleme sağlar. Her iki çok iş parçacığı türü hakkında daha fazla bilgi için, [İş Parçacığı Güvenli Koleksiyonu'nun Ne Zaman Kullanılacağı](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)konusuna bakın.  
  
- Yalnızca dizeleri kabul eden koleksiyonlara mı ihtiyacınız var?  
  
  - <xref:System.Collections.Specialized.StringCollection>(dayalı) <xref:System.Collections.IList>ve <xref:System.Collections.Specialized.StringDictionary> <xref:System.Collections.IDictionary>(dayalı) <xref:System.Collections.Specialized> ad alanında bulunmaktadır.  
  
  - Buna ek olarak, <xref:System.Collections.Generic> ad alanındaki genel koleksiyon sınıflarından herhangi birini, genel tür bağımsız <xref:System.String> değişkenleri için sınıfı belirterek güçlü bir şekilde yazılan dize koleksiyonları olarak kullanabilirsiniz. Örneğin, bir değişkeni [Liste\<Dizesi>](xref:System.Collections.Generic.List%601) veya [Sözlük<String,String>](xref:System.Collections.Generic.Dictionary%602)türüne ait olarak bildirebilirsiniz.
  
## <a name="linq-to-objects-and-plinq"></a>LinQ nesneler ve PLINQ için  
 LINQ to Objects, geliştiricilerin nesne türü uygulandığı sürece bellek nesneleri için LINQ <xref:System.Collections.IEnumerable> sorgularını kullanmasına olanak tanır. <xref:System.Collections.Generic.IEnumerable%601> LINQ sorguları verilere erişmek için ortak bir desen sağlar, genellikle standart `foreach` döngülere göre daha kısa ve okunabilirdir ve filtreleme, sıralama ve gruplandırma özellikleri sağlar. Daha fazla bilgi için [nesnelere LINQ (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) ve [Nesnelere LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)bakın.  
  
 PLINQ, çok çekirdekli bilgisayarların daha verimli kullanımı yoluyla birçok senaryoda daha hızlı sorgu yürütmesi sunabilen Nesnelere LINQ'nin paralel bir şekilde uygulanmasını sağlar. Daha fazla bilgi için [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [İş Parçacığı Güvenli Koleksiyonları](../../../docs/standard/collections/thread-safe/index.md)
