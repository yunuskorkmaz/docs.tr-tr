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
ms.openlocfilehash: 77740f86265db86c998af25e6e9ed4c20a7014e6
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835752"
---
# <a name="commonly-used-collection-types"></a>Çok Kullanılan Koleksiyon Türleri
Koleksiyon, karma tabloları, kuyrukları, yığınları, paketleri, sözlük ve listeler gibi veri koleksiyonlarının ortak çeşitlemeleri türleridir.  
  
 Koleksiyonları temel <xref:System.Collections.ICollection> arabirimi <xref:System.Collections.IList> arabirimi <xref:System.Collections.IDictionary> arabirimi ya da genel karşılıkları. <xref:System.Collections.IList> Arabirimi ve <xref:System.Collections.IDictionary> arabirimi hem de türetilir <xref:System.Collections.ICollection> arabirim; bu nedenle, tüm koleksiyonlar dayalı <xref:System.Collections.ICollection> doğrudan veya dolaylı olarak arabirim. Temel koleksiyonlardaki <xref:System.Collections.IList> arabirimi (gibi <xref:System.Array>, <xref:System.Collections.ArrayList>, veya <xref:System.Collections.Generic.List%601>) veya doğrudan üzerinde <xref:System.Collections.ICollection> arabirimi (gibi <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> veya <xref:System.Collections.Generic.LinkedList%601>), her öğenin yalnızca bir değer içeriyor. Temel koleksiyonlardaki <xref:System.Collections.IDictionary> arabirimi (gibi <xref:System.Collections.Hashtable> ve <xref:System.Collections.SortedList> sınıfları <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedList%602> Genel sınıflar), veya <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfları, her öğe hem anahtar hem de bir değer içerir.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Sınıftır benzersiz anahtarları olan değerlerin bir listesini katıştırılmış içindeki değerleri ve bu nedenle, bir liste gibi ve sözlük gibi davranır olduğundan.  
  
 Genel koleksiyonlar, güçlü yazım, yazım için en iyi çözümdür. Ancak, genel türler, dilinizi desteklemiyorsa <xref:System.Collections> ad alanı içeren temel koleksiyonlar gibi <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, ve <xref:System.Collections.DictionaryBase>, olan koleksiyon sınıfları oluşturmak için genişletilmiş soyut taban sınıfları olduğu kesin türü belirtilmiş. Verimli çok iş parçacıklı koleksiyon erişim gerekli olduğunda genel koleksiyonları kullanın <xref:System.Collections.Concurrent> ad alanı.  
  
 Öğeleri nasıl depolandığını, nasıl sıralanacağını, aramalar nasıl gerçekleştirilir ve nasıl karşılaştırmalarının bağlı olarak koleksiyonları değişebilir. <xref:System.Collections.Queue> Sınıfı ve <xref:System.Collections.Generic.Queue%601> ilk-giren ilk çıkar listeler, genel bir sınıf sağlar ancak <xref:System.Collections.Stack> sınıfı ve <xref:System.Collections.Generic.Stack%601> son giren ilk-çıkar listeleri genel bir sınıf sağlar. <xref:System.Collections.SortedList> Sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel sınıf sağlamak sıralanmış sürümleri <xref:System.Collections.Hashtable> sınıfı ve <xref:System.Collections.Generic.Dictionary%602> genel bir sınıf. Öğeleri bir <xref:System.Collections.Hashtable> veya <xref:System.Collections.Generic.Dictionary%602> yalnızca öğe, ancak öğelerinin anahtar tarafından erişilebilir bir <xref:System.Collections.SortedList> veya <xref:System.Collections.ObjectModel.KeyedCollection%602> anahtarı veya öğenin dizinini tarafından erişilemiyor. Sıfır dışındaki tüm koleksiyonlar dizinlerde <xref:System.Array>, sıfır olmayan bir dizi sağlar.  
  
 LINQ to Objects özelliği nesne türünün uyguladığı sürece bellek içi nesnelere erişmek için LINQ sorguları kullanmanıza olanak tanır <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. LINQ sorguları, verilere erişmek için yaygın bir düzen sağlar; genellikle daha kısa süren ve okunabilir standart olan `foreach` döngü; ve filtreleme, sıralama ve Gruplama yetenekler sağlar. LINQ sorguları da performansı artırır. Daha fazla bilgi için [LINQ to Objects'in (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects'in (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), ve [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)|Bulunan çeşitli koleksiyon türlerini açıklar [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]yığınlar, kuyruklar, listeler, diziler ve sözlükleri dahil olmak üzere.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Karma tabanlı sözlük jenerik ve jenerik olmayan türleri özelliklerini açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Listeler ve kümeleri için sıralama işlevselliği sağlayan sınıflar açıklanmaktadır.|  
|[Genel Türler](../../../docs/standard/generics/index.md)|Genel koleksiyonlar, temsilciler ve arabirimler tarafından sağlanan dahil olmak üzere genel türler özelliğini açıklar [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Özellik belgelerine bağlantılar sağlar C#, Visual Basic ve Visual C++ ve reflection gibi destek teknolojileri için.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
