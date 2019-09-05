---
title: Entity Framework’e Genel Bakış
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 0934afa96a88b48d8af2d613e83ba793e2f75e71
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248600"
---
# <a name="entity-framework-overview"></a>Entity Framework genel bakış

, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veri odaklı yazılım uygulamalarının geliştirilmesini destekleyen ADO.net ' deki bir teknolojiler kümesidir. Veri tabanlı uygulamaların mimarları ve geliştiricileri, iki farklı hedefe ulaşmak için ihtiyaç duymasına karşı çok daha ağır. Bunlar, çöztikleri iş sorunlarının varlıklarını, ilişkilerini ve mantığını modellemeye ve ayrıca verileri depolamak ve almak için kullanılan veri altyapılarıyla birlikte çalışmalıdır. Veriler, her biri kendi protokollerine sahip birden fazla depolama sistemine yayılabilir. tek bir depolama sistemiyle çalışan uygulamaların bile, depolama sisteminin gereksinimlerini, verimli ve sürdürülebilir uygulama kodu yazma gereksinimlerine göre dengelenmesi gerekir.

, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiricilerin, bu verilerin depolandığı temel veritabanı tabloları ve sütunları ile ilgilenmenize gerek kalmadan, etki alanına özgü nesne ve müşteriler ve müşteri adresleri gibi özellikler biçimindeki verilerle çalışmasını sağlar . [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]Sayesinde, geliştiriciler verilerle ilgilendiklerinde daha yüksek bir soyutlama düzeyinde çalışabilir ve geleneksel uygulamalardan daha az kodla veri odaklı uygulamalar oluşturabilir ve bakımını yapabilir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ,[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] .NET Framework bir bileşeni olduğundan, uygulamalar sürüm 3,5 SP1 ile başlayan .NET Framework yüklü herhangi bir bilgisayarda çalıştırılabilir.

## <a name="give-life-to-models"></a>Modellere yaşam verin
 Uygulama veya hizmet oluştururken bir veya daha fazla uygulama ya da hizmet, bir etki alanı modeli, mantıksal model ve fiziksel bir model olmak üzere, bir veya daha fazla genel tasarım yaklaşımıdır. Etki alanı modeli, modellenen sistemdeki varlıkları ve ilişkileri tanımlar. İlişkisel bir veritabanının mantıksal modeli, varlıkları ve ilişkileri yabancı anahtar kısıtlamalarına sahip tablolarla normalleştirir. Fiziksel model bölümlendirme ve dizin oluşturma gibi depolama ayrıntılarını belirterek belirli bir veri altyapısının özelliklerine yöneliktir.

 Fiziksel model, performansı artırmak için veritabanı yöneticileri tarafından iyileştirilmektedir, ancak uygulama kodu yazan programcılar öncelikle SQL sorguları yazarak ve saklı yordamları çağırarak kendi kendilerini mantıksal modelle çalışmaya göre sorgular. Etki alanı modelleri genellikle bir uygulamanın gereksinimlerini yakalamak ve iletişim kurmak için kullanılan bir araç olarak, bir projenin erken aşamalarında görüntülenen ve ele alınan ve daha sonra terk edilmiş bir şekilde, ve ardından bırakılmış bir uygulama için bir araç olarak kullanılır. Birçok geliştirme ekibi, bir kavramsal model oluşturmayı atlar ve ilişkisel bir veritabanındaki tabloları, sütunları ve anahtarları belirterek başlar.

 , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiricilerin etki alanı modelindeki varlıkları ve ilişkileri (içinde [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] *kavramsal* model olarak adlandırılır) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sorgulayabilme olanağı sunarak, bu işlemleri veri kaynağına çevirmek için bir yaşam süresi sağlar. Belirli komutlar. Bu, uygulamaları belirli bir veri kaynağındaki sabit kodlanmış bağımlılıklardan boşaltır.

 Code First ile çalışırken kavramsal model, koddaki depolama modeliyle eşlenir. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modeli nesne türlerine ve tanımladığınız ek yapılandırmalara göre çıkarabilir. Eşleme meta verileri, etki alanı türlerinizi nasıl tanımladığınıza ve kodda sağladığınız ek yapılandırma bilgilerine göre çalışma zamanı sırasında oluşturulur. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]meta verilere bağlı olarak veritabanını gereken şekilde oluşturur. Daha fazla bilgi için bkz. [kavramsal model oluşturma ve eşleme](https://go.microsoft.com/fwlink/?LinkID=235382).

 Varlık Veri Modeli araçlarıyla çalışırken, kavramsal model, depolama modeli ve ikisi arasındaki eşlemeler, XML tabanlı şemalarda ifade edilir ve karşılık gelen ad uzantılarına sahip dosyalarda tanımlanır:

- Kavramsal şema tanım dili (CSDL) kavramsal modeli tanımlar. CSDL varlık veri modeli uygulamasıdır. [](../entity-data-model.md) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Dosya uzantısı. csdl.

- Depo şeması tanım dili (SSDL), mantıksal model olarak da adlandırılan depolama modelini tanımlar. Dosya uzantısı. ssdl.

- Eşleme belirtim dili (MSL), depolama ve kavramsal modeller arasındaki eşlemeleri tanımlar. Dosya uzantısı. msl 'dir.

Depolama modeli ve eşlemeler, kavramsal modelde, veri sınıflarında veya uygulama kodunda değişiklik yapılması gerekmeden gerektiği şekilde değiştirilebilir. Depolama modelleri sağlayıcıya özgü olduğundan, çeşitli veri kaynakları arasında tutarlı bir kavramsal model ile çalışabilirsiniz.

, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu modeli ve eşleme dosyalarını, kavramsal modeldeki varlıklara ve ilişkilere karşı, veri kaynağındaki eşdeğer işlemlere karşı oluşturma, okuma, güncelleştirme ve silme işlemleri için kullanır. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modeldeki varlıkları veri kaynağındaki saklı yordamlara eşleştirmeyi de destekler. Daha fazla bilgi için bkz. [csdl, SSDL ve MSL belirtimleri](./language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Nesneleri verilerle eşleme
 Nesne odaklı programlama, veri depolama sistemleriyle etkileşime geçmek için bir zorluk doğurur. Sınıfların organizasyonu ilişkisel veritabanı tablolarının organizasyonunu sıklıkla yansıtsa da, sığdırma kusursuz değildir. Birden çok normalleştirilmiş tablo sıklıkla tek bir sınıfa karşılık gelir ve sınıflar arasındaki ilişkiler genellikle tablolar arasındaki ilişkilerden farklı şekilde temsil edilir. Örneğin, bir satış siparişi için müşteriyi göstermek üzere, `Order` bir sınıf bir `Customer` sınıfın örneğine başvuru içeren bir özellik kullanabilir, ancak `Order` veritabanındaki tablo satırı yabancı anahtar sütunu (veya sütun kümesi) içerdiğinde `Customer` tablodaki birincil anahtar değerine karşılık gelen bir değer. Bir `Customer` sınıf, `Order` sınıfının örneklerinin bir koleksiyonunu `Orders` içeren adlı bir özelliğe sahip olabilir, ancak `Customer` veritabanındaki tablo karşılaştırılabilir bir sütun içermez. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Geliştiricilere bu şekilde ilişkileri temsil etme esnekliği sağlar veya veritabanında gösterildiği gibi ilişkileri daha yakından modelleyebilir.

 Mevcut çözümler, genellikle "Impedance uyuşmazlığı" olarak adlandırılan ve yalnızca nesne odaklı sınıfları ve özellikleri ilişkisel tablo ve sütunlara eşleyerek bu boşluğu köprü oluşturmaya çalıştı. Bu geleneksel yaklaşımı [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] yerine, mantıksal modellerdeki ilişkisel tabloları, sütunları ve yabancı anahtar kısıtlamalarını kavramsal modellerdeki varlıklara ve ilişkilere eşler. Bu, hem nesneleri tanımlamada hem de mantıksal modeli iyileştirirken daha fazla esneklik sağlar. Varlık Veri Modeli araçları, kavramsal modeli temel alan genişletilebilir veri sınıfları oluşturur. Bu sınıflar, geliştiricinin eklediği ek üyelerle genişletilebilen kısmi sınıflardır. Varsayılan olarak, belirli bir kavramsal model için oluşturulan sınıflar, varlıkları nesneler olarak görselleştirme ve değişiklikleri izleme ve kaydetme için hizmet sağlayan temel sınıflardan türetilir. Geliştiriciler bu sınıfları, ilişkilerle ilgili nesneler olarak varlıklar ve ilişkiler ile çalışmak için kullanabilir. Geliştiriciler bir kavramsal model için oluşturulan sınıfları da özelleştirebilir. Daha fazla bilgi için bkz. [nesneleriyle çalışma](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Varlık verilerine erişme ve değişiklik

Diğer bir nesne ilişkisel eşleme çözümünün daha fazla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] olması, uygulamaların kavramsal modelde varlık ve ilişki olarak temsil edilen verilere erişmesini ve bu verileri değiştirmesini sağlar. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Model ve eşleme dosyalarındaki bilgileri kullanarak nesne sorgularını kavramsal modelde gösterilen varlık türlerine, veri kaynağına özgü sorgulara çevirecek şekilde dönüştürür. Sorgu sonuçları, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] yönettiği nesnelere uygulanır. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modeli sorgulamak ve nesneleri döndürmek için aşağıdaki yolları sağlar:

- LINQ to Entities. Kavramsal modelde tanımlanan varlık türlerini sorgulamak için dil ile tümleşik sorgu (LINQ) desteği sağlar. Daha fazla bilgi için bkz. [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Kavramsal modeldeki varlıklarla doğrudan çalıştırılan ve Varlık Veri Modeli kavramları destekleyen, depolama bağımsız bir SQL diyalekti. [!INCLUDE[esql](../../../../../includes/esql-md.md)], EntityClient sağlayıcısı kullanılarak yürütülen nesne sorguları ve sorgularıyla birlikte kullanılır. Daha fazla bilgi için bkz. [Entity SQL genel bakış](./language-reference/entity-sql-overview.md).

, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] EntityClient veri sağlayıcısını içerir. Bu sağlayıcı bağlantıları yönetir, varlık sorgularını veri kaynağına özgü sorgulara çevirir ve varlık verilerini nesnelere getirmek için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kullanılan bir veri okuyucuyu döndürür. Nesne gerçekleştirmesi gerekli olmadığında, EntityClient sağlayıcısı, uygulamaların sorguları yürütmesine [!INCLUDE[esql](../../../../../includes/esql-md.md)] ve döndürülen salt okunurdur veri okuyucuyu kullanmasına olanak tanıyarak standart bir ADO.NET veri sağlayıcısı gibi de kullanılabilir. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).

Aşağıdaki diyagramda verilere erişim [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mimarisi gösterilmektedir:

![Entity Framework mimari diyagramı](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Varlık veri modeli araçları, kavramsal modeldeki varlık kapsayıcısını temsil eden `System.Data.Objects.ObjectContext` veya `System.Data.Entity.DbContext` ondan türetilmiş bir sınıf oluşturabilir. Bu nesne bağlamı, değişiklikleri izleme ve kimlikleri, eşzamanlılık ve ilişkileri yönetme olanakları sağlar. Bu sınıf Ayrıca veri kaynağına `SaveChanges` ekleme, güncelleştirme ve silme işlemlerini yazan bir yöntem sunar. Sorgular gibi bu değişiklikler, sistem tarafından veya geliştirici tarafından belirtilen saklı yordamlar tarafından otomatik olarak oluşturulan komutlara göre yapılır.

## <a name="data-providers"></a>Veri sağlayıcıları

`EntityClient` Sağlayıcı, kavramsal varlıklar ve ilişkiler açısından verilere erişerek ADO.NET sağlayıcı modelini genişletir. Kullanan sorguları [!INCLUDE[esql](../../../../../includes/esql-md.md)]yürütür. [!INCLUDE[esql](../../../../../includes/esql-md.md)]veritabanıyla iletişim kurmayı sağlayan `EntityClient` temel sorgu dili sağlar. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).

, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kurallı komut ağaçlarını destekleyen güncelleştirilmiş bir SqlClient veri sağlayıcısı içerir. Daha fazla bilgi için bkz. [Entity Framework Için SqlClient](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Varlık veri modeli araçları

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Çalışma zamanı ile birlikte Visual Studio, eşleme ve modelleme araçlarını içerir. Daha fazla bilgi için bkz. [modelleme ve eşleme](modeling-and-mapping.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Hakkında [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]daha fazla bilgi için bkz.

[Başlarken](getting-started.md) -basit [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bir uygulamanın nasıl oluşturulacağını gösteren hızlı [Başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))kullanarak hızlı bir şekilde nasıl çalışmaya başlacağınız ve çalıştırılacağı hakkında bilgi sağlar.

[Entity Framework terimleri](terminology.md) - [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgelerde kullanılan ve varlık veri modeli tarafından tanıtılan birçok terimi tanımlar.

[Entity Framework kaynaklar](resources.md) -uygulamalar oluşturmaya [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] yönelik kavramsal konuların ve dış konuların ve kaynakların bağlantılarını sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](index.md)
