---
title: Karma Tablo ve Sözlük Koleksiyon Türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
ms.openlocfilehash: a6f234b6205fd30507b9342d9839db6adcddfc2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711382"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Karma Tablo ve Sözlük Koleksiyon Türleri
Sınıf <xref:System.Collections.Hashtable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> genel sınıflar <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi uygular. Genel <xref:System.Collections.Generic.Dictionary%602> sınıf da <xref:System.Collections.Generic.IDictionary%602> genel arabirimi uygular. Bu nedenle, bu koleksiyonlarda her öğe bir anahtar ve değer çiftidir.  
  
 Nesne, <xref:System.Collections.Hashtable> koleksiyonun öğelerini içeren kovalardan oluşur. <xref:System.Collections.Hashtable>Kova, çoğu koleksiyondan daha kolay ve hızlı arama ve alma yapan, içindeki öğelerin sanal bir alt grubudur. Her kova, karma işlev kullanılarak oluşturulan ve öğenin anahtarına dayanan bir karma koduyla ilişkilidir.  
  
 Genel <xref:System.Collections.Generic.HashSet%601> sınıf, benzersiz öğeler içeren sıralanmamış bir koleksiyondur.  
  
 Karma işlev, bir anahtara dayalı sayısal karma kodu döndüren bir algoritmadır. Anahtar, depolanan nesnenin bazı özelliğinin değeridir. Karma işlev her zaman aynı anahtar için aynı karma kodu döndürmelidir. Bir karma işlevin iki farklı anahtar için aynı karma kodu oluşturması mümkündür, ancak karma tablodan öğeleri alırken her benzersiz anahtar sonuçları için benzersiz bir karma kod oluşturan karma işlev.  
  
 A <xref:System.Collections.Hashtable> öğesi olarak kullanılan her nesne yöntemin <xref:System.Object.GetHashCode%2A> bir uygulama kullanarak kendisi için bir karma kod oluşturmak gerekir. Ancak, bir uygulamayı parametrelerinden biri olarak <xref:System.Collections.Hashtable> kabul eden <xref:System.Collections.Hashtable> bir oluşturucu <xref:System.Collections.IHashCodeProvider> kullanarak bir deki tüm öğeler için karma işlev de belirtebilirsiniz.  
  
 Bir nesne , bir <xref:System.Collections.Hashtable>, bu nesnenin karma kodu eşleşen karma kodu ile ilişkili kova saklanır. Bir değer <xref:System.Collections.Hashtable>aranırken, karma kodu bu değer için oluşturulur ve bu karma koduyla ilişkili kova aranır.  
  
 Örneğin, bir dize için karma işlevi dizedeki her karakterin ASCII kodlarını alabilir ve karma kod oluşturmak için bunları bir araya getirebilir. Dize "piknik" dize "sepet" için karma kodu farklı bir karma kodu olurdu; bu nedenle, dizeleri "piknik" ve "sepet" farklı kovalar olacaktır. Buna karşılık, "stresli" ve "tatlılar" aynı karma kodu olurdu ve aynı kova olurdu.  
  
 Ve sınıflar sınıfla aynı işlevsellik vardır. <xref:System.Collections.Hashtable> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Generic.Dictionary%602> Belirli bir tür (dışında) <xref:System.Object>bir değer türleri için daha <xref:System.Collections.Hashtable> iyi performans sağlar. Bunun nedeni, tür <xref:System.Collections.Hashtable> deki <xref:System.Object>öğelerin; bu nedenle, bir değer türünü depolarken veya aldığınızda genellikle kutulama ve kutulamayı çıkarma oluşur. Birden <xref:System.Collections.Concurrent.ConcurrentDictionary%602> çok iş parçacığı koleksiyona aynı anda erişiyor olabilir sınıf kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
