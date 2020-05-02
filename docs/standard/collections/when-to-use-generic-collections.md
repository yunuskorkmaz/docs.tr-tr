---
title: Genel Koleksiyonları Ne Zaman Kullanılacağı
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: feccd8c53e5171889666ed407258b9d36ad8a140
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728192"
---
# <a name="when-to-use-generic-collections"></a>Genel koleksiyonların kullanılma zamanı

Genel koleksiyonları kullanmak, bir temel koleksiyon türünden türemenize ve türe özgü Üyeler uygulamanıza gerek kalmadan tür güvenliği 'nin otomatik avantajını sağlar. Genel koleksiyon türleri, genellikle karşılık gelen genel olmayan koleksiyon türlerinden (ve genel olmayan taban koleksiyon türlerinden türetilen türlerden daha iyi) daha iyi bir şekilde gerçekleştirilir, çünkü genel türler ile, genel türler ile öğeleri kullanıma almanız gerekmez.

.NET Standard 1,0 veya sonraki bir sürümü hedefleyen programlar için, birden çok iş parçacığı koleksiyondaki öğeleri <xref:System.Collections.Concurrent> eşzamanlı olarak ekleme veya kaldırma gibi durumlarda ad alanındaki genel koleksiyon sınıflarını kullanın. Ayrıca, sandeğiştirici kullanılabilirliği istendiğinde, <xref:System.Collections.Immutable> ad alanındaki genel koleksiyon sınıflarını göz önünde bulundurun.

Aşağıdaki genel türler var olan koleksiyon türlerine karşılık gelir:

- <xref:System.Collections.Generic.List%601>, öğesine <xref:System.Collections.ArrayList>karşılık gelen genel sınıftır.

- <xref:System.Collections.Generic.Dictionary%602>ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , öğesine <xref:System.Collections.Hashtable>karşılık gelen genel sınıflardır.

- <xref:System.Collections.ObjectModel.Collection%601>, öğesine <xref:System.Collections.CollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.Collection%601>temel sınıf olarak kullanılabilir, ancak aksine <xref:System.Collections.CollectionBase>soyut değildir, bu da kullanımını çok daha kolay hale getirir.

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, öğesine <xref:System.Collections.ReadOnlyCollectionBase>karşılık gelen genel sınıftır. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>soyut değildir ve var olan <xref:System.Collections.Generic.List%601> bir salt okunurdur koleksiyon olarak ortaya çıkarmak kolaylaşır.

- <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Immutable.ImmutableQueue%601>,,, Ve <xref:System.Collections.Immutable.ImmutableSortedSet%601> genel sınıflar, aynı ada sahip ilgili olmayan genel sınıflara karşılık gelir. <xref:System.Collections.Immutable.ImmutableArray%601> <xref:System.Collections.Generic.SortedList%602>

## <a name="additional-types"></a>Ek türler

Birkaç genel koleksiyon türü genel olmayan karşılıkiçermez. Bunlar aşağıdakileri içerir:

- <xref:System.Collections.Generic.LinkedList%601>, O (1) ekleme ve kaldırma işlemleri sağlayan genel amaçlı bağlantılı bir listesidir.

- <xref:System.Collections.Generic.SortedDictionary%602>, için <xref:System.Collections.Generic.SortedList%602>yararlı bir alternatif sağlayan O ( `n`günlük) ekleme ve alma işlemleri içeren sıralanmış bir sözlüktür.

- <xref:System.Collections.ObjectModel.KeyedCollection%602>, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlayan bir liste ve sözlük arasında karma bir yoldur.

- <xref:System.Collections.Concurrent.BlockingCollection%601>sınırlayıcı ve engelleme işlevleriyle bir koleksiyon sınıfı uygular.

- <xref:System.Collections.Concurrent.ConcurrentBag%601>Sıralanmamış öğelerin hızlı bir şekilde eklenmesini ve kaldırılmasını sağlar.

### <a name="immutable-builders"></a>Sabit oluşturucular

Uygulamanızdaki işlevleri kullanmayı istediğinizde, <xref:System.Collections.Immutable> ad alanı kullanabileceğiniz genel koleksiyon türlerini sunar. Tüm sabit koleksiyon türleri, birden çok `Builder` mutasyonunuzda performansı iyileştirebileceği sınıflar sunar. `Builder` Sınıf işlem işlemleri kesilebilir durumda. Tüm kumalar tamamlandığında, tüm düğümleri "dondurmak" `ToImmutable` ve örneğin bir <xref:System.Collections.Immutable.ImmutableList%601>sabit genel koleksiyon oluşturmak için yöntemini çağırın.

`Builder` Nesnesi, genel `CreateBuilder()` olmayan yöntem çağırarak oluşturulabilir. Bir `Builder` örneğinden, çağırabilirsiniz `ToImmutable()`. Benzer şekilde, `Immutable*` koleksiyondan, genel sabit koleksiyondan bir `ToBuilder()` Oluşturucu örneği oluşturmak için öğesini çağırabilirsiniz. Aşağıdakiler çeşitli `Builder` türlerdir.

- <xref:System.Collections.Immutable.ImmutableArray%601.Builder>
- <xref:System.Collections.Immutable.ImmutableDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableHashSet%601.Builder>
- <xref:System.Collections.Immutable.ImmutableList%601.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder>

## <a name="linq-to-objects"></a>Nesnelere LINQ

LINQ to Objects özelliği, nesne türü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimini uyguladığı sürece, bellek ıçı nesnelere erişmek için LINQ sorgularını kullanmanıza olanak sağlar. LINQ sorguları verilere erişim için ortak bir model sağlar; genellikle standart `foreach` döngülere göre daha kısa ve okunabilir; ve filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="additional-functionality"></a>Ek Işlevsellik
Genel türlerden bazıları genel olmayan koleksiyon türlerinde bulunmayan işlevlere sahiptir. Örneğin, <xref:System.Collections.Generic.List%601> genel <xref:System.Collections.ArrayList> olmayan sınıfına karşılık gelen sınıfı, listeyi aramak için yöntemler belirtmenize imkan tanıyan temsilci gibi genel <xref:System.Predicate%601> temsilcileri kabul eden bir dizi yöntemi, <xref:System.Action%601> listenin her bir öğesi üzerinde işlem yapan yöntemleri temsil eden temsilciyi ve <xref:System.Converter%602> türler arasında dönüştürmeleri tanımlamanızı sağlayan temsilciyi içerir.

<xref:System.Collections.Generic.List%601> Sınıfı, listeyi sıralamak ve aramak için kendi <xref:System.Collections.Generic.IComparer%601> genel arabirim uygulamalarınızı belirtmenizi sağlar. <xref:System.Collections.Generic.SortedDictionary%602> Ve <xref:System.Collections.Generic.SortedList%602> sınıflarının bu özelliği de vardır. Ayrıca, bu sınıflar koleksiyon oluşturulduğunda Karşılaştırıcılar belirtmenizi sağlar. Benzer şekilde, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfları kendi eşitlik karşılaştırmalarınızı belirtmenizi sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar ve veri yapıları](../../../docs/standard/collections/index.md)
- [Yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Genel Türler](../../../docs/standard/generics/index.md)
