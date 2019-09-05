---
title: Güvenlik konuları (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: d1fb104f336938cc83d53cae71a8132f9b648dc6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248548"
---
# <a name="security-considerations-entity-framework"></a>Güvenlik konuları (Entity Framework)
Bu konuda, uygulamaları geliştirmeye, dağıtmaya ve çalıştırmaya [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] özgü güvenlik konuları açıklanmaktadır. Ayrıca, güvenli .NET Framework uygulamalar oluşturmaya yönelik önerileri de izlemeniz gerekir. Daha fazla bilgi için bkz. [Güvenliğe genel bakış](../security-overview.md).  
  
## <a name="general-security-considerations"></a>Genel güvenlik konuları  
 Aşağıdaki güvenlik konuları, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]kullanan tüm uygulamalar için geçerlidir.  
  
#### <a name="use-only-trusted-data-source-providers"></a>Yalnızca güvenilir veri kaynağı sağlayıcıları kullanın.  
 Bir sağlayıcının veri kaynağıyla iletişim kurması için aşağıdakileri yapması gerekir:  
  
- ' Dan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]bağlantı dizesini alın.  
  
- Komut ağacını veri kaynağının yerel sorgu diline çevirin.  
  
- Sonuç kümelerini birleştirin ve döndürün.  
  
 Oturum açma işlemi sırasında, Kullanıcı parolasını temel alan bilgiler, temel alınan veri kaynağının ağ kitaplıkları aracılığıyla sunucusuna geçirilir. Kötü amaçlı bir sağlayıcı Kullanıcı kimlik bilgilerini çalabilir, kötü amaçlı sorgular oluşturabilir veya sonuç kümesiyle daha fazla oynayabilir.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Hassas verileri korumak için bağlantınızı şifreleyin.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veri şifrelemeyi doğrudan işlemez. Kullanıcılar bir genel ağ üzerinden verilere erişebilirse, uygulamanızın güvenliği artırmak için veri kaynağıyla şifreli bir bağlantı kurması gerekir. Daha fazla bilgi için, veri kaynağınıza yönelik güvenlikle ilgili belgelere bakın. SQL Server veri kaynağı için bkz. [SQL Server bağlantıları şifreleme](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Bağlantı dizesinin güvenliğini sağlayın.  
 Veri kaynağınıza erişimi korumak, bir uygulamayı güvenli hale getirirken en önemli amaçlardan biridir. Bir bağlantı dizesi, güvenliği sağlanmayacaksa veya yanlış oluşturulursa, olası bir güvenlik açığı sunar. Bağlantı bilgilerini düz metin olarak depoladığınızda veya bellekte kalıcı hale getirikten, sisteminizin tamamını tehlikeye atdığınızda. Bağlantı dizelerini güvenli hale getirmek için önerilen yöntemler aşağıda verilmiştir:  
  
- Windows kimlik doğrulamasını bir SQL Server veri kaynağıyla kullanın.  
  
     SQL Server veri kaynağına bağlanmak için Windows kimlik doğrulaması kullandığınızda bağlantı dizesinde oturum açma ve parola bilgileri bulunmaz.  
  
- Korumalı yapılandırmayı kullanarak yapılandırma dosyası bölümlerini şifreleyin.  
  
     ASP.NET, bir yapılandırma dosyasındaki hassas bilgileri şifrelemenizi sağlayan korumalı yapılandırma adlı bir özellik sağlar. Birincil olarak ASP.NET için tasarlanmış olsa da, Windows uygulamalarındaki yapılandırma dosyalarının bölümlerini şifrelemek için korumalı yapılandırma ' yı da kullanabilirsiniz. Yeni korunan yapılandırma özelliklerine ilişkin ayrıntılı bir açıklama için bkz. [korumalı yapılandırma kullanarak yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
- Bağlantı dizelerini güvenli yapılandırma dosyalarında depolayın.  
  
     Kaynak kodunuza asla bağlantı dizelerini katıştırmanız gerekir. Bağlantı dizelerini, uygulamanızın koduna ekleme gereksinimini ortadan kaldıran yapılandırma dosyalarında depolayabilirler. Varsayılan olarak, Varlık Veri Modeli Sihirbazı bağlantı dizelerini uygulama yapılandırma dosyasında depolar. Yetkisiz erişimi engellemek için bu dosyayı güvenli hale getirin.  
  
- Bağlantıları dinamik olarak oluştururken bağlantı dizesi oluşturucuları kullanın.  
  
     Çalışma zamanında bağlantı dizeleri oluşturmanız gerekiyorsa, <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfını kullanın. Bu dize Oluşturucu sınıfı, geçersiz giriş bilgilerini doğrulayarak ve aşarak bağlantı dizesi ekleme saldırılarını önlemeye yardımcı olur. Daha fazla bilgi için [nasıl yapılır: Bir EntityConnection bağlantı dizesi](how-to-build-an-entityconnection-connection-string.md)oluşturun. Ayrıca, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] bağlantı dizesinin parçası olan veri kaynağı bağlantı dizesini oluşturmak için uygun dize Oluşturucu sınıfını kullanın. ADO.NET sağlayıcıları için bağlantı dizesi oluşturucuları hakkında daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../connection-string-builders.md).  
  
 Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Bir EntityConnection 'ı güvenilmeyen kullanıcılarla kullanıma sunma.  
 Bir <xref:System.Data.EntityClient.EntityConnection> nesne, temel alınan bağlantının bağlantı dizesini gösterir. Bir <xref:System.Data.EntityClient.EntityConnection> nesneye erişimi olan bir Kullanıcı, <xref:System.Data.ConnectionState> temel alınan bağlantının öğesini de değiştirebilir. Sınıf <xref:System.Data.EntityClient.EntityConnection> , iş parçacığı güvenli değil.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Bağlantıları güvenlik bağlamı dışında geçirmeyin.  
 Bir bağlantı kurulduktan sonra, onu güvenlik bağlamı dışına iletmemelidir. Örneğin, bir bağlantıyı açma iznine sahip bir iş parçacığı bağlantıyı genel bir konumda depomamalıdır. Bağlantı genel bir konumda kullanılabiliyorsa, başka bir kötü amaçlı iş parçacığı bu izne açıkça verilmeden açık bağlantıyı kullanabilir.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Oturum açma bilgilerinin ve parolaların bir bellek dökümünde görünebilir olabileceğini unutmayın.  
 Bağlantı dizesinde veri kaynağı oturum açma ve parola bilgileri sağlandığında bu bilgiler, atık toplama geri kazanır kaynaklara kadar bellekte tutulur. Bu, bir parola dizesinin artık bellekte ne zaman kalmadığını belirlemeyi olanaksız hale getirir. Bir uygulama kilitlenirse, bir bellek dökümü dosyası gizli güvenlik bilgileri içerebilir ve uygulamayı çalıştıran kullanıcı ve bilgisayara yönetici erişimi olan herhangi bir Kullanıcı, bellek dökümü dosyasını görüntüleyebilir. Microsoft SQL Server bağlantılar için Windows kimlik doğrulamasını kullanın.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Kullanıcılara yalnızca veri kaynağında gerekli izinleri verin.  
 Bir veri kaynağı Yöneticisi yalnızca kullanıcılara gerekli izinleri vermelidir. [!INCLUDE[esql](../../../../../includes/esql-md.md)] INSERT, Update veya DELETE gibi verileri değiştiren DML deyimlerini desteklemeseler de, kullanıcılar veri kaynağı bağlantısına erişmeye devam edebilir. Kötü amaçlı bir Kullanıcı bu bağlantıyı, veri kaynağının yerel dilinde DML deyimlerini yürütmek için kullanabilir.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Uygulamaları minimum izinlerle çalıştırın.  
 Yönetilen bir uygulamanın tam güven izniyle çalışmasına izin vermek için .NET Framework, uygulamanın bilgisayarınıza erişimini sınırlamaz. Bu, uygulamanızdaki bir güvenlik açığını sistemin tüm güvenliğinin aşılmasına olanak tanıyabilir. .NET Framework kod erişimi güvenliğini ve diğer güvenlik mekanizmalarını kullanmak için, uygulamaları kısmi güven izinleri kullanarak ve uygulamanın çalışmasını sağlamak için gereken minimum izin kümesiyle çalıştırmalısınız. Aşağıdaki kod erişim izinleri, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamanız için gereken en düşük izinlerdir:  
  
- <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> belirtilen meta veri dosyalarını açmak veya <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> meta veri dosyaları için bir dizin aramak için.  
  
- <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> LINQ to Entities sorguları desteklemek için.  
  
- <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> bir <xref:System.Transactions> öğesinegörelisteleme<xref:System.Transactions.Transaction>.  
  
- <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> arabirimini<xref:System.Runtime.Serialization.ISerializable> kullanarak özel durumları seri hale getirmek için.  
  
- Veritabanı bağlantısı açma ve veritabanı <xref:System.Data.SqlClient.SqlClientPermission> için bir SQL Server veritabanı gibi komutları yürütme izni.  
  
 Daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](../code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Güvenilmeyen uygulamalar yüklemeyin.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Herhangi bir güvenlik izinlerini zorlamaz ve güvenilir olup olmamasına bakılmaksızın işlem içinde Kullanıcı tarafından sağlanan veri nesne kodu çağırır. İstemcinin kimlik doğrulamasının ve yetkilendirmesinin, veri deposu ve uygulamanız tarafından gerçekleştirildiğinden emin olun.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Tüm yapılandırma dosyalarına erişimi kısıtlayın.  
 Bir yöneticinin, enterprisesec. config, Security. config, Machine. conf ve uygulama yapılandırma dosyası \< *uygulaması*> dahil olmak üzere bir uygulama için yapılandırmayı belirten tüm dosyalara yazma erişimini kısıtlamalı olması gerekir. exe. config.  
  
 Sağlayıcı sabit adı App. config dosyasında değiştirilebilir. İstemci uygulaması, bir güçlü ad kullanarak standart sağlayıcı fabrikası aracılığıyla temel sağlayıcıya erişim sorumluluğunu almalıdır.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Model ve eşleme dosyalarıyla izinleri kısıtlayın.  
 Bir yöneticinin model ve eşleme dosyalarına (. edmx,. csdl,. ssdl ve. MSL) yazma erişimini kısıtlamalı ve yalnızca modeli veya eşlemeleri değiştiren kullanıcılara kısıtlama gerekir. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Yalnızca çalışma zamanında bu dosyalara okuma erişimi gerektirir. Yönetici ayrıca, Varlık Veri Modeli araçları tarafından oluşturulan nesne katmanına ve önceden derlenmiş görünüm kaynak kodu dosyalarına erişimi kısıtlamalı.  
  
## <a name="security-considerations-for-queries"></a>Sorgular için güvenlik konuları  
 Kavramsal model sorgulanırken aşağıdaki güvenlik konuları geçerlidir. Bu noktalar, EntityClient [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanan sorgular ve LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]ve sorgu Oluşturucu yöntemleri kullanılarak nesne sorguları için geçerlidir.  
  
#### <a name="prevent-sql-injection-attacks"></a>SQL ekleme saldırılarını önleyin.  
 Uygulamalar genellikle dış giriş alır (bir kullanıcı veya başka bir harici aracıdan) ve bu girişe göre eylemler gerçekleştirir. Kullanıcı veya dış aracıdan doğrudan veya dolaylı olarak türetilen tüm girişler, yetkisiz eylemler gerçekleştirmek için hedef dilin söz dizimini kullanan içeriğe sahip olabilir. Hedef dil Transact-SQL gibi bir Yapılandırılmış Sorgu Dili (SQL) olduğunda, bu işleme SQL ekleme saldırısı olarak bilinir. Kötü niyetli bir Kullanıcı, komutları doğrudan sorguya ekleyebilir, bir veritabanı tablosunu bırakabilir, hizmet reddine neden olabilir veya gerçekleştirilen işlemin yapısını değiştirebilir.  
  
- [!INCLUDE[esql](../../../../../includes/esql-md.md)]ekleme saldırıları:  
  
     SQL ekleme saldırıları ' de [!INCLUDE[esql](../../../../../includes/esql-md.md)] , bir sorgu koşulunda ve parametre adlarında kullanılan değerlere kötü amaçlı giriş sağlayarak gerçekleştirilebilir. SQL ekleme riskinden kaçınmak için, Kullanıcı girişini hiçbir şekilde [!INCLUDE[esql](../../../../../includes/esql-md.md)] komut metniyle birleştirmelisiniz.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)]sorgular, sabit değerlerin kabul edildiği her yerde parametreleri kabul eder. Harici bir aracıdan doğrudan sorguya ekleme sabit değerleri yerine parametreli sorgular kullanmanız gerekir. Ayrıca, Entity SQL güvenli bir şekilde oluşturmak için [Sorgu Oluşturucu yöntemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100)) kullanmayı göz önünde bulundurmanız gerekir.  
  
- LINQ to Entities ekleme saldırıları:  
  
     Sorgu kompozisyonu LINQ to Entities mümkün olsa da, nesne modeli API 'SI aracılığıyla yapılır. Sorguların [!INCLUDE[esql](../../../../../includes/esql-md.md)] aksine, LINQ to Entities sorguları dize düzenleme veya birleştirme kullanılarak oluşmazlar ve geleneksel SQL ekleme saldırılarına maruz kalabilir.  
  
#### <a name="prevent-very-large-result-sets"></a>Çok büyük sonuç kümelerini önleyin.  
 Çok büyük bir sonuç kümesi, istemci, kaynakları sonuç kümesinin boyutuyla orantılı şekilde kullanan işlemler yapıyorsa istemci sistemin kapatılmasını sağlayabilir. Beklenmedik şekilde büyük sonuç kümeleri aşağıdaki koşullarda oluşabilir:  
  
- Uygun filtre koşullarını içermeyen büyük bir veritabanına göre sorgular.  
  
- Sunucuda Kartezyen birleştirmeler oluşturan sorgularda.  
  
- İç içe [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgularda.  
  
 Kullanıcı girişini kabul ettiğinizde, girişin sonuç kümelerinin sistem tarafından işleyebileceğinden daha büyük olmasına neden olduğundan emin olmanız gerekir. Sonuç kümesinin boyutunu sınırlamak için <xref:System.Linq.Queryable.Take%2A> LINQ to Entities veya ' [!INCLUDE[esql](../../../../../includes/esql-md.md)] de [LIMIT](./language-reference/limit-entity-sql.md) işleci içindeki yöntemi de kullanabilirsiniz.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Potansiyel olarak güvenilmeyen arayanlara Yöntemler oluştururken IQueryable sonuçlarının Döndürülmekten kaçının.  
 Potansiyel olarak <xref:System.Linq.IQueryable%601> güvenilmeyen çağıranlara gösterilen metotlardan türler aşağıdaki nedenlerle döndürülmekten kaçının:  
  
- Bir <xref:System.Linq.IQueryable%601> tür sunan sorgunun tüketicisi, güvenli verileri açığa çıkaran veya sonuç kümesinin boyutunu artıran sonuç üzerinde Yöntemler çağırabilir. Örneğin, aşağıdaki yöntem imzasını göz önünde bulundurun:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Bu sorgunun bir tüketicisi, sorgunun açığa `.Include("Orders")` çıkarmak istemediğiniz verileri `IQueryable<Customer>` almak için döndürülen üzerinde çağırabilir. Bu durum, yöntemin <xref:System.Collections.Generic.IEnumerable%601> dönüş türünün ( `.ToList()`gibi) sonuçları üreten bir yöntemi (gibi) değiştirip çağırarak önlenebilir.  
  
- Sonuçlar üzerinde yinelendiğinde <xref:System.Linq.IQueryable%601> sorgularyürütüldüğüiçin,birtürsunansorgununbirtüketicisioluşturulan<xref:System.Linq.IQueryable%601> özel durumları yakalayabilir. Özel durumlar, tüketiciye yönelik tasarlanmamış bilgiler içerebilir.  
  
## <a name="security-considerations-for-entities"></a>Varlıklara yönelik güvenlik konuları  
 Aşağıdaki güvenlik konuları, oluşturma ve varlık türleriyle çalışırken geçerlidir.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Uygulama etki alanları arasında bir ObjectContext paylaşmayın.  
 Birden fazla uygulama etki alanı ilepaylaşma,bağlantıdizesindebilgisunabilir.<xref:System.Data.Objects.ObjectContext> Bunun yerine, seri hale getirilmiş nesneleri veya nesne grafiklerini diğer uygulama etki alanına aktarmanız ve ardından bu nesneleri bu uygulama etki <xref:System.Data.Objects.ObjectContext> alanında bir öğesine eklemeniz gerekir. Daha fazla bilgi için bkz. [nesneleri serileştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
#### <a name="prevent-type-safety-violations"></a>Tür güvenliği ihlallerini engelleyin.  
 Tür güvenliği ihlal edilirse [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , nesnelerdeki verilerin bütünlüğünü garanti edemez. Güvenilmeyen uygulamaların tam güvenle kod erişim güvenliği ile çalışmasına izin verirseniz tür güvenlik ihlalleri oluşabilir.  
  
#### <a name="handle-exceptions"></a>Özel durumları işleyin.  
 Try-catch bloğunun <xref:System.Data.Objects.ObjectContext> içindeki yöntem ve özelliklere erişin. Yakalama özel durumları, işlenmeyen özel durumların, <xref:System.Data.Objects.ObjectStateManager> veya model bilgilerinde (tablo adları gibi) uygulamanızın kullanıcılarına sunulmasını önler.  
  
## <a name="security-considerations-for-aspnet-applications"></a>ASP.NET uygulamaları için güvenlik konuları  

ASP.NET uygulamalarında yollarla çalışırken aşağıdakileri göz önünde bulundurmanız gerekir.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ana bilgisayarınızda yol denetimleri yapıp gerçekleştirmediğini doğrulayın.  
 `|DataDirectory|` (Kanal sembolleri içine alınmış) değiştirme dizesi kullanıldığında, ADO.net çözümlenen yolun desteklendiğini doğrular. Örneğin, ".." arkasında `DataDirectory`yer verilmez. Web uygulaması kök işlecini (`~`) çözümlemek için aynı denetim, ASP.NET barındırma işlemi tarafından gerçekleştirilir. IIS bu denetimi gerçekleştirir; Ancak, IIS dışındaki konaklar çözümlenen yolun desteklendiğini doğrulayamayabilir. Bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamayı dağıttığınız konağın davranışını bilmeniz gerekir.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Çözümlenmiş yol adları hakkında varsayımlar yapmayın.  
 Kök işlecinin (`~`) `DataDirectory` ve değiştirme dizesinin çözümlenme değerlerinin [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamanın çalışma zamanı sırasında sabit kalması gerekir, ancak konağın bu değerleri değiştirmesini kısıtlamaz.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Dağıtımdan önce yol uzunluğunu doğrulayın.  
 Bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamayı dağıtılmadan önce, kök işlecinin (~) ve `DataDirectory` değiştirme dizesinin değerlerinin işletim sistemindeki yol uzunluğunun sınırlarını aşmadığından emin olmalısınız. ADO.NET veri sağlayıcıları, yol uzunluğunun geçerli sınırlar dahilinde olmasını sağlamaz.  
  
## <a name="security-considerations-for-adonet-metadata"></a>ADO.NET meta verileri için güvenlik konuları  
 Model ve eşleme dosyalarını oluştururken ve bunlarla çalışırken aşağıdaki güvenlik konuları geçerlidir.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Günlüğe kaydetme yoluyla hassas bilgileri gösterme.  
ADO.NET meta veri hizmeti bileşenleri özel bilgileri günlüğe almaz. Erişim kısıtlamaları nedeniyle döndürülebilecek sonuçlar varsa, veritabanı yönetim sistemleri ve dosya sistemleri, hassas bilgiler içerebilecek bir özel durum yerine sıfır sonuç döndürmelidir.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Güvenilmeyen kaynaklardan MetadataWorkspace nesnelerini kabul etmez.  
 Uygulamalar, <xref:System.Data.Metadata.Edm.MetadataWorkspace> güvenilmeyen kaynaklardan sınıfının örneklerini kabul etmemelidir. Bunun yerine, bir çalışma alanını açıkça bir kaynaktan oluşturmanız ve doldurmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [Dağıtım Konuları](deployment-considerations.md)
- [Geçiş Konuları](migration-considerations.md)
