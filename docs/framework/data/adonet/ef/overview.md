---
title: Entity Framework'e Genel Bakış
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 35eb3b1503c8754752662aef0c5101251d60d49c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493548"
---
# <a name="entity-framework-overview"></a>Entity Framework'e Genel Bakış

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ADO.NET'te veri yönelimli yazılım uygulamaları geliştirilmesini destekleyen teknoloji kümesidir. Mimarların ve geliştiricilerin veri odaklı uygulamaları çok farklı olan iki hedeflerini gerçekleştirmek üzere gereken işlerinin. Varlıklar, ilişkileri ve iş sorunlarını çözmeye mantığını modeli gerekir ve veri depolayıp almak için kullanılan bir veri altyapıları ile de çalışmalıdır. Veriler, her biri kendi protokolleri birden çok depolama sistemi kapsayabilir; tek bir depolama sistemi ile çalışma, hatta uygulamalar, verimli ve sürdürülebilir uygulama kod yazmayı gereksinimleriyle karşılaştırarak depolama sisteminin gereksinimlerini dengelemeniz gerekir.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiricilerinin kendilerini temel alınan veritabanı tabloları ve bu verilerin depolandığı sütunları ile uğraşmak zorunda kalmadan etki alanına özgü nesneler ve müşteriler ve Müşteri adresleri gibi özellikler formundaki verilerle çalışmasını sağlayan . İle [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], kullanıcıların verileri ile işlem ve oluşturabilmesi ve veri odaklı uygulamaları geleneksel uygulamalardan daha az kod korumak, geliştiricilerin daha yüksek bir soyutlama düzeyinde çalışabilir. Çünkü [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bir bileşeni olan [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamaları herhangi bir bilgisayar üzerinde çalıştırabilirsiniz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 SP1 sürümünden itibaren yüklenir.

## <a name="give-life-to-models"></a>Modellere hayat verin
 Bir uygulama veya hizmet oluşturmaya uygulamaya veya hizmete üç parçalara ayrılması olduğunda çalışmalarını uzun süredir davam ve ortak tasarım yaklaşımı: etki alanı modeli, mantıksal bir model ve fiziksel bir model. Etki alanı modeli, varlıklar ve ilişkiler modellenmiş bir sistemde tanımlar. Varlıklar ve ilişkiler yabancı anahtar kısıtlamaları olan tablolar halinde bir ilişkisel veritabanına yönelik mantıksal modelin normalleştirir. Fiziksel model bölümleme ve dizin oluşturma gibi depolama ayrıntıları belirterek belirli veri altyapısı özelliklerini ele alır.

 Fiziksel model, performansı artırmak için Veritabanı yöneticileri tarafından iyileştirilmektedir ancak öncelikle uygulama kodu yazan programcılar kendilerini SQL sorguları yazma ve saklı yordam çağırma mantıksal modelin diyagramı ile çalışma için sınırlamak. Etki alanı modelleri ve görüntülenebilir ve bir proje erken aşamalarında ele alınan ve vazgeçtiği sık etkisiz diyagramları olarak bir uygulama gereksinimlerini iletişim kurmak için bir araç olarak genel olarak kullanılır. Birçok geliştirme ekipleri, kavramsal model oluşturma atlayın ve ilişkisel bir veritabanında tabloları, sütunları ve anahtarları belirterek başlayın.

 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Sorgu varlıklar ve ilişkiler etki alanı modeli içinde geliştiricilere etkinleştirerek modellere yaşam sağlar (adlı bir *kavramsal* model içinde [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) bağlı sırasında [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] olanlar çevirmek için veri kaynağına özgü komutlar işlemlere. Bu, belirli bir veri kaynağı sabit kodlu bağımlılıklar uygulamalardan serbest bırakır.

 Code First ile çalışırken, kavramsal model kod depolama modelinde eşleştirilir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nesne türleri ve tanımladığınız ek yapılandırmalar göre kavramsal model çıkarabilir. Eşleme meta veriler, nasıl kod içinde sağladığınız ek yapılandırma bilgilerine ve etki alanı türleri tanımlanan, bir birleşimini temel çalışma zamanı sırasında oluşturulur. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gereken veritabanı meta verileri temel alarak oluşturur. Daha fazla bilgi için [oluşturma ve bir kavramsal Model eşlemesi](https://go.microsoft.com/fwlink/?LinkID=235382).

 Varlık veri modeli araçları ile çalışırken, kavramsal model ve depolama modeli iki arasındaki eşlemeleri XML tabanlı şemalarda ifade ve karşılık gelen adı uzantılarıyla biter dosyalarında tanımlanan:

-   Kavramsal şema tanım dili (CSDL) kavramsal model tanımlar. CSDL olduğu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]'s uygulaması [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md). Dosya uzantısı .csdl ' dir.

-   Store şeması tanım dili (SSDL) mantıksal model olarak da adlandırılan depolama modelinin tanımlar. Dosya uzantısı .ssdl ' dir.

-   Eşleme belirtimi dili (MSL) kavramsal modeller ve depolama arasındaki eşlemeleri tanımlar. Dosya uzantısı .msl ' dir.

Eşlemeleri ve depolama modeli, kavramsal model, veri sınıflarını veya uygulama kodu değişikliğe gerek kalmadan gerektiği gibi değiştirebilirsiniz. Depolama modelleri, sağlayıcıya özgü olduğundan, çeşitli veri kaynakları arasında tutarlı bir kavramsal model ile çalışabilirsiniz.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu model ve eşleme dosyaları oluşturmak için okuma, güncelleştirme ve silme işlemleri varlıklar ve ilişkiler veri kaynağında eşdeğer işlemlerine kavramsal modelde karşı kullanır. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bile veri kaynağındaki saklı yordamlar için kavramsal model eşlemesi varlıkları destekler. Daha fazla bilgi için [CSDL, SSDL ve MSL belirtimleri](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Verilere Map nesneleri
 Nesne yönelimli programlama, veri depolama sistemleri ile etkileşim kurmak için bir sınama oluşturur. Kuruluş sınıflarının sık ilişkisel veritabanı tabloları organizasyonu yansıtır olsa da, uygun kusursuz değil. Birden çok normalleştirilmiş tablo, tek bir sınıfa sık karşılık gelir ve tablolar arasındaki ilişkileri temsil daha sınıflar arasındaki ilişkileri genellikle farklı şekilde temsil edilir. Örneğin, bir satış siparişi için müşteri temsil etmek için bir `Order` sınıf örneğine başvuru içeren bir özellik kullanıyor olabileceğiniz bir `Customer` sınıfı sırada bir `Order` veritabanındaki tabloda satır içeren bir yabancı anahtar sütunu (veya sütun kümesi) birincil bir anahtar değere karşılık gelen bir değer ile `Customer` tablo. A `Customer` sınıf adında bir özelliğe sahip `Orders` örneklerinin bir koleksiyonunu içeren `Order` sınıfı sırada `Customer` tablolu bir veritabanında karşılaştırılabilir sütunu yok. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiricileri bu şekilde ya da daha yakından ilişkileri modellemek için ilişkileri veritabanında gösterildiği temsil etmek için esneklik sağlar.

 Mevcut çözümleri, bir "empedans Uyuşmazlığı", yalnızca nesne yönelimli eşleme sınıfları ve özellikleri ilişkisel tablolar ve sütunlar için sık çağrılması bu boşluğu arasında köprü kuracak şekilde çalıştınız. Geleneksel bu yaklaşımı tercih yerine [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ilişkisel tabloları, sütunları ve mantıksal modellerde yabancı anahtar kısıtlamaları, varlıkları ve ilişkileri kavramsal modellerde eşler. Bu nesneleri tanımlama ve mantıksal model en iyi duruma getirme, daha fazla esneklik sağlar. [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Araçları kavramsal model temelinde genişletilebilir veri sınıfları oluşturun. Bu Geliştirici ekler, ek üyeleriyle genişletilmiş kısmi sınıflar sınıflardır. Varsayılan olarak, varlıklar nesneleri olarak gerçekleştirilmesini ve değişiklikleri kaydetme ve izleme hizmetleri sağlayan temel sınıflar için belirli bir kavramsal model oluşturulan sınıflar türetin. Geliştiriciler, bu sınıflar, varlıkları ve ilişkileri ilişkilendirmeleri ilgili nesneleri olarak çalışmak için kullanabilir. Geliştiriciler için kavramsal bir modeli oluşturulan sınıflar da özelleştirebilirsiniz. Daha fazla bilgi için [nesneleriyle çalışma](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Varlık veri erişimi ve değiştirme

Birden fazla yalnızca başka bir nesne ilişkisel eşleme çözümü [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] erişmek ve varlıklar ve ilişkiler kavramsal modeldeki olarak temsil edilen veri değiştirmek uygulamaları temelde yöneliktir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modelde veri kaynağına özgü sorgulara temsil edilen varlık türleri nesne sorguları çevirmek için model ve eşleme dosyalarını bilgileri kullanır. Sorgu sonuçları nesnelerini gerçekleştirilmiş olan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] yönetir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal bir modeli sorgulama ve nesneleri döndürmek için aşağıdaki yöntemleri sağlar:

-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Kavramsal modelde tanımlı varlık türleri sorgulama için dil ile tümleşik sorgu (LINQ) desteği sağlar. Daha fazla bilgi için [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).

-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Doğrudan kavramsal modeldeki varlıklar ile çalışır ve destekleyen SQL depolamadan bağımsız SQL diyalektiği [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kavramları. [!INCLUDE[esql](../../../../../includes/esql-md.md)] hem nesne sorguları ve EntityClient sağlayıcısı ile yürütülen sorguları ile kullanılır. Daha fazla bilgi için [Entity SQL'e genel bakış](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] EntityClient veri sağlayıcısı içerir. Bu sağlayıcı bağlantıları yönetir, veri kaynağına özgü sorgulara varlık sorguları çevirir ve döndüren bir veri okuyucu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] varlık veri nesnelerini gerçekleştirmek için kullanır. Nesne gerçekleştirme gerekli olmadığı durumlarda, EntityClient sağlayıcısı de gibi standart kullanılabilir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] etkinleştirerek uygulamaları çalıştırmak veri sağlayıcısı [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular ve döndürülen salt okunur veri okuyucu kullanma. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

Aşağıdaki diyagramda gösterilmektedir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] verilerine erişmek için Mimari:

![Entity Framework mimari diyagramı](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Araçları, türetilen bir sınıf üretebilir `System.Data.Objects.ObjectContext` veya `System.Data.Entity.DbContext` , kavramsal modeldeki varlık kapsayıcısı temsil eder. Bu nesne bağlamı kimlikleri, eşzamanlılık ve ilişkileri yönetme ve değişiklikleri izleme olanakları sağlar. Bu sınıf ayrıca kullanıma sunan bir `SaveChanges` ekler, yazar yöntemi güncelleştirir ve veri kaynağına siler. Sorgular gibi komutları geliştirici tarafından belirtilen saklı yordamları veya sistem tarafından otomatik olarak oluşturulan ya da bu değişiklik yapılmaz.

## <a name="data-providers"></a>Veri sağlayıcıları

`EntityClient` Sağlayıcısı genişletir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] verilerini kavramsal varlıklar ve ilişkiler açısından erişerek sağlayıcı modeli. Kullanan sorguları yürüten [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] sağlayan temel alınan sorgu dili sağlar `EntityClient` veritabanıyla iletişim kurmak için. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bir güncel SqlClient verileri kurallı komut ağaçlarını destekleyen sağlayıcı içerir. Daha fazla bilgi için [Entity Framework için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Varlık veri modeli araçları

İle birlikte [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] çalışma zamanı, Visual Studio, eşleme ve modelleme araçları içerir. Daha fazla bilgi için [modelleme ve eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Hakkında daha fazla bilgi edinmek için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bkz:

[Başlarken](../../../../../docs/framework/data/adonet/ef/getting-started.md) - alma hakkında bilgi sağlar ve hızlı bir şekilde kullanarak çalışan [hızlı](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675), nasıl basit bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.

[Entity Framework terimleri](../../../../../docs/framework/data/adonet/ef/terminology.md) -birçok varlık veri modeli tarafından sunulan koşullarını tanımlar ve [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve içinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri.

[Entity Framework kaynakları](../../../../../docs/framework/data/adonet/ef/resources.md) - kavramsal konulara bağlantılar sağlar ve dış konuları ve yapı kaynakları için bağlantıları [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamalar.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
