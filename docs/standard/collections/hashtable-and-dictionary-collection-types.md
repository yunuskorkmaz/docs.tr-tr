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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711382"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Karma Tablo ve Sözlük Koleksiyon Türleri
<xref:System.Collections.Hashtable?displayProperty=nameWithType> sınıfı ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> genel sınıfları, <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimini uygular. <xref:System.Collections.Generic.Dictionary%602> genel sınıfı, <xref:System.Collections.Generic.IDictionary%602> genel arabirimini de uygular. Bu nedenle, bu koleksiyonlardaki her öğe bir anahtar ve değer çiftidir.  
  
 <xref:System.Collections.Hashtable> nesnesi, koleksiyonun öğelerini içeren demetlerden oluşur. Demet, <xref:System.Collections.Hashtable>içindeki öğelerin bir sanal alt grubudur ve bu, arama ve alma işlemlerini birçok koleksiyondan daha kolay ve hızlı bir şekilde gerçekleştirir. Her demet, bir karma işlev kullanılarak oluşturulan ve öğesinin anahtarını temel alan bir karma kodla ilişkilendirilir.  
  
 Genel <xref:System.Collections.Generic.HashSet%601> sınıfı, benzersiz öğeleri kapsayan sıralanmamış bir koleksiyondur.  
  
 Karma işlevi, bir anahtara dayalı sayısal bir karma kodu döndüren algoritmadır. Anahtar, depolanan nesnenin bazı özelliğinin değeridir. Karma işlev her zaman aynı anahtar için aynı karma kodu döndürmelidir. Bir karma işlevin iki farklı anahtar için aynı karma kodu oluşturması mümkündür, ancak her benzersiz anahtar için benzersiz bir karma kod üreten bir karma işlev, karma tablodaki öğeleri alırken daha iyi performans elde edilir.  
  
 Bir <xref:System.Collections.Hashtable> öğe olarak kullanılan her nesne, <xref:System.Object.GetHashCode%2A> yönteminin bir uygulamasını kullanarak kendisi için bir karma kod oluşturabilmelidir. Ancak, parametrelerinden biri olarak <xref:System.Collections.IHashCodeProvider> uygulamasını kabul eden bir <xref:System.Collections.Hashtable> Oluşturucusu kullanarak bir <xref:System.Collections.Hashtable> tüm öğeleri için bir karma işlevi de belirtebilirsiniz.  
  
 Bir <xref:System.Collections.Hashtable>bir nesne eklendiğinde, nesnenin karma koduyla eşleşen karma kodla ilişkili demet 'de depolanır. <xref:System.Collections.Hashtable>için bir değer aranmakta olduğunda, bu değer için karma kodu oluşturulur ve bu karma kodla ilişkili demet aranır.  
  
 Örneğin, bir dize için bir karma işlevi dizedeki her bir karakterin ASCII kodlarını alabilir ve bir karma kod oluşturmak için bunları birlikte ekleyebilir. "Picnic" dizesinin "Sepet" dizesinin karma kodundan farklı bir karma kodu olmalıdır; Bu nedenle, "Picnic" ve "Sepet" dizeleri farklı demetlere ait olacaktır. Buna karşılık "stthere" ve "destts" aynı karma koda sahip olur ve aynı demet içinde olur.  
  
 <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfları <xref:System.Collections.Hashtable> sınıfıyla aynı işlevselliğe sahiptir. Belirli bir türün <xref:System.Collections.Generic.Dictionary%602> (<xref:System.Object>dışında), değer türleri için <xref:System.Collections.Hashtable> göre daha iyi performans sağlar. Bunun nedeni, <xref:System.Collections.Hashtable> öğelerinin <xref:System.Object>türünde olması. Bu nedenle, kutulama ve kutudan çıkarma genellikle bir değer türünü depoladığınızda veya aldığınızda oluşur. Birden çok iş parçacığı koleksiyona aynı anda erişildiğinde <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfı kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
