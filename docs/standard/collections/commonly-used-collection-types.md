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
ms.openlocfilehash: 47e54bb76c65dd5acc8ce1921ee385a5cb55cf95
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287997"
---
# <a name="commonly-used-collection-types"></a>Çok Kullanılan Koleksiyon Türleri
Koleksiyon türleri, karma tablolar, kuyruklar, yığınlar, paketler, sözlükler ve listeler gibi veri koleksiyonlarının ortak çeşitleridir.  
  
 Koleksiyonlar <xref:System.Collections.ICollection> arabirim, <xref:System.Collections.IList> arabirim, <xref:System.Collections.IDictionary> arabirim veya genel karşılıklarına dayalıdır. Arabirim <xref:System.Collections.IList> ve <xref:System.Collections.IDictionary> arabirim her ikisi de <xref:System.Collections.ICollection> arabiriminden türetilir; bu nedenle, tüm koleksiyonlar <xref:System.Collections.ICollection> doğrudan veya dolaylı olarak arayüze dayalıdır. <xref:System.Collections.IList>Arayüzde (örneğin,, <xref:System.Array> <xref:System.Collections.ArrayList> veya <xref:System.Collections.Generic.List%601> ) veya doğrudan arayüzde (örneğin,,, veya) temel alan koleksiyonlarda <xref:System.Collections.ICollection> <xref:System.Collections.Queue> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack> <xref:System.Collections.Concurrent.ConcurrentStack%601> <xref:System.Collections.Generic.LinkedList%601> , her öğe yalnızca bir değer içerir. <xref:System.Collections.IDictionary>Arayüze ( <xref:System.Collections.Hashtable> ve <xref:System.Collections.SortedList> sınıfları, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Generic.SortedList%602> Genel sınıfları gibi) veya sınıfları temel alan koleksiyonlar içinde <xref:System.Collections.Concurrent.ConcurrentDictionary%602> her öğe hem bir anahtar hem de bir değer içerir.  <xref:System.Collections.ObjectModel.KeyedCollection%602>Sınıf, değerler içine gömülü anahtarlar içeren bir değer listesi olduğundan ve bu nedenle, bir liste ve sözlük gibi davranır.  
  
 Genel Koleksiyonlar, güçlü yazma için en iyi çözümdür. Ancak, diliniz genel türleri desteklemiyorsa, <xref:System.Collections> ad alanı, ve gibi temel koleksiyonları içerir ve bu, <xref:System.Collections.CollectionBase> <xref:System.Collections.ReadOnlyCollectionBase> <xref:System.Collections.DictionaryBase> türü kesin belirlenmiş koleksiyon sınıfları oluşturmak için Genişletilebilir temel sınıflardır. Verimli çok iş parçacıklı koleksiyon erişimi gerektiğinde, ad alanındaki genel koleksiyonları kullanın <xref:System.Collections.Concurrent> .  
  
 Koleksiyonlar, öğelerin nasıl depolandığını, nasıl sıralandıklarını, aramaların nasıl gerçekleştirileceğini ve karşılaştırmaların nasıl yapıldığını bağlı olarak farklılık gösterebilir. <xref:System.Collections.Queue>Sınıfı ve <xref:System.Collections.Generic.Queue%601> Genel sınıfı ilk ilk çıkar liste sağlar, ancak <xref:System.Collections.Stack> sınıfı ve <xref:System.Collections.Generic.Stack%601> Genel sınıfı en son ilk çıkar listeler sağlar. <xref:System.Collections.SortedList>Sınıfı ve <xref:System.Collections.Generic.SortedList%602> Genel sınıfı, sınıfının sıralanmış sürümlerini <xref:System.Collections.Hashtable> ve <xref:System.Collections.Generic.Dictionary%602> genel sınıfını sağlar. A veya a öğelerine <xref:System.Collections.Hashtable> <xref:System.Collections.Generic.Dictionary%602> yalnızca öğenin anahtarıyla erişilebilir, ancak bir veya a öğelerinden biri, <xref:System.Collections.SortedList> <xref:System.Collections.ObjectModel.KeyedCollection%602> anahtar veya öğenin dizini tarafından erişilebilir. Tüm koleksiyonlardaki dizinler, sıfır tabanlı <xref:System.Array> olmayan dizilere izin veren, hariç sıfır tabanlıdır.  
  
 LINQ to Objects özelliği, nesne türü veya uyguladığı sürece, bellek içi nesnelere erişmek için LINQ sorgularını kullanmanıza olanak sağlar <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> . LINQ sorguları verilere erişim için ortak bir model sağlar; genellikle standart döngülerden daha kısa ve okunabilir `foreach` ; filtreleme, sıralama ve gruplama özellikleri sağlar. LINQ sorguları da performansı iyileştirebilir. Daha fazla bilgi için bkz. [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)ve [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Koleksiyonlar ve veri yapıları](index.md)|.NET Framework, yığınlar, kuyruklar, listeler, diziler ve sözlükler dahil çeşitli koleksiyon türlerini açıklar.|  
|[Hashtable ve Sözlük Koleksiyon Türleri](hashtable-and-dictionary-collection-types.md)|Genel ve genel olmayan karma tabanlı sözlük türlerinin özelliklerini açıklar.|  
|[Sıralanmış koleksiyon türleri](sorted-collection-types.md)|Listeler ve kümeler için sıralama işlevselliği sağlayan sınıfları açıklar.|  
|[Genel Türler](../generics/index.md)|.NET Framework tarafından belirtilen genel koleksiyonlar, temsilciler ve arabirimler dahil olmak üzere genel türler özelliğini açıklar. C#, Visual Basic ve Visual C++ için özellik belgelerinin bağlantılarını ve yansıma gibi destekleyici teknolojileri sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
