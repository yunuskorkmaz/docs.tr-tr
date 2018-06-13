---
title: Çok Kullanılan Koleksiyon Türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- objects [.NET Framework], grouping in collections
- generics [.NET Framework], collections
- IList interface, grouping data in collections
- IDictionary interface, grouping data in collections
- grouping data in collections, generic collection types
- Collections classes
- generic collections
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e1fd970c0aab064fbc7da76d3c4f32f572aca21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571257"
---
# <a name="commonly-used-collection-types"></a>Çok Kullanılan Koleksiyon Türleri
Koleksiyon, karma tabloları, kuyrukları, yığınları, paketler, sözlükler ve listeler gibi veri koleksiyonları ortak varyasyonları türleridir.  
  
 Koleksiyonları temel <xref:System.Collections.ICollection> arabirimi, <xref:System.Collections.IList> arabirimi, <xref:System.Collections.IDictionary> arabirimi ya da genel dekiler. <xref:System.Collections.IList> Arabirimi ve <xref:System.Collections.IDictionary> arabirimi hem de türetilir <xref:System.Collections.ICollection> arabirim; bu nedenle, tüm koleksiyonlar dayalı <xref:System.Collections.ICollection> doğrudan veya dolaylı olarak arabirim. Temel koleksiyonlarda <xref:System.Collections.IList> arabirimi (gibi <xref:System.Array>, <xref:System.Collections.ArrayList>, veya <xref:System.Collections.Generic.List%601>) veya doğrudan üzerinde <xref:System.Collections.ICollection> arabirimi (gibi <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> veya <xref:System.Collections.Generic.LinkedList%601>), her öğe yalnızca bir değer içeriyor. Temel koleksiyonlarda <xref:System.Collections.IDictionary> arabirimi (gibi <xref:System.Collections.Hashtable> ve <xref:System.Collections.SortedList> sınıfları <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedList%602> Genel sınıflar), veya <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfları, her bir öğe içeren bir anahtarı ve değeri.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Sınıftır benzersiz anahtarlara sahip bir değer listesi katıştırılmış içindeki değerleri ve bu nedenle, bir listesi gibi ve bir sözlük gibi davranır olduğundan.  
  
 Genel koleksiyonlar güçlü yazmak için en iyi çözümdür. Ancak, dilinizi genel türler, desteklemiyorsa <xref:System.Collections> ad alanı içeren temel koleksiyonları gibi <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, ve <xref:System.Collections.DictionaryBase>, olan koleksiyon sınıfları oluşturmak için genişletilmiş soyut taban sınıfları olduğu kesin türü belirtilmiş. Verimli çok iş parçacıklı koleksiyonu erişim gerekli olduğunda, genel koleksiyonlarda kullanmak <xref:System.Collections.Concurrent> ad alanı.  
  
 Koleksiyonları öğeleri nasıl depolandığını sonra nasıl sıralanacağını aramalar nasıl gerçekleştirilir ve karşılaştırmaları nasıl yapılır bağlı olarak değişebilir. <xref:System.Collections.Queue> Sınıfı ve <xref:System.Collections.Generic.Queue%601> genel sınıfı sağlayan ilk olarak ilk çıkar listeleri sırada <xref:System.Collections.Stack> sınıfı ve <xref:System.Collections.Generic.Stack%601> genel sınıfı son-giren ilk çıkar listeler sağlayın. <xref:System.Collections.SortedList> Sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı sağlamak sıralanmış sürümlerini <xref:System.Collections.Hashtable> sınıfı ve <xref:System.Collections.Generic.Dictionary%602> genel bir sınıf. Öğelerini bir <xref:System.Collections.Hashtable> veya <xref:System.Collections.Generic.Dictionary%602> yalnızca anahtarı öğesi ancak öğelerini tarafından erişilebilen bir <xref:System.Collections.SortedList> veya <xref:System.Collections.ObjectModel.KeyedCollection%602> anahtar veya öğenin dizini tarafından erişilebilir. Sıfır dışındaki tüm koleksiyonlar dizinlerde <xref:System.Array>, sıfır tabanlı olmayan diziler izin verir.  
  
 LINQ to nesneleri özelliği nesne türü uygulayan sürece bellek içi nesnelere erişmek için LINQ sorgularını kullanmanıza olanak tanır <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. LINQ sorguları verilerine erişmek için genel bir desen sağlar; genellikle daha kısa ve standart okunabilir olan `foreach` döngü; ve filtreleme, sıralama ve yetenekleri gruplandırma sağlar. LINQ sorguları da performansı artırabilir. Daha fazla bilgi için bkz: [nesnelere LINQ](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) ve [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)|Kullanılabilen çeşitli koleksiyon türleri açıklanmaktadır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]yığınları, kuyruklar, listeler, dizileri ve sözlükleri dahil olmak üzere.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve nongeneric karma tabanlı sözlük türleri özelliklerini açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Listeler ve ayarlar için sıralama işlevselliği sağlayan sınıflar açıklanmaktadır.|  
|[Genel Türler](../../../docs/standard/generics/index.md)|Genel koleksiyonlar, temsilciler ve tarafından sağlanan arabirimler de dahil olmak üzere genel türler özelliği açıklanmakta [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. C#, Visual Basic ve Visual C++ özellik belgelerine ve yansıma gibi teknolojileri destekleyen için bağlantılar sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
