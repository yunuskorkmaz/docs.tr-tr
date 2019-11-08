---
title: Entity Framework’e Genel Bakış
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: b68db4f139330ccc1da5057498a37a08d00ba266
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738500"
---
# <a name="entity-framework-overview"></a>Entity Framework genel bakış

Entity Framework, veri odaklı yazılım uygulamalarının geliştirilmesini destekleyen ADO.NET ' deki bir teknolojiler kümesidir. Veri tabanlı uygulamaların mimarları ve geliştiricileri, iki farklı hedefe ulaşmak için ihtiyaç duymasına karşı çok daha ağır. Bunlar, çöztikleri iş sorunlarının varlıklarını, ilişkilerini ve mantığını modellemeye ve ayrıca verileri depolamak ve almak için kullanılan veri altyapılarıyla birlikte çalışmalıdır. Veriler, her biri kendi protokollerine sahip birden fazla depolama sistemine yayılabilir. tek bir depolama sistemiyle çalışan uygulamaların bile, depolama sisteminin gereksinimlerini, verimli ve sürdürülebilir uygulama kodu yazma gereksinimlerine göre dengelenmesi gerekir.

Entity Framework, geliştiricilerin bu verilerin bulunduğu temel veritabanı tabloları ve sütunları ile ilgilenmenize gerek kalmadan, etki alanına özgü nesne ve müşteriler ve müşteri adresleri gibi özellikler biçimindeki verilerle çalışabilmesini sağlar. saklanmalıdır. Entity Framework, geliştiriciler verilerle ilgilendiklerinde daha yüksek bir soyutlama düzeyinde çalışabilir ve geleneksel uygulamalardan daha az kodla veri odaklı uygulamalar oluşturabilir ve bakımını yapabilir. Entity Framework, .NET Framework bir bileşeni olduğundan Entity Framework uygulamalar, sürüm 3,5 SP1 ile başlayan .NET Framework yüklü herhangi bir bilgisayarda çalıştırılabilir.

## <a name="give-life-to-models"></a>Modellere yaşam verin
 Uygulama veya hizmet oluştururken bir veya daha fazla uygulama ya da hizmet, bir etki alanı modeli, mantıksal model ve fiziksel bir model olmak üzere, bir veya daha fazla genel tasarım yaklaşımıdır. Etki alanı modeli, modellenen sistemdeki varlıkları ve ilişkileri tanımlar. İlişkisel bir veritabanının mantıksal modeli, varlıkları ve ilişkileri yabancı anahtar kısıtlamalarına sahip tablolarla normalleştirir. Fiziksel model bölümlendirme ve dizin oluşturma gibi depolama ayrıntılarını belirterek belirli bir veri altyapısının özelliklerine yöneliktir.

 Fiziksel model, performansı artırmak için veritabanı yöneticileri tarafından iyileştirilmektedir, ancak uygulama kodu yazan programcılar öncelikle SQL sorguları yazarak ve saklı yordamları çağırarak kendi kendilerini mantıksal modelle çalışmaya göre sorgular. Etki alanı modelleri genellikle bir uygulamanın gereksinimlerini yakalamak ve iletişim kurmak için kullanılan bir araç olarak, bir projenin erken aşamalarında görüntülenen ve ele alınan ve daha sonra terk edilmiş bir şekilde, ve ardından bırakılmış bir uygulama için bir araç olarak kullanılır. Birçok geliştirme ekibi, bir kavramsal model oluşturmayı atlar ve ilişkisel bir veritabanındaki tabloları, sütunları ve anahtarları belirterek başlar.

 Entity Framework, geliştiricilerin etki alanı modelindeki varlıkları ve ilişkileri (Entity Framework *kavramsal* model olarak adlandırılır), bu işlemleri veri kaynağına çevirmek için Entity Framework bağlı olarak, bir yandan modeller sağlar – Belirli komutlar. Bu, uygulamaları belirli bir veri kaynağındaki sabit kodlanmış bağımlılıklardan boşaltır.

 Code First ile çalışırken kavramsal model, koddaki depolama modeliyle eşlenir. Entity Framework, kavramsal modeli, nesne türlerine ve tanımladığınız ek yapılandırmalara göre çıkarsalabilir. Eşleme meta verileri, etki alanı türlerinizi nasıl tanımladığınıza ve kodda sağladığınız ek yapılandırma bilgilerine göre çalışma zamanı sırasında oluşturulur. Entity Framework, meta verileri temel alarak veritabanını gereken şekilde oluşturur. Daha fazla bilgi için bkz. [kavramsal model oluşturma ve eşleme](https://go.microsoft.com/fwlink/?LinkID=235382).

 Varlık Veri Modeli araçlarıyla çalışırken, kavramsal model, depolama modeli ve ikisi arasındaki eşlemeler, XML tabanlı şemalarda ifade edilir ve karşılık gelen ad uzantılarına sahip dosyalarda tanımlanır:

- Kavramsal şema tanım dili (CSDL) kavramsal modeli tanımlar. CSDL, Entity Framework [varlık veri modeli](../entity-data-model.md)uygulamasıdır. Dosya uzantısı. csdl.

- Depo şeması tanım dili (SSDL), mantıksal model olarak da adlandırılan depolama modelini tanımlar. Dosya uzantısı. ssdl.

- Eşleme belirtim dili (MSL), depolama ve kavramsal modeller arasındaki eşlemeleri tanımlar. Dosya uzantısı. msl 'dir.

Depolama modeli ve eşlemeler, kavramsal modelde, veri sınıflarında veya uygulama kodunda değişiklik yapılması gerekmeden gerektiği şekilde değiştirilebilir. Depolama modelleri sağlayıcıya özgü olduğundan, çeşitli veri kaynakları arasında tutarlı bir kavramsal model ile çalışabilirsiniz.

Entity Framework bu modeli ve eşleme dosyalarını, kavramsal modeldeki varlıklara ve ilişkilere yönelik olarak veri kaynağındaki eşdeğer işlemlere karşı oluşturma, okuma, güncelleştirme ve silme işlemleri için kullanır. Entity Framework, kavramsal modeldeki varlıkların veri kaynağındaki saklı yordamlara eşlenmesini de destekler. Daha fazla bilgi için bkz. [csdl, SSDL ve MSL belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).

## <a name="map-objects-to-data"></a>Nesneleri verilerle eşleme
 Nesne odaklı programlama, veri depolama sistemleriyle etkileşime geçmek için bir zorluk doğurur. Sınıfların organizasyonu ilişkisel veritabanı tablolarının organizasyonunu sıklıkla yansıtsa da, sığdırma kusursuz değildir. Birden çok normalleştirilmiş tablo sıklıkla tek bir sınıfa karşılık gelir ve sınıflar arasındaki ilişkiler genellikle tablolar arasındaki ilişkilerden farklı şekilde temsil edilir. Örneğin, bir satış siparişi için müşteriyi göstermek üzere bir `Order` sınıfı, bir `Customer` sınıfının örneğine başvuru içeren bir özellik kullanabilir, ancak veritabanındaki bir `Order` tablo satırı, bir değeri olan bir yabancı anahtar sütunu (veya sütun kümesi) içeriyorsa `Customer` tablosundaki bir birincil anahtar değerine karşılık gelir. Bir `Customer` sınıfı, `Order` sınıfının örneklerinin bir koleksiyonunu içeren `Orders` adında bir özelliğe sahip olabilir, ancak bir veritabanındaki `Customer` tablo, karşılaştırılabilir bir sütuna sahip değildir. Entity Framework, geliştiricilere bu şekilde ilişkileri temsil etme esnekliği sağlar veya veritabanında gösterildiği gibi ilişkileri daha yakından modelleyebilir.

 Mevcut çözümler, genellikle "Impedance uyuşmazlığı" olarak adlandırılan ve yalnızca nesne odaklı sınıfları ve özellikleri ilişkisel tablo ve sütunlara eşleyerek bu boşluğu köprü oluşturmaya çalıştı. Entity Framework, bu geleneksel yaklaşımı almak yerine, mantıksal modellerdeki ilişkisel tabloları, sütunları ve yabancı anahtar kısıtlamalarını kavramsal modellerdeki varlıklara ve ilişkilere eşler. Bu, hem nesneleri tanımlamada hem de mantıksal modeli iyileştirirken daha fazla esneklik sağlar. Varlık Veri Modeli araçları, kavramsal modeli temel alan genişletilebilir veri sınıfları oluşturur. Bu sınıflar, geliştiricinin eklediği ek üyelerle genişletilebilen kısmi sınıflardır. Varsayılan olarak, belirli bir kavramsal model için oluşturulan sınıflar, varlıkları nesneler olarak görselleştirme ve değişiklikleri izleme ve kaydetme için hizmet sağlayan temel sınıflardan türetilir. Geliştiriciler bu sınıfları, ilişkilerle ilgili nesneler olarak varlıklar ve ilişkiler ile çalışmak için kullanabilir. Geliştiriciler bir kavramsal model için oluşturulan sınıfları da özelleştirebilir. Daha fazla bilgi için bkz. [nesneleriyle çalışma](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Varlık verilerine erişme ve değişiklik

Diğer bir nesne ilişkisel eşleme çözümünden daha fazlasına sahip Entity Framework, uygulamaların kavramsal modelde varlık ve ilişki olarak temsil edilen verilere erişmesini ve bunları değiştirmesini sağlama konusunda temel olarak kullanılır. Entity Framework, nesne sorgularını kavramsal modelde gösterilen varlık türlerine ve veri kaynağına özgü sorgulara dönüştürmek için modeldeki bilgileri ve eşleme dosyalarını kullanır. Sorgu sonuçları, Entity Framework yönettiği nesnelere uygulanır. Entity Framework kavramsal modeli sorgulamak ve nesneleri döndürmek için aşağıdaki yolları sağlar:

- LINQ to Entities. Kavramsal modelde tanımlanan varlık türlerini sorgulamak için dil ile tümleşik sorgu (LINQ) desteği sağlar. Daha fazla bilgi için bkz. [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Kavramsal modeldeki varlıklarla doğrudan çalıştırılan ve Varlık Veri Modeli kavramları destekleyen, depolama bağımsız bir SQL diyalekti. [!INCLUDE[esql](../../../../../includes/esql-md.md)], her ikisi de EntityClient sağlayıcısı kullanılarak yürütülen nesne sorguları ve sorgularıyla kullanılır. Daha fazla bilgi için bkz. [Entity SQL genel bakış](./language-reference/entity-sql-overview.md).

Entity Framework EntityClient veri sağlayıcısını içerir. Bu sağlayıcı bağlantıları yönetir, varlık sorgularını veri kaynağına özgü sorgulara çevirir ve Entity Framework varlık verilerini nesnelere getirmek için kullandığı bir veri okuyucusu döndürür. Nesne gerçekleştirmesi gerekli olmadığında, EntityClient sağlayıcısı, uygulamaların [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorguları yürütmesini ve döndürülen salt okunurdur veri okuyucuyu kullanmasını sağlayarak standart bir ADO.NET veri sağlayıcısı gibi de kullanılabilir. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).

Aşağıdaki diyagramda verilere erişim için Entity Framework mimarisi gösterilmektedir:

![Entity Framework mimari diyagramı](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Varlık Veri Modeli Araçlar, kavramsal modeldeki varlık kapsayıcısını temsil eden `System.Data.Objects.ObjectContext` veya `System.Data.Entity.DbContext` türetilmiş bir sınıf oluşturabilir. Bu nesne bağlamı, değişiklikleri izleme ve kimlikleri, eşzamanlılık ve ilişkileri yönetme olanakları sağlar. Bu sınıf Ayrıca veri kaynağına ekleme, güncelleştirme ve silme işlemlerini yazan bir `SaveChanges` yöntemi sunar. Sorgular gibi bu değişiklikler, sistem tarafından veya geliştirici tarafından belirtilen saklı yordamlar tarafından otomatik olarak oluşturulan komutlara göre yapılır.

## <a name="data-providers"></a>Veri sağlayıcıları

`EntityClient` sağlayıcı, kavramsal varlıklar ve ilişkiler açısından verilere erişerek ADO.NET sağlayıcı modelini genişletir. [!INCLUDE[esql](../../../../../includes/esql-md.md)]kullanan sorguları yürütür. [!INCLUDE[esql](../../../../../includes/esql-md.md)], `EntityClient` veritabanıyla iletişim kurmasını sağlayan temel sorgu dili sağlar. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).

Entity Framework, kurallı komut ağaçlarını destekleyen güncelleştirilmiş bir SqlClient Veri Sağlayıcısı içerir. Daha fazla bilgi için bkz. [Entity Framework Için SqlClient](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Varlık veri modeli araçları

Entity Framework çalışma zamanıyla birlikte, Visual Studio eşleme ve modelleme araçlarını içerir. Daha fazla bilgi için bkz. [modelleme ve eşleme](modeling-and-mapping.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Entity Framework hakkında daha fazla bilgi edinmek için bkz.:

[Başlarken](getting-started.md) -basit bir Entity Framework uygulamasının nasıl oluşturulacağını gösteren hızlı [Başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))kullanarak hızlı bir şekilde çalışmaya başlamak ve bunların nasıl çalıştırılacağı hakkında bilgiler sağlar.

[Entity Framework terimleri](terminology.md) -Varlık Veri Modeli ve Entity Framework tarafından tanıtılan ve Entity Framework belgelerinde kullanılan koşulların çoğunu tanımlar.

[Entity Framework kaynaklar](resources.md) -Entity Framework uygulamalar oluşturmaya yönelik kavramsal konuların ve dış konuların ve kaynakların bağlantılarını sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](index.md)
