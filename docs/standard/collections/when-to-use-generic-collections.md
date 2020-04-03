---
title: Genel Koleksiyonları Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: bbf8ec7f61981332b6984488b369fee62959b92a
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635893"
---
# <a name="when-to-use-generic-collections"></a>Genel koleksiyonların ne zaman kullanılacağı

Genel koleksiyonları kullanmak, temel koleksiyon türünden türeme ve türe özgü üyeleri uygulamak zorunda kalmadan tür güvenliğinden otomatik olarak yararlanmanızı sağlar. Genel koleksiyon türleri, genel koleksiyon öğeleri değer türleri olduğunda, genel koleksiyon öğelerini kutulamak gerekmediği için genellikle ilgili genel olmayan koleksiyon türlerinden (ve genel olmayan temel toplama türlerinden türetilen türlerden daha iyi) daha iyi performans gösterir.  
  
 .NET Framework 4 veya sonraki leri hedefleyen programlar için, birden <xref:System.Collections.Concurrent> çok iş parçacığı aynı anda koleksiyondan öğe eklendiğinde veya kaldırılıyor olabilirken ad alanında genel koleksiyon sınıflarını kullanmanız gerekir.  
  
 Aşağıdaki genel türler varolan toplama türlerine karşılık gelir:  
  
- <xref:System.Collections.Generic.List%601>'ye <xref:System.Collections.ArrayList>karşılık gelen genel sınıftır.  
  
- <xref:System.Collections.Generic.Dictionary%602>ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> karşılık gelen genel <xref:System.Collections.Hashtable>sınıflardır.  
  
- <xref:System.Collections.ObjectModel.Collection%601>'ye <xref:System.Collections.CollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.Collection%601>bir taban sınıf olarak kullanılabilir, <xref:System.Collections.CollectionBase>ancak aksine, soyut değildir, hangi kullanımı çok daha kolay hale getirir.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>'ye <xref:System.Collections.ReadOnlyCollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>soyut değildir ve varolan <xref:System.Collections.Generic.List%601> bir koleksiyonu salt okunur olarak ortaya çıkarmayı kolaylaştıran bir oluşturucuya sahiptir.  
  
- , <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>, <xref:System.Collections.Generic.SortedList%602> , ve genel sınıflar aynı adlara sahip ilgili genel olmayan sınıflara karşılık gelir.  
  
## <a name="additional-types"></a>Ek Türler  
 Birkaç genel koleksiyon türü, genel olmayan karşılıkları yoktur. Bunlar şunlardır:  
  
- <xref:System.Collections.Generic.LinkedList%601>O(1) ekleme ve kaldırma işlemlerini sağlayan genel amaçlı bağlantılı bir listedir.  
  
- <xref:System.Collections.Generic.SortedDictionary%602>O(log) `n`ekleme ve alma işlemleri ile sıralanmış bir sözlüktür, bu da <xref:System.Collections.Generic.SortedList%602>onu .'a kullanışlı bir alternatif yapar.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602>kendi anahtarlarını içeren nesneleri depolamak için bir yol sağlayan bir liste ve sözlük arasında bir melezdir.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601>bağlama ve engelleme işlevi içeren bir toplama sınıfı uygular.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601>hızlı ekleme ve sıralanmamış öğelerin kaldırılmasını sağlar.  
  
## <a name="linq-to-objects"></a>Nesnelere LINQ  
 LINQ to Objects özelliği, nesne türü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi uyguladığı sürece bellek içi nesnelere erişmek için LINQ sorgularını kullanmanıza olanak tanır. LINQ sorguları verilere erişmek için ortak bir desen sağlar; genellikle standart `foreach` döngülere göre daha kısa ve okunabilir; ve filtreleme, sıralama ve gruplandırma özellikleri sağlar. LINQ sorguları da performansı artırabilir. Daha fazla bilgi için [linq to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)konusuna bakın.  
  
## <a name="additional-functionality"></a>Ek İşlevsellik  
 Genel türlerden bazıları, genel olmayan koleksiyon türlerinde bulunmayan işlevselliklere sahiptir. Örneğin, genel <xref:System.Collections.Generic.List%601> olmayan <xref:System.Collections.ArrayList> sınıfa karşılık gelen sınıfın, listeyi arama yöntemlerini belirtmenize olanak <xref:System.Predicate%601> tanıyan temsilci, listenin her öğesinde <xref:System.Action%601> hareket eden yöntemleri temsil eden temsilci ve <xref:System.Converter%602> türler arasındaki dönüşümleri tanımlamanıza olanak tanıyan temsilci gibi genel özneleri kabul eden bir dizi yöntemi vardır.  
  
 Sınıf, <xref:System.Collections.Generic.List%601> listeyi sıralamak <xref:System.Collections.Generic.IComparer%601> ve aramak için kendi genel arabirim uygulamalarınızı belirtmenize olanak tanır. <xref:System.Collections.Generic.SortedDictionary%602> Ve <xref:System.Collections.Generic.SortedList%602> sınıflar da bu yeteneğe sahiptir. Ayrıca, bu sınıflar koleksiyon oluşturulduğunda karşılaştırıcılar belirtmenize izin verilir. Benzer şekilde, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıflar kendi eşitlik karşılaştırıcıları belirtmenize izin sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Genel Türler](../../../docs/standard/generics/index.md)
