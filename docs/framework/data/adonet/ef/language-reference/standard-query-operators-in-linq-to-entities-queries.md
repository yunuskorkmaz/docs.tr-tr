---
title: LINQ to Entities Sorgularında Standart Sorgu İşleçleri
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 23aea5fe1bcee8d043a7f093790cb45a1edc4aae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173646"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>LINQ to Entities Sorgularında Standart Sorgu İşleçleri

Bir sorguda, veri kaynağından almak istediğiniz bilgileri belirtirsiniz. Bir sorgu, döndürülmeden önce bu bilgilerin nasıl sıralanacağını, gruplanacağını ve şekillendirilmiş olduğunu da belirtebilir. LINQ, bir sorguda kullanabileceğiniz standart sorgu yöntemleri kümesi sağlar. Bu yöntemlerin çoğu diziler üzerinde çalışır; Bu bağlamda, bir sıra türü <xref:System.Collections.Generic.IEnumerable%601> arabirimini veya arabirimini uygulayan bir nesnedir <xref:System.Linq.IQueryable%601> . Standart sorgu işleçleri sorgu işlevselliği filtreleme, projeksiyon, toplama, sıralama, gruplama, sayfalama ve daha fazlasını içerir. Daha sık kullanılan standart sorgu işleçlerinden bazılarının sorgu ifadesi söz dizimi kullanılarak çağrılabilmesi için adanmış anahtar sözcük sözdizimi vardır. Sorgu ifadesi, bir sorguyu Yöntem tabanlı eşinden daha hızlı bir şekilde ifade etmenin farklı, daha okunabilir bir yoludur. Sorgu ifadesi yan tümceleri, derleme zamanında sorgu yöntemlerine yapılan çağrılara çevrilir. Denk sorgu ifadesi yan tümcelerine sahip standart sorgu işleçleri listesi için bkz. [Standart sorgu Işleçlerine genel bakış](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 LINQ to Entities sorgularda standart sorgu işleçlerinin hepsi desteklenmez. Daha fazla bilgi için bkz. [desteklenen ve desteklenmeyen LINQ yöntemleri (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md). Bu konu, LINQ to Entities özgü standart sorgu işleçleri hakkında bilgi sağlar. LINQ to Entities sorgularındaki bilinen sorunlar hakkında daha fazla bilgi için, bkz. [LINQ to Entities bilinen sorunlar ve konular](known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Yansıtma ve filtreleme yöntemleri  

 *Projeksiyon* , bir sonuç kümesinin öğelerini istediğiniz biçimde dönüştürmeyi ifade eder. Örneğin, sonuç kümesindeki her bir nesneden ihtiyacınız olan özelliklerin bir alt kümesini projeye aktarabilirsiniz, bir özelliği proje üzerinde veya matematiksel bir hesaplama gerçekleştirebilir ya da tüm nesneyi sonuç kümesinden bir proje üzerinde oluşturabilirsiniz. Projeksiyon yöntemleri `Select` ve ' dir `SelectMany` .  
  
 *Filtreleme* , sonuç kümesini yalnızca belirtilen bir koşulla eşleşen öğeleri içerecek şekilde kısıtlama işlemini ifade eder. Filtreleme yöntemi `Where` .  
  
 Projeksiyon ve filtreleme yöntemlerinin çoğu aşırı yüklemesi, konumsal bir bağımsız değişkeni kabul eden dışında LINQ to Entities desteklenir.  
  
## <a name="join-methods"></a>JOIN yöntemleri  

 Birleştirme, birbirleriyle gezinebilir bir ilişkisi olmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir. İki veri kaynağını birleştirmek, bir veri kaynağındaki nesnelerin ortak bir özniteliği veya özelliği paylaşan diğer veri kaynağındaki nesnelerle ilişkilendirilmesi. JOIN yöntemleri `Join` ve ' dir `GroupJoin` .  
  
 JOIN yöntemlerinin çoğu aşırı yüklemesi, kullanan bir istisna ile desteklenir <xref:System.Collections.Generic.IEqualityComparer%601> . Bunun nedeni, karşılaştırıcının veri kaynağına çevrilemediğinden oluşur.  
  
## <a name="set-methods"></a>Yöntemler Ayarlama  

 LINQ içindeki işlemleri ayarlama, sonuç kümelerinin aynı veya başka bir koleksiyondaki (veya ayarlanan) eşdeğer öğelerin yokluğunda bulunduğu sorgu işlemleridir. Ayarlama yöntemleri,,,,, `All` `Any` `Concat` `Contains` `DefaultIfEmpty` `Distinct` , `EqualAll` , `Except` , `Intersect` , ve `Union` .  
  
 Küme yöntemlerinin çoğu aşırı yüklemesi LINQ to Entities desteklenir, ancak LINQ to Objects kıyasla davranışlarda bazı farklılıklar vardır. Bununla birlikte, <xref:System.Collections.Generic.IEqualityComparer%601> karşılaştırıcı veri kaynağına çevrilemediğinden, ' ı kullanan ayarlama yöntemleri desteklenmez.  
  
## <a name="ordering-methods"></a>Sıralama yöntemleri  

 Sıralama veya sıralama, bir veya daha fazla özniteliğe göre bir sonuç kümesinin öğelerini sıralamayı ifade eder. Birden fazla sıralama ölçütü belirterek, bir grup içindeki özellikleri kesebilirsiniz.  
  
 Sıralama yöntemlerinin çoğu aşırı yüklemesi, kullanan olanlar dışında desteklenir <xref:System.Collections.Generic.IComparer%601> . Bunun nedeni, karşılaştırıcının veri kaynağına çevrilemediğinden oluşur. Sıralama yöntemleri,,, ve ' dir `OrderBy` `OrderByDescending` `ThenBy` `ThenByDescending` `Reverse` .  
  
 Sorgu veri kaynağında yürütüldüğü için sıralama davranışı CLR 'de yürütülen sorgulardan farklı olabilir. Bunun nedeni, büyük/küçük harf sıralaması, Kanji sıralaması ve null sıralaması gibi sıralama seçeneklerinin veri kaynağında ayarlanabileceğinden kaynaklanır. Veri kaynağına bağlı olarak, bu sıralama seçenekleri CLR 'den farklı sonuçlar üretebilirler.  
  
 Birden fazla sıralama işleminde aynı anahtar seçiciyi belirtirseniz, yinelenen bir sıralama üretilecektir. Bu geçerli değil ve bir özel durum oluşturulacak.  
  
## <a name="grouping-methods"></a>Gruplandırma yöntemleri  

 Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verilerin gruplara yerleştirilmesi anlamına gelir. Gruplandırma yöntemi `GroupBy` .  
  
 Gruplandırma yöntemlerinin çoğu aşırı yüklemesi desteklenir, ancak kullanan olanlar hariç <xref:System.Collections.Generic.IEqualityComparer%601> . Bunun nedeni, karşılaştırıcının veri kaynağına çevrilemediğinden oluşur.  
  
 Gruplandırma yöntemleri, anahtar seçici için ayrı bir alt sorgu kullanılarak veri kaynağıyla eşleştirilir. Anahtar Seçici karşılaştırma alt sorgusu, değerleri karşılaştırma ile ilgili sorunlar da dahil olmak üzere veri kaynağının semantiğini kullanarak yürütülür `null` .  
  
## <a name="aggregate-methods"></a>Toplama yöntemleri  

 Toplama işlemi, bir değerler koleksiyonundan tek bir değeri hesaplar. Örneğin, bir aylık günlük sıcaklık değeri olan ortalama günlük sıcaklık, bir toplama işlemidir. Toplama yöntemleri,,,,, ve ' dir `Aggregate` `Average` `Count` `LongCount` `Max` `Min` `Sum` .  
  
 Toplam yöntemlerin çoğu aşırı yüklemesi desteklenir. Null değerlerle ilgili davranış için, toplama yöntemleri veri kaynağı semantiğini kullanır. Null değerler dahil edildiğinde toplama yöntemlerinin davranışı, kullanılan arka uç veri kaynağına bağlı olarak farklı olabilir. Veri kaynağının semantiğini kullanan toplama yöntemi davranışı Ayrıca CLR metotlarından beklenden farklı olabilir. Örneğin, SQL Server yöntemi için varsayılan davranış, `Sum` özel durum oluşturmak yerine herhangi bir null değeri yok saymaya yöneliktir.  
  
 İşlevin taşması gibi toplamadan kaynaklanan tüm özel durumlar, sorgu sonuçlarının atımı olması `Sum` sırasında veri kaynağı özel durumları veya Entity Framework özel durumlar olarak oluşturulur.  
  
 Veya gibi bir sıra üzerinden hesaplamayı içeren yöntemler için, `Sum` `Average` sunucuda fiili hesaplama gerçekleştirilir. Sonuç olarak, sunucuda tür dönüştürmeleri ve duyarlık kaybı meydana gelebilir ve sonuçlar CLR semantiği kullanılarak beklenilenden farklı olabilir.  
  
 Null/null olmayan değerler için toplama yöntemlerinin varsayılan davranışı aşağıdaki tabloda gösterilmiştir:  
  
|Yöntem|Veri yok|Tüm null değerler|Bazı null değerler|Null değer yok|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Null döndürür.|Null döndürür.|Bir dizideki null olmayan değerlerin ortalamasını döndürür.|Bir sayısal değer dizisinin ortalamasını hesaplar.|  
|`Count`|0 döndürür|Dizideki null değer sayısını döndürür.|Dizideki null ve null olmayan değerlerin sayısını döndürür.|Dizideki öğe sayısını döndürür.|  
|`Max`|Null döndürür.|Null döndürür.|Bir dizideki null olmayan en büyük değeri döndürür.|Bir dizideki en büyük değeri döndürür.|  
|`Min`|Null döndürür.|Null döndürür.|Dizide null olmayan en küçük değeri döndürür.|Sıradaki En küçük değeri döndürür.|  
|`Sum`|Null döndürür.|Null döndürür.|Dizideki null olmayan değerin toplamını döndürür.|Bir sayısal değer dizisinin toplamını hesaplar.|  
  
## <a name="type-methods"></a>Tür yöntemleri  

 Tür dönüştürme ve test ile ilgilenen iki LINQ yöntemi, Entity Framework bağlamında desteklenir. Bu, yalnızca desteklenen türlerin uygun Entity Framework türüyle eşlenen türler olduğu anlamına gelir. Bu türlerin bir listesi için bkz. [kavramsal model türleri (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl). Tür yöntemleri `Convert` ve ' dir `OfType` .  
  
 `OfType` varlık türleri için desteklenir. `Convert` kavramsal model temel türleri için desteklenir.  C# `is` ve `as` yöntemleri de desteklenir.  
  
## <a name="paging-methods"></a>Sayfalama yöntemleri  

 Sayfalama işlemleri bir dizideki tek bir öğeyi veya birden çok öğeyi döndürür. Desteklenen sayfalama yöntemleri,,,, ve ' dir `First` `FirstOrDefault` `Single` `SingleOrDefault` `Skip` `Take` .  
  
 Bir dizi disk belleği yöntemi, işlevleri veri kaynağına eşleyememe ya da veri kaynağındaki örtük küme sırası eksikliği nedeniyle desteklenmez. Varsayılan bir değer döndüren yöntemler kavramsal model temel türleri ve başvuru türleri ile null varsayılanlarla kısıtlıdır. Boş bir dizide yürütülen disk belleği metotları null döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Desteklenen ve Desteklenmeyen LINQ Yöntemleri (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)
- [Standart Sorgu İşleçlerine Genel Bakış](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))
