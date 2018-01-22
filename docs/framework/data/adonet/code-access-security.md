---
title: "Kod erişimi güvenliği ve ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e69073f757c07c5dd262900d4d8f7ad2cc83cdc4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="code-access-security-and-adonet"></a>Kod erişimi güvenliği ve ADO.NET
.NET Framework rol tabanlı güvenlik yanı sıra kod erişim güvenliği (CAS), her ikisi de ortak dil çalışma zamanı tarafından (CLR) sağlanan ortak bir altyapı kullanılarak uygulanan sunar. Yönetilmeyen kod dünyasında uygulamaların çoğu kullanıcı veya asıl izinlerle yürütün. Sonuç olarak, bilgisayar sistemleri kötü amaçlı olduğunda tehlikeye bozuk ve özel veri olabilir veya yazılım hatası doldurulmuş bir kullanıcı tarafından yükseltilmiş ayrıcalıklarla çalıştırın.  
  
 Bunun aksine, .NET Framework yönetilen kod yürütme kodu tek başına uygulanabilir kod erişim güvenliği içerir. Kod çalıştırılmasına izin olup kodun kaynak veya kodun kimlik, kimliği değil yalnızca asıl diğer yönlerini bağlıdır değil. Bu yönetilen olasılığını azaltır kodu olabilir.  
  
## <a name="code-access-permissions"></a>Kod Erişim İzinleri  
 Kod yürütüldüğünde, CLR güvenlik sistemi tarafından değerlendirilir kanıt sunar. Genellikle, bu bulgu kaynak URL, site ve bölge ve derlemenin emin olun dijital imzalar dahil olmak üzere kod oluşur.  
  
 CLR kodu gerçekleştirmek için izni olan işlemleri gerçekleştirmek için kod sağlar. Kod izinleri isteyebilir ve bu istekleri yönetici tarafından ayarlanan güvenlik ilkesini temel alarak dikkate alınır.  
  
> [!NOTE]
>  CLR yürütülen kod kendisini izinleri olamaz. Örneğin, kod isteyebilir ve bir güvenlik ilkesi sağlar, ancak hiçbir zaman daha fazla izin verilen daha az izin verilmesi. İzin verme, hiçbir izinlerle hiç başlatın ve sonra gerçekleştirilen belirli bir görev için dar izinleri ekleyin. Tüm izinleri ile başlayan ve tek tek olanları engelleme müşteri adayları gerekli daha fazla izin verme gelen istenmeyen güvenlik açıklarını içerebilir güvenli olmayan uygulamalar için. Daha fazla bilgi için bkz: [NIB: güvenlik ilkesi yapılandırma](http://msdn.microsoft.com/library/0f130bcd-1bba-4346-b231-0bcca7dab1a4) ve [NIB: Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Kod erişim izinleri üç tür vardır:  
  
-   `Code access permissions`öğesinden türetilen <xref:System.Security.CodeAccessPermission> sınıfı. Dosyaları ve ortam değişkenleri gibi korunan kaynaklara erişim için ve yönetilmeyen koda erişme gibi korunan işlemlerini gerçekleştirmek için izinler gereklidir.  
  
-   `Identity permissions`bir derlemeyi tanımlamak özelliklerini temsil eder. İzinleri olan bir dijital imza gibi öğeleri içerebilir veya kod geldiği kanıt üzerinde temel bir derleme verilir. Kimlik izinleri de türetilen <xref:System.Security.CodeAccessPermission> temel sınıfı.  
  
-   `Role-based security permissions`sorumlu belirtilen kimliğe sahip olup belirtilen bir rol üyesi olan üzerinde temel alır. <xref:System.Security.Permissions.PrincipalPermission> Sınıfı, her iki bildirim temelli ve kesinlik temelli izin denetimleri etkin sorumlunun karşı olanak tanır.  
  
 Kod bir kaynağa erişmek veya bir işlem gerçekleştirmek için yetkili olup olmadığını belirlemek için her çağıran talep izin verilen izinleri karşılaştırma çağrı yığını zamanının güvenlik sistemi erişir. Çağrı yığınında herhangi bir çağırıcı talep edilen izni yoksa bir <xref:System.Security.SecurityException> oluşturulur ve erişimi reddetti.  
  
### <a name="requesting-permissions"></a>İzinleri isteyen  
 Hangi izinlerin çalıştırmak için ve yalnızca gerçekten gerek duyduğu izinleri almasını sağlamak için uygulamanızın gerektirdiği çalışma zamanı hakkında bilgilendirmek için istekte bulunan izinleri amacı budur. Örneğin, uygulamanızın yerel diske veri yazmak gerekirse, gerektirdiği <xref:System.Security.Permissions.FileIOPermission>. Bu izni verilmiş taşınmadığından, diske yazma çalıştığında uygulama başarısız olur. Ancak, uygulama isterse `FileIOPermission` ve izin verilmeyen, uygulama outset sırasında özel durum oluşturur ve yüklenmez.  
  
 Burada uygulama yalnızca diskten verileri okumak için gereken bir senaryoda, tüm yazma izinleri hiçbir zaman verilmesi isteyebilir. Bir hata veya kötü amaçlı saldırı durumunda kodunuzun üzerinde çalıştığı veri zarar veremez. Daha fazla bilgi için bkz: [NIB: izinleri isteyen](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## <a name="role-based-security-and-cas"></a>Rol tabanlı güvenlik ve CA'ları  
 Rol tabanlı güvenlik ve kod erişim güvenliği (CAS) uygulama, genel güvenlik uygulamanız için geliştirir. Rol tabanlı güvenlik bir Windows hesabı veya güvenlik sorumlusu hakkında bilgi geçerli iş parçacığının kullanılabilir hale getirir, özel bir kimlik temel alabilir. Ayrıca, uygulamaları genellikle veri veya kullanıcı tarafından sağlanan kimlik bilgileri temel alarak kaynaklara erişim sağlamak için gereklidir. Genellikle, bu tür uygulamalar, bir kullanıcı rolü denetleyin ve bu rollere göre kaynaklarına erişimi sağlayın.  
  
 Rol tabanlı güvenlik, geçerli kullanıcı ve ilişkili rollerinin çalışma zamanında tanımlamak bir bileşen sağlar. Bu bilgiler daha sonra çalışma zamanında izinler kümesini belirlemek için CA ilke kullanılarak eşleştirilir. Belirtilen uygulama için bir etki alanı, konak varsayılan rol tabanlı güvenlik ilkesini değiştirmek ve bir kullanıcı ve bu kullanıcı ile ilişkilendirilen roller temsil eden bir varsayılan güvenlik sorumlusu ayarlayın.  
  
 CLR izinlerini yönetilen kod kısıtlamalar zorlama kendi mekanizması uygulamak için kullanır. Rol tabanlı güvenlik izinleri bir kullanıcı (veya kullanıcı adına hareket Aracısı) belirli bir kimliğe sahip veya belirtilen bir rol üyesi olup olmadığını bulmak için bir mekanizma sağlar. Daha fazla bilgi için bkz: [güvenlik izinleri](http://msdn.microsoft.com/library/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 Oluşturmakta olduğunuz uygulama türüne bağlı olarak, rol tabanlı izinlere veritabanında uygulama de dikkate almalısınız. SQL Server'ın rol tabanlı güvenlik hakkında daha fazla bilgi için bkz: [SQL Server Güvenlik](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Derlemeler  
 Derlemeleri dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve .NET Framework uygulaması için güvenlik izinleri temel birimini oluşturur. Derleme türleri ile birlikte çalışır ve işlevlerin bir mantıksal birim oluşturmak için yerleşik kaynakları oluşan bir koleksiyon sağlar. CLR için bütünleştirilmiş bağlamı dışında bir türü yok. Oluşturma ve derlemeleri dağıtma hakkında daha fazla bilgi için bkz: [Derlemelerle programlama](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Güçlü adlandırma derlemeler  
 Güçlü ad veya dijital imza, düz metin adını, sürüm numarasını ve kültür bilgilerini (sağlanmışsa) artı bir ortak anahtar ve dijital imza içeren derlemenin kimliğini oluşur. Dijital imza karşılık gelen özel anahtarı kullanarak bir derleme dosyası oluşturulur. Derleme dosyası adları ve derlemeyi oluşturan tüm dosyaların karmaları içeren derleme bildirimi içerir.  
  
 Güçlü bir derlemeyi adlandırma bir uygulama veya bileşenin diğer yazılım açıkça başvurmak için kullanabileceği benzersiz bir kimliği verir. Güçlü adlandırma derlemeler, saldırgan kod içeren bütünleştirilmiş kandırılan karşı korur. Güçlü adlandırma bir bileşen farklı sürümleri arasında sürüm oluşturma tutarlılığı sağlar. Genel Derleme Önbelleği (GAC) dağıtılacak tanımlayıcı ad derlemeleri gerekir. Daha fazla bilgi için bkz: [bkz](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>ADO.NET 2.0 kısmi güven  
 ADO.NET 2. 0'da, SQL Server, OLE DB, ODBC için .NET Framework veri sağlayıcısı ve Oracle için .NET Framework veri sağlayıcısı için .NET Framework veri sağlayıcısı için .NET Framework veri sağlayıcısı için şimdi içindeki tüm çalışma kısmen güvenilen ortamları. Yalnızca .NET Framework'ün önceki sürümlerde <xref:System.Data.SqlClient> değerinden tam güven uygulamalarında desteklenir.  
  
 En azından, SQL Server sağlayıcısını kullanarak kısmen güvenilir uygulama yürütme olmalıdır ve <xref:System.Data.SqlClient.SqlClientPermission> izinleri.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Kısmi güven izni öznitelik özellikleri  
 Kısmi güven senaryoları için kullandığınız <xref:System.Data.SqlClient.SqlClientPermissionAttribute> üyeleri daha da fazla kısıtlamak yetenekler için .NET Framework veri sağlayıcısı için SQL Server.  
  
 Aşağıdaki tabloda kullanılabilir listeler <xref:System.Data.SqlClient.SqlClientPermissionAttribute> özellikleri ve açıklamaları:  
  
|İzni özniteliği özelliği|Açıklama|  
|-----------------------------------|-----------------|  
|`Action`|Eylemi alır veya bir güvenlik ayarlar. Devralınan <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Etkinleştirir veya bir bağlantı dizesi boş parola kullanımını devre dışı bırakır. Geçerli değerler `true` (boş parola kullanımını etkinleştirmek için) ve `false` (boş parola kullanımını devre dışı bırakmak için). Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|İzin verilen bağlantı dizesini tanımlar. Birden çok bağlantı dizeleri tanımlanabilir. **Not:** bir kullanıcı kimliği veya parola bağlantı dizenizi içermez. Bu sürümde .NET Framework yapılandırma aracını kullanarak bağlantı dizesi kısıtlamalarını değiştiremezsiniz. <br /><br /> Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|İzin verilen veya izin verilmeyen bağlantı dizesi parametreleri tanımlar. Bağlantı dizesi parametreleri biçiminde tanımlanan  *\<parametre adı > =*. Noktalı virgül (;) kullanarak ayrılmış birden çok parametre belirtilebilir. **Not:** belirtmezseniz, `KeyRestrictions`, ancak ayarladığınız `KeyRestrictionBehavior` özelliğine `AllowOnly` veya `PreventUsage`, hiçbir ek bağlantı dizesi parametresi izin verilir. Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|İzin verilen yalnızca ek parametreler olarak bağlantı dizesi parametreleri tanımlar (`AllowOnly`), ya da izin verilmeyen ek parametreleri tanımlar (`PreventUsage`). `AllowOnly`varsayılandır. Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Türetilen bir sınıfta uygulandığında bu öznitelik için benzersiz bir tanımlayıcı alır. Devralınan <xref:System.Attribute>.|  
|`Unrestricted`|Kaynak Kısıtlanmamış izni bildirilmiş olup olmadığını gösterir. Devralınan <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>ConnectionString sözdizimi  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `connectionStrings` kullanılacak yalnızca belirli bağlantı dizesi izin vermek için bir yapılandırma dosyası öğesi. Bkz: [bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings.md) depolamak ve bağlantı dizelerini yapılandırma dosyaları alma hakkında daha fazla bilgi.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>KeyRestrictions sözdizimi  
 Aşağıdaki örnek aynı bağlantı dizesini sağlar, kullanmayı sağlayan `Encrypt` ve `Packet``Size` bağlantı dizesi seçenekleri, ancak başka bir bağlantı dizesi seçenekleri kullanımını kısıtlar.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior PreventUsage sözdizimi ile  
 Aşağıdaki örnek, aynı bağlantı dizesini sağlar ve dışındaki diğer tüm bağlantı parametrelerini verir `User Id`, `Password` ve `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior AllowOnly sözdizimi ile  
 Aşağıdaki örnek de içeren iki bağlantı dizeleri etkinleştirir `Initial Catalog`, `Connection Timeout`, `Encrypt`, ve `Packet Size` parametreleri. Diğer tüm bağlantı dizesi parametreleri kısıtlanır.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Kısmi güven özel izin kümesi ile etkinleştirme  
 Kullanımını etkinleştirmek için <xref:System.Data.SqlClient> izinleri özel bir bölge için bir Sistem Yöneticisi ve belirli bir bölgenin ayarlama iznini ayarladığınızda özel bir izni oluşturmalısınız. İzin kümeleri gibi varsayılan `LocalIntranet`, değiştirilemez. Örneğin, dahil etmek için <xref:System.Data.SqlClient> sahip kodu için izinler bir <xref:System.Security.Policy.Zone> , `LocalIntranet`, bir sistem yöneticisi için izni kopyalamak `LocalIntranet`, "CustomLocalIntranet" yeniden adlandırmak, ekleme <xref:System.Data.SqlClient> izinlerini, içe aktar kullanılarak ayarlanan CustomLocalIntranet izin [Caspol.exe (kod erişim güvenliği ilke aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)ve izin kümesini ayarlama `LocalIntranet_Zone` CustomLocalIntranet için.  
  
### <a name="sample-permission-set"></a>Örnek izin kümesi  
 .NET Framework veri sağlayıcısı için SQL Server için kısmen güvenilen bir senaryoda bir örnek izni verilmiştir. Özel izin kümeleri oluşturma hakkında daha fazla bilgi için bkz: [NIB: yapılandırma izni ayarlar kullanarak Caspol.exe](http://msdn.microsoft.com/library/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>ADO.NET kod erişimi güvenliği izinleri kullanarak doğrulanıyor  
 Kısmi güven senaryoları için belirli yöntemler için CA'ları ayrıcalıkları kodunuzda belirterek gerektirebilir bir <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Bu ayrıcalık kısıtlı güvenlik ilkesi tarafından yürürlükte izin verilmiyorsa, kodunuzu çalıştırmadan önce özel durum oluşur. Güvenlik İlkesi hakkında daha fazla bilgi için bkz: [NIB: Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) ve [NIB: güvenlik ilkesi en iyi yöntemler](http://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bağlantı dizesi gerektirir kodunun nasıl yazılacağını gösterir. Sınırsız izinleri reddetme benzetim <xref:System.Data.SqlClient>, uygulayan bir Sistem Yöneticisi gerçek dünyada CA ilke kullanılarak.  
  
> [!IMPORTANT]
>  ADO.NET için CA'ları izinleri tasarlarken, en kısıtlayıcı çalışması (izinleri hiç) ile başlayın ve kod gerçekleştirmek için gereken belirli görev için gereken belirli özel izinleri eklemek için doğru deseni olur. Aynı bağlantı dizesini ifade birçok yolu olduğundan tüm izinleri ile başlayan ve belirli bir izin reddetme ters düzeni güvenli değildir. Örneğin, tüm izinlerle başlatın ve sonra bağlantı dizesini kullanımını engellemek çalışırsanız "sunucu someserver =", "server=someserver.mycompany.com" dizesi hala izin verilir. Her zaman izin vererek başlatarak, izni kümesinde delik olduğunu olasılığını azaltmak.  
  
 Aşağıdaki kodda nasıl `SqlClient` oluşturur güvenlik talep gerçekleştiren bir <xref:System.Security.SecurityException> uygun CA'lar izinleri yerinde değilse. <xref:System.Security.SecurityException> Çıkış konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Konsol penceresinde bu çıktı görmeniz gerekir:  
  
```  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>Yönetilmeyen kod ile birlikte çalışabilirlik  
 Yönetilmeyen kod CLR dışında çalışan kod adı verilir. Bu nedenle, güvenlik mekanizmaları CA'lar gibi yönetilmeyen koda uygulanamaz. COM bileşenlerini, ActiveX arabirimleri ve Win32 API işlevleri yönetilmeyen kod gösterilebilir. Özel güvenlik konuları, böylece genel uygulama güvenliği tehlikeye değil yönetilmeyen kod yürütülürken uygulayın. Daha fazla bilgi için bkz: [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md).  
  
 .NET Framework COM birlikte çalışma üzerinden erişim sağlayarak geriye dönük uyumluluk varolan COM bileşenleri de destekler. İlgili COM türlerini almak için COM birlikte çalışma araçları kullanarak COM bileşenlerini .NET Framework uygulamasına dahil edebilirsiniz. İçeri aktarılan sonra COM türlerini kullanmak hazır olursunuz. COM birlikte çalışma ayrıca COM istemcilerin derleme meta verilerini bir tür kitaplığı dışarı aktarma ve yönetilen bileşen bir COM bileşeni kaydı tarafından yönetilen kod erişmesine olanak sağlar. Daha fazla bilgi için bkz: [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Yerel Güvenlik ve .NET Framework kodu PAVE](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [Kod erişimi güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)  
 [Rol Tabanlı Güvenlik](http://msdn.microsoft.com/library/239442e3-5be4-4203-b7fd-793baffea803)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
