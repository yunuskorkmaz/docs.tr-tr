---
title: Güvenlik konuları (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 337424395186532969734e0977ea111d8995a154
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="security-considerations-entity-framework"></a>Güvenlik konuları (Entity Framework)
Bu konuda, geliştirme, dağıtmak ve çalıştırmak için belirli güvenlik konuları açıklanmaktadır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamalar. Öneriler güvenli oluşturmak için izlemeniz gereken [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar. Daha fazla bilgi için bkz: [güvenliğine genel bakış](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Genel güvenlik konuları  
 Aşağıdaki güvenlik hususlarını kullanan tüm uygulamalar için geçerli [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Yalnızca güvenilir veri kaynak sağlayıcıları kullanın.  
 Veri kaynağı ile iletişim kurmak için bir sağlayıcı aşağıdakileri yapmanız gerekir:  
  
-   Bağlantı dizesi alma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Veri kaynağının yerel sorgu dili komutu ağacına çevir.  
  
-   Derleyecek ve sonuç kümesi döndürür.  
  
 Oturum açma işlemi sırasında kullanıcı parolasını temel bilgileri, veri kaynağındaki ağ kitaplıkları sunucuya geçirilir. Kötü amaçlı bir sağlayıcı kullanıcı kimlik bilgilerini çalabilir, kötü amaçlı sorgular oluşturmak veya sonuç kümesiyle değiştirmesine.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Hassas verileri korumak için bağlantınızı şifreleyin.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Doğrudan veri şifrelemesi işlemez. Kullanıcılar verileri ortak bir ağ üzerinden erişirseniz, uygulamanızın güvenliğini artırmak için veri kaynağı şifreli bir bağlantı oluşturmanız gerekir. Daha fazla bilgi için veri kaynağınız için güvenlikle ilgili belgelerine bakın. SQL Server veri kaynağı için [SQL Server bağlantılarını şifreleme](http://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Bağlantı dizesi güvenliğini sağlayın.  
 Veri kaynağınıza erişimi korumaya yönelik en önemli hedeflerini uygulama hale getirirken biridir. Bir bağlantı dizesi, güvenli olmayan veya hatalı oluşturulmuş olası bir güvenlik açığı gösterir. Düz metin olarak bağlantı bilgilerini depolamak ya da bellekte kalır, tüm sisteminizi tehlikeye riski oluşur. Bağlantı dizelerinin güvenliğini sağlamak için önerilen yöntemler şunlardır:  
  
-   Windows kimlik doğrulaması ile bir SQL Server veri kaynağı kullanın.  
  
     Bağlantı dizesi, bir SQL Server veri kaynağına bağlanmak için Windows kimlik doğrulaması kullandığınızda, oturum açma ve parola bilgilerini içermiyor.  
  
-   Yapılandırma dosyası bölümlerinin korumalı Yapılandırması'nı kullanarak şifreler.  
  
     ASP.NET yapılandırma dosyasında hassas bilgileri şifrelemek sağlar korumalı yapılandırma adlı bir özelliği sağlar. Öncelikli olarak ASP.NET için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarını yapılandırma dosyalarında bölümleri şifrelemek için kullanabilirsiniz. Yeni korumalı yapılandırma özellikleri ayrıntılı bir açıklaması için bkz: [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
-   Bağlantı dizeleri, güvenli yapılandırma dosyalarını depolar.  
  
     Kaynak kodunuz hiçbir zaman bağlantı dizelerini katıştırma. Bağlantı dizeleri, uygulamanızın kodda katıştırmak için ortadan kaldırır bir yapılandırma dosyalarında depolayabilir. Varsayılan olarak, varlık veri modeli Sihirbazı bağlantı dizelerini uygulama yapılandırma dosyasında depolar. Yetkisiz erişimi önlemek için bu dosya güvenli gerekir.  
  
-   Bağlantı dizesi oluşturucular dinamik olarak bağlantıları oluşturulurken kullanılır.  
  
     Bağlantı dizeleri çalışma zamanında oluşturmalıdır kullanırsanız <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfı. Bu dize Oluşturucusu sınıfının doğrulama ve geçersiz giriş bilgileri kaçış bağlantı dizesi ekleme saldırıları önlemeye yardımcı olur. Daha fazla bilgi için bkz: [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Ayrıca parçası olan veri kaynağı bağlantı dizesi oluşturmak için uygun dize Oluşturucusu sınıfını kullanmak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bağlantı dizesi. ADO.NET sağlayıcısı için bağlantı dizesi oluşturucular hakkında daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Güvenilmeyen kullanıcıların bir EntityConnection gösterme.  
 Bir <xref:System.Data.EntityClient.EntityConnection> nesne temel bağlantısının bağlantı dizesi kullanıma sunar. Erişimi olan bir kullanıcı bir <xref:System.Data.EntityClient.EntityConnection> nesne da değiştirebilir <xref:System.Data.ConnectionState> temel alınan bağlantı. <xref:System.Data.EntityClient.EntityConnection> Sınıfı iş parçacığı içinde korumalı değil.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Güvenlik bağlamı dışında bağlantı geçmeyin.  
 Bağlantı kurulduktan sonra bu güvenlik bağlamı dışında başarılı gerekir. Örneğin, bir bağlantı açmak için izni olan bir iş parçacığı bağlantı genel bir konumda depolamalısınız değil. Daha sonra bağlantı genel bir konumda kullanılabilir ise, başka bir kötü amaçlı iş parçacığı açıkça ona bu izni olmadan bağlantı Aç kullanabilirsiniz.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Oturum açma bilgileri ve parolaları bir bellek dökümü görünür olabileceğine dikkat edin.  
 Veri kaynağı oturum açma ve parola bilgilerini bağlantı dizesini sağlandığında atık toplama kaynakları geri kazanır kadar bu bilgileri bellekte tutulur. Bu, bir parola dizesi artık bellekte olduğunda belirlemek mümkün kılar. Bir uygulama çökerse bellek dökümü dosyasına hassas güvenlik bilgileri içerebilir ve uygulama ve herhangi bir kullanıcı bilgisayar için yönetici erişimine sahip çalışan kullanıcı bellek dökümü dosyasına görüntüleyebilirsiniz. Microsoft SQL Server bağlantıları için Windows kimlik doğrulaması kullanın.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Kullanıcılar yalnızca veri kaynağındaki gereken izinleri verin.  
 Bir veri kaynağı Yöneticisi, kullanıcılara yalnızca gerekli izinleri vermeniz gerekir. Olsa bile [!INCLUDE[esql](../../../../../includes/esql-md.md)] değil INSERT, UPDATE veya DELETE, kullanıcıların gibi verileri değiştirme destek DML deyimleri veri kaynağı bağlantısı erişmeye devam etmez. Kötü niyetli bir kullanıcı veri kaynağı dillerinde DML deyimlerini yürütmek için bu bağlantıyı kullanabilirsiniz.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Uygulamaları en az izinlerle çalıştırın.  
 Yönetilen bir uygulamanın tam güven izniyle çalışmasına izin verdiğinizde [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] bilgisayarınıza uygulamanın erişimi sınırlamaz. Bu bir güvenlik açığı tüm sistemden uygulamanızda sağlayabilir. Kod erişimi güvenliği ve diğer güvenlik mekanizmaları kullanmayı [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], kısmi güven izinleri kullanarak ve en düşük işlevi uygulamaya etkinleştirmek için gereken izinler kümesini ile uygulamalar çalıştırmanız gerekir. Kod erişim izinleri en düşük izinlerdir, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama gereksinimleri:  
  
-   <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> belirtilen meta veri dosyaları açmaya veya <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> meta veri dosyaları bir dizinde aramak için.  
  
-   <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> Entities sorgularında LINQ desteklemek için.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> içinde listeleme bir <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> kullanarak özel durum seri hale getirmek için <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Bir veritabanı bağlantısı açın ve veritabanında komutları gibi yürütme izni <xref:System.Data.SqlClient.SqlClientPermission> SQL Server veritabanı için.  
  
 Daha fazla bilgi için bkz: [kod erişim güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Güvenilmeyen uygulamalar yüklemeyin.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tüm güvenlik izinleri zorlamaz ve hiçbir kullanıcı tarafından sağlanan veri nesne kodu, güvenilir olup olmamasına bakılmaksızın işleminde çağırır. Kimlik doğrulama ve yetkilendirme istemcinin gerçekleştirilir, uygulama ve veri deposu tarafından emin olun.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Tüm yapılandırma dosyalarına erişimi sınırlayın.  
 Yönetici, yapılandırma dahil enterprisesec.config, security.config, machine.conf, bir uygulama için belirttiğiniz tüm dosyaları ve uygulama yapılandırma dosyasını yazma erişimini kısıtlama gerekir \< *uygulama* >. exe.config.  
  
 Sağlayıcı sabit adı App.config dosyasının içinde değiştirilebilir. İstemci uygulaması sorumluluk temel alınan sağlayıcı standart sağlayıcısı üzerinden erişmek için güçlü bir ad kullanarak Fabrika modeli almanız gerekir.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Eşleme dosyaları ve model için izinleri kısıtlayın.  
 Bir yönetici, modeli ve eşleme dosyaları (.edmx, .csdl, .ssdl ve .msl) yalnızca model veya eşlemelerini değiştirmek kullanıcılar için yazma erişimini kısıtlamanız gerekir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Yalnızca çalışma zamanında bu dosyalarına yönelik okuma erişimi gerektirir. Yönetici ayrıca nesne katmanına erişimi kısıtlamalısınız ve tarafından oluşturulan kaynak kodu dosyaları önceden derlenmiş görüntüleyin [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları.  
  
## <a name="security-considerations-for-queries"></a>Sorgular için güvenlik konuları  
 Aşağıdaki güvenlik hususlarını kavramsal model sorgulanırken uygulayın. Bu noktalar uygulamak [!INCLUDE[esql](../../../../../includes/esql-md.md)] EntityClient kullanan sorgular ve LINQ, kullanarak nesne sorguları [!INCLUDE[esql](../../../../../includes/esql-md.md)]ve Sorgu Oluşturucu yöntemleri.  
  
#### <a name="prevent-sql-injection-attacks"></a>SQL ekleme saldırılarını önler.  
 Uygulamaları sık dış giriş (bir kullanıcı veya başka bir dış aracı) alın ve bu girişinize göre eylemleri gerçekleştirebilirsiniz. Tüm kullanıcı veya bir dış aracı doğrudan veya dolaylı olarak türetilmiş giriş izinsiz eylemler gerçekleştirmek için hedef dil söz dizimini kullanan içerik olabilir. Hedef dil olduğunda bir yapılandırılmış sorgu dili (SQL), aşağıdaki gibi [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], bu işleme bir SQL ekleme saldırısı bilinir. Kötü niyetli bir kullanıcının sorguyu doğrudan komutlar ekleme ve bir veritabanı tablosu bırakın, hizmet reddine neden veya aksi halde gerçekleştirilmekte olan işlemin doğası değiştirebilirsiniz.  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)] ekleme saldırıları:  
  
     SQL ekleme saldırıları yapılabilir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kötü amaçlı bir sorgu koşulu ve parametre adları kullanılan değerleri giriş sağlayarak. SQL ekleme riskini önlemek için hiç kullanıcı girişi ile birleştirmelisiniz [!INCLUDE[esql](../../../../../includes/esql-md.md)] komut metni.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] Sorgu parametreleri değişmez değerleri kabul edildiğini her yerde kabul eder. Sorguyu doğrudan bir dış aracının injecting değişmez değerler yerine parametreli sorgular kullanmanız gerekir. Güvenli bir şekilde oluşturmak için Sorgu Oluşturucu yöntemleri kullanarak de dikkate almalısınız [varlık SQL](http://msdn.microsoft.com/library/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] ekleme saldırıları:  
  
     Sorgu oluşturma mümkün olsa da [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], nesne modeli API'si gerçekleştirilir. Farklı [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorguları, [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] sorguları, dize düzenlemesi veya birleştirme kullanarak değil oluşur ve geleneksel SQL ekleme saldırılara açık değildir.  
  
#### <a name="prevent-very-large-result-sets"></a>Çok büyük sonuç kümeleri engeller.  
 Çok büyük bir sonuç kümesi istemci sonuç kümesi boyutuna orantılı kaynaklarını tüketebilir işlemleri çalışıyorsa kapatmak istemci sistemin neden olabilir. Beklenmedik bir şekilde büyük sonuç kümeleri aşağıdaki koşullarda oluşabilir:  
  
-   Büyük bir veritabanı sorguları, uygun filtre koşulları dahil etmeyin.  
  
-   Sorgularda, sunucuda Kartezyen birleştirmeler oluşturun.  
  
-   İçinde iç içe geçmiş [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular.  
  
 Kullanıcı girişi kabul ederken giriş sonuç kümeleri sistem ele alabilir değerinden daha büyük hale gelmesine sebep olamaz emin olmanız gerekir. Aynı zamanda <xref:System.Linq.Queryable.Take%2A> yönteminde [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] veya [sınırı](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../includes/esql-md.md)] sonuç kümesi boyutunu sınırlamak için.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Arayanlar sunan yöntemlere potansiyel olarak güvenilmeyen zaman Iqueryable sonuçları döndüren kaçının.  
 Döndürme kaçının <xref:System.Linq.IQueryable%601> potansiyel olarak güvenilmeyen arayanlara aşağıdaki nedenlerle sunulan yöntemleri türlerinden:  
  
-   Bir tüketici kullanıma sunan bir sorgunun bir <xref:System.Linq.IQueryable%601> türü, güvenli veri kullanıma sunmak veya sonuç kümesi boyutunu artırın sonucuna yöntemleri çağrısı. Örneğin, aşağıdaki yöntemi imzası göz önünde bulundurun:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Bu sorgunun bir tüketici çağırabilirsiniz `.Include("Orders")` döndürülen üzerinde `IQueryable<Customer>` sorgu kullanıma sunmak için istiyordunuz değil veri alınamadı. Bu yöntemin dönüş türünü değiştirerek önlenebilir <xref:System.Collections.Generic.IEnumerable%601> ve bir yöntemi çağırma (aşağıdaki gibi `.ToList()`) sonuçları gerçeğe.  
  
-   Çünkü <xref:System.Linq.IQueryable%601> sorgu sonuçları gösterir query tüketicisi üzerinden, yinelendiğinde yürütülen bir <xref:System.Linq.IQueryable%601> türü oluşturulan özel durumları yakalama. Özel durumlar için tüketici amaçlanmamıştır bilgiler içerebilir.  
  
## <a name="security-considerations-for-entities"></a>Varlıklar için güvenlik konuları  
 Aşağıdaki güvenlik hususlarını oluşturma ve varlık türleri ile çalışma olduğunda geçerlidir.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Bir ObjectContext uygulama etki alanları arasında paylaşmayın.  
 Paylaşımı bir <xref:System.Data.Objects.ObjectContext> ile birden fazla uygulama etki alanı bilgileri bağlantı dizesinde getirebilir. Bunun yerine, serileştirilmiş nesneler veya nesne grafiklerinin diğer uygulama etki alanı denetleyicisine aktarmak ve ardından bu nesnelerle ekleyin bir <xref:System.Data.Objects.ObjectContext> bu uygulama etki alanındaki. Daha fazla bilgi için bkz: [seri hale getirme nesnelerini](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### <a name="prevent-type-safety-violations"></a>Tür güvenlik ihlallerini engeller.  
 Tür güvenliği ihlal edilirse [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nesnelerindeki veri bütünlüğünü garanti edemez. Güvenilmeyen uygulamaların tam güven kod erişim güvenliği ile çalışmasına izin ver tür güvenlik ihlallerini oluşabilir.  
  
#### <a name="handle-exceptions"></a>Özel durumları işleme.  
 Erişim yöntemleri ve özellikleri bir <xref:System.Data.Objects.ObjectContext> try-catch bloğu içinde. Özel durumları yakalama engeller girişlerinde gösterme gelen işlenmeyen özel durumlar <xref:System.Data.Objects.ObjectStateManager> veya model bilgileri (örneğin, tablo adları) kullanıcılar için uygulamanızın.  
  
## <a name="security-considerations-for-aspnet-applications"></a>ASP.NET uygulamaları için güvenlik konuları  
 Yollarında ile çalışırken aşağıdaki düşünülmesi gereken [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] uygulamalar.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ana yol denetimleri gerçekleştirip gerçekleştirmediğini doğrulayın.  
 Zaman `|DataDirectory|` (kanal sembolleri alınmış) değiştirme dizesi kullanılır, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] çözümlenen yol desteklediğini doğrular. Örneğin, "..." arkasında izin verilmiyor `DataDirectory`. Web uygulaması kök işleci çözmek için aynı onay (`~`) barındırma işlemi tarafından gerçekleştirilen [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. IIS, bu denetimi gerçekleştirir; Bununla birlikte, IIS dışındaki ana çözümlenen yol desteklendiğini doğrulayın değil. Ana bilgisayar üzerinde dağıttığınız davranışını bilmeniz gereken bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Çözümlenen yol adları hakkında varsayımlar yapmayın.  
 Ancak, değerlere kök işleci (`~`) ve `DataDirectory` değiştirme dizesi Çöz kalır sabit uygulamanın çalışma zamanı sırasında [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bu değerleri değiştirme ana bilgisayarın kısıtlamaz.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Dağıtımdan önce yol uzunluğu doğrulayın.  
 Dağıtmadan önce bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulaması emin olun, kök işleci (~) değerlerini ve `DataDirectory` değiştirme dizesi işletim sistemindeki yol uzunluğu sınırı aşmadığından. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri sağlayıcıları, yol uzunluğu geçerli sınırlarda olduğundan emin olursunuz.  
  
## <a name="security-considerations-for-adonet-metadata"></a>ADO.NET meta veriler için güvenlik konuları  
 Oluşturma ve model ve eşleme dosyaları ile çalışırken aşağıdaki güvenlik hususlarını uygulayın.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Günlüğe kaydetme aracılığıyla hassas bilgilerin açığa çıkarmaz.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] meta veri hizmet bileşenleri herhangi bir özel bilgi oturum açılamıyor. Erişim kısıtlamaları nedeniyle döndürülen sonuç yoksa veritabanı yönetim sistemleri ve dosya sistemleri, hassas bilgiler içeren bir özel durum oluşturma yerine sıfır sonuçların döndürülmesi gerekir.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Güvenilir olmayan kaynaklardan gelen MetadataWorkspace nesneleri kabul etmez.  
 Uygulamaları kabul örneklerini <xref:System.Data.Metadata.Edm.MetadataWorkspace> güvenilir olmayan kaynaklardan gelen sınıfı. Bunun yerine, açıkça oluşturun ve bu tür bir kaynaktan bir çalışma alanı doldurmak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Geçiş Konuları](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
