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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711408"
---
# <a name="commonly-used-collection-types"></a>Çok Kullanılan Koleksiyon Türleri
Toplama türleri, karma tablolar, kuyruklar, yığınlar, çantalar, sözlükler ve listeler gibi veri koleksiyonlarının ortak varyasyonlarıdır.  
  
 Koleksiyonlar <xref:System.Collections.ICollection> arabirime, <xref:System.Collections.IList> arabirime, <xref:System.Collections.IDictionary> arabirimine veya genel karşılıklarına dayanır. Arabirim <xref:System.Collections.IList> ve <xref:System.Collections.IDictionary> arabirim hem <xref:System.Collections.ICollection> de arabirimden türetilmiştir; bu nedenle, tüm koleksiyonlar <xref:System.Collections.ICollection> doğrudan veya dolaylı olarak arabirimi temel alır. <xref:System.Collections.IList> Arabirimine <xref:System.Array>(, <xref:System.Collections.ArrayList>, veya) <xref:System.Collections.Generic.List%601>veya doğrudan <xref:System.Collections.ICollection> arabirim <xref:System.Collections.Queue>(, , <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> <xref:System.Collections.Generic.LinkedList%601>, veya ), tüm öğe yalnızca bir değer içerir. <xref:System.Collections.IDictionary> Arabirimi <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList> (sınıflar <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedList%602> genel sınıflar gibi) veya <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıflara dayalı koleksiyonlarda, her öğe hem bir anahtar hem de bir değer içerir.  Sınıf <xref:System.Collections.ObjectModel.KeyedCollection%602> benzersizdir, çünkü değerlere gömülü anahtarları olan değerlerin bir listesidir ve bu nedenle bir liste ve sözlük gibi hareket eder.  
  
 Genel koleksiyonlar güçlü yazma için en iyi çözümdür. Ancak, diliniz genel jenerikleri <xref:System.Collections> desteklemiyorsa, ad alanı <xref:System.Collections.CollectionBase> <xref:System.Collections.ReadOnlyCollectionBase>, <xref:System.Collections.DictionaryBase>, ve , güçlü bir şekilde yazılan koleksiyon sınıfları oluşturmak için genişletilebilen soyut temel sınıflar gibi temel koleksiyonları içerir. Verimli çok iş parçacığı koleksiyonu erişimi gerektiğinde, <xref:System.Collections.Concurrent> ad alanında genel koleksiyonları kullanın.  
  
 Koleksiyonlar, öğelerin nasıl depolanmasına, nasıl sıralandırılın, aramaların nasıl yapıldığına ve karşılaştırmaların nasıl yapıldığına bağlı olarak değişebilir. Sınıf <xref:System.Collections.Queue> ve <xref:System.Collections.Generic.Queue%601> genel sınıf ilk ilk çıkış listelerini sağlarken, <xref:System.Collections.Stack> <xref:System.Collections.Generic.Stack%601> sınıf ve genel sınıf son-ilk çıkış listelerini sağlar. Sınıf <xref:System.Collections.SortedList> ve <xref:System.Collections.Generic.SortedList%602> genel sınıf, sınıfın ve <xref:System.Collections.Hashtable> genel <xref:System.Collections.Generic.Dictionary%602> sınıfın sıralanmış sürümlerini sağlar. A <xref:System.Collections.Hashtable> veya a <xref:System.Collections.Generic.Dictionary%602> öğelerine yalnızca öğenin anahtarıyla erişilebilir, ancak <xref:System.Collections.SortedList> a <xref:System.Collections.ObjectModel.KeyedCollection%602> veya a'nın öğelerine anahtar veya öğenin dizini tarafından erişilebilir. Tüm koleksiyonlarda dizinler sıfır tabanlı <xref:System.Array>olmayan diziler sağlar dışında, sıfır tabanlı.  
  
 LINQ to Objects özelliği, nesne türü uygulandığı sürece bellek içi nesnelere erişmek için <xref:System.Collections.IEnumerable> LINQ sorgularını kullanmanıza olanak tanır. <xref:System.Collections.Generic.IEnumerable%601> LINQ sorguları verilere erişmek için ortak bir desen sağlar; genellikle standart `foreach` döngülere göre daha kısa ve okunabilir; ve filtreleme, sıralama ve gruplandırma özellikleri sağlar. LINQ sorguları da performansı artırabilir. Daha fazla bilgi için [linq to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)konusuna bakın.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)|Yığınlar, kuyruklar, listeler, diziler ve sözlükler dahil olmak üzere .NET Framework'de bulunan çeşitli koleksiyon türlerini tartışır.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|  
|[Sıralanmış Koleksiyon Türleri](../../../docs/standard/collections/sorted-collection-types.md)|Listeler ve kümeler için sıralama işlevi sağlayan sınıfları açıklar.|  
|[Genel Türler](../../../docs/standard/generics/index.md)|.NET Framework tarafından sağlanan genel koleksiyonlar, temsilciler ve arabirimler de dahil olmak üzere genel özellikler özelliğini açıklar. C#, Visual Basic ve Visual C++ için özellik belgelerine ve yansıma gibi destek teknolojilerine bağlantılar sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
