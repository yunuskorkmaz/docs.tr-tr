---
title: "Başarım düşünceleri (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e27d6ec040557d682082a6fb5a05677ad52afae9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="performance-considerations-entity-framework"></a>Başarım düşünceleri (Entity Framework)
Bu konu, ADO.NET Entity Framework performans özelliklerini açıklar ve Entity Framework uygulamalarının performansını geliştirmeye yardımcı olmak için bazı noktalar sağlar.  
  
## <a name="stages-of-query-execution"></a>Sorgu yürütme aşamaları  
 Sorguları Entity Framework performansının daha iyi anlamak için bir sorgu karşı kavramsal model yürütür ve veri nesneleri olarak döndürür yaptığında gerçekleşen işlem anlamaya yardımcı olur. Aşağıdaki tabloda bu işlemleri dizisi açıklanmaktadır.  
  
|Çalışma|Göreli maliyet|Sıklık|Açıklamalar|  
|---------------|-------------------|---------------|--------------|  
|Meta veriler yükleniyor|Orta|Bir kez her uygulama etki alanı.|Entity Framework tarafından kullanılan model ve eşleme meta verileri içine yüklenir bir <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Bu meta verileri genel olarak önbelleğe alınır ve diğer örneklerine kullanılabilir <xref:System.Data.Objects.ObjectContext> aynı uygulama etki alanı.|  
|Veritabanı bağlantısı açılıyor|Orta<sup>1</sup>|gerektiğinde.|Veritabanı için açık bir bağlantı değerli bir kaynak kullandığından [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] açar ve yalnızca gerektiğinde veritabanı bağlantıyı kapatır. Bağlantı açıkça açabilirsiniz. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).|  
|Görünümler oluşturma|Yüksek|Bir kez her uygulama etki alanı. (Önceden oluşturulabilir.)|Entity Framework kavramsal model karşı sorgu yürütme veya veri kaynağına değişiklikleri kaydetmeden önce veritabanına erişmek için yerel sorgu görünümleri kümesi oluşturmanız gerekir. Bu görünümler oluşturma yüksek maliyet nedeniyle görünümlerini önceden oluşturmak ve bunları tasarım zamanında projeye ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: sorgu performansını artırmak için Pre-Generate görünümleri](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).|  
|Sorgu hazırlama|Orta<sup>2</sup>|Bir kez her benzersiz sorgu için.|Sorgu komutu oluşturun, model ve eşleme meta verileri temel alan bir komut ağacındaki oluşturmak ve döndürülen veri şekli tanımlamak için maliyetleri içerir. Varlık SQL sorgusu komutları ve LINQ sorgularını şimdi önbelleğe alındığı için aynı sorgu sonraki yürütmeleri daha kısa sürer. Bu maliyet sonraki yürütmeleri azaltmak için derlenmiş LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenmiş sorguları otomatik olarak önbelleğe alınan LINQ sorgularını daha etkili olabilir. Daha fazla bilgi için bkz: [derlenmiş sorgu (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). LINQ Sorgu yürütme hakkında genel bilgi için bkz: [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Not:** uygulamak Entities sorgularında LINQ `Enumerable.Contains` bellek içi koleksiyonlara işleci otomatik olarak önbelleğe alınmaz. Ayrıca derlenmiş LINQ sorgularını bellek içi koleksiyonlarda kümesini parametreleştirme izin verilmiyor.|  
|Sorgu yürütme|Düşük<sup>2</sup>|Bir kez her sorgu için.|ADO.NET veri sağlayıcıyı kullanarak veri kaynağına karşı komutu yürütülürken maliyeti. Çoğu veri kaynakları sorgu planlarını önbelleğe nedeniyle aynı sorgu sonraki yürütmeleri bile daha az zaman alabilir.|  
|Yükleme ve türleri doğrulanıyor|Düşük<sup>3</sup>|İçin bir kez her <xref:System.Data.Objects.ObjectContext> örneği.|Türleri yüklenir ve kavramsal model tanımlayan türleriyle doğrulandı.|  
|İzleme|Düşük<sup>3</sup>|Bir sorgunun döndürdüğü kez her nesne için. <sup>4</sup>|Bir sorgu kullanıyorsa <xref:System.Data.Objects.MergeOption.NoTracking> birleştirme seçeneği, bu aşama performansını etkilemez.<br /><br /> Sorgu kullanıyorsa <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> birleştirme seçeneği, sorgu sonuçları izlenir <xref:System.Data.Objects.ObjectStateManager>. Bir <xref:System.Data.EntityKey> sorgu döndürür ve izlenen her nesne için oluşturulan oluşturmak için kullanılan bir <xref:System.Data.Objects.ObjectStateEntry> içinde <xref:System.Data.Objects.ObjectStateManager>. Varolan <xref:System.Data.Objects.ObjectStateEntry> bulunabilir <xref:System.Data.EntityKey>, varolan nesne döndürdü. Varsa <xref:System.Data.Objects.MergeOption.PreserveChanges>, veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> seçeneği kullanıldığında, nesne, döndürülmeden önce güncelleştirilir.<br /><br /> Daha fazla bilgi için bkz: [kimlik çözümleme, durum yönetimi ve değişiklik izleme](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
|Nesneleri gerçekleştirilmesini|Orta<sup>3</sup>|Bir sorgunun döndürdüğü kez her nesne için. <sup>4</sup>|Döndürülen okuma işlemi <xref:System.Data.Common.DbDataReader> nesne nesneleri oluşturma ve her örneği değerlere dayalı özellik değerlerinin <xref:System.Data.Common.DbDataRecord> sınıfı. Nesne zaten varsa <xref:System.Data.Objects.ObjectContext> ve sorgu kullanır <xref:System.Data.Objects.MergeOption.AppendOnly> veya <xref:System.Data.Objects.MergeOption.PreserveChanges> birleştirme seçenekleri, bu aşama performansını etkilemez. Daha fazla bilgi için bkz: [kimlik çözümleme, durum yönetimi ve değişiklik izleme](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
  
 <sup>1</sup> bağlantı havuzu bir veri kaynağı sağlayıcı uygular, bir bağlantı açarak maliyetini havuzu arasında dağıtılır. SQL Server için .NET sağlayıcısı bağlantı havuzu destekler.  
  
 <sup>2</sup> maliyeti ile artan sorgu karmaşıklığını artırır.  
  
 <sup>3</sup> orantılı sorgu tarafından döndürülen nesne sayısı için toplam maliyetini artırır.  
  
 <sup>4</sup> EntityClient return sorguladığından EntityClient sorgular için bu yükünü gerekli değil bir <xref:System.Data.EntityClient.EntityDataReader> nesneleri yerine. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Ek hususlar  
 Entity Framework uygulamalarının performansını etkileyebilecek diğer konular şunlardır:  
  
### <a name="query-execution"></a>Sorgu Yürütme  
 Sorguları yoğun kaynak olabileceğinden, kodunuzda ve hangi bilgisayarda hangi noktada bir sorgu yürütülür göz önünde bulundurun.  
  
#### <a name="deferred-versus-immediate-execution"></a>Hemen bir yürütme karşı ertelenmiş  
 Oluştururken bir <xref:System.Data.Objects.ObjectQuery%601> veya LINQ Sorgu, sorgu hemen yürütülmedi. Sorgu yürütme sonuçları gibi gerekli kadar ertelenmiş sırasında bir `foreach` (C#) veya `For Each` (Visual Basic) numaralandırma veya onu doldurmak için atandığında bir <xref:System.Collections.Generic.List%601> koleksiyonu. Sorgu yürütmeye başlar çağırdığınızda hemen <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> yöntemi bir <xref:System.Data.Objects.ObjectQuery%601> veya LINQ yöntemi çağırdığınızda bir singleton sorgu gibi döndürür <xref:System.Linq.Enumerable.First%2A> veya <xref:System.Linq.Enumerable.Any%2A>. Daha fazla bilgi için bkz: [nesne sorguları](http://msdn.microsoft.com/library/0768033c-876f-471d-85d5-264884349276) ve [sorgu yürütme (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>LINQ sorgularını istemci-tarafı yürütülmesi  
 LINQ sorgusu yürütme, veri kaynağı barındıran bilgisayara etmesine karşın, bir LINQ Sorgu bazı bölümleri istemci bilgisayarda hesaplanan. Daha fazla bilgi için depolama yürütme bölümüne bakın [sorgu yürütme (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Sorgu ve karmaşıklık eşleme  
 Tek tek sorgular ve varlık modeli eşlemesindeki karmaşıklık sorgu performansı önemli bir etkisi olmaz.  
  
#### <a name="mapping-complexity"></a>Eşleme karmaşıklık  
 Basit bire bir eşleme varlıkları kavramsal modelde ve depolama modelindeki tablolar arasında daha karmaşık modelleri bire bir eşleme modelleri'den daha karmaşık komutları oluşturur.  
  
#### <a name="query-complexity"></a>Sorgu karmaşıklık  
 Çok sayıda veri kaynağında yürütülen veya büyük miktarda veri döndüren komutları birleşimlerde gerektiren sorguları aşağıdaki yollarla performansını etkileyebilir:  
  
-   Basit görünen kavramsal model sorguları veri kaynağına karşı daha karmaşık sorgular yürütme neden olabilir. Entity Framework veri kaynağına karşı eşdeğer bir sorgu kavramsal model bir sorgu çevirir olduğundan bu durum oluşabilir. Varlıklar arasında bir ilişki birleştirme tabloya eşlendiğinde veri kaynağı sorgusu yürütülen sorgu komut bir veya daha fazla birleştirmeler gerektirebilir veya tek bir varlık ayarladığınızda veri kaynağındaki birden fazla tabloya kavramsal model eşler.  
  
    > [!NOTE]
    >  Kullanım <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemi <xref:System.Data.Objects.ObjectQuery%601> veya <xref:System.Data.EntityClient.EntityCommand> belirli bir sorgu için veri kaynağına karşı yürütülen komutları görüntülemek için sınıflar. Daha fazla bilgi için bkz: [nasıl yapılır: deposu komutları görüntülemek](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
-   İç içe geçmiş varlık SQL sorguları sunucuda birleştirmeler oluşturabilir ve çok sayıda satır döndürebilir.  
  
     İç içe bir sorgu projeksiyon yan tümcesindeki bir örneği verilmiştir:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ayrıca, bu tür sorgular iç içe geçmiş sorgular arasında nesneleri çoğaltma ile tek bir sorgu oluşturmak sorgu ardışık düzen neden. Bu nedenle, tek bir sütun birden çok kez yinelenebilir. SQL Server dahil olmak üzere bazı veritabanlarında, bu, sunucu performansını düşürebilir çok büyük büyümeye TempDB tablo neden olabilir. İç içe geçmiş sorgular yürüttüğünüzde dikkatli olunmalıdır.  
  
-   İstemci sonuç kümesi boyutuna orantılı şekilde kaynaklarını tüketebilir işlemleri çalışıyorsa büyük miktarda veri neden dönüş herhangi bir sorgu performansı düşebilir. Böyle durumlarda, sorgu tarafından döndürülen veri miktarını sınırlamak düşünmelisiniz. Daha fazla bilgi için bkz: [nasıl yapılır: sorgu sonuçlarını aracılığıyla sayfa](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
 Entity Framework tarafından otomatik olarak oluşturulan herhangi bir komut açıkça veritabanı geliştirici tarafından yazılan benzer komutları daha karmaşık olabilir. Veri kaynağında yürütülen tüm komutları açık denetime ihtiyacınız varsa, bir tablo değerli fonksiyon veya saklı yordam için bir eşleme tanımlama göz önünde bulundurun.  
  
#### <a name="relationships"></a>İlişkiler  
 En iyi sorgu performansını için hem varlık modeli ilişkilendirmesinde ve veri kaynağındaki mantıksal ilişkileri olarak varlıklar arasındaki ilişkiler tanımlamanız gerekir.  
  
### <a name="query-paths"></a>Sorgu yolları  
 Yürüttüğünüzde varsayılan olarak, bir <xref:System.Data.Objects.ObjectQuery%601>, ilgili nesneler (ilişkilerin temsil eden nesneler olmasına rağmen) alınmadı. İlişkili nesneleri üç yöntemden birini yükleyebilirsiniz:  
  
1.  Önce sorgu yolunu ayarlama <xref:System.Data.Objects.ObjectQuery%601> yürütülür.  
  
2.  Çağrı `Load` nesneyi kullanıma sunan gezinti özelliği yöntemi.  
  
3.  Ayarlama <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> seçeneği <xref:System.Data.Objects.ObjectContext> için `true`. Nesne Katman koduyla oluşturduğunuzda bu otomatik olarak yapılır [Entity Data Model Designer](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf). Daha fazla bilgi için bkz: [oluşturulan kod genel bakış](http://msdn.microsoft.com/library/6a88ea38-6a90-4107-bc33-531b79ce5b6a).  
  
 Hangi seçeneğin kullanılacağını düşünürken, kolaylığını veritabanında istek sayısı ve tek bir sorguda döndürülen veri miktarını arasında olduğundan emin olun. Daha fazla bilgi için bkz: [yüklenirken ilişkili nesneleri](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
#### <a name="using-query-paths"></a>Sorgu yolları kullanma  
 Sorgu yolları bir sorgunun döndürdüğü nesneleri grafik tanımlayın. Bir sorgu yol tanımladığınızda, yalnızca tek bir istek veritabanında yolunu tanımlar tüm nesneleri döndürmek için gereklidir. Sorgu yollarını kullanarak karmaşık komutları gibi görünen Basit Nesne sorgularından veri kaynağına karşı yürütülen neden olabilir. Bu durum, bir veya daha fazla birleştirmeler tek sorgu ilişkili nesneleri döndürmek için gerekli kaynaklanır. Bu karmaşıklık devralma veya çok-çok ilişkileri içeren bir yolu olan bir varlık gibi bir karmaşık varlık modeli sorguları büyüktür.  
  
> [!NOTE]
>  Kullanım <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemi tarafından oluşturulan komutu görmek için bir <xref:System.Data.Objects.ObjectQuery%601>. Daha fazla bilgi için bkz: [nasıl yapılır: deposu komutları görüntülemek](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
 Çok fazla ilgili nesne sorgu yolunu içerir veya çok fazla satır veri nesneleri içeren, veri kaynağı sorgusu tamamlayamıyor olabilir. Sorgu veri kaynağı özelliklerini aşıyor Ara geçici depolama gerektiriyorsa Bu oluşur. Bu durumda, ilgili nesneleri açıkça yükleyerek veri kaynağı sorgusu karmaşıklığını azaltabilir.  
  
#### <a name="explicitly-loading-related-objects"></a>İlişkili nesneleri açıkça yükleniyor  
 İlişkili nesneleri çağırarak açıkça yükleyebilir `Load` döndüren bir gezinti özelliği yöntemi bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601>. Her zaman gerektirir veritabanına gidiş açıkça yüklenen nesneler `Load` olarak adlandırılır.  
  
> [!NOTE]
>  çağırırsanız `Load` kullandığınızda gibi döndürülen nesne koleksiyonu döngü sırasında `foreach` deyimi (`For Each` Visual Basic'te), tek bir veri kaynağı özgü sağlayıcısı birden fazla etkin sonuç kümeleri desteklemesi gerekir bağlantı. SQL Server veritabanı için bir değerini belirtmeniz gerekir `MultipleActiveResultSets = true` sağlayıcı bağlantı dizesinde.  
  
 De kullanabilirsiniz <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> olduğunda yöntemi hiçbir <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601> varlıklar özellikleri. POCO varlıklar kullanırken kullanışlıdır.  
  
 Açıkça yüklenirken nesneleri JOIN sayısını azaltır ve gereksiz verileri miktara ilgili rağmen `Load` açıkça büyük sayıda nesne yüklenirken pahalı hale gelebilir veritabanına yinelenen bağlantıları gerektirir.  
  
### <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Çağırdığınızda <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> yöntemi bir <xref:System.Data.Objects.ObjectContext>, ayrı oluşturma, update veya delete komutu her eklenen, güncellenen veya silinen nesnenin bağlamında oluşturulur. Bu komutlar, tek bir işlemde veri kaynağı üzerinde yürütülür. Sorgularla oluşturun, performans güncelleştirme ve silme işlemleri gibi kavramsal modelde eşleme karmaşıklığına bağlıdır.  
  
### <a name="distributed-transactions"></a>Dağıtılmış işlemler  
 Dağıtılmış İşlem Düzenleyicisi (DTC) tarafından yönetilen kaynaklara gerektiren işlemler açık bir işlem içinde DTC gerektirmeyen benzer bir işlem çok daha pahalı olur. DTC yükseltmesine aşağıdaki durumlarda gerçekleşir:  
  
-   Bir SQL Server 2000 veritabanı veya başka bir veri kaynağına yönelik bir işlemi her zaman açık bir işlemle DTC için açık işlemleri yükseltin.  
  
-   SQL Server 2005 bağlantısı tarafından yönetildiğinde karşı bir işlemle açık bir işlem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bu bağlantı kapatılacak ve tek bir işlem içinde yeniden açılacak her SQL Server 2005'in bir DTC yükseltir nedeniyle oluşur varsayılan davranışını olduğu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. SQL Server 2008 kullanırken bu DTC yükseltme gerçekleşmez. SQL Server 2005 kullanırken bu yükseltme önlemek için açıkça açın ve işlem içinde bağlantıyı kapatın. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
 Açık bir işlem içinde bir veya daha fazla işlem çalıştırıldığında kullanılan bir <xref:System.Transactions> işlem. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="strategies-for-improving-performance"></a>Performansı artırmak için stratejileri  
 Aşağıdaki stratejilerden kullanarak Entity Framework sorgularda genel performansını artırabilir.  
  
#### <a name="pre-generate-views"></a>Görünümlerini önceden oluşturmak  
 Bir varlık modelini temel alan görünümler oluşturma önemli bir maliyet bir uygulama bir sorguyu yürüten ilk saattir. Projeye tasarım sırasında eklenebilecek Visual Basic veya C# kod dosyası olarak önceden görünümlerinizi EdmGen.exe yardımcı programını kullanın. Metin şablonu dönüştürme araç seti, önceden derlenmiş görünümleri oluşturmak için de kullanabilirsiniz. Önceden üretilmiş görünümleri, belirtilen varlık modeli geçerli sürümü ile uyumlu olduklarından emin olmak için çalışma zamanında doğrulanır. Daha fazla bilgi için bkz [nasıl yapılır: sorgu performansını artırmak için Pre-Generate görünümleri](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579) ve [yalıtma performans görünümlerle önceden derlenmiş/öncesi-generated Entity Framework 4'te](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409).  
  
 Çok büyük modelleri ile çalışırken, aşağıdaki değerlendirme geçerlidir:  
  
 .NET meta veri biçimi 16.777.215 (0xFFFFFF değerine) belirli bir ikili kullanıcı dize karakter sayısını sınırlar. Çok büyük bir modelin için görünümleri oluşturma ve görünüm dosyası bu boyutu sınırına ulaştığında, "hiçbir mantıksal alan daha fazla kullanıcı dizesi oluşturmak için sol." alırsınız derleme hatası. Bu boyut sınırlaması tüm yönetilen ikili dosyaları için geçerlidir. Daha fazla bilgi için bkz: [blog](http://go.microsoft.com/fwlink/?LinkId=201476) , büyük ve karmaşık modelleriyle çalışırken hatayı önlemek gösterilmiştir.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Sorgular için NoTracking birleştirme seçeneği kullanmayı deneyin  
 Nesne bağlamı döndürülen nesneleri izlemek için gereken bir maliyeti yoktur. Nesnelerdeki değişiklikleri algılama ve aynı mantıksal varlık için birden çok istek aynı nesne örneğini dönüş sağlamayı gerektirir nesneleri eklenmesi bir <xref:System.Data.Objects.ObjectContext> örneği. Güncelleştirme ve silme nesnelere planlamadığınızı ve kimlik yönetimi gerektirmez kullanmayı <xref:System.Data.Objects.MergeOption.NoTracking> sorguları yürüttüğünüzde birleştirme seçenekleri.  
  
#### <a name="return-the-correct-amount-of-data"></a>Doğru veri miktarını döndürür  
 Bazı senaryolarda kullanarak bir sorgu yolu belirterek <xref:System.Data.Objects.ObjectQuery%601.Include%2A> yöntemdir çok daha hızlı, daha az sayıda gidiş dönüş veritabanına gerektiriyor. Daha az veri artıklığı bakımından daha az birleştirmeler daha basit sorgularıyla neden ancak, diğer senaryolarda, ilgili nesneleri yüklemek için veritabanına ek gidiş dönüş daha hızlı olabilir. Bu nedenle, ilgili nesneleri almak için çeşitli şekillerde performansını test etme öneririz. Daha fazla bilgi için bkz: [yüklenirken ilişkili nesneleri](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
 Tek bir sorguda çok fazla veri döndüren önlemek için sorgunun sonuçlarını daha kolay yönetilebilir gruplar halinde disk belleği göz önünde bulundurun. Daha fazla bilgi için bkz: [nasıl yapılır: sorgu sonuçlarını aracılığıyla sayfa](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>ObjectContext kapsamını sınırlamak  
 Çoğu durumda, oluşturmalısınız bir <xref:System.Data.Objects.ObjectContext> içinde örnek bir `using` deyimi (`Using…End Using` Visual Basic'te). Kod deyimi blok çıktığında nesne bağlamla ilişkili kaynakları otomatik olarak atıldı olduğunu sağlayarak bu performansı artırabilir. Ancak, ne zaman denetimleri bağlı nesne bağlamı tarafından yönetilen nesneleri <xref:System.Data.Objects.ObjectContext> bağlama gerekli ve el ile elden sürece örneği'nin saklanabilir. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Veritabanı bağlantısı el ile açma göz önünde bulundurun  
 Olduğunda, uygulamanızın nesne sorguları bir dizi yürütür veya sık çağıran <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> kalıcı hale getirmek için oluşturma, güncelleştirme ve silme işlemleri veri kaynağına [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sürekli açık gerekir ve veri kaynağına bağlantıyı kapatın. Bu durumda, el ile bu işlemleri ve kapatma veya bağlantısını işlemlerin tamamlandığı zaman atma başlangıç bağlantı açma göz önünde bulundurun. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="performance-data"></a>Performans Verileri  
 Entity Framework için bazı performans verileri üzerinde aşağıdaki gönderileri yayımlanır [ADO.NET ekip blogu](http://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [ADO.NET Entity Framework - Bölüm 1 performansını keşfetme](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [ADO.NET Entity Framework – Bölüm 2 performansını keşfetme](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [ADO.NET Entity Framework performans karşılaştırması](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştirme ve Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
