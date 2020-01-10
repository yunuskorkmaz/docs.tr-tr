---
title: Genel Koleksiyonları Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 7d59259c1cab6842ef62888bf5326225394d8d44
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711213"
---
# <a name="when-to-use-generic-collections"></a>Genel Koleksiyonları Ne Zaman Kullanılacağı
Genel koleksiyonları kullanmak genellikle önerilir, çünkü bir temel koleksiyon türünden türemeniz ve türe özgü Üyeler uygulamanız gerekmeden tür güvenliği avantajını elde etmeniz gerekir. Genel koleksiyon türleri genellikle karşılık gelen genel olmayan koleksiyon türlerinden (ve genel olmayan temel koleksiyon türlerinden türetilen türlerden daha iyidir), koleksiyon öğeleri değer türleri olduğunda daha iyi bir hale gelir çünkü genel türler öğelerin Box 'a gerek yoktur.  
  
 .NET Framework 4 veya sonraki sürümlerini hedefleyen programlar için, birden çok iş parçacığı koleksiyona aynı anda öğe ekleme veya kaldırma gibi durumlarda, <xref:System.Collections.Concurrent> ad alanında genel koleksiyon sınıflarını kullanmanız gerekir.  
  
 Aşağıdaki genel türler var olan koleksiyon türlerine karşılık gelir:  
  
- <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>karşılık gelen genel sınıftır.  
  
- <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Hashtable>karşılık gelen genel sınıflardır.  
  
- <xref:System.Collections.ObjectModel.Collection%601>, <xref:System.Collections.CollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.Collection%601> temel sınıf olarak kullanılabilir, ancak <xref:System.Collections.CollectionBase>aksine soyut değildir. Bu, kullanımını çok daha kolay hale getirir.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, <xref:System.Collections.ReadOnlyCollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> soyut değildir ve var olan bir <xref:System.Collections.Generic.List%601> salt okunurdur bir koleksiyon olarak açığa çıkarmak kolaylaşır.  
  
- <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>ve <xref:System.Collections.Generic.SortedList%602> genel sınıfları aynı adlara sahip ilgili olmayan genel sınıflara karşılık gelir.  
  
## <a name="additional-types"></a>Ek türler  
 Birkaç genel koleksiyon türü genel olmayan karşılıkiçermez. Bunlar aşağıdakileri içerir:  
  
- <xref:System.Collections.Generic.LinkedList%601>, O (1) ekleme ve kaldırma işlemleri sağlayan genel amaçlı bağlantılı bir listesidir.  
  
- <xref:System.Collections.Generic.SortedDictionary%602>, O (günlük `n`) ekleme ve alma işlemleri içeren sıralanmış bir sözlüktür ve bu, <xref:System.Collections.Generic.SortedList%602>yararlı bir alternatif sağlar.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602>, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlayan bir liste ve sözlük arasında karma bir yoldur.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> sınırlayıcı ve engelleyici işlevlerle bir koleksiyon sınıfı uygular.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> Sıralanmamış öğelerin hızlı bir şekilde eklenmesini ve kaldırılmasını sağlar.  
  
## <a name="linq-to-objects"></a>Nesnelere LINQ  
 LINQ to Objects özelliği, nesne türü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimini uyguladığı sürece, bellek içi nesnelere erişmek için LINQ sorgularını kullanmanıza olanak sağlar. LINQ sorguları verilere erişim için ortak bir model sağlar; genellikle standart `foreach` döngülerinden daha kısa ve okunabilir; ve filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Ek Işlevsellik  
 Genel türlerden bazıları genel olmayan koleksiyon türlerinde bulunmayan işlevlere sahiptir. Örneğin, genel olmayan <xref:System.Collections.ArrayList> sınıfına karşılık gelen <xref:System.Collections.Generic.List%601> sınıfında, listeyi aramak için yöntemler belirtmenize olanak tanıyan <xref:System.Predicate%601> temsilcisi gibi genel temsilcileri kabul eden bir dizi yöntem vardır. Bu, listedeki her öğe üzerinde işlem yapan yöntemleri temsil eden <xref:System.Action%601> temsil ve türler arasında dönüştürmeleri tanımlamanızı sağlayan <xref:System.Converter%602> temsilcisidir.  
  
 <xref:System.Collections.Generic.List%601> sınıfı, listeyi sıralamak ve aramak için kendi <xref:System.Collections.Generic.IComparer%601> genel arabirim uygulamalarınızı belirtmenizi sağlar. <xref:System.Collections.Generic.SortedDictionary%602> ve <xref:System.Collections.Generic.SortedList%602> sınıflarında de bu yetenek vardır. Ayrıca, bu sınıflar koleksiyon oluşturulduğunda Karşılaştırıcılar belirtmenizi sağlar. Benzer biçimde, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfları kendi eşitlik karşılaştırmalarınızı belirtmenizi sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Genel Türler](../../../docs/standard/generics/index.md)
