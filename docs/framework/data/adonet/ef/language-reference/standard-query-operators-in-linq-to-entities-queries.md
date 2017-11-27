---
title: "LINQ to Entities sorgularında standart sorgu işleçleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97782834480e8acb5f66d8da2099089b1c47e093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>LINQ to Entities sorgularında standart sorgu işleçleri
Bir sorgu, veri kaynağından almak istediğiniz bilgileri belirtin. Bir sorgu de nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtebilirsiniz. LINQ sorguda kullanabileceğiniz standart sorgu yöntemler kümesi sağlar. Bu yöntemlerin çoğu sıraları üzerinde çalışır; Bu bağlamda, türü uygulayan bir nesne sırasıdır <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri sorgu işlevi filtreleme, yansıtma, toplama, sıralama, gruplandırma, disk belleği ve daha fazlasını içerir. Bazıları, böylece sorgu ifade sözdizimi kullanılarak çağrılabilir işleçleri anahtar sözcüğü sözdizimi ayrılmış standart sorgu sık kullanılır. Bir sorgu ifadesi, bir sorgu tabanlı yöntemini eşdeğer daha ifade etmek için farklı, daha okunabilir bir yoludur. Sorgu ifadesi yan tümceleri derleme zamanında sorgu yöntemleri çağrıları içine çevrilir. Eşdeğer sorgu ifadesi yan tümceleri sahip standart sorgu işleçleri listesi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Standart sorgu işleçleri tüm desteklenen [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular. Daha fazla bilgi için bkz: [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Bu konuda özgü standart sorgu işleçleri hakkında bilgi verilmektedir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Bilinen sorunlar hakkında daha fazla bilgi için [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları, bkz: [bilinen sorunlar ve dikkat edilmesi gerekenler LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Projeksiyon ve yöntemleri filtreleme  
 *Projeksiyon* bir sonuç kümesi istenen forma öğelerini dönüştürme için başvuruyor. Örneğin, bir alt özellikler kümesini yansıtabilirsiniz sonuç her nesnesinden ayarlamanız, bir özellik proje ve matematiksel bir hesaplama gerçekleştirmek veya nesnenin tamamı sonuç kümesinden yansıtabilirsiniz. Projeksiyon yöntemleri `Select` ve `SelectMany`.  
  
 *Filtreleme* belirtilen bir koşul eşleşen öğeleri içeren sonuç kısıtlama işlemi başvuruyor. Filtreleme yöntemi `Where`.  
  
 Projeksiyon ve yöntemleri filtreleme çoğu aşırı desteklenen [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], konumsal bir bağımsız değişken kabul olanlar dışında.  
  
## <a name="join-methods"></a>Yöntemleri katılma  
 Birleştirme, birbirlerine gezinebilir hiçbir ilişki sahip veri kaynaklarına hedef sorgularda önemli bir işlemdir. İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı bir ortak özniteliği ya da özellik paylaşan diğer veri kaynağı nesneleri ile ilişkidir. Birleşim yöntemleri `Join` ve `GroupJoin`.  
  
 Birleşim yöntemlerinin çoğu aşırı, kullananlar dışında desteklenen bir <xref:System.Collections.Generic.IEqualityComparer%601>. Veri kaynağına karşılaştırıcı çevrilemiyor nedeni budur.  
  
## <a name="set-methods"></a>Yöntemler Ayarlama  
 Ayarlama işlemleri LINQ varlığının veya yokluğunun içinde aynı veya başka bir koleksiyon (ya da kümesi) eşdeğer öğelerinin kendi sonuç kümeleri temel sorgu işlemleri ' dir. Set yöntemleri `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, ve `Union`.  
  
 Set yöntemlerinin çoğu aşırı desteklenen [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], ancak bazı nesnelere LINQ ile karşılaştırıldığında davranış farklılıkları. Ancak, kullanan yöntemleri Ayarla bir <xref:System.Collections.Generic.IEqualityComparer%601> karşılaştırıcı veri kaynağına dönüştürülemeyen çünkü desteklenmez.  
  
## <a name="ordering-methods"></a>Sıralama yöntemleri  
 Sıralama ya da sıralama, bir veya daha fazla özniteliklerini temel alarak bir sonuç kümesi öğeleri sıralama için ifade eder. Birden fazla sıralama ölçütü belirterek, bir grup içindeki TIES bozulabilir.  
  
 Sıralama yöntemlerinin çoğu aşırı, kullananlar dışında desteklenen bir <xref:System.Collections.Generic.IComparer%601>. Veri kaynağına karşılaştırıcı çevrilemiyor nedeni budur. Sıralama yöntemleri `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, ve `Reverse`.  
  
 Sorgu veri kaynağı üzerinde çalıştırıldığı için sıralama davranışı CLR sorgular farklı olabilir. Sıralama, sıralama, kanji durumu gibi seçenekler sıralama ve null sıralama, veri kaynağında ayarlanabilir olmasıdır. Veri kaynağı bağlı olarak bu sıralama seçenekleri CLR daha farklı sonuçlar doğurabilir.  
  
 Birden fazla sıralama işlemi aynı anahtar Seçici belirtirseniz, yinelenen sıralama oluşturulur. Bu geçerli değildir ve bir özel durum.  
  
## <a name="grouping-methods"></a>Gruplandırma yöntemleri  
 Gruplandırma, böylece her grup içindeki öğeleri ortak bir özniteliği paylaşan veri gruplar halinde yerleştirmek için ifade eder. Gruplandırma yöntemi `GroupBy`.  
  
 Gruplandırma yöntemlerinin çoğu aşırı, kullananlar dışında desteklenen bir <xref:System.Collections.Generic.IEqualityComparer%601>. Veri kaynağına karşılaştırıcı çevrilemiyor nedeni budur.  
  
 Gruplandırma yöntemleri için anahtar Seçici ayrı bir alt sorgu kullanarak veri kaynağına eşlenir. Karşılaştırma için ilgili sorunlar da dahil olmak üzere veri kaynağını semantiği kullanarak anahtar Seçici karşılaştırma alt sorgu yürütülür `null` değerleri.  
  
## <a name="aggregate-methods"></a>Toplama yöntemleri  
 Bir toplama işlemi, tek bir değer değerler koleksiyonundan hesaplar. Örneğin, bir ayın eşitleyeceğini günlük sıcaklık değerlerin gelen ortalama günlük sıcaklık hesaplama bir toplama işlemi olur. Birleşik yöntemleri `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, ve `Sum`.  
  
 Birleşik yöntemlerinin çoğu aşırı desteklenir. Null değerler için ilgili davranışı için veri kaynağı semantiğini toplama yöntemlerini kullanın. Null değerler dahil edildiğinde toplama yöntemleri davranışını hangi arka uç veri kaynağı bağlı olarak kullanılıyor, farklı olabilir. Veri kaynağının özelliklerini kullanarak toplama yöntemi davranışı CLR yöntemleri beklenenden farklı olabilir. Örneğin, varsayılan davranışı `Sum` SQL Server'da yöntemi bir özel durum atma yerine null tüm değerleri yok sayın etmektir.  
  
 Taşma gibi toplama kaynaklanan tüm özel durumlar `Sum` işlev, sorgu sonuçları materialization sırasında veri kaynağı özel durumları veya Entity Framework özel durumlar atılır.  
  
 Bir dizisi üzerinde bir hesaplama gibi ilgili bu yöntemleri için `Sum` veya `Average`, gerçek hesaplama sunucu üzerinde gerçekleştirilir. Sonuç olarak, türü dönüşümleri duyarlık kaybına sunucuda oluşabilir ve sonuçları CLR anlamsallarını kullanarak beklenenden farklı olabilir.  
  
 Varsayılan davranışı toplama yöntemleri null/null olmayan değerler için aşağıdaki tabloda gösterilmiştir:  
  
|Yöntem|Veri yok|Tüm null değerler|Bazı null değerler|Hiçbir null değerler|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Null değeri döndürür.|Null değeri döndürür.|Bir dizisinde null olmayan değerlerin ortalamasını döndürür.|Sayısal değerler dizisi ortalamasını hesaplar.|  
|`Count`|0 döndürür|Null değerlerin sayısını sırada döndürür.|Boş ve null olmayan değerlerin sayısını sırada döndürür.|Dizide öğe sayısını döndürür.|  
|`Max`|Null değeri döndürür.|Null değeri döndürür.|En büyük değeri null olmayan bir sırada döndürür.|En büyük değer bir sırada döndürür.|  
|`Min`|Null değeri döndürür.|Null değeri döndürür.|Minimum değeri null olmayan bir sırada döndürür.|En düşük değer bir sırada döndürür.|  
|`Sum`|Null değeri döndürür.|Null değeri döndürür.|Null olmayan değer toplamını bir sırada döndürür.|Sayısal değerler dizisi toplamını hesaplar.|  
  
## <a name="type-methods"></a>Tür yöntemleri  
 Tür dönüştürmeleri ve test etme ile ilgili iki LINQ yöntemleri bağlamında desteklenir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Bu yalnızca desteklenen türler uygun eşleme türleri anlamına gelir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] türü. Bu tür bir listesi için bkz: [kavramsal Model türü (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4). Türü yöntemleri `Convert` ve `OfType`.  
  
 `OfType`varlık türleri için desteklenir. `Convert`kavramsal model ilkel türler için desteklenir.  C# `is` ve `as` yöntemleri de desteklenir.  
  
## <a name="paging-methods"></a>Disk belleği yöntemleri  
 Sayfalandırma işlemleri tek, belirli bir öğe bir dizisini döndürür. Öğe yöntemleri `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take`, `TakeWhile`.  
  
 Disk belleği yöntemleri sayısı, veri kaynağına veya veri kaynağı üzerinde kümelerinin örtük sıralama olmaması işlevleri eşlemek için bağlanamama ya da son desteklenmez. Varsayılan değer döndüren yöntemler kavramsal model temel eleman türleri ve başvuru türleri null varsayılanları ile kısıtlanır. Boş bir dizi üzerinde yürütülen disk belleği yöntemleri null döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
