---
title: Performans Hususları (Varlık Çerçevesi)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 0ff018fe0d8199dcd790bcd3de18751662e0a92b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149745"
---
# <a name="performance-considerations-entity-framework"></a>Performans Hususları (Varlık Çerçevesi)
Bu konu, varlık çerçevesinin ADO.NET performans özelliklerini açıklar ve Varlık Çerçevesi uygulamalarının performansını artırmaya yardımcı olmak için bazı hususlar sağlar.  
  
## <a name="stages-of-query-execution"></a>Sorgu Yürütme Aşamaları  
 Varlık Çerçevesi'ndeki sorguların performansını daha iyi anlamak için, bir sorgu kavramsal bir modele karşı yürütüldüğünde ve verileri nesne olarak döndürdüğünde oluşan işlemleri anlamak yararlıdır. Aşağıdaki tabloda bu işlem dizilimi açıklanmaktadır.  
  
|İşlem|Göreli Maliyet|Frequency|Yorumlar|  
|---------------|-------------------|---------------|--------------|  
|Meta verileri yükleme|Orta|Her uygulama etki alanında bir kez.|Varlık Çerçevesi tarafından kullanılan model ve eşleme <xref:System.Data.Metadata.Edm.MetadataWorkspace>meta verileri bir . Bu meta veriler genel olarak önbelleğe alınır ve <xref:System.Data.Objects.ObjectContext> aynı uygulama etki alanında diğer örnekleri için kullanılabilir.|  
|Veritabanı bağlantısını açma|Orta<sup>1</sup>|Gerektiği gibi.|Veritabanına açık bir bağlantı değerli bir kaynak tükettiği için, Varlık Çerçevesi veritabanı bağlantısını yalnızca gerektiği gibi açar ve kapatır. Ayrıca bağlantıyı açıkça açabilirsiniz. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))|  
|Görünüm oluşturma|Yüksek|Her uygulama etki alanında bir kez. (Önceden oluşturulabilir.)|Varlık Çerçevesi'nin bir sorguyu kavramsal bir modele karşı yürütemeden veya veri kaynağında değişiklik kaydedebilmek için veritabanına erişmek için bir dizi yerel sorgu görünümü oluşturması gerekir. Bu görünümleri oluşturmanın yüksek maliyeti nedeniyle, görünümleri önceden oluşturabilir ve tasarım zamanında projeye ekleyebilirsiniz. Daha fazla bilgi için [bkz: Sorgu Performansını Artırmak için Görünümleri Önceden Oluştur.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))|  
|Sorguyu hazırlama|Orta<sup>2</sup>|Her benzersiz sorgu için bir kez.|Sorgu komutunu oluşturmak, modele dayalı bir komut ağacı oluşturmak ve meta verileri eşleme maliyetlerini içerir ve döndürülen verilerin şeklini tanımlar. Artık hem Entity SQL sorgu komutları hem de LINQ sorguları önbelleğe alındığından, aynı sorgunun daha sonraki yürütmeleri daha az zaman alır. Daha sonraki yürütmelerde bu maliyeti azaltmak için derlenmiş LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenen sorgular otomatik olarak önbelleğe alınmış LINQ sorgularından daha verimli olabilir. Daha fazla bilgi için [derlenmiş sorgulara (LINQ to Ntities)](./language-reference/compiled-queries-linq-to-entities.md)bakın. LINQ sorgu yürütmesi hakkında genel bilgi için [LINQ to Ntities 'a](./language-reference/linq-to-entities.md)bakın. **Not:**  `Enumerable.Contains` Işleci bellek içi koleksiyonlara uygulayan Varlıklara LINQ sorguları otomatik olarak önbelleğe alınmaz. Ayrıca derlenmiş LINQ sorgularında bellek içi koleksiyonları parametrelendirmeye izin verilmez.|  
|Sorguyu yürütme|Düşük<sup>2</sup>|Her sorgu için bir kez.|ADO.NET veri sağlayıcısını kullanarak komutu veri kaynağına karşı yürütme maliyeti. Çoğu veri kaynağı sorgu planlarını önbelleğe aldığı için, aynı sorgunun daha sonraki yürütmeleri daha da kısa sürebilir.|  
|Yükleme ve doğrulama türleri|Düşük<sup>3</sup>|Her örnek <xref:System.Data.Objects.ObjectContext> için bir kez.|Türler, kavramsal modelin tanımladığı türlere göre yüklenir ve doğrulanır.|  
|İzleme|Düşük<sup>3</sup>|Bir sorgunun döndürdettiği her nesne için bir kez. <sup>4</sup>|Bir sorgu birleştirme <xref:System.Data.Objects.MergeOption.NoTracking> seçeneğini kullanıyorsa, bu aşama performansı etkilemez.<br /><br /> Sorgu <xref:System.Data.Objects.MergeOption.AppendOnly>, , <xref:System.Data.Objects.MergeOption.PreserveChanges>veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> birleştirme seçeneğini kullanırsa, <xref:System.Data.Objects.ObjectStateManager>sorgu sonuçları . Sorgunun döndürdüğü her <xref:System.Data.Objects.ObjectStateEntry> izlenen <xref:System.Data.Objects.ObjectStateManager>nesne için bir <xref:System.Data.EntityKey> ürün oluştur Varolan <xref:System.Data.Objects.ObjectStateEntry> bir nesne için <xref:System.Data.EntityKey>bulunabilir, varolan nesne döndürülür. <xref:System.Data.Objects.MergeOption.PreserveChanges>, veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> seçenek kullanılırsa, nesne döndürülmeden önce güncelleştirilir.<br /><br /> Daha fazla bilgi için [bkz: Kimlik Çözümü, Devlet Yönetimi ve Değişiklik İzleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100))|  
|Nesneleri maddeleştirme|Orta<sup>3</sup>|Bir sorgunun döndürdettiği her nesne için bir kez. <sup>4</sup>|Döndürülen <xref:System.Data.Common.DbDataReader> nesneyi okuma ve nesneleri oluşturma ve <xref:System.Data.Common.DbDataRecord> sınıfın her örneğindeki değerleri temel alan özellik değerlerini ayarlama işlemi. Nesne zaten varsa <xref:System.Data.Objects.ObjectContext> ve sorgu veya <xref:System.Data.Objects.MergeOption.AppendOnly> <xref:System.Data.Objects.MergeOption.PreserveChanges> birleştirme seçeneklerini kullanıyorsa, bu aşama performansı etkilemez. Daha fazla bilgi için [bkz: Kimlik Çözümü, Devlet Yönetimi ve Değişiklik İzleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100))|  
  
 <sup>1</sup> Bir veri kaynağı sağlayıcısı bağlantı havuzu uyguladığında, bağlantı açma maliyeti havuz adedine dağıtılır. SQL Server için .NET Sağlayıcısı bağlantı havuzunu destekler.  
  
 <sup>2</sup> Artan sorgu karmaşıklığıyla maliyet artar.  
  
 <sup>3</sup> Toplam maliyet, sorgu tarafından döndürülen nesne sayısıyla orantılı olarak artar.  
  
 <sup>4</sup> EntityClient sorguları nesneler yerine bir <xref:System.Data.EntityClient.EntityDataReader> döndürüldeğinden, bu genel ek bilgi EntityClient sorguları için gerekli değildir. Daha fazla bilgi için Entity [Framework için EntityClient Sağlayıcısı'na](entityclient-provider-for-the-entity-framework.md)bakın.  
  
## <a name="additional-considerations"></a>Ek Hususlar  
 Aşağıda, Varlık Çerçevesi uygulamalarının performansını etkileyebilecek diğer hususlar yer alınmalıdır.  
  
### <a name="query-execution"></a>Sorgu Yürütme  
 Sorgular kaynak yoğun olabileceğinden, kodunuzun hangi noktada ve sorgunun hangi bilgisayarda yürütüleceğini göz önünde bulundurun.  
  
#### <a name="deferred-versus-immediate-execution"></a>Ertelenmiş karşı hemen yürütme  
 Bir <xref:System.Data.Objects.ObjectQuery%601> veya LINQ sorgusu oluşturduğunuzda, sorgu hemen yürütülmeyebilir. Sorgu yürütmesi, `foreach` (C#) veya (Visual Basic) numaralandırma sırasında veya `For Each` bir <xref:System.Collections.Generic.List%601> koleksiyonu doldurmak için atandığında olduğu gibi sonuçlar gerekli olana kadar ertelenir. Sorgu yürütme <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> hemen bir <xref:System.Data.Objects.ObjectQuery%601> yöntem çağırdığınızda veya bir tekton sorgusu döndüren bir <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.Any%2A>LINQ yöntemi çağırdığınızda başlar, gibi veya . Daha fazla bilgi için bkz. [Nesne Sorguları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) ve [Sorgu Yürütme (LinQ to Varlıklar)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>LINQ sorgularının istemci tarafı yürütmesi  
 Linq sorgusunun yürütülmesi veri kaynağını barındıran bilgisayarda gerçekleşse de, LINQ sorgusunun bazı bölümleri istemci bilgisayarda değerlendirilebilir. Daha fazla bilgi için Sorgu Yürütmenin Mağaza Yürütme [bölümüne bakın (LINQ to Ntities)](./language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Sorgu ve Eşleme Karmaşıklığı  
 Tek tek sorguların ve varlık modelindeki eşlemenin karmaşıklığı sorgu performansı üzerinde önemli bir etkiye sahip olacaktır.  
  
#### <a name="mapping-complexity"></a>Harita karmaşıklığı  
 Kavramsal modeldeki varlıklar ve depolama modelindeki tablolar arasındaki basit bire bir eşlemeden daha karmaşık olan modeller, bire bir eşlenebilen modellere göre daha karmaşık komutlar oluşturur.  
  
#### <a name="query-complexity"></a>Sorgu karmaşıklığı  
 Veri kaynağına karşı yürütülen komutlarda çok sayıda birleştirme gerektiren veya büyük miktarda veri döndüren sorgular performansı aşağıdaki şekillerde etkileyebilir:  
  
- Basit görünen kavramsal bir modele karşı sorgular, veri kaynağına karşı daha karmaşık sorguların yürütülmesine neden olabilir. Varlık Çerçevesi, kavramsal bir modele karşı bir sorguyu veri kaynağına karşı eşdeğer bir sorguya çevirdiği için bu durum oluşabilir. Kavramsal modelde tek bir varlık, veri kaynağında birden fazla tabloyla eşlendiğinde veya varlıklar arasındaki ilişki bir birleştirme tablosuna eşlendiğinde, veri kaynağı sorgusuna karşı yürütülen sorgu komutu bir veya daha fazla birleştirme gerektirebilir.  
  
    > [!NOTE]
    > Belirli <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> bir sorgu <xref:System.Data.Objects.ObjectQuery%601> <xref:System.Data.EntityClient.EntityCommand> için veri kaynağına karşı yürütülen komutları görüntülemek için veya sınıfların yöntemini kullanın. Daha fazla bilgi için [bkz: Mağaza Komutlarını görüntüleyin.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))  
  
- İç içe varlık SQL sorguları sunucuda birleştirmeler oluşturabilir ve çok sayıda satır döndürebilir.  
  
     Aşağıdaki, projeksiyon yan tümcesindeki iç içe bir sorgu örneğiverilmiştir:  
  
    ```sql  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ayrıca, bu tür sorgular sorgu ardışık bir iç içe sorgular arasında nesnelerin çoğaltılması ile tek bir sorgu oluşturmak için neden olur. Bu nedenle, tek bir sütun birden çok kez çoğaltılabilir. SQL Server da dahil olmak üzere bazı veritabanlarında, bu, TempDB tablosunun çok büyük büyümesine neden olabilir ve bu da sunucu performansını düşürebilir. İç içe sorguları çalıştırdığınızda dikkatli olunmalıdır.  
  
- Büyük miktarda veri döndüren sorgular, istemci kaynak tüketen işlemleri sonuç kümesinin boyutuyla orantılı bir şekilde gerçekleştiriyorsa performansın düşmesine neden olabilir. Bu gibi durumlarda, sorgu tarafından döndürülen veri miktarını sınırlamayı düşünmelisiniz. Daha fazla bilgi için [bkz: Sorgu Sonuçları Aracılığıyla Sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Varlık Çerçevesi tarafından otomatik olarak oluşturulan komutlar, bir veritabanı geliştiricisi tarafından açıkça yazılmış benzer komutlardan daha karmaşık olabilir. Veri kaynağınıza karşı yürütülen komutlar üzerinde açık denetime ihtiyacınız varsa, tablo değerindeki bir işleve veya depolanan yordama eşleme tanımlamayı düşünün.  
  
#### <a name="relationships"></a>İlişkiler  
 En iyi sorgu performansı için, varlıklar arasındaki ilişkileri hem varlık modelinde ilişkilendirmeler hem de veri kaynağındaki mantıksal ilişkiler olarak tanımlamanız gerekir.  
  
### <a name="query-paths"></a>Sorgu Yolları  
 Varsayılan olarak, bir <xref:System.Data.Objects.ObjectQuery%601>, ilgili nesneleri yürüttettiğinizde döndürülmez (ilişkileri temsil eden nesneler olsa da). İlgili nesneleri üç şekilde yükleyebilirsiniz:  
  
1. Yürütülmeden önce <xref:System.Data.Objects.ObjectQuery%601> sorgu yolunu ayarlayın.  
  
2. Nesnenin `Load` maruz karadığı gezinti özelliğindeki yöntemi arayın.  
  
3. <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> Seçeneğini şu şekilde <xref:System.Data.Objects.ObjectContext> `true`ayarlayın. [Varlık Veri Modeli Tasarımcısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))ile nesne katmanı kodu oluşturduğunuzda bunun otomatik olarak yapıldığını unutmayın. Daha fazla bilgi için [oluşturulan koda genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100))ala.  
  
 Hangi seçeneği kullanacağınızı düşündüğünüzde, veritabanına karşı istek sayısı ile tek bir sorguda döndürülen veri miktarı arasında bir denge olduğunu unutmayın. Daha fazla bilgi için Bkz. [İlgili Nesneleri Yükleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))  
  
#### <a name="using-query-paths"></a>Sorgu yollarını kullanma  
 Sorgu yolları, sorgunun döndürdettiği nesnelerin grafiğini tanımlar. Bir sorgu yolu tanımladığınızda, yolun tanımladığı tüm nesneleri döndürmek için veritabanına karşı yalnızca tek bir istek gerekir. Sorgu yollarının kullanılması, basit görünen nesne sorgularından veri kaynağına karşı yürütülen karmaşık komutlara neden olabilir. Bir veya daha fazla birleştirmenin tek bir sorguda ilgili nesneleri döndürmek için gerekli olması nedeniyle bu oluşur. Bu karmaşıklık, kalıtımlı bir varlık veya çok-çok ilişkileri içeren bir yol gibi karmaşık bir varlık modeline karşı sorgularda daha büyüktür.  
  
> [!NOTE]
> Bir <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> <xref:System.Data.Objects.ObjectQuery%601>. tarafından oluşturulacak komutu görmek için yöntemi kullanın Daha fazla bilgi için [bkz: Mağaza Komutlarını görüntüleyin.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))  
  
 Bir sorgu yolu çok fazla ilgili nesne içeriyorsa veya nesneler çok fazla satır verisi içeriyorsa, veri kaynağı sorguyu tamamlayamayabilir. Bu, sorgu veri kaynağının yeteneklerini aşan ara geçici depolama gerektiriyorsa oluşur. Bu durumda, ilgili nesneleri açıkça yükleyerek veri kaynağı sorgusunun karmaşıklığını azaltabilirsiniz.  
  
#### <a name="explicitly-loading-related-objects"></a>İlgili nesneleri açıkça yükleme  
 Bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601>. döndüren bir `Load` gezinti özelliği üzerinde yöntemi çağırarak ilgili nesneleri açıkça yükleyebilirsiniz. Nesnelerin açıkça yüklenmesi, her çağrıldığında `Load` veritabanına gidiş-dönüş gerektirir.  
  
> [!NOTE]
> deyimi kullandığınızda (Visual Basic'te) `Load` `For Each` döndürülen nesneler topluluğu üzerinden döngü oluştururken ararsanız, veri kaynağına özgü sağlayıcının tek bir bağlantıda birden çok etkin sonuç kümesini desteklemesi gerekir. `foreach` BIR SQL Server veritabanı için sağlayıcı `MultipleActiveResultSets = true` bağlantı dizesinde bir değer belirtmeniz gerekir.  
  
 Varlıklar da yoksa <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> <xref:System.Data.Objects.DataClasses.EntityCollection%601> özellik <xref:System.Data.Objects.DataClasses.EntityReference%601> olmadığında da yöntemi kullanabilirsiniz. Bu, POCO varlıklarını kullanırken kullanışlıdır.  
  
 İlgili nesnelerin açıkça yüklenmesi birleştirme sayısını azaltacak ve gereksiz veri miktarını azaltsa da, `Load` veritabanına yinelenen bağlantılar gerektirir ve bu da çok sayıda nesneyi açıkça yüklerken maliyetli olabilir.  
  
### <a name="saving-changes"></a>Değişiklikleri Kaydetme  
 Bir , <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> bağlam içinde <xref:System.Data.Objects.ObjectContext>eklenen, güncelleştirilen veya silinen her nesne için ayrı bir oluşturma, güncelleştirme veya silme komutu üzerinde yöntem çağırdığınızda. Bu komutlar tek bir işlemde veri kaynağında yürütülür. Sorgularda olduğu gibi, oluşturma, güncelleştirme ve silme işlemlerinin performansı, kavramsal modeldeki eşlemenin karmaşıklığına bağlıdır.  
  
### <a name="distributed-transactions"></a>Dağıtılmış İşlemler  
 Dağıtılmış hareket koordinatörü (DTC) tarafından yönetilen kaynakları gerektiren açık bir işlemdeki işlemler, DTC gerektirmeyen benzer bir işlemden çok daha pahalı olacaktır. DTC'ye terfi aşağıdaki durumlarda gerçekleşecektir:  
  
- Bir SQL Server 2000 veritabanına veya DTC'ye müstehcen hareketleri her zaman tanıtan başka bir veri kaynağına karşı yapılan bir işlemle yapılan açık bir işlem.  
  
- Bağlantı Entity Framework tarafından yönetildiğinde SQL Server 2005'e karşı yapılan bir işlemle açık bir işlem. Bunun nedeni, SQL Server 2005'in, varlık çerçevesinin varsayılan davranışı olan tek bir işlem içinde bir bağlantı kapatıldığında ve yeniden açıldığında DTC'ye terfi etmesidir. Bu DTC promosyonu SQL Server 2008 kullanırken gerçekleşmez. SQL Server 2005'i kullanırken bu promosyonu önlemek için işlem içindeki bağlantıyı açıkça açmanız ve kapatmanız gerekir. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))  
  
 Bir işlem içinde bir veya daha fazla <xref:System.Transactions> işlem yürütüldüğünde açık bir işlem kullanılır. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))  
  
## <a name="strategies-for-improving-performance"></a>Performansı Artırma Stratejileri  
 Aşağıdaki stratejileri kullanarak Varlık Çerçevesi'ndeki sorguların genel performansını artırabilirsiniz.  
  
#### <a name="pre-generate-views"></a>Önceden oluşturma görünümleri  
 Bir varlık modeline dayalı görünüm oluşturma, bir uygulamanın bir sorguyu ilk kez yürütmesi önemli bir maliyettir. Tasarım sırasında projeye eklenebilecek görsel temel veya C# kodu dosyası olarak görünümleri önceden oluşturmak için EdmGen.exe yardımcı programını kullanın. Önceden derlenmiş görünümler oluşturmak için Metin Şablonu Dönüştürme Araç Kiti'ni de kullanabilirsiniz. Önceden oluşturulan görünümler, belirtilen varlık modelinin geçerli sürümüyle tutarlı olduğundan emin olmak için çalışma zamanında doğrulanır. Daha fazla bilgi için [bkz: Sorgu Performansını Artırmak için Görünümleri Önceden Oluştur.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
  
 Çok büyük modellerle çalışırken aşağıdaki hususlar geçerlidir:  
  
 .NET meta veri biçimi, belirli bir ikilideki kullanıcı dize karakter sayısını 16.777.215 (0xFFFFFF) ile sınırlar. Çok büyük bir model için görünüm ler oluşturuyorsanız ve görünüm dosyası bu boyut sınırına ulaşıyorsa, "Daha fazla kullanıcı dizeleri oluşturmak için mantıksal alan kalmaz." hata derlemek. Bu boyut sınırlaması tüm yönetilen ikililer için geçerlidir. Daha fazla bilgi için, büyük ve karmaşık modellerle çalışırken hatadan nasıl kaçınılanın gösteriş yapan [bloga](https://docs.microsoft.com/archive/blogs/appfabriccat/solving-the-no-logical-space-left-to-create-more-user-strings-error-and-improving-performance-of-pre-generated-views-in-visual-studio-net4-entity-framework) bakın.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Sorgular için NoTracking birleştirme seçeneğini kullanmayı düşünün  
 Nesne bağlamında döndürülen nesneleri izlemek için gereken bir maliyet vardır. Nesnelerdeki değişiklikleri algılamak ve aynı mantıksal varlık için birden çok isteğin aynı nesne örneğini döndürmesini sağlamak, nesnelerin bir <xref:System.Data.Objects.ObjectContext> örne eklenmesini gerektirir. Nesnelere güncelleştirmeler veya silmeler yapmayı planlamıyorsanız ve kimlik yönetimi <xref:System.Data.Objects.MergeOption.NoTracking> gerektirmiyorsa, sorguları yürütürken birleştirme seçeneklerini kullanmayı düşünün.  
  
#### <a name="return-the-correct-amount-of-data"></a>Doğru veri miktarını döndürme  
 Bazı senaryolarda, <xref:System.Data.Objects.ObjectQuery%601.Include%2A> yöntemi kullanarak bir sorgu yolu belirtmek çok daha hızlıdır, çünkü veritabanına daha az gidiş dönüş gerektirir. Ancak, diğer senaryolarda, ilgili nesneleri yüklemek için veritabanına ek gidiş-dönüş gezileri daha hızlı olabilir, çünkü daha az birleşimiçeren basit sorgular daha az veri artıklığıyla sonuçlanır. Bu nedenle, ilgili nesneleri almak için çeşitli yolların performansını test öneririz. Daha fazla bilgi için Bkz. [İlgili Nesneleri Yükleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))  
  
 Tek bir sorguda çok fazla veri döndürmeyi önlemek için, sorgunun sonuçlarını daha yönetilebilir gruplara ayırmayı düşünün. Daha fazla bilgi için [bkz: Sorgu Sonuçları Aracılığıyla Sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Nesne Bağlamının kapsamını sınırlandırın  
 Çoğu durumda, bir deyim <xref:System.Data.Objects.ObjectContext> içinde `using` (Visual`Using…End Using` Basic' de) bir örnek oluşturmanız gerekir. Bu, kod ekstre bloğundan çıktığında nesne bağlamıyla ilişkili kaynakların otomatik olarak elden çıkarılmasını sağlayarak performansı artırabilir. Ancak, denetimler nesne bağlamı tarafından yönetilen nesnelere bağlandığında, <xref:System.Data.Objects.ObjectContext> bağlama gerekli olduğu sürece örnek tutulmalıdır ve el ile imha. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Veritabanı bağlantısını el ile açmayı düşünün  
 Uygulamanız oluşturma, güncelleştirme ve veri kaynağına <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> işlemleri silmek için bir dizi nesne sorgusu veya sık sık çağrıda bulunduğunda, Varlık Çerçevesi'nin veri kaynağına olan bağlantıyı sürekli olarak açması ve kapatması gerekir. Bu gibi durumlarda, bu işlemlerin başlangıcında bağlantıyı el ile açmayı ve işlemler tamamlandığında bağlantıyı kapatmayı veya atmayı düşünün. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))  
  
## <a name="performance-data"></a>Performans Verileri  
 Varlık Çerçevesi için bazı performans verileri [ADO.NET takım blogunda](https://docs.microsoft.com/archive/blogs/adonet/)aşağıdaki gönderilerde yayınlanır:  
  
- [ADO.NET Varlık Çerçevesinin Performansını Keşfetmek - Bölüm 1](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-1)  
  
- [ADO.NET Varlık Çerçevesinin Performansını Keşfetmek – Bölüm 2](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-2)  
  
- [ADO.NET Varlık Çerçeve Performans Karşılaştırması](https://docs.microsoft.com/archive/blogs/adonet/ado-net-entity-framework-performance-comparison)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme ve Dağıtım Konuları](development-and-deployment-considerations.md)
