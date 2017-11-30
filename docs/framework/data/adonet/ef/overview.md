---
title: "Entity Framework genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05b87dfbb54de87ce7591dd6363d56ab69ebb8a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-framework-overview"></a>Entity Framework genel bakış
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ADO.NET Veri odaklı yazılım uygulamaları geliştirme desteği teknolojileri kümesidir. İki çok farklı hedeflerine ulaşmasına gerek mimarları ve geliştiricileri veri odaklı uygulamalar zorlandığınız. Varlıklar, ilişkileri ve iş sorunlarını çözme mantığını model gerekir ve depolamak ve verileri almak için kullanılan veri yapısıyla de çalışması gerekir. Veriler birden çok depolama sistemleri, her biri kendi protokollerle yayılabilir; tek bir depolama sistemiyle çalışacak bile uygulamaları verimli ve sürdürülebilir uygulama kodu yazarken gereksinimleri karşı depolama sistem gereksinimlerini dengelemeniz gerekir.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kendilerini temel alınan veritabanı tabloları ve sütunları bu verilerin depolandığı ilgilendiren gerek kalmadan etki alanına özgü nesneleri ve müşteriler ve Müşteri adresleri gibi özellikleri biçiminde verilerle çalışmak için geliştiricilere olanak sağlar . İle [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bunlar Dağıt verilerle ve oluşturabilir ve daha az kod geleneksel uygulamalarında ile veri odaklı uygulamalar korumak, geliştiricilerin daha yüksek bir soyutlama düzeyinde çalışabilir. Çünkü [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bir bileşeni olan [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamalar, herhangi bir bilgisayarda çalıştırabilirsiniz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 3.5 SP1 ile başlayarak yüklenir.  
  
 Bu konudaki aşağıdaki bölümler hakkında daha fazla ayrıntı sağlamak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   [Modellere yaşam vermiş](#LifeToModels)  
  
-   [Veri nesneleri eşleme](#MappingObjectsToData)  
  
-   [Verilere erişme ve varlık verilerini değiştirme](#AccessingData)  
  
-   [Veri sağlayıcıları](#DataProviders)  
  
-   [Varlık veri modeli araçları](#Tools)  
  
-   [Daha fazla öğrenme](#LearnMore)  
  
<a name="LifeToModels"></a>   
## <a name="giving-life-to-models"></a>Modellere yaşam vermiş  
 Bir uygulama veya hizmet oluşturma uygulamanın veya hizmetin bölümünün üç kısma olduğunda döngümüzün ve ortak tasarım yaklaşımı: etki alanı modeli, mantıksal bir model ve fiziksel bir model. Etki alanı modeli, model alınmıştır sistemde varlıkları ve ilişkileri tanımlar. İlişkisel bir veritabanına yönelik mantıksal modelin varlıkları ve ilişkileri yabancı anahtar kısıtlamaları olan tablolara normalleştirir. Fiziksel model bölümlendirme ve dizin oluşturma gibi depolama ayrıntıları belirterek belirli veri altyapısı yeteneklerini giderir.  
  
 Fiziksel model performansını artırmak için Veritabanı yöneticileri tarafından iyileştirilmiştir, ancak uygulama kod öncelikle yazma programcıları kendilerini SQL sorguları yazma ve saklı yordamlar çağırma mantıksal modeli ile çalışmak için sınırlamak. Etki alanı modelleri, genellikle yakalamak ve bir uygulamayı görüntülenebilir ve proje erken aşamada ele alınan ve ardından terk sık etkisiz durumda diyagramları olarak gereksinimlerini iletişim için bir aracı olarak kullanılır. Birçok geliştirme ekiplerinin kavramsal model oluşturma atlayın ve tablolar, sütunlar ve anahtarları bir ilişkisel veritabanı belirterek başlayın.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Sorgu varlıkları ve ilişkileri etki alanı modelinde geliştiricilerine etkinleştirerek modellerine yaşam verir (adlı bir *kavramsal* içindeki model [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) güvenmek sırasında [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] olanlar çevirmek için veri kaynağı – özel komutlar için işlemleri. Bu, belirli bir veri kaynağı üzerinde sabit kodlu bağımlılıklar uygulamadan boşaltır.  
  
 Code First ile çalışırken, kavramsal model kod depolama modelinde eşleştirilir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nesne türleri ve tanımladığınız ek yapılandırmalar göre kavramsal model çıkarımını. Eşleme meta veri çalışma sırasında kod içinde nasıl sağladığınız ek yapılandırma bilgilerini ve etki alanı türleri tanımlanan bileşimi göre oluşturulur. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]Veritabanı gerektiği gibi meta verileri temel alarak oluşturur. Daha fazla bilgi için bkz: [oluşturma ve kavramsal Model eşleme](http://go.microsoft.com/fwlink/?LinkID=235382).  
  
 Varlık veri modeli araçları ile çalışırken, kavramsal model ve depolama modeli ikisi arasındaki eşlemeleri XML tabanlı şemalarda ifade ve karşılık gelen adı uzantılarına sahip dosyalarında tanımlanan:  
  
-   Kavramsal şema tanım dili (CSDL) kavramsal model tanımlar. CSDL olan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]'s uyarlamasını [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md). .Csdl dosya uzantısıdır.  
  
-   Depo şeması tanım dili (SSDL) mantıksal model olarak da adlandırılan depolama modelinin tanımlar. .Ssdl dosya uzantısıdır.  
  
-   Eşleme belirtimi dili (MSL) depolama ve kavramsal modeller arasındaki eşlemeleri tanımlar. Dosya uzantısı .msl ' dir.  
  
 Depolama modeli ve eşlemelerini kavramsal model, veri sınıflarını veya uygulama kodu değişiklik gerektirmeden gerektiği gibi değiştirebilirsiniz. Depolama modelleri sağlayıcıya özgü olduğundan, çeşitli veri kaynakları arasında tutarlı bir kavramsal model ile çalışabilirsiniz.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu modeli ve dosyaları oluşturmak için eşleme, okuma, güncelleştirme ve silme işlemleri varlıkları ve ilişkileri kavramsal modelde veri kaynağındaki eşdeğer işlemlerine karşı kullanır. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bile veri kaynağındaki saklı yordamlar için kavramsal model eşleme varlıklar destekler. Daha fazla bilgi için bkz: [CSDL, SSDL ve MSL belirtimlerini](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).  
  
<a name="MappingObjectsToData"></a>   
## <a name="mapping-objects-to-data"></a>Veri nesneleri eşleme  
 Nesne odaklı programlama veri depolama sistemlerle etkileşim için bir zorluk oluşturur. Sınıfları organizasyonu sık ilişkisel veritabanı tablolarını organizasyonu yansıtan rağmen uygun kusursuz değil. Birden çok normalleştirilmiş tablolar tek bir sınıf sık karşılık gelir ve tablolar arasında ilişkiler temsil daha sınıflar arasındaki ilişkileri genellikle farklı şekilde gösterilir. Örneğin, bir satış siparişi için müşteri temsil etmek için bir `Order` sınıfı örneği için bir başvuru içeren bir özelliği kullanabilecekleri bir `Customer` sınıfı, sırada bir `Order` bir veritabanında tablo satır içeren bir yabancı anahtar sütunu (veya sütun kümesini) bir birincil anahtar değerine karşılık gelen bir değer ile `Customer` tablo. A `Customer` sınıfı adlı bir özellik olması `Orders` örneklerinin bir koleksiyonunu içeren `Order` sınıfı, sırada `Customer` tablolu bir veritabanında karşılaştırılabilir sütun yok. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiriciler veritabanında gösterildiği ilişkileri bu şekilde ya da daha yakından ilişkileri modellemek için temsil etmek için esneklik sağlar.  
  
 Var olan çözümler genellikle bir "empedanslı Uyuşmazlığı", yalnızca eşleme nesne yönelimli sınıfları ve özellikleri ilişkisel tablolar ve sütunlar için tarafından çağrılır bu boşluğu kapatmak denediniz. Bu geleneksel yaklaşım benimseyerek yerine [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] varlıkları ve ilişkileri kavramsal modellerde ilişkisel tablolar, sütunlar ve yabancı anahtar kısıtlamaları mantıksal modellerde eşler. Bu, hem nesneleri tanımlama ve mantıksal model en iyi duruma getirme, daha fazla esneklik sağlar. [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Araçlar kavramsal modele dayalı genişletilebilir veri sınıfları oluşturur. Bu sınıfların Geliştirici ekler ek üyeleriyle genişletilmiş kısmi sınıflarıdır. Varsayılan olarak, belirli bir kavramsal model için oluşturulan sınıflar varlıkları nesneleri olarak gerçekleştirilmesini ve izleme ve değişiklikleri kaydetme hizmetleri sağlayan temel sınıfından türetilir. Geliştiricilerin bu sınıfların göre ilişkileri ilgili nesneler olarak varlıkları ve ilişkileri ile çalışmak için kullanabilirsiniz. Geliştiriciler ayrıca kavramsal model için oluşturulan sınıflar özelleştirebilirsiniz. Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
<a name="AccessingData"></a>   
## <a name="accessing-and-changing-entity-data"></a>Verilere erişme ve varlık verilerini değiştirme  
 Birden fazla yalnızca başka bir nesne ilişkisel eşleme çözüm [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] temelde erişmek ve varlıkları ve ilişkileri kavramsal modelde olarak temsil edilir verileri değiştirmek uygulamalar hakkında etkinleştirmektir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modelde veri kaynağı özgü sorgulara temsil edilen varlık türleri nesne sorguları çevirmek için model ve eşleme dosyalarındaki bilgileri kullanır. Sorgu sonuçları nesnelerine gerçekleştirilip, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] yönetir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal model sorgulamak ve nesneleri döndürmek için aşağıdaki yöntemleri sağlar:  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Kavramsal modelde tanımlanan varlık türleri sorgulamak için dil ile tümleşik sorgu (LINQ) desteği sağlar. Daha fazla bilgi için bkz: [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Bir depolama bağımsız diyalekti doğrudan kavramsal modelde varlıklarla çalışır ve destekleyen SQL [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kavramları. [!INCLUDE[esql](../../../../../includes/esql-md.md)]hem nesne sorguları ve EntityClient sağlayıcısı kullanılarak yürütülen sorguları ile kullanılır. Daha fazla bilgi için bkz: [varlık SQL genel bakış](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] EntityClient veri sağlayıcısı içerir. Bu sağlayıcı bağlantıları yönetir, veri kaynağı özgü sorgulara varlık sorguları çevirir ve bir veri okuyucu döndüren [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] varlık veri nesnelerini gerçekleştirmeye için kullanır. Nesne materialization gerekli olmadığı durumlarda, EntityClient sağlayıcısı ayrıca gibi standart bir kullanılabilir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] yürütmek uygulamaları etkinleştirerek veri sağlayıcısı [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular ve döndürülen salt okunur veri okuyucu kullanabilir. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Aşağıdaki diyagramda gösterilmektedir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] verilere erişmek için mimarisi:  
  
 ![Entity Framework mimari diyagramı](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")  
  
 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Araçları, türetilmiş bir sınıf oluşturabilir `System.Data.Objects.ObjectContext` veya `System.Data.Entity.DbContext` , kavramsal model varlık kapsayıcısında temsil eder. Bu nesne bağlamı değişiklikleri izlemek ve kimlikleri, eşzamanlılık ve ilişkileri yönetme için olanakları sağlar. Bu sınıf ayrıca kullanıma sunan bir `SaveChanges` ekler, yazar yöntemi güncelleştirir ve veri kaynağına siler. Sorgular gibi bu değişiklikler ya da geliştirici tarafından belirtilen saklı yordamları veya sistem tarafından otomatik olarak oluşturulan komutları tarafından yapılır.  
  
<a name="DataProviders"></a>   
## <a name="data-providers"></a>Veri sağlayıcıları  
 `EntityClient` Sağlayıcı genişletir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri kavramsal varlıkları ve ilişkileri bakımından erişerek sağlayıcı modeli. Kullanan sorguları yürüten [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)]sağlayan temel sorgu dili sağlar `EntityClient` veritabanıyla iletişim kurmak için. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bir güncelleştirilmiş SqlClient Veri kurallı komut ağaçlarını destekleyen sağlayıcısı içerir. Daha fazla bilgi için bkz: [Entity Framework SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).  
  
<a name="Tools"></a>   
## <a name="entity-data-model-tools"></a>Varlık veri modeli araçları  
 İle birlikte [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] çalışma zamanı, [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] eşleme ve modelleme araçlarını içerir. Daha fazla bilgi için bkz: [modelleme ve eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).  
  
<a name="LearnMore"></a>   
## <a name="learning-more"></a>Daha fazla öğrenme  
 Aşağıdaki konular hakkında daha fazla bilgi sağlayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
 [Başlarken](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 Alma hakkında bilgi sağlar ve hızlı şekilde kullanmaya çalışıyor [Hızlı Başlangıç](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675), basit bir oluşturulacağını gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.  
  
 [Entity Framework terminolojisi](../../../../../docs/framework/data/adonet/ef/terminology.md)  
 Çoğu varlık veri modeli tarafından sunulan koşullarını tanımlar ve [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve içinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri.  
  
 [Varlık çerçevesi kaynakları](../../../../../docs/framework/data/adonet/ef/resources.md)  
 Kavramsal konulara bağlantılar ve dış konulara ve kaynaklara bağlantılar için yapı sağlayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamalar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
