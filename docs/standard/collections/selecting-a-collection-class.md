---
title: Koleksiyon Sınıfı Seçme
description: .NET ' te hangi koleksiyon sınıfının seçileceğine karar verme hakkında bilgi edinin. Yanlış tür kullanımı, koleksiyonun kullanımını kısıtlayabilir.
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
ms.openlocfilehash: 52a839661a09d6fa7561d67b82d1c1bf854e3cfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600821"
---
# <a name="selecting-a-collection-class"></a>Koleksiyon Sınıfı Seçme

Koleksiyon sınıfınızı dikkatle seçtiğinizden emin olun. Yanlış tür kullanımı, koleksiyonun kullanımını kısıtlayabilir.

> [!IMPORTANT]
> Ad alanındaki türleri kullanmaktan kaçının <xref:System.Collections> . Koleksiyonların genel ve eş zamanlı sürümleri, daha yüksek tür güvenliği ve diğer geliştirmeler nedeniyle önerilir.

Aşağıdaki soruları göz önünde bulundurun:

- Öğenin genellikle değeri alındıktan sonra atıldığı sıralı bir liste gerekiyor mu?

  - Yanıt Evet ise, ilk kez <xref:System.Collections.Queue> <xref:System.Collections.Generic.Queue%601> , ilk çıkar (FIFO) davranışına ihtiyacınız varsa sınıfı veya genel sınıf kullanmayı düşünün. <xref:System.Collections.Stack> <xref:System.Collections.Generic.Stack%601> En son, ilk çıkar (LIFO) davranışına ihtiyacınız varsa sınıfını veya genel sınıfı kullanmayı düşünün. Birden çok iş parçacığından güvenli erişim için, ve için eşzamanlı sürümleri <xref:System.Collections.Concurrent.ConcurrentQueue%601> kullanın <xref:System.Collections.Concurrent.ConcurrentStack%601> . Dengesgöz önünde bulundurulması için, ve ' nin sabit sürümlerini değerlendirin <xref:System.Collections.Immutable.ImmutableQueue%601> <xref:System.Collections.Immutable.ImmutableStack%601> .

  - Aksi takdirde, diğer koleksiyonları kullanmayı göz önünde bulundurun.

- Öğelere FıFO, LıFO veya Random gibi belirli bir sırada erişmeniz gerekiyor mu?

  - <xref:System.Collections.Queue>Sınıfının yanı sıra <xref:System.Collections.Generic.Queue%601> ,, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Immutable.ImmutableQueue%601> genel sınıfların hepsi de FIFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](thread-safe/when-to-use-a-thread-safe-collection.md)?

  - <xref:System.Collections.Stack>Sınıfının yanı sıra <xref:System.Collections.Generic.Stack%601> ,, <xref:System.Collections.Concurrent.ConcurrentStack%601> ve <xref:System.Collections.Immutable.ImmutableStack%601> genel SıNıFLARıN her ikisi de LIFO erişimi sunar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](thread-safe/when-to-use-a-thread-safe-collection.md)?

  - <xref:System.Collections.Generic.LinkedList%601>Genel sınıf, başa veya kuyruklu bir sıralı erişime izin verir.

- Dizine göre her öğeye erişmeniz mi gerekiyor?

  - <xref:System.Collections.ArrayList>Ve <xref:System.Collections.Specialized.StringCollection> sınıfları ve <xref:System.Collections.Generic.List%601> Genel sınıfı, öğesinin sıfır tabanlı diziniyle öğelerine erişim sağlar. Dengesgöz önünde bulundurulması için, sabit genel sürümleri <xref:System.Collections.Immutable.ImmutableArray%601> ve <xref:System.Collections.Immutable.ImmutableList%601> .

  - <xref:System.Collections.Hashtable>,, <xref:System.Collections.SortedList> <xref:System.Collections.Specialized.ListDictionary> , Ve <xref:System.Collections.Specialized.StringDictionary> sınıfları ve <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfları öğe anahtarına göre öğelerine erişim sağlar. Ayrıca, buna karşılık gelen çeşitli türlerde sabit sürümler vardır: <xref:System.Collections.Immutable.ImmutableHashSet%601> , <xref:System.Collections.Immutable.ImmutableDictionary%602> , <xref:System.Collections.Immutable.ImmutableSortedSet%601> , ve <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

  - <xref:System.Collections.Specialized.NameObjectCollectionBase>Ve sınıfları ve ve <xref:System.Collections.Specialized.NameValueCollection> <xref:System.Collections.ObjectModel.KeyedCollection%602> <xref:System.Collections.Generic.SortedList%602> Genel sınıfları, kendi öğelerine sıfır tabanlı dizin ya da öğenin anahtarı ile erişim sağlar.

- Her öğe bir değer, bir anahtar ve bir değer birleşimi ya da bir anahtar ve birden çok değer birleşimi içerir mi?

  - Bir değer: <xref:System.Collections.IList> arabirime veya genel arabirime göre koleksiyonlardan herhangi birini kullanın <xref:System.Collections.Generic.IList%601> . Sabit bir seçenek için genel arabirimi göz önünde bulundurun <xref:System.Collections.Immutable.IImmutableList%601> .

  - Bir anahtar ve bir değer: <xref:System.Collections.IDictionary> arabirime veya genel arabirime göre koleksiyonlardan herhangi birini kullanın <xref:System.Collections.Generic.IDictionary%602> . Sabit bir seçenek için <xref:System.Collections.Immutable.IImmutableSet%601> veya genel arabirimlerini göz önünde bulundurun <xref:System.Collections.Immutable.IImmutableDictionary%602> .

  - Gömülü anahtara sahip bir değer: <xref:System.Collections.ObjectModel.KeyedCollection%602> Genel sınıfı kullanın.

  - Bir anahtar ve birden çok değer: <xref:System.Collections.Specialized.NameValueCollection> sınıfını kullanın.

- Öğeleri girildiklerinde farklı şekilde sıralamak mı gerekiyor?

  - <xref:System.Collections.Hashtable>Sınıfı kendi öğelerini kendi karma kodlarına göre sıralar.

  - <xref:System.Collections.SortedList>Sınıfı ve <xref:System.Collections.Generic.SortedList%602> ve <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfları öğelerini anahtara göre sıralar. Sıralama düzeni, <xref:System.Collections.IComparer> <xref:System.Collections.SortedList> sınıfı için ve genel arabirim uygulama üzerinde ve <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfları için uygulamaya göre belirlenir. İki genel tür üzerinde daha <xref:System.Collections.Generic.SortedDictionary%602> iyi performans sağlar <xref:System.Collections.Generic.SortedList%602> , ancak <xref:System.Collections.Generic.SortedList%602> daha az bellek tüketir.

  - <xref:System.Collections.ArrayList>bir <xref:System.Collections.ArrayList.Sort%2A> uygulamayı parametre olarak alan bir yöntem sağlar <xref:System.Collections.IComparer> . Genel karşılığı, genel olarak, bir <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.IComparer%601> parametre olarak genel arabirimin bir uygulamasını alan bir yöntem sağlar.

- Bilgilerin hızlı aramalarında ve alınmasına mi ihtiyacınız var?

  - <xref:System.Collections.Specialized.ListDictionary><xref:System.Collections.Hashtable>küçük koleksiyonlardan (10 öğe veya daha az) daha hızlıdır. <xref:System.Collections.Generic.Dictionary%602>Genel sınıf genel sınıftan daha hızlı arama sağlar <xref:System.Collections.Generic.SortedDictionary%602> . Çoklu iş parçacıklı uygulama <xref:System.Collections.Concurrent.ConcurrentDictionary%602> . <xref:System.Collections.Concurrent.ConcurrentBag%601>Sıralanmamış veriler için hızlı çoklu iş parçacıklı ekleme sağlar. Çoklu iş parçacıklı türler hakkında daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonu ne zaman kullanılır](thread-safe/when-to-use-a-thread-safe-collection.md)?

- Yalnızca dizeleri kabul eden koleksiyonlara mi ihtiyacınız var?

  - <xref:System.Collections.Specialized.StringCollection>(tabanlı <xref:System.Collections.IList> ) ve <xref:System.Collections.Specialized.StringDictionary> (tabanlı <xref:System.Collections.IDictionary> ) <xref:System.Collections.Specialized> ad alanıdır.

  - Ayrıca, <xref:System.Collections.Generic> <xref:System.String> genel tür bağımsız değişkenleri için sınıfını belirterek, ad alanındaki genel koleksiyon sınıflarından herhangi birini kesin olarak belirlenmiş dize koleksiyonları olarak kullanabilirsiniz. Örneğin, bir değişkeni [liste \<String> ](xref:System.Collections.Generic.List%601) veya [Sözlük<dize, dize>](xref:System.Collections.Generic.Dictionary%602)türünde olacak şekilde bildirebilirsiniz.

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects ve PLıNQ

LINQ to Objects, geliştiricilerin, nesne türü veya uyguladığı sürece, bellek içi nesnelere erişmek için LINQ sorguları kullanmasına olanak sağlar <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> . LINQ sorguları verilere erişim için ortak bir model sağlar, genellikle standart döngülerden daha kısa ve okunabilir `foreach` ve filtreleme, sıralama ve gruplama özellikleri sağlar. Daha fazla bilgi için bkz. [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) ve [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLıNQ, çok çekirdekli bilgisayarların kullanımını daha verimli bir şekilde kullanarak çok sayıda senaryoda daha hızlı sorgu yürütme sunabilme LINQ to Objects paralel bir uygulamasını sağlar. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [İş parçacığı güvenli Koleksiyonlar](thread-safe/index.md)
