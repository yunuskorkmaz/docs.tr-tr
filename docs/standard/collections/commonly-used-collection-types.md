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
ms.openlocfilehash: 1004a2f9a0594d9150d147dec1e16b56205e0d13
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711408"
---
# <a name="commonly-used-collection-types"></a>Çok Kullanılan Koleksiyon Türleri
Koleksiyon türleri, karma tablolar, kuyruklar, yığınlar, paketler, sözlükler ve listeler gibi veri koleksiyonlarının ortak çeşitleridir.  
  
 Koleksiyonlar <xref:System.Collections.ICollection> arabirimine, <xref:System.Collections.IList> arabirimine, <xref:System.Collections.IDictionary> arabirimine veya onların genel karşılıklarına dayalıdır. <xref:System.Collections.IList> arabirimi ve <xref:System.Collections.IDictionary> arabirimi her ikisi de <xref:System.Collections.ICollection> arabiriminden türetilir; Bu nedenle, tüm koleksiyonlar doğrudan veya dolaylı olarak <xref:System.Collections.ICollection> arabirimini temel alır. <xref:System.Collections.IList> arabirimine (<xref:System.Array>, <xref:System.Collections.ArrayList>veya <xref:System.Collections.Generic.List%601>gibi) veya doğrudan <xref:System.Collections.ICollection> arabirimine (<xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> veya <xref:System.Collections.Generic.LinkedList%601>gibi) göre, her öğe yalnızca bir değer içerir. <xref:System.Collections.IDictionary> arabirimine (<xref:System.Collections.Hashtable> ve <xref:System.Collections.SortedList> sınıfları, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedList%602> genel sınıfları) veya <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıflarına göre, her öğe hem bir anahtar hem de bir değer içerir.  <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfı, değerler içine gömülü anahtarlar içeren bir değerler listesi olduğundan ve bu nedenle, bir liste gibi ve bir sözlük gibi davrandığı için benzersizdir.  
  
 Genel Koleksiyonlar, güçlü yazma için en iyi çözümdür. Ancak diliniz, genel türleri desteklemiyorsa, <xref:System.Collections> ad alanı <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>ve <xref:System.Collections.DictionaryBase>gibi temel koleksiyonları içerir ve bu, türü kesin belirlenmiş koleksiyon sınıfları oluşturmak için Genişletilebilir temel sınıflardır. Verimli çok iş parçacıklı koleksiyon erişimi gerektiğinde, <xref:System.Collections.Concurrent> ad alanındaki genel koleksiyonları kullanın.  
  
 Koleksiyonlar, öğelerin nasıl depolandığını, nasıl sıralandıklarını, aramaların nasıl gerçekleştirileceğini ve karşılaştırmaların nasıl yapıldığını bağlı olarak farklılık gösterebilir. <xref:System.Collections.Queue> sınıfı ve <xref:System.Collections.Generic.Queue%601> genel sınıfı ilk ilk çıkar liste sağlar, ancak <xref:System.Collections.Stack> sınıfı ve <xref:System.Collections.Generic.Stack%601> genel sınıfı, en son ilk çıkar listeler sağlar. <xref:System.Collections.SortedList> sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı, <xref:System.Collections.Hashtable> sınıfının ve <xref:System.Collections.Generic.Dictionary%602> genel sınıfının sıralanmış sürümlerini sağlar. Bir <xref:System.Collections.Hashtable> veya <xref:System.Collections.Generic.Dictionary%602> öğeleri yalnızca öğenin anahtarıyla erişilebilir, ancak bir <xref:System.Collections.SortedList> ya da <xref:System.Collections.ObjectModel.KeyedCollection%602> öğelerine ya da öğenin diziniyle erişilebilir. Tüm koleksiyonlardaki dizinler, sıfır tabanlı olmayan dizilere izin veren <xref:System.Array>dışında sıfır tabanlıdır.  
  
 LINQ to Objects özelliği, nesne türü <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>uyguladığı sürece, bellek içi nesnelere erişmek için LINQ sorgularını kullanmanıza olanak sağlar. LINQ sorguları verilere erişim için ortak bir model sağlar; genellikle standart `foreach` döngülerinden daha kısa ve okunabilir; ve filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)|.NET Framework, yığınlar, kuyruklar, listeler, diziler ve sözlükler dahil çeşitli koleksiyon türlerini açıklar.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Listeler ve kümeler için sıralama işlevselliği sağlayan sınıfları açıklar.|  
|[Genel Türler](../../../docs/standard/generics/index.md)|.NET Framework tarafından belirtilen genel koleksiyonlar, temsilciler ve arabirimler dahil olmak üzere genel türler özelliğini açıklar. , Visual Basic ve görsel C# C++için özellik belgelerinin ve yansıma gibi teknolojilerin desteklenmesi için bağlantılar sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
