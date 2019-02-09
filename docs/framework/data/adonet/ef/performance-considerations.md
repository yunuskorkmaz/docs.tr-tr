---
title: Performansla ilgili önemli noktalar (varlık çerçevesi)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 4b6d3d4dbf801a7b0cc378482ad4d0d29a915be3
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904807"
---
# <a name="performance-considerations-entity-framework"></a>Performansla ilgili önemli noktalar (varlık çerçevesi)
Bu konu, ADO.NET varlık çerçevesi performans özelliklerini açıklar ve Entity Framework uygulamalarının performansını artırmak için bazı değerlendirmeleri sağlar.  
  
## <a name="stages-of-query-execution"></a>Sorgu yürütme aşamaları  
 Sorgular, Entity Framework performansının daha iyi anlamak için bir sorgu kavramsal model karşı yürütür ve verileri nesne gibi döndürür yaptığında gerçekleşen işlem anlamak yararlıdır. Aşağıdaki tabloda, bu bir dizi işlem açıklanmaktadır.  
  
|Çalışma|Göreli maliyeti|Sıklık|Açıklamalar|  
|---------------|-------------------|---------------|--------------|  
|Meta verileri yükleniyor|Orta|Bir kez her uygulama etki alanında.|Entity Framework tarafından kullanılan model ve eşleme meta veri olarak yüklendiği bir <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Bu meta verileri genel olarak önbelleğe alınır ve diğer örnekleri için kullanılabilir <xref:System.Data.Objects.ObjectContext> aynı uygulama etki alanında.|  
|Veritabanı bağlantısı açılıyor|Orta<sup>1</sup>|Gerektiğinde.|Veritabanına bir bağlantı değerli bir kaynak kullandığından [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] açılır ve yalnızca gerektiğinde veritabanı bağlantıyı kapatır. Bağlantı açıkça de açabilirsiniz. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Görünüm oluşturma|Yüksek|Bir kez her uygulama etki alanında. (Ön üretilemez.)|Varlık çerçevesi kavramsal modeline karşı bir sorgu yürütme veya değişiklikleri veri kaynağına kaydetmek için önce yerel sorgu görünümleri veritabanına erişmek için bir dizi oluşturmanız gerekir. Bu görünümler oluşturmanın yüksek maliyetinden nedeniyle önceden görünümlerinizi ve tasarım zamanında projeye ekleyin. Daha fazla bilgi için [nasıl yapılır: Sorgu performansını artırmak için önceden görünümlerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Sorgu hazırlanıyor|Orta<sup>2</sup>|Bir kez her benzersiz sorgu için.|Sorgu komutu oluşturun, model ve eşleme meta verileri temel alan bir komut ağacı oluşturmak ve döndürülen verinin şeklini tanımlamak için maliyetlerini içerir. Artık hem varlık SQL sorgu komutlarını hem de LINQ sorguları önbelleğe alındığından, aynı sorgu sonraki yürütmeleri daha kısa sürer. Bu sonraki yürütme sayısı maliyeti azaltmak için derlenmiş LINQ sorguları kullanmaya devam edebilirsiniz ve derlenmiş sorgular otomatik olarak önbelleğe LINQ sorguları daha verimli olabilir. Daha fazla bilgi için [derlenmiş sorgular (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). LINQ Sorgu yürütme hakkında genel bilgi için bkz: [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Not:**  LINQ to Entities sorgularında, uygulama `Enumerable.Contains` işleci bellek içi koleksiyonlara otomatik olarak önbelleğe alınmaz. Bellek içi koleksiyonları derlenmiş LINQ sorgularında ayrıca kümesini parametreleştirme izin verilmez.|  
|Sorgu yürütülüyor|Düşük<sup>2</sup>|Bir kez her sorgu için.|ADO.NET veri sağlayıcıyı kullanarak veri kaynağına karşı komut yürütmenin maliyeti. Çoğu veri kaynakları sorgu planlarına önbelleğe almak için aynı sorgu sonraki yürütmeleri bile daha az zaman alabilir.|  
|Yükleme ve türleri doğrulanıyor|Düşük<sup>3</sup>|Her biri için bir kez <xref:System.Data.Objects.ObjectContext> örneği.|Türleri yüklenir ve kavramsal model tanımlayan türlerine karşı doğrulandı.|  
|İzleme|Düşük<sup>3</sup>|Bir sorgu döndüren bir kez her nesne için. <sup>4</sup>|Bir sorgu kullanıyorsa <xref:System.Data.Objects.MergeOption.NoTracking> birleştirme seçeneği, bu aşama performansını etkilemez.<br /><br /> Sorgu kullanıyorsa <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> birleştirme seçeneği, sorgu sonuçları izlenir <xref:System.Data.Objects.ObjectStateManager>. Bir <xref:System.Data.EntityKey> sorguyu döndürür ve izlenen her nesne için oluşturulan oluşturmak için kullanılan bir <xref:System.Data.Objects.ObjectStateEntry> içinde <xref:System.Data.Objects.ObjectStateManager>. Varolan <xref:System.Data.Objects.ObjectStateEntry> bulunabilir <xref:System.Data.EntityKey>, var olan nesne döndürülür. Varsa <xref:System.Data.Objects.MergeOption.PreserveChanges>, veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> seçeneği kullanıldığında, nesneyi döndürülmeden önce güncelleştirilir.<br /><br /> Daha fazla bilgi için [kimlik çözümlemesi, durum yönetimi ve değişiklik izleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Nesneleri düzeniyle|Orta<sup>3</sup>|Bir sorgu döndüren bir kez her nesne için. <sup>4</sup>|Döndürülen okuma işleminin <xref:System.Data.Common.DbDataReader> nesne nesneleri oluşturma ve her örneğinde değerlere göre özellik değerlerini ayarlama <xref:System.Data.Common.DbDataRecord> sınıfı. Nesne zaten varsa <xref:System.Data.Objects.ObjectContext> ve sorgu kullanan <xref:System.Data.Objects.MergeOption.AppendOnly> veya <xref:System.Data.Objects.MergeOption.PreserveChanges> birleştirme seçeneklerini, bu aşama performansını etkilemez. Daha fazla bilgi için [kimlik çözümlemesi, durum yönetimi ve değişiklik izleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> bağlantı havuzu bir veri kaynağı sağlayıcı uygular, bir bağlantı açmak maliyeti havuz arasında dağıtılır. SQL Server için .NET sağlayıcısı, bağlantı havuzu destekler.  
  
 <sup>2</sup> maliyeti daha yüksek sorgu karmaşıklığı artırır.  
  
 <sup>3</sup> orantılı sorgu tarafından döndürülen nesne sayısı için toplam maliyet artar.  
  
 <sup>4</sup> EntityClient dönüş sorguladığından EntityClient sorgular için bu ek yükü gerekli değil bir <xref:System.Data.EntityClient.EntityDataReader> nesneler yerine. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Dikkat edilecek diğer noktalar  
 Entity Framework uygulamalarının performansını etkileyebilecek diğer konular şunlardır:  
  
### <a name="query-execution"></a>Sorgu Yürütme  
 Yoğun kaynak sorgular bu nedenle, kod ve hangi bilgisayarda hangi noktada sorgu yürütülür göz önünde bulundurun.  
  
#### <a name="deferred-versus-immediate-execution"></a>Ertelenmiş hemen yürütme  
 Oluştururken bir <xref:System.Data.Objects.ObjectQuery%601> veya LINQ sorgusunu sorgu hemen yürütülemeyebilir. Sorgu yürütme sonuçları gibi gerekli olup kadar ertelenmiş sırasında bir `foreach` (C#) veya `For Each` numaralandırması (Visual Basic) veya ne zaman doldurmak için atanır bir <xref:System.Collections.Generic.List%601> koleksiyonu. Sorgu yürütme başlangıcı çağırdığınızda hemen <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> metodunda bir <xref:System.Data.Objects.ObjectQuery%601> veya LINQ yöntemi çağırdığınızda döndürür gibi tek sorgu <xref:System.Linq.Enumerable.First%2A> veya <xref:System.Linq.Enumerable.Any%2A>. Daha fazla bilgi için [nesne sorgularını](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) ve [sorgu yürütme (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>İstemci tarafı yürütülmesini LINQ sorguları  
 Veri kaynağını barındıran bilgisayarda bir LINQ sorgusunun yürütülmesi karşın, istemci bilgisayarda bir LINQ Sorgu bazı bölümlerini değerlendirilebilir. Daha fazla bilgi için bkz: Store yürütme bölümü [sorgu yürütme (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Sorgu ve karmaşıklık eşleme  
 Her sorgu ve varlık modeli eşlemede karmaşıklığı sorgu performansı üzerinde önemli bir etkisi olacaktır.  
  
#### <a name="mapping-complexity"></a>Eşleme karmaşıklığı  
 Daha karmaşık komutlar bire bir eşleme sahip modellerinin basit bire bir eşleme kavramsal modeldeki varlıklar depolama modelindeki tablolar arasında daha karmaşık modelleri oluşturun.  
  
#### <a name="query-complexity"></a>Sorgu karmaşıklığı  
 Çok sayıda veri kaynağına karşı yürütülen veya, büyük miktarda veri döndüren komutlar birleşimlerde gerektiren sorguları, aşağıdaki yollarla performansını etkileyebilir:  
  
-   Basit görünen kavramsal modeline karşı sorgular, veri kaynağına karşı daha karmaşık sorgular yürütülmesine neden olabilir. Varlık çerçevesi kavramsal modeline karşı bir sorgu veri kaynağına karşı eşdeğer bir sorguda çevirir. çünkü bu durum oluşabilir. Tek bir varlık kümesi'nde, veri kaynağında birden fazla tablo kavramsal model eşlendiği veya varlıklar arasında ilişki birleştirme tabloya eşlendiğinde, veri kaynağı sorgusu karşı yürütülen sorgu komutu bir veya daha fazla birleştirme işlemleri gerektirebilir.  
  
    > [!NOTE]
    >  Kullanım <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemi <xref:System.Data.Objects.ObjectQuery%601> veya <xref:System.Data.EntityClient.EntityCommand> belirli bir sorgu için veri kaynağına karşı yürütülen komutlar görüntülemek için sınıflar. Daha fazla bilgi için [nasıl yapılır: Store komutlarını görüntülemesine](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
-   İç içe geçmiş Entity SQL sorguları sunucuda birleştirmeler oluşturabilir ve çok sayıda satır döndürebilir.  
  
     Bir projeksiyon yan tümcesi iç içe bir sorgu örneği verilmiştir:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ayrıca, iç içe geçmiş sorgular arasında nesneleri çoğaltma ile tek bir sorgu oluşturmak sorgu işlem hattındaki sorgularını neden. Bu nedenle, tek bir sütun birden çok defa yinelenebilir. SQL Server dahil olmak üzere bazı veritabanlarında, bu sunucu performansı azaltabilir, çok büyük büyümesine TempDB tablo neden olabilir. İç içe geçmiş sorgular yürütme dikkatli olunması.  
  
-   İstemci sonuç kümesinin boyutuna orantılı bir şekilde kaynak kullanan işlemleri gerçekleştiriliyorsa, büyük miktarda veri neden olabilir döndüren sorgular performansı düşebilir. Böyle durumlarda, sorgu tarafından döndürülen veri miktarını sınırlamak düşünmelisiniz. Daha fazla bilgi için [nasıl yapılır: Sonuçlar sayfası sorguyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Entity Framework tarafından otomatik olarak oluşturulan herhangi bir komut açıkça veritabanı geliştirici tarafından yazılan benzer komutları daha karmaşık olabilir. Veri kaynağına karşı yürütülen komutlar kesin denetime ihtiyacınız varsa, bir tablo değerli işlev veya saklı yordam için bir eşleme tanımlama göz önünde bulundurun.  
  
#### <a name="relationships"></a>İlişkiler  
 Optimum sorgu performansı için varlık modeli ilişkilendirmeler hem mantıksal ilişkileri veri kaynağındaki varlıklar arasındaki ilişkilerin tanımlamanız gerekir.  
  
### <a name="query-paths"></a>Sorgu yolları  
 Varsayılan olarak yürüttüğünüzde bir <xref:System.Data.Objects.ObjectQuery%601>, ilgili nesneler (ilişkilerin temsil eden nesneleri olmasına rağmen) alınmadı. Üç yoldan biriyle ilgili nesneleri yükleyebilirsiniz:  
  
1.  Önce sorgu yolunu <xref:System.Data.Objects.ObjectQuery%601> yürütülür.  
  
2.  Çağrı `Load` nesneyi gösteren Gezinti özelliğindeki yöntemi.  
  
3.  Ayarlama <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> seçeneğini <xref:System.Data.Objects.ObjectContext> için `true`. Nesne Katmanı kodu ile oluşturduğunuzda bu otomatik olarak yapılır [varlık veri modeli Tasarımcısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Daha fazla bilgi için [oluşturulan kod genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Hangi seçeneğin kullanılacağını düşünürken, veritabanında isteklerinin sayısı ve tek bir sorguda döndürülen veri miktarını arasında bir denge olduğunu unutmayın. Daha fazla bilgi için [ilgili nesneler Yükleniyor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Sorgu yollar kullanarak  
 Bir sorgunun döndürdüğü nesnelerin grafik sorgu tanımlar. Sorgu yolu tanımladığınızda, veritabanında yalnızca tek bir istek yolunu tanımlar tüm nesneleri döndürme için gereklidir. Sorgu yolları kullanarak karmaşık komutlar görünüşte Basit Nesne sorgularından veri kaynağına karşı yürütülen neden olabilir. Bu durum, tek bir sorguda ilgili nesneler döndürmek için gereken bir veya daha fazla birleştirmeler kaynaklanır. Bu karmaşıklığı, varlık devralma veya çok-çok ilişkileri içeren bir yol gibi bir karmaşık varlık modeline karşı sorgular büyüktür.  
  
> [!NOTE]
>  Kullanım <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemi tarafından oluşturulan komut görmek için bir <xref:System.Data.Objects.ObjectQuery%601>. Daha fazla bilgi için [nasıl yapılır: Store komutlarını görüntülemesine](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Bir sorgu yolu çok fazla ilgili nesne içerir ya da çok fazla satır veri nesneleri içeren veri kaynağı sorgu tamamlayamıyor olabilir. Sorgu veri kaynağı özelliklerini aşan Ara geçici depolama gerektiriyorsa Bu durum gerçekleşir. Bu durumda, ilgili nesneleri açıkça yükleyerek veri kaynağı sorgusu karmaşıklığını azaltabilir.  
  
#### <a name="explicitly-loading-related-objects"></a>İlgili nesneler açıkça yükleniyor  
 İlgili nesneler çağrılarak açıkça yükleyebilir `Load` döndüren bir gezinti özelliği metodunda bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601>. Açıkça nesneleri yüklenirken bir gidiş dönüş veritabanına her zaman gerektirir `Load` çağrılır.  
  
> [!NOTE]
>  Eğer `Load` kullandığınızda gibi döndürülen nesnelerin koleksiyonu aracılığıyla döngü sırasında `foreach` deyimi (`For Each` Visual Basic'te), birden çok etkin sonuç kümesi tek bir veri kaynağına özgü sağlayıcısı desteklemesi gerekir bağlantı. Bir SQL Server veritabanı için bir değerini belirtmeniz gerekir `MultipleActiveResultSets = true` sağlayıcısı bağlantı dizesinde.  
  
 Ayrıca <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> olduğunda yöntemi hiçbir <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601> varlıklardaki özellikleri. POCO varlık kullanırken, bu yararlıdır.  
  
 İlgili nesneler JOIN sayısını azaltır ve yedekli veri miktarı azalır açıkça yükleniyor olsa da `Load` açıkça büyük sayıda nesne yüklenirken pahalı hale gelebilir veritabanı yinelenen bağlantı gerektirir.  
  
### <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Çağırdığınızda <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metodunda bir <xref:System.Data.Objects.ObjectContext>, ayrı create, update veya delete komutu her eklenen, güncelleştirilen veya silinen nesnenin bağlamında oluşturulur. Bu komutlar, tek bir işlemde veri kaynağı üzerinde yürütülür. Sorgularla performansını oluşturma, güncelleştirme ve silme işlemleri gibi kavramsal model eşlemede karmaşıklığına bağlıdır.  
  
### <a name="distributed-transactions"></a>Dağıtılmış işlemler  
 Dağıtılmış İşlem Düzenleyicisi (DTC) tarafından yönetilen kaynaklara gerektiren işlem açık bir işlemde DTC gerektirmeyen benzer bir işlem çok daha pahalı olur. DTC yükseltmesine aşağıdaki durumlarda oluşur:  
  
-   Her zaman bir işlem bir SQL Server 2000 veritabanı veya başka bir veri kaynağı ile açık bir işlem DTC için açık işlemleri tanıtın.  
  
-   Bağlantı tarafından yönetilmediği durumlarda SQL Server 2005 yönelik bir işlem olan açık bir işlem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bağlantı kapatıldı ve tek bir işlem içinde açılamaz her SQL Server 2005 bir DTC yükseltir. Bu kaynaklanır varsayılan davranışını olduğu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bu DTC promosyon, SQL Server 2008 kullanılırken gerçekleşmez. SQL Server 2005 kullanırken bu yükseltmeyi önlemek için açıkça açın ve işlem içinde bağlantıyı kapatın. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Açık işlem içindeki bir veya daha fazla işlem çalıştırıldığında kullanılan bir <xref:System.Transactions> işlem. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Performansı geliştirme stratejileri  
 Aşağıdaki stratejileri kullanarak Entity Framework sorgularda genel performansını artırabilir.  
  
#### <a name="pre-generate-views"></a>Görünümleri önceden oluştur  
 Bir varlık modelini temel alan bir görünüm oluşturma önemli maliyet bir uygulama bir sorgu yürütüldüğünde ilk açıklamadır. Önceden görünümleri projeye tasarım sırasında eklenebilecek Visual Basic veya C# kod dosyası olarak üretmek için Edmgen.exe'yi yardımcı programını kullanın. Metin şablonu dönüştürme araç seti, önceden derlenmiş görünümleri oluşturmak için de kullanabilirsiniz. Önceden üretilmiş görünümleri, belirtilen varlık modeli geçerli sürümü ile uyumlu olduklarından emin olmak için çalışma zamanında doğrulanır. Daha fazla bilgi için [nasıl yapılır: Sorgu performansını artırmak için önceden görünümlerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Çok büyük modelleri ile çalışırken, aşağıdaki önemli noktalar geçerlidir:  
  
 .NET meta veri biçimi 16.777.215 (0xFFFFFF değerine) belirtilen bir ikili kullanıcı dize karakter sayısını sınırlar. Çok büyük bir model için görünümleri oluşturduğunu ve görünüm dosyası bu boyutu sınırına ulaştığında, "mantıksal boşluk daha fazla kullanıcı dizeleri oluşturmak için sol." alırsınız derleme hatası. Bu boyut sınırlaması, tüm yönetilen ikililer için geçerlidir. Daha fazla bilgi için [blog](https://go.microsoft.com/fwlink/?LinkId=201476) , büyük ve karmaşık modelleri ile çalışırken, hatayı önlemek gösterilmektedir.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Sorgular için NoTracking birleştirme seçeneği kullanmayı düşünün  
 Döndürülen nesne bağlamı nesneleri izlemek için gereken bir maliyeti yoktur. Nesnelerde yapılan değişiklikler algılanıyor ve aynı mantıksal varlık için birden çok isteği aynı nesne örneği döndürür sağlamayı gerektirir nesneleri eklenmesi bir <xref:System.Data.Objects.ObjectContext> örneği. Güncelleştirme ve silme nesnelere yapmayı planladığınız değil ve kimlik yönetimi gerektirmez, kullanmayı <xref:System.Data.Objects.MergeOption.NoTracking> sorgular yürütme seçenekleri birleştirme.  
  
#### <a name="return-the-correct-amount-of-data"></a>Doğru veri miktarını döndürür  
 Bazı senaryolarda, yolu kullanarak bir sorgu belirten <xref:System.Data.Objects.ObjectQuery%601.Include%2A> veritabanı daha az sayıda gidiş dönüş gerektirdiğinden yöntemi çok daha hızlı. Çünkü daha az veri artıklığı bakımından daha az birleşimler daha basit sorgular neden ancak diğer senaryolarda, ilgili nesneleri yüklemek için veritabanına ek gidiş dönüş daha hızlı olabilir. Bu nedenle, ilgili nesneleri almak için çeşitli yollar performansını test etme öneririz. Daha fazla bilgi için [ilgili nesneler Yükleniyor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Tek bir sorguda çok fazla veri döndüren önlemek için sorgunun sonuçlarının disk belleği daha yönetilebilir gruplara göz önünde bulundurun. Daha fazla bilgi için [nasıl yapılır: Sonuçlar sayfası sorguyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>ObjectContext kapsamını sınırlandırmak  
 Çoğu durumda, oluşturacağınız bir <xref:System.Data.Objects.ObjectContext> içinde örnek bir `using` deyimi (`Using…End Using` Visual Basic'te). Kod deyim bloğunu çıktığında nesne bağlamı ile ilişkili kaynakları otomatik olarak kaldırıldıklarından sağlayarak bu performansı artırabilir. Ancak, ne zaman denetimleri ilişkili nesne bağlamı tarafından yönetilen nesnelere <xref:System.Data.Objects.ObjectContext> bağlama gerekli ve el ile elden sürece örnek'in saklanabilir. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Veritabanı bağlantısı el ile açmayı göz önünde bulundurun  
 Uygulamanızı bir dizi nesne sorgusu yürütür veya sık çağırır olduğunda <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> kalıcı hale getirmek için oluşturma, güncelleştirme ve silme işlemleri veri kaynağına [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sürekli olarak açmak gerekir ve veri kaynağı bağlantısını kapatın. Bu gibi durumlarda el ile bu işlemleri ve kapatma veya işlemlerin tamamlandığı zaman bağlantısı kesilirken başlangıcında bağlantı açmayı göz önünde bulundurun. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Performans Verileri  
 Entity Framework için bazı performans verileri aşağıdaki gönderilerinde yayımlanan [ADO.NET ekibi blogu](https://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [ADO.NET Entity Framework - 1. Bölüm performansını keşfetme](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [ADO.NET Entity Framework – Bölüm 2 performansını keşfetme](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [ADO.NET Entity Framework performans karşılaştırması](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Geliştirme ve Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
