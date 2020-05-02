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
ms.openlocfilehash: d79f1ca0d264a5a17306bb66f285b6fbe6b4e7ca
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728481"
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme

Koleksiyon sınıfınızı dikkatle seçtiğinizden emin olun. Yanlış tür kullanımı, koleksiyonun kullanımını kısıtlayabilir.

> [!IMPORTANT]
> <xref:System.Collections> Ad alanındaki türleri kullanmaktan kaçının. Koleksiyonların genel ve eş zamanlı sürümleri, daha yüksek tür güvenliği ve diğer geliştirmeler nedeniyle önerilir.

Aşağıdaki soruları göz önünde bulundurun:

- Öğenin genellikle değeri alındıktan sonra atıldığı sıralı bir liste gerekiyor mu?

  - Yanıt Evet ise, ilk kez <xref:System.Collections.Queue> , ilk çıkar <xref:System.Collections.Generic.Queue%601> (FIFO) davranışına ihtiyacınız varsa sınıfı veya genel sınıf kullanmayı düşünün. En son, <xref:System.Collections.Stack> ilk çıkar ( <xref:System.Collections.Generic.Stack%601> LIFO) davranışına ihtiyacınız varsa sınıfını veya genel sınıfı kullanmayı düşünün. Birden çok iş parçacığından güvenli erişim için, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>için eşzamanlı sürümleri kullanın. Dengesgöz önünde bulundurulması için, ve <xref:System.Collections.Immutable.ImmutableQueue%601> <xref:System.Collections.Immutable.ImmutableStack%601>' nin sabit sürümlerini değerlendirin.

  - Aksi takdirde, diğer koleksiyonları kullanmayı göz önünde bulundurun.

- Öğelere FıFO, LıFO veya Random gibi belirli bir sırada erişmeniz gerekiyor mu?

  - <xref:System.Collections.Queue> Sınıfının yanı sıra <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Immutable.ImmutableQueue%601> genel sınıfların hepsi de FIFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?

  - <xref:System.Collections.Stack> Sınıfının yanı sıra <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, ve <xref:System.Collections.Immutable.ImmutableStack%601> genel sınıfların her ikisi de LIFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?

  - <xref:System.Collections.Generic.LinkedList%601> Genel sınıf, başa veya kuyruklu bir sıralı erişime izin verir.

- Dizine göre her öğeye erişmeniz mi gerekiyor?

  - <xref:System.Collections.ArrayList> Ve <xref:System.Collections.Specialized.StringCollection> sınıfları ve <xref:System.Collections.Generic.List%601> genel sınıfı, öğesinin sıfır tabanlı diziniyle öğelerine erişim sağlar. Dengesgöz önünde bulundurulması için, sabit genel sürümleri <xref:System.Collections.Immutable.ImmutableArray%601> ve. <xref:System.Collections.Immutable.ImmutableList%601>

  - <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>,, <xref:System.Collections.Specialized.StringDictionary> Ve sınıfları ve <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları öğe anahtarına göre öğelerine erişim sağlar. Ayrıca, buna karşılık gelen çeşitli türlerde sabit sürümler vardır: <xref:System.Collections.Immutable.ImmutableHashSet%601>, <xref:System.Collections.Immutable.ImmutableDictionary%602>, <xref:System.Collections.Immutable.ImmutableSortedSet%601>, ve <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>.

  - <xref:System.Collections.Specialized.NameObjectCollectionBase> Ve <xref:System.Collections.Specialized.NameValueCollection> sınıfları <xref:System.Collections.ObjectModel.KeyedCollection%602> ve ve <xref:System.Collections.Generic.SortedList%602> genel sınıfları, kendi öğelerine sıfır tabanlı dizin ya da öğenin anahtarı ile erişim sağlar.

- Her öğe bir değer, bir anahtar ve bir değer birleşimi ya da bir anahtar ve birden çok değer birleşimi içerir mi?

  - Bir değer: <xref:System.Collections.IList> arabirime veya <xref:System.Collections.Generic.IList%601> genel arabirime göre koleksiyonlardan herhangi birini kullanın. Sabit bir seçenek için <xref:System.Collections.Immutable.IImmutableList%601> genel arabirimi göz önünde bulundurun.

  - Bir anahtar ve bir değer: <xref:System.Collections.IDictionary> arabirime veya <xref:System.Collections.Generic.IDictionary%602> genel arabirime göre koleksiyonlardan herhangi birini kullanın. Sabit bir seçenek için <xref:System.Collections.Immutable.IImmutableSet%601> veya <xref:System.Collections.Immutable.IImmutableDictionary%602> genel arabirimlerini göz önünde bulundurun.

  - Gömülü anahtara sahip bir değer: <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıfı kullanın.

  - Bir anahtar ve birden çok değer: <xref:System.Collections.Specialized.NameValueCollection> sınıfını kullanın.

- Öğeleri girildiklerinde farklı şekilde sıralamak mı gerekiyor?

  - <xref:System.Collections.Hashtable> Sınıfı kendi öğelerini kendi karma kodlarına göre sıralar.

  - <xref:System.Collections.SortedList> Sınıfı ve <xref:System.Collections.Generic.SortedList%602> ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları öğelerini anahtara göre sıralar. Sıralama düzeni <xref:System.Collections.IComparer> , <xref:System.Collections.SortedList> sınıfı için ve genel <xref:System.Collections.Generic.IComparer%601> arabirim <xref:System.Collections.Generic.SortedList%602> uygulama üzerinde ve <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfları için uygulamaya göre belirlenir. İki genel tür üzerinde daha iyi <xref:System.Collections.Generic.SortedDictionary%602> performans sağlar <xref:System.Collections.Generic.SortedList%602>, ancak <xref:System.Collections.Generic.SortedList%602> daha az bellek tüketir.

  - <xref:System.Collections.ArrayList>bir <xref:System.Collections.IComparer> uygulamayı <xref:System.Collections.ArrayList.Sort%2A> parametre olarak alan bir yöntem sağlar. Genel karşılığı, <xref:System.Collections.Generic.List%601> genel olarak, bir parametre olarak <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.IComparer%601> genel arabirimin bir uygulamasını alan bir yöntem sağlar.

- Bilgilerin hızlı aramalarında ve alınmasına mi ihtiyacınız var?

  - <xref:System.Collections.Specialized.ListDictionary>küçük koleksiyonlardan <xref:System.Collections.Hashtable> (10 öğe veya daha az) daha hızlıdır. <xref:System.Collections.Generic.Dictionary%602> Genel sınıf <xref:System.Collections.Generic.SortedDictionary%602> genel sınıftan daha hızlı arama sağlar. Çoklu iş parçacıklı uygulama <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>Sıralanmamış veriler için hızlı çoklu iş parçacıklı ekleme sağlar. Çoklu iş parçacıklı türler hakkında daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)?

- Yalnızca dizeleri kabul eden koleksiyonlara mi ihtiyacınız var?

  - <xref:System.Collections.Specialized.StringCollection>(tabanlı <xref:System.Collections.IList>) ve <xref:System.Collections.Specialized.StringDictionary> (tabanlı <xref:System.Collections.IDictionary>) <xref:System.Collections.Specialized> ad alanında yer alır.

  - Ayrıca, genel tür bağımsız değişkenleri için <xref:System.Collections.Generic> <xref:System.String> sınıfını belirterek, ad alanındaki genel koleksiyon sınıflarından herhangi birini kesin olarak belirlenmiş dize koleksiyonları olarak kullanabilirsiniz. Örneğin, [liste\<dizesi>](xref:System.Collections.Generic.List%601) veya [sözlük<dize, dize>](xref:System.Collections.Generic.Dictionary%602)türünde bir değişken bildirebilirsiniz.

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects ve PLıNQ

LINQ to Objects, geliştiricilerin, nesne türü veya <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>uyguladığı sürece, bellek ıçı nesnelere erişmek için LINQ sorguları kullanmasına olanak sağlar. LINQ sorguları verilere erişim için ortak bir model sağlar, genellikle standart `foreach` döngülerden daha kısa ve okunabilir ve filtreleme, sıralama ve gruplama özellikleri sağlar. Daha fazla bilgi için bkz. [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) ve [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLıNQ, çok çekirdekli bilgisayarların kullanımını daha verimli bir şekilde kullanarak çok sayıda senaryoda daha hızlı sorgu yürütme sunabilme LINQ to Objects paralel bir uygulamasını sağlar. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [İş parçacığı güvenli Koleksiyonlar](../../../docs/standard/collections/thread-safe/index.md)
