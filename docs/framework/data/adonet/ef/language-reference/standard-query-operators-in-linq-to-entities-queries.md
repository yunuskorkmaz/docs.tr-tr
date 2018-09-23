---
title: LINQ to Entities sorgularında standart sorgu işleçleri
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 302fa281767fc95e9a9a2192382034b3a519cd92
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586681"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>LINQ to Entities sorgularında standart sorgu işleçleri
Bir sorgu, veri kaynağından almak istediğiniz bilgileri belirtin. Bir sorgu, ayrıca nasıl bu bilgileri sıralanmış, gruplandırılmış ve döndürülmeden önce şeklinde belirtebilirsiniz. LINQ sorguda kullanabileceğiniz standart sorgu yöntem sunmaktadır. Bu yöntemlerin çoğu dizileri üzerinde çalışır; Bu bağlamda türü uygulayan bir nesne dizisidir <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri sorgu işlevselliği, filtreleme, projeksiyon, toplama, sıralama, gruplandırma, sayfalama ve daha fazlasını içerir. Bazıları, standart sorgu işleçleri anahtar sözcüğü sözdizimi adanmış böylece sorgu ifade sözdizimi kullanılarak çağrılabilir sık kullanılır. Bir sorgu ifadesinde, bir sorgu yöntemi tabanlı eşdeğer daha ifade etmek için farklı, daha okunabilir bir yoludur. Sorgu ifadesi tümceleri sorgu yöntemlere yapılan çağrılar derleme zamanında çevrilir. Eşdeğer sorgu ifadesi tümceleri sahip standart sorgu işleçleri bir listesi için bkz. [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Standart sorgu işleçlerinin tüm desteklenen [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular. Daha fazla bilgi için [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Bu konuda özgü standart sorgu işleçleri hakkında bilgi sağlanır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Bilinen sorunlar hakkında daha fazla bilgi için [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgularını görmek [bilinen sorunlar ve dikkat edilmesi gerekenler LINQ to Entities'de](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Öngörü ve yöntemleri filtreleme  
 *Projeksiyon* öğelerini bir sonuç kümesi istenilen biçime dönüştürme için ifade eder. Örneğin, bir özellik alt kümesi yansıtabilirsiniz sonuçta her bir nesneden ayarlamanız gerekir, proje bir özelliği ve bir matematiksel bir hesaplama gerçekleştirmek veya sonuç kümesinin tamamını nesneden yansıtabilirsiniz. Projeksiyon yöntemler `Select` ve `SelectMany`.  
  
 *Filtreleme* sonuç kümesini, belirtilen bir koşulla eşleşen öğeleri içerecek şekilde sınırlama işlemi için ifade eder. Filtreleme yöntemidir `Where`.  
  
 Projeksiyon ve yöntemleri filtreleme çoğu aşırı yüklemeler desteklenir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], konumsal bağımsız değişken kabul eden olanlar hariç.  
  
## <a name="join-methods"></a>Yöntemleri katılın  
 Birleştirme, birbiriyle gezilebilir hiçbir ilişkisi olan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir. Birleşim iki veri kaynaklarının bir veri kaynağı nesneleri bir ortak özniteliği veya özelliği paylaşan diğer veri kaynağı nesneleri ile işbirliğidir. Birleşim yöntemleri `Join` ve `GroupJoin`.  
  
 Birleştirme yöntemlerinin çoğu aşırı yüklemeler, kullananlar hariç desteklenen bir <xref:System.Collections.Generic.IEqualityComparer%601>. Karşılaştırıcı veri kaynağına dönüştürülemeyen olmasıdır.  
  
## <a name="set-methods"></a>Yöntemler Ayarlama  
 LINQ ayarlama işlemleri, varlığı veya yokluğu, eşdeğer öğelerin aynı veya başka bir koleksiyonu (veya kümesi), sonuç kümesi temel sorgu işlemleri ' dir. Set yöntemleri `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, ve `Union`.  
  
 Kümesi yöntemlerinin çoğu aşırı yüklemeler desteklenir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], LINQ to Objects'in karşılaştırıldığında davranışı bazı farklılıklar olsa. Ancak, kullanan yöntemleri Ayarla bir <xref:System.Collections.Generic.IEqualityComparer%601> karşılaştırıcı veri kaynağına dönüştürülemeyen için desteklenmez.  
  
## <a name="ordering-methods"></a>Sıralama yöntemleri  
 Sıralama veya sıralama, bir veya daha fazla özniteliklerine dayalı bir sonuç kümesi öğelerinin sıralama için ifade eder. Birden fazla sıralama ölçütü belirterek, bir grup içindeki TIES bozabilir.  
  
 Sıralama yöntemlerinin çoğu aşırı yüklemeler, kullananlar hariç desteklenen bir <xref:System.Collections.Generic.IComparer%601>. Karşılaştırıcı veri kaynağına dönüştürülemeyen olmasıdır. Sıralama yöntemleri `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, ve `Reverse`.  
  
 Sorgu veri kaynağında yürütülen olduğundan, sıralama davranışını CLR içinde yürütülen sorgular farklılık gösterebilir. Sıralama, sıralama, kanji çalışması gibi seçeneklere sıralama ve null sıralama, veri kaynağında ayarlanabilir olmasıdır. Veri kaynağına bağlı olarak, bu sıralama seçenekleri CLR değerinden farklı sonuçlar üretebilir.  
  
 Birden fazla sıralama işlemi aynı anahtar Seçici'yi belirtirseniz, yinelenen sıralama oluşturulur. Bu geçerli değildir ve bir özel durum oluşturulur.  
  
## <a name="grouping-methods"></a>Gruplandırma yöntemleri  
 Gruplandırma, böylece ortak bir özniteliği her gruptaki öğe paylaştırmak veri gruplar halinde yerleştirmeye ifade eder. Gruplandırma yöntemi `GroupBy`.  
  
 Gruplandırma yöntemlerinin çoğu aşırı yüklemeler, kullananlar hariç desteklenen bir <xref:System.Collections.Generic.IEqualityComparer%601>. Karşılaştırıcı veri kaynağına dönüştürülemeyen olmasıdır.  
  
 Gruplandırma yöntemleri anahtar Seçici için ayrı bir alt sorgu kullanarak veri kaynağına eşlenir. Karşılaştırma için ilgili sorunlar da dahil olmak üzere, veri kaynağının semantiği kullanarak anahtar Seçici karşılaştırma alt sorgu yürütülür `null` değerleri.  
  
## <a name="aggregate-methods"></a>Toplama yöntemi  
 Bir toplama işlemi, değerlerin bir koleksiyonunu tek bir değeri hesaplar. Örneğin, bir aya ait günlük sıcaklık değerleri değerinde gelen günlük ortalama sıcaklık hesaplama bir toplama işlemi olur. Toplama yöntemleridir `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, ve `Sum`.  
  
 Toplama yöntemlerinin çoğu aşırı yüklemeler desteklenir. Null değerler için ilgili davranışı için veri kaynağı semantiğine toplama yöntemleri kullanın. Null değerler söz konusu olduğunda toplama yöntemleri davranışını hangi arka uç veri kaynağına bağlı olarak kullanılıyor, farklı olabilir. Veri kaynağı semantiği kullanarak toplama yöntemi davranışı CLR yöntemlerinden beklenenden farklı olabilir. Örneğin, varsayılan davranışı `Sum` SQL Server'da yöntemi olan bir özel durum oluşturmaktansa null değerleri yok sayılacak.  
  
 Toplama, bir taşmasından gibi kaynaklanan özel durumları `Sum` işlev, sorgu sonuçları materialization sırasında veri kaynağı özel durumları veya Entity Framework özel durumlar olarak atılır.  
  
 Bir hesaplama gibi bir dizisi üzerinde içeren bu yöntemleri için `Sum` veya `Average`, gerçek hesaplaması, sunucu üzerinde gerçekleştirilir. Sonuç olarak, türü dönüşümleri sunucuda kesinlik kaybı oluşabilir ve sonuçları CLR semantiği kullanarak beklenenden farklı olabilir.  
  
 Varsayılan davranışı için null/boş olmayan değerlerinin toplama yöntemleri, aşağıdaki tabloda gösterilmiştir:  
  
|Yöntem|Veri yok|Tüm null değerler|Bazı null değerler|Null değer yok|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Null değeri döndürür.|Null değeri döndürür.|Bir dizideki null olmayan değerlerin ortalamasını döndürür.|Bir dizi sayısal değerlerin ortalamasını hesaplar.|  
|`Count`|0 döndürür|Null değerlerin sayısını, sırasını döndürür.|Dizide null ve boş olmayan değerlerin sayısını döndürür.|Dizideki öğelerin sayısını döndürür.|  
|`Max`|Null değeri döndürür.|Null değeri döndürür.|Bir dizideki en büyük boş olmayan bir değer döndürür.|Bir dizideki en büyük değeri döndürür.|  
|`Min`|Null değeri döndürür.|Null değeri döndürür.|Bir dizisinde en az bir null olmayan değer döndürür.|Bir dizideki en küçük değeri döndürür.|  
|`Sum`|Null değeri döndürür.|Null değeri döndürür.|Bir dizideki null olmayan değer toplamını döndürür.|Bir dizi sayısal değerlerin toplamını hesaplar.|  
  
## <a name="type-methods"></a>Tür yöntemleri  
 Tür dönüştürme ve test ile ilgilenirken siz iki LINQ yöntemleri bağlamında desteklenir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Bu yalnızca desteklenen türleri uygun eşleme türleri olduğu anlamına gelir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] türü. Bu tür bir listesi için bkz. [kavramsal Model türleri (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4). Tür yöntemler `Convert` ve `OfType`.  
  
 `OfType` varlık türleri için desteklenir. `Convert` kavramsal model temel türler için desteklenir.  C# `is` ve `as` yöntemleri de desteklenir.  
  
## <a name="paging-methods"></a>Disk belleği yöntemlerinin  
 Sayfalandırma işlemleri tek bir öğe veya birden çok öğe bir dizisini döndürür. Desteklenen disk belleği yöntemler `First`, `FirstOrDefault`, `Single`, `SingleOrDefault`, `Skip`, ve `Take`.  
  
 Disk belleği yöntemlerinin sayısı, söz konusu veri kaynağına veya olmaması veri kaynağındaki ayarlar örtük sıralama işlevleri eşlemek için ya da son desteklenmez. Varsayılan bir değer döndüren yöntemler kavramsal model ilkel türler ve null Varsayılanları başvuru türleriyle kısıtlanır. Boş bir dizi üzerinde yürütülen disk belleği yöntemlerinin null döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen ve Desteklenmeyen LINQ Yöntemleri (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Standart Sorgu İşleçlerine Genel Bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
