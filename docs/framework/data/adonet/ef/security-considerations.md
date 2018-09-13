---
title: Güvenlik konuları (varlık çerçevesi)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 25d313f9c6f71d946ed8d9cc5db2e99dc84983b3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710894"
---
# <a name="security-considerations-entity-framework"></a>Güvenlik konuları (varlık çerçevesi)
Bu konuda, geliştirme, dağıtma ve çalıştırma için belirli güvenlik konuları açıklanmaktadır. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamalar. Güvenli oluşturmaya yönelik önerileri de izlemelidir [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar. Daha fazla bilgi için [güvenliğine genel bakış](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Genel güvenlik konuları  
 Aşağıdaki güvenlik hususlarını kullanan tüm uygulamalar için uygulama [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Yalnızca güvenilir veri kaynak sağlayıcıları kullanır.  
 Veri kaynağı ile iletişim kurmak için bir sağlayıcı aşağıdakileri yapmanız gerekir:  
  
-   Bağlantı dizesini alma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Veri kaynağının yerel sorgu diline komut ağacı çevir.  
  
-   Birleştirin ve sonuç kümesi döndürür.  
  
 Oturum açma işlemi sırasında kullanıcının parolasını temel bilgileri temel alınan veri kaynağının ağ kitaplıkları sunucuya geçirilir. Kötü amaçlı bir sağlayıcı kullanıcı kimlik bilgilerini çalan, kötü amaçlı sorgular oluşturmak veya sonuç kümesiyle değiştirmesine.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Bağlantınızı hassas verileri korumak için şifreleme.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Doğrudan veri şifreleme işlemez. Kullanıcılar, veri, ortak bir ağ üzerinden erişirseniz, uygulama güvenliğini artırmak için veri kaynağı şifreli bir bağlantı oluşturmanız gerekir. Daha fazla bilgi için veri kaynağınız için güvenlikle ilgili belgelere bakın. SQL Server veri kaynağı için bkz: [SQL Server bağlantılarını şifreleme](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Bağlantı dizesi güvenli hale getirin.  
 Veri kaynağı erişimi korumaya en önemli hedeflerinden bir uygulamanın güvenliğini sağlama andır. Bir bağlantı dizesi, güvenli olmayan veya hatalı oluşturulmuş olası bir güvenlik açığı sunar. Bağlantı bilgilerini düz metin olarak depolamak ya da bellekte kalıcı sisteminizin ödün riski oluşur. Bağlantı dizelerinin güvenliğini sağlamak için önerilen yöntemler şunlardır:  
  
-   Windows kimlik doğrulaması ile SQL Server veri kaynağı kullanın.  
  
     Bağlantı dizesi, bir SQL Server veri kaynağına bağlanmak için Windows kimlik doğrulaması kullandığınızda, oturum açma ve parola bilgilerini içermiyor.  
  
-   Korumalı yapılandırmayı kullanarak yapılandırma dosyasının bölümlerini şifreler.  
  
     ASP.NET sayesinde bir yapılandırma dosyasındaki hassas bilgileri şifrelemek korumalı yapılandırma adı verilen bir özellik sağlar. Öncelikli olarak ASP.NET için tasarlanmış olsa da, Windows uygulamalarını yapılandırma dosyalarında bölümleri şifrelemek için korumalı yapılandırma da kullanabilirsiniz. Yeni korumalı yapılandırma özelliklerinin ayrıntılı bir açıklaması için bkz [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
-   Bağlantı dizeleri, güvenli yapılandırma dosyalarında Store.  
  
     Bağlantı dizelerini kaynak kodunuzda hiçbir zaman ekleme. Bağlantı dizelerini uygulamanızın kodunda eklemek gereğini ortadan kaldırır bir yapılandırma dosyalarında depolayabilir. Varsayılan olarak, varlık veri modeli Sihirbazı bağlantı dizeleri uygulama yapılandırma dosyasında depolar. Yetkisiz erişimi önlemek için bu dosyanın güvenlik altına almanız gerekir.  
  
-   Bağlantı dizesi Oluşturucular, dinamik bir bağlantı oluşturulurken kullanın.  
  
     Bağlantı dizeleri çalışma zamanında oluşturmalıdır kullanırsanız <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfı. Bu dize builder sınıfı doğrulanıyor ve geçersiz giriş bilgileri kaçış bağlantı dizesi ekleme saldırılarını önlemeye yardımcı olur. Daha fazla bilgi için [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Uygun dize builder sınıfı parçası olan veri kaynağı bağlantı dizesi oluşturmak için de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bağlantı dizesi. ADO.NET sağlayıcıları için bağlantı dizesi oluşturucular hakkında daha fazla bilgi için bkz. [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Daha fazla bilgi için [bağlantı bilgilerini koruma](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Güvenilmeyen kullanıcıların bir EntityConnection sunmaz.  
 Bir <xref:System.Data.EntityClient.EntityConnection> nesnesi, temel alınan bağlantı, bağlantı dizesi kullanıma sunar. Erişimi olan bir kullanıcı bir <xref:System.Data.EntityClient.EntityConnection> nesne da değiştirebilir <xref:System.Data.ConnectionState> temel alınan bağlantı. <xref:System.Data.EntityClient.EntityConnection> Sınıf iş parçacığı güvenli değil.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Güvenlik bağlamı dışında bağlantı geçirmeyin.  
 Bağlantı kurulduktan sonra bu güvenlik bağlamı dışında geçmelidir değil. Örneğin, bir bağlantı açmak için izni olan bir iş parçacığı, genel bir konumda bağlantı depolanmamalıdır. Ardından bağlantıyı genel bir konumda kullanılabilir haldeyse, başka bir kötü amaçlı iş parçacığı kendisine verilen bu izin olmadan bağlantı kullanabilirsiniz.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Oturum açma bilgileri ve parolaları içinde bir bellek dökümü görünür olabileceğine dikkat edin.  
 Bağlantı dizesinde veri kaynağı oturum açma ve parola bilgilerini sağlandığında, atık toplama kaynaklarını geri kazanır kadar bu bilgileri bellekte tutulur. Bu, bir parola dizesi artık bellek olmadığında belirlemek mümkün kılar. Bir uygulama çökerse, bir bellek dökümü dosyasına önemli güvenlik bilgileri içerebilir ve uygulama ve herhangi bir kullanıcı bilgisayarda yönetici erişimine sahip çalıştıran kullanıcının bellek dökümü dosyasına görüntüleyebilirsiniz. Microsoft SQL Server bağlantıları için Windows kimlik doğrulaması kullanın.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Kullanıcılar, veri kaynağındaki yalnızca gerekli izinleri verin.  
 Bir veri kaynağı Yöneticisi, kullanıcılara yalnızca gerekli izinleri vermeniz gerekir. Olsa da [!INCLUDE[esql](../../../../../includes/esql-md.md)] değil gibi INSERT, UPDATE veya DELETE, kullanıcıların verileri değiştirme desteği DML deyimleri veri kaynağına bağlantı erişmeye devam edebilirsiniz yapar. Kötü niyetli bir kullanıcı, veri kaynağının dillerinde DML deyimleri yürütmek için bu bağlantıyı kullanabilirsiniz.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>En düşük izinlere sahip uygulamalar çalıştırın.  
 Yönetilen uygulama tam güven iznine çalışmasına izin verdiğinizde [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] bilgisayarınıza uygulamanın erişimi kısıtlamaz. Bu bir güvenlik açığı, uygulamanızdaki tüm sisteminin güvenliğini bozmasına gerek sağlayabilir. Kod erişimi güvenliği ve başka bir güvenlik mekanizması kullanmayı [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], kısmi güven izinleri kullanarak ve en düşük işlev uygulamasını etkinleştirmek için gereken izinler kümesini ile uygulamaları çalıştırmanız gerekir. Aşağıdaki kod erişim izinleri olan en düşük izinleri, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama gereksinimlerine göre:  
  
-   <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> belirtilen meta veri dosyaları açmaya veya <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> meta veri dosyaları için bir dizin aranacak.  
  
-   <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> Entities sorgularında LINQ desteklemek için.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> listeleme için bir <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> özel durumları kullanarak seri hale getirmek için <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Veritabanı bağlantısı açın ve veritabanı komutları gibi yürütecek izni <xref:System.Data.SqlClient.SqlClientPermission> bir SQL Server veritabanı için.  
  
 Daha fazla bilgi için [kod erişimi güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Güvenilmeyen uygulamalar yüklemeyin.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Herhangi bir güvenlik izni zorunlu kılmaz ve bunu güvenilir olup olmamasına bakılmaksızın işlemindeki herhangi bir kullanıcı tarafından sağlanan veri nesnesi kod çağırır. Kimlik doğrulama ve yetkilendirme istemcinin gerçekleştirilir, uygulama ve veri deposu tarafından emin olun.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Tüm yapılandırma dosyaları için erişimi kısıtlayın.  
 Bir yönetici, yapılandırma enterprisesec.config, security.config, machine.conf, dahil olmak üzere, bir uygulama için belirttiğiniz tüm dosyaları ve uygulama yapılandırma dosyasını yazma erişimi kısıtlamanız gerekir \< *uygulama* >. exe.config olarak.  
  
 Sağlayıcının değişmez adı app.config dosyasında değiştirilebilir. İstemci uygulaması, Fabrika modeline güçlü bir ad kullanarak alttaki sağlayıcı standart sağlayıcısı üzerinden erişmek için sorumluluğunu üstlenmelidir.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Model ve eşleme dosyalarını kısıtlayın.  
 Bir yönetici, model ve eşleme dosyalarını (.edmx, .csdl, .ssdl ve .msl) yalnızca model veya eşlemelerini değiştirmek kullanıcılar için yazma erişimi kısıtlamanız gerekir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Yalnızca çalışma zamanında bu dosyalarına yönelik okuma erişimi gerektirir. Yönetici nesne katmanı için de erişimi sınırlamanız gerekir ve tarafından oluşturulan önceden derlenmiş görünümü kaynak kodu dosyaları [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları.  
  
## <a name="security-considerations-for-queries"></a>Sorgular için güvenlik konuları  
 Aşağıdaki güvenlik hususlarını kavramsal model sorgulanırken uygulayın. Bu noktalar uygulamak [!INCLUDE[esql](../../../../../includes/esql-md.md)] EntityClient kullanan sorgular ve LINQ, kullanarak nesne sorgularını [!INCLUDE[esql](../../../../../includes/esql-md.md)]ve Sorgu Oluşturucu yöntemleri.  
  
#### <a name="prevent-sql-injection-attacks"></a>SQL ekleme saldırıları engeller.  
 Uygulamaları sık dış girişi (bir kullanıcı veya başka bir dış aracı) alan ve bu giriş temelinde eylemleri gerçekleştirebilirsiniz. Herhangi bir kullanıcı veya bir dış aracı doğrudan veya dolaylı olarak türetilmiş giriş izinsiz eylemler gerçekleştirmek için hedef dili söz dizimini kullanan içerik olabilir. Hedef dil olduğunda bir yapılandırılmış sorgu dili (SQL), aşağıdakiler gibi [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], bu işleme, SQL ekleme saldırısına bilinir. Kötü niyetli bir kullanıcı sorguyu doğrudan komutları ekleme ve bir veritabanı tablosu bırakın, hizmet reddine neden veya aksi halde gerçekleştirilmekte olan işlemin yapısını değiştirebilirsiniz.  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)] ekleme saldırılarını:  
  
     SQL ekleme saldırılarına karşı yapılabilir [!INCLUDE[esql](../../../../../includes/esql-md.md)] tarafından kötü amaçlı bir sorgu koşulu ve parametre adları kullanılan değerleri giriş sağlama. SQL ekleme riskini önlemek için hiçbir kullanıcı girişi ile birleştirmemelisiniz [!INCLUDE[esql](../../../../../includes/esql-md.md)] komut metni.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular, her yerde değişmez değerleri kabul edildiğini parametreleri kabul eder. Sorguyu doğrudan yerine bir dış aracı ekleme değişmez parametreli sorgular kullanmanız gerekir. Güvenli bir şekilde oluşturmak için Sorgu Oluşturucu yöntemleri kullanmayı da düşünmelisiniz [varlık SQL](https://msdn.microsoft.com/library/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] ekleme saldırılarını:  
  
     Sorgu oluşturmak mümkün olsa da [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], nesne modeli API aracılığıyla gerçekleştirilir. Farklı [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] sorguları, dize düzenlemesi veya birleştirme kullanarak değil oluşur ve bunlar geleneksel SQL ekleme saldırılarına açık değildir.  
  
#### <a name="prevent-very-large-result-sets"></a>Çok büyük sonuç kümelerinin engelleyin.  
 Çok büyük bir sonuç kümesi, istemci sonuç kümesinin boyutuna orantılı kaynak kullanan işlemleri gerçekleştiriliyorsa kapatmak istemci sistemi neden olabilir. Beklenmedik bir şekilde büyük sonuç kümeleri, aşağıdaki koşullarda oluşabilir:  
  
-   Büyük bir veritabanında sorgularda, uygun filtre koşulları dahil değildir.  
  
-   Sorgularda, sunucuda Kartezyen birleştirmeleri oluşturun.  
  
-   İçinde iç içe geçmiş [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgular.  
  
 Kullanıcı girişi kabul ederken giriş sonuç kümeleri sistem başa çıkabilir değerinden daha büyük hale gelmesine neden olamaz emin olmanız gerekir. Ayrıca <xref:System.Linq.Queryable.Take%2A> yönteminde [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] veya [sınırı](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../includes/esql-md.md)] sonuç kümesinin boyutunu sınırlamak için.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Iqueryable sonuçları döndüren ifşa edildi yöntemlere çağıranlar potansiyel olarak güvenilmeyen olduğunda kaçının.  
 Geri dönmekten kaçının <xref:System.Linq.IQueryable%601> potansiyel olarak güvenilmeyen arayanlara aşağıdaki nedenlerle kullanıma sunulan yöntemleri türleri:  
  
-   Kullanıma sunan bir sorgunun bir tüketici bir <xref:System.Linq.IQueryable%601> türü sonuç kümesinin boyutunu artırın veya Güvenli verilerin açığa sonucu üzerinde yöntemleri çağırmak. Örneğin, aşağıdaki yöntem imzasını göz önünde bulundurun:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Bu sorgunun bir tüketici çağırabilir `.Include("Orders")` döndürülen üzerinde `IQueryable<Customer>` sorgu kullanıma sunmak için istediniz değil veri almak için. Bu yöntemin dönüş türünü değiştirerek önlenebilir <xref:System.Collections.Generic.IEnumerable%601> ve bir yöntemi çağırma (gibi `.ToList()`), sonuçları gerçekleştiren.  
  
-   Çünkü <xref:System.Linq.IQueryable%601> sonuçları, üzerinden kullanıma sunan bir sorgunun bir tüketici yinelendiğinde sorguları çalıştırılır bir <xref:System.Linq.IQueryable%601> türü attığı özel durumları yakalamak. Özel durumlar için tüketici amaçlanmaz bilgiler içerebilir.  
  
## <a name="security-considerations-for-entities"></a>Varlıkları için güvenlik konuları  
 Aşağıdaki güvenlik konuları oluşturma ve varlık türleri ile çalışmaktan olduğunda geçerlidir.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Bir Objectcontext'e uygulama etki alanları arasında paylaşmayın.  
 Paylaşımı bir <xref:System.Data.Objects.ObjectContext> ile birden fazla uygulama etki alanı bağlantı dizesindeki bilgiler ortaya çıkarabilir. Bunun yerine, serileştirilmiş nesneler veya nesne grafiklerini diğer uygulama etki alanı denetleyicisine aktarmak ve ardından bu nesnelere ekleyin bir <xref:System.Data.Objects.ObjectContext> uygulama etki alanındaki. Daha fazla bilgi için [nesneleri serileştirmek](https://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### <a name="prevent-type-safety-violations"></a>Tür güvenlik ihlallerini önleyin.  
 Tür güvenliği ihlal edilirse [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nesnelerdeki verilerin bütünlüğünü garanti edemez. Güvenilmeyen uygulamaların tam güvenilir kod erişimi güvenliği çalışmasına izin verirseniz tür güvenlik ihlallerini oluşabilir.  
  
#### <a name="handle-exceptions"></a>Özel durumları işler.  
 Erişim yöntemleri ve özellikleri bir <xref:System.Data.Objects.ObjectContext> bir try-catch bloğu içinde. Özel durumları yakalama engeller girişleri gösterme gelen işlenmeyen özel durumları <xref:System.Data.Objects.ObjectStateManager> veya model bilgileri (örneğin, tablo adları) kullanıcılar için uygulamanızın.  
  
## <a name="security-considerations-for-aspnet-applications"></a>ASP.NET uygulamaları için güvenlik konuları  
 Aşağıdaki yolları ile çalışırken düşünülmesi gereken [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] uygulamalar.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ana yolu denetimleri gerçekleştirir olup olmadığını doğrulayın.  
 Zaman `|DataDirectory|` (kanal sembolleri alınmış) değiştirme dizesi kullanılır, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] çözümlenen yol desteklediğini doğrular. Örneğin, "..." arkasında izin verilmiyor `DataDirectory`. Web uygulaması kök işleci çözmek için aynı denetlemenin (`~`) barındırma işlemi tarafından gerçekleştirilen [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. IIS bu denetimi gerçekleştirir; Bununla birlikte, IIS dışında konakları çözümlenen yol desteklendiğini doğrulayın değil. Dağıttığınız konak davranışı bilmeniz gereken bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Çözümlenen yol adları hakkında varsayımlar yapmayın.  
 Olsa da değerlere kök işleci (`~`) ve `DataDirectory` değiştirme dizesi Çözümle kalmalıdır sabit uygulamanın çalışma zamanı sırasında [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ana bilgisayarın bu değerleri değiştirme kısıtlamaz.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Dağıtımdan önce yol uzunluğu doğrulayın.  
 Dağıtmadan önce bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama emin olmanız gerekir, kök işleci (~) değerlerini ve `DataDirectory` değiştirme dizesi yol uzunluğu işletim sisteminde sınırlarını aşan değil. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri sağlayıcıları yol uzunluğu geçerli sınırlar içinde olduğundan emin olun değil.  
  
## <a name="security-considerations-for-adonet-metadata"></a>ADO.NET meta veriler için güvenlik konuları  
 Aşağıdaki güvenlik konuları oluşturma ve model ve eşleme dosyalarını çalışma uygulayın.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Günlüğe kaydetme üzerinden hassas bilgiler açığa çıkarmayın.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] meta veri hizmet bileşenleri herhangi bir özel bilgi oturum açmayın. Erişim kısıtlamaları nedeniyle döndürülen sonuç yoksa, veritabanı yönetim sistemleri ve dosya sistemleri, hassas bilgiler içerebilir bir özel durum oluşturma yerine sıfır sonuçların döndürülmesi gerekir.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Güvenilir olmayan kaynaklardan gelen MetadataWorkspace nesneleri kabul etmez.  
 Uygulamaları kabul örneklerini <xref:System.Data.Metadata.Edm.MetadataWorkspace> güvenilmeyen kaynaklardan sınıfı. Bunun yerine, açıkça oluşturmak ve gerekir bu tür bir kaynaktan bir çalışma alanı doldurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Geçiş Konuları](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
