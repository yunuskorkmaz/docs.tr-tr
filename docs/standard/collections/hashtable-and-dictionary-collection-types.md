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
ms.openlocfilehash: b228f5db16ba01969b77d601becfb94ac0506d1e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287971"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Karma Tablo ve Sözlük Koleksiyon Türleri
<xref:System.Collections.Hashtable?displayProperty=nameWithType>Sınıfı ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Genel sınıfları <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimini uygular. <xref:System.Collections.Generic.Dictionary%602>Genel sınıf Ayrıca <xref:System.Collections.Generic.IDictionary%602> genel arabirimini de uygular. Bu nedenle, bu koleksiyonlardaki her öğe bir anahtar ve değer çiftidir.  
  
 Bir <xref:System.Collections.Hashtable> nesne, koleksiyonun öğelerini içeren demetlerden oluşur. Bir demet, içindeki öğelerin bir sanal alt grubudur ve <xref:System.Collections.Hashtable> Bu, arama ve alma işlemlerini birçok koleksiyondan daha kolay ve hızlı bir şekilde gerçekleştirir. Her demet, bir karma işlev kullanılarak oluşturulan ve öğesinin anahtarını temel alan bir karma kodla ilişkilendirilir.  
  
 Genel <xref:System.Collections.Generic.HashSet%601> sınıf, benzersiz öğeleri kapsayan sıralanmamış bir koleksiyondur.  
  
 Karma işlevi, bir anahtara dayalı sayısal bir karma kodu döndüren algoritmadır. Anahtar, depolanan nesnenin bazı özelliğinin değeridir. Karma işlev her zaman aynı anahtar için aynı karma kodu döndürmelidir. Bir karma işlevin iki farklı anahtar için aynı karma kodu oluşturması mümkündür, ancak her benzersiz anahtar için benzersiz bir karma kod üreten bir karma işlev, karma tablodaki öğeleri alırken daha iyi performans elde edilir.  
  
 Bir öğesi olarak kullanılan her bir nesne <xref:System.Collections.Hashtable> , yönteminin bir uygulamasını kullanarak kendisi için bir karma kod oluşturabilmelidir <xref:System.Object.GetHashCode%2A> . Ancak, <xref:System.Collections.Hashtable> <xref:System.Collections.Hashtable> parametrelerinden biri olarak bir uygulamayı kabul eden bir oluşturucuyu kullanarak içindeki tüm öğeleri için bir karma işlevi de belirtebilirsiniz <xref:System.Collections.IHashCodeProvider> .  
  
 Bir nesne öğesine eklendiğinde <xref:System.Collections.Hashtable> , nesnenin karma koduyla eşleşen karma kodla ilişkili demet 'de depolanır. İçinde için bir değer aranmakta olduğunda <xref:System.Collections.Hashtable> , bu değer için karma kodu oluşturulur ve bu karma kodla ilişkili demet aranır.  
  
 Örneğin, bir dize için bir karma işlevi dizedeki her bir karakterin ASCII kodlarını alabilir ve bir karma kod oluşturmak için bunları birlikte ekleyebilir. "Picnic" dizesinin "Sepet" dizesinin karma kodundan farklı bir karma kodu olmalıdır; Bu nedenle, "Picnic" ve "Sepet" dizeleri farklı demetlere ait olacaktır. Buna karşılık "stthere" ve "destts" aynı karma koda sahip olur ve aynı demet içinde olur.  
  
 <xref:System.Collections.Generic.Dictionary%602>Ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfları sınıfıyla aynı işlevselliğe sahiptir <xref:System.Collections.Hashtable> . <xref:System.Collections.Generic.Dictionary%602>Belirli bir türün (dışındaki <xref:System.Object> ) bir değeri, bir değer türü için daha iyi performans sağlar <xref:System.Collections.Hashtable> . Bunun nedeni, öğesinin <xref:System.Collections.Hashtable> türünde olması <xref:System.Object> , bu nedenle kutulama ve kutudan çıkarma genellikle bir değer türünü depoladığınızda veya alırken meydana gelir. <xref:System.Collections.Concurrent.ConcurrentDictionary%602>Birden çok iş parçacığı koleksiyona aynı anda erişildiğinde sınıf kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Yaygın olarak kullanılan koleksiyon türleri](commonly-used-collection-types.md)
