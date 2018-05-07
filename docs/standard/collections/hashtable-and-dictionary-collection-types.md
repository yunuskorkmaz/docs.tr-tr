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
ms.openlocfilehash: 6f682ba370e364629d6b79c5cedd28b4af834e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hashtable-and-dictionary-collection-types"></a>Karma Tablo ve Sözlük Koleksiyon Türleri
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Sınıfı ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Genel sınıflar uygulamak <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi. <xref:System.Collections.Generic.Dictionary%602> Genel sınıfı ayrıca uygulayan <xref:System.Collections.Generic.IDictionary%602> genel arabirim. Bu nedenle, bu koleksiyonları her bir öğesinde bir anahtar ve değer çifti ' dir.  
  
 A <xref:System.Collections.Hashtable> nesnesi koleksiyon öğelerini içeren demet oluşur. Bir sanal alt öğeleri içinde kova grubudur <xref:System.Collections.Hashtable>, arama ve alma yapar daha kolay ve daha hızlıdır çoğu koleksiyonlarda. Her demet karma işlevi kullanılarak oluşturulur ve öğenin anahtarı temel bir karma kod ile ilişkilidir.  
  
 Genel <xref:System.Collections.Generic.HashSet%601> sınıfı, sırasız bir benzersiz öğeleri içeren koleksiyon.  
  
 Hash işlevi bir anahtarı temel sayısal karma kodu döndürür bir algoritmadır. Anahtar depolanmakta nesnenin bazı özelliğinin değeri. Hash işlevi her zaman aynı anahtar için aynı karma koda döndürmelidir. İki farklı anahtarlar aynı karma kodunu oluşturmak için bir karma işlevi, ancak öğeleri karma tablosundan alınırken daha iyi performans her benzersiz anahtar sonuçlar için bir benzersiz karma kodu oluşturan karma işlevi mümkündür.  
  
 Bir öğe olarak kullanılan her nesne bir <xref:System.Collections.Hashtable> bir karma kod kendisi için uygulaması kullanarak oluşturabilir olmalıdır <xref:System.Object.GetHashCode%2A> yöntemi. Ancak, tüm öğeler için karma işlevi de belirleyebileceğiniz bir <xref:System.Collections.Hashtable> kullanarak bir <xref:System.Collections.Hashtable> kabul Oluşturucusu bir <xref:System.Collections.IHashCodeProvider> parametrelerinden biri olarak uygulama.  
  
 İçin bir nesne eklendiğinde bir <xref:System.Collections.Hashtable>, nesnenin karma kodu ile eşleşen karma kodu ile ilişkili demet depolanır. Ne zaman bir değer aranır için de <xref:System.Collections.Hashtable>karma kod için bu değer oluşturulur ve bu karma kodu ile ilişkili demet aranır.  
  
 Örneğin, bir dize için bir karma işlevi bir dizede her karakter ASCII kodlarından alın ve bunları birlikte bir karma kodu oluşturmak için ekleyin. "Piknik" dize "sepet"; dize ilişkin karma kodu farklı bir karma kod gerekir Bu nedenle, dizeleri "Piknik" ve "sepet" içinde farklı demet olacaktır. Buna karşılık, "kullanımı yoğun" ve "desserts" aynı karma koda sahip ve aynı aralığındaki olacaktır.  
  
 <xref:System.Collections.Generic.Dictionary%602> Ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfları aynı işlevselliğe sahip <xref:System.Collections.Hashtable> sınıfı. A <xref:System.Collections.Generic.Dictionary%602> belirli bir türdeki (dışında <xref:System.Object>) daha iyi performans sağlayan bir <xref:System.Collections.Hashtable> değer türleri için. Bunun nedeni, öğelerini <xref:System.Collections.Hashtable> türü <xref:System.Object>; bu nedenle, kutulama ve kutudan çıkarma genellikle ortaya depolamak ya da bir değer türü alır. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Birden çok iş parçacığı koleksiyonunun aynı anda erişirken sınıfı'nin kullanılması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IDictionary>  
 <xref:System.Collections.IHashCodeProvider>  
 <xref:System.Collections.Generic.Dictionary%602>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>  
 [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
