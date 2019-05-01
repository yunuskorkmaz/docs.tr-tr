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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fefd9f95a669c9c0384cefe41322c7a10a96a3b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909044"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Karma Tablo ve Sözlük Koleksiyon Türleri
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Sınıfı ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Genel sınıflar uygulamak <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi. <xref:System.Collections.Generic.Dictionary%602> Genel bir sınıf uygulayan <xref:System.Collections.Generic.IDictionary%602> genel arabirim. Bu nedenle, bu koleksiyonlardaki her öğe bir anahtar-değer çiftidir.  
  
 A <xref:System.Collections.Hashtable> nesnesi koleksiyon öğelerini içeren kovaları oluşur. Bir sanal alt öğeleri içinde bir demet oluşturuyorum <xref:System.Collections.Hashtable>, alma ve arama yapar daha kolay ve çoğu koleksiyonlarda daha hızlı. Her bir demete bir karma işlevi kullanılarak oluşturulur ve öğe anahtarına göre bir karma kod ile ilişkilidir.  
  
 Genel <xref:System.Collections.Generic.HashSet%601> sırasız koleksiyonunun benzersiz öğeleri içeren bir sınıftır.  
  
 Bir karma işlevi anahtarına göre sayısal karma kodu döndürür bir algoritmadır. Depolanmakta olan nesnenin bazı özelliğinin değeri anahtardır. Bir karma işlevi, her zaman aynı anahtar için aynı karma kodu döndürmesi gerekir. İki farklı anahtarlara aynı karma kodunu oluşturmak için bir karma işlevi, ancak daha iyi performans, öğeleri karma tablosundan alınırken her benzersiz anahtar sonuçları için bir benzersiz karma kodu oluşturan bir karma işlev mümkündür.  
  
 Bir öğe olarak kullanılan her nesne bir <xref:System.Collections.Hashtable> uygulaması kullanarak üretmeden kendisi için bir karma kod olmalıdır <xref:System.Object.GetHashCode%2A> yöntemi. Ancak tüm öğeler için bir karma işlevi ayrıca belirtebileceğiniz bir <xref:System.Collections.Hashtable> kullanarak bir <xref:System.Collections.Hashtable> kabul eden Oluşturucu bir <xref:System.Collections.IHashCodeProvider> parametrelerinden biri olarak uygulama.  
  
 İçin bir nesne eklendiğinde bir <xref:System.Collections.Hashtable>, nesnenin karma kodu eşleşen karma kod ile ilişkili olan demetinde depolanır. Ne zaman bir değer aranır için de <xref:System.Collections.Hashtable>karma kod için bu değer oluşturulur ve bu karma koduyla ilişkili demetine aranır.  
  
 Örneğin, bir dize için karma işlevi bir dizedeki her karakterin ASCII kodları ele ve birlikte bir karma kod oluşturmak için bunları ekleyebilirsiniz. "Pikniğini" dize "sepet"; dize için karma kodu farklı bir karma kod gerekir Bu nedenle, farklı demet dizeleri "pikniğini" ve "sepet" olacaktır. Buna karşılık, "denebilecek" ve "desserts" aynı karma koda sahip ve aynı kovada olacaktır.  
  
 <xref:System.Collections.Generic.Dictionary%602> Ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıf ile aynı işlevlere sahip <xref:System.Collections.Hashtable> sınıfı. A <xref:System.Collections.Generic.Dictionary%602> belirli bir türdeki (dışında <xref:System.Object>) daha iyi performans sağlayan bir <xref:System.Collections.Hashtable> değer türleri için. Bunun nedeni, öğeleri <xref:System.Collections.Hashtable> türü <xref:System.Object>; bu nedenle, kutulama ve kutudan genellikle ortaya depolamak ya da bir değer türü alınamıyor. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Birden çok iş parçacığı koleksiyonu aynı anda erişirken sınıfı'nin kullanılması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
