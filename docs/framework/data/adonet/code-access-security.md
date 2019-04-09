---
title: Kod Erişimi Güvenliği ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 6c26ae82939a3d011ecb7ecd97e162ab2f45cd48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174115"
---
# <a name="code-access-security-and-adonet"></a>Kod Erişimi Güvenliği ve ADO.NET
.NET Framework, rol tabanlı güvenlik yanı sıra kod erişimi güvenliği (CAS), ikisi için de ortak dil çalışma (CLR) tarafından sağlanan bir ortak altyapısı kullanılarak uygulanan sunar. Yönetilmeyen kod dünyasında, çoğu uygulama sorumlusu ve kullanıcı izinleriyle çalıştırın. Sonuç olarak, bilgisayar sistemlerini kötü amaçlı, gizliliği bozulmuş ve özel veri olabilir veya yazılım hatası doldurulmuş yükseltilmiş ayrıcalıklara sahip bir kullanıcı tarafından çalıştırılır.  
  
 Bunun aksine, .NET Framework yönetilen kodu yürüten kodu tek başına uygulanan kod erişim güvenliği içerir. Olup kodun çalışmasına izin verilen veya kodun kaynak veya diğer yönleri kodun kimlik, kimliği değil yalnızca asıl bağlıdır değil. Bu yönetilen olasılığını azaltır kodu yanlış.  
  
## <a name="code-access-permissions"></a>Kod Erişim İzinleri  
 Kod yürütüldüğünde CLR güvenlik sistemi tarafından değerlendirilen kanıt sunar. Genellikle, bu bulgu kaynağı URL'si, site ve bölge ve derleme kimliğini sağlayan dijital imzalar dahil olmak üzere kod oluşur.  
  
 CLR kod gerçekleştirmek için izni olan işlemleri gerçekleştirmek için kod sağlar. Kod izinler isteyebilir ve bu istekleri yönetici tarafından ayarladığınız güvenlik ilkesine göre dikkate alınır.  
  
> [!NOTE]
>  CLR içinde yürütülen kodun kendisi verilemiyor. Örneğin, kod isteyebilir ve güvenlik ilkesinin izin verdiği ancak hiçbir zaman daha fazla izin verilen daha az izin verilmesi. İzin verirken hiçbir izinlerle hiç başlatın ve sonra gerçekleştirilen belirli görev için en düşük izinleri ekleyin. Tüm izinleri ile başlayan ve ardından tek olanları reddetme müşteri adayları gerekli daha fazla izin veren gelen istenmeyen güvenlik açıkları içerebilir güvenli uygulamalar için. Daha fazla bilgi için [güvenlik ilkesi yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) ve [Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Kod erişim izinleri üç tür vardır:  
  
-   `Code access permissions` öğesinden türetilen <xref:System.Security.CodeAccessPermission> sınıfı. Dosyaları ve ortam değişkenleri gibi korumalı kaynaklara erişmek için ve yönetilmeyen koda erişme gibi korumalı işlemlerini gerçekleştirmek için izinler gereklidir.  
  
-   `Identity permissions` bir derlemeyi tanımlamak özelliklerini temsil eder. Bir derleme, bir dijital imza gibi öğeleri içerebilir veya kod geldiği kanıta göre izinleri verilir. Kimlik izinleri de türetilen <xref:System.Security.CodeAccessPermission> temel sınıfı.  
  
-   `Role-based security permissions` sorumlu belirli bir kimliğe sahip olup belirtilen bir rol üyesi üzerinde temel alır. <xref:System.Security.Permissions.PrincipalPermission> Sınıfı, hem bildirim temelli ve buyurgan izin denetimleri etkin sorumlunun karşı olanak tanır.  
  
 Kod bir kaynağa veya bir işlemi gerçekleştirmek için yetkili olup olmadığını belirlemek için çalışma zamanının güvenlik sistemi her arayanın talep izin verilen izinler karşılaştırma çağrı yığını erişir. Çağrı yığınındaki herhangi bir çağırıcı talep edilen iznine sahip değilse bir <xref:System.Security.SecurityException> oluşturulur ve erişimi reddetti.  
  
### <a name="requesting-permissions"></a>İzinler isteyen  
 İzinler isteyen amacı çalıştırmak için ve yalnızca gerçekten gerekli izinleri aldığından emin olmak için hangi izinlerin uygulamanızın gerektirdiği çalışma zamanı bilgilendirmektir. Örneğin, uygulamanızın yerel diske veri yazmak gerekiyorsa gerektiriyorsa <xref:System.Security.Permissions.FileIOPermission>. Bu izin verilen henüz, diske yazma girişiminde bulunduğunda uygulama başarısız olur. Ancak, uygulama isterse `FileIOPermission` ve izin verilmeyen, uygulama gizliliğe özel oluşturur ve yüklenmeyecek.  
  
 Uygulamayı yalnızca diskten verileri okumak için gereken yere bir senaryoda, hiçbir zaman herhangi bir yazma izni verilmesi isteyebilir. Bir hata veya kötü amaçlı saldırı durumunda kodunuzun üzerinde çalıştığı veri zarar veremez. Daha fazla bilgi için [izinleri isteyen](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Rol tabanlı güvenlik ve CA'ları  
 Rol tabanlı güvenlik ve kod erişim güvenliği (CAS) hem uygulama, uygulamanız için genel güvenliği geliştirir. Rol tabanlı güvenlik bir Windows hesabı veya güvenlik sorumlusunun hakkında bilgi için geçerli iş parçacığı kullanılabilir hale getirme özel bir kimlik temel alabilir. Ayrıca, uygulamaları genellikle veri veya kullanıcı tarafından sağlanan kimlik bilgilerini temel kaynaklarına erişim sağlamak için gerekli değildir. Genellikle, bu tür uygulamalar, bir kullanıcının rolünü denetlemek ve bu rollere göre kaynaklarına erişim sağlama.  
  
 Bir bileşen çalışma zamanında geçerli kullanıcılar ve ilişkili rolleri tanımlamak rol tabanlı güvenlik sağlar. Bu bilgi çalışma zamanında izinler kümesini belirlemek için bir CAS ilkesini kullanmayı eşlenir. Belirtilen uygulama etki alanı için konağın varsayılan rol tabanlı güvenlik ilkesini değiştirmek ve bir kullanıcı ve bu kullanıcı ile ilişkilendirilen roller temsil eden bir varsayılan güvenlik sorumlusu kümesi.  
  
 CLR, yönetilen kod üzerindeki kısıtlamalar uygulamaya yönelik, mekanizma uygulamak için izinleri kullanır. Rol tabanlı güvenlik izinleri, kullanıcı (veya kullanıcı adına hareket Aracısı) belirli bir kimliğe sahip veya belirtilen bir rol üyesi olup olmadığını keşfetmek için bir mekanizma sağlar. Daha fazla bilgi için [güvenlik izinleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 Oluşturmakta olduğunuz uygulama türüne bağlı olarak, rol tabanlı izinlere veritabanında uygulama düşünmelisiniz. SQL Server rol tabanlı güvenlik hakkında daha fazla bilgi için bkz. [SQL Server güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Derlemeleri  
 Derlemeler dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve .NET Framework uygulaması için güvenlik izinleri temel birimini oluşturur. Derleme türleri ve birlikte çalışan ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan kaynakları koleksiyonu sağlar. CLR, bir derleme bağlamı dışında bir tür yok. Oluşturma ve derlemeleri dağıtma hakkında daha fazla bilgi için bkz. [Derlemelerle programlama](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Derlemelerin tanımlayıcı adlandırma  
 Bir tanımlayıcı ad ya da dijital imza basit metin adı, sürüm numarasını ve (sağlanmışsa) kültür bilgilerini, artı bir ortak anahtar ve bir dijital imza içeren derlemenin kimliğini oluşur. Dijital imza, karşılık gelen özel anahtarı kullanarak bir derleme dosyasından oluşturulur. Derleme dosya adları ve derlemeyi oluşturan tüm dosyaların karma değerlerini içeren derleme bildirimini içerir.  
  
 Tanımlayıcı ad derleme oluşturma, bir uygulama veya bileşenin diğer yazılım açıkça başvururken kullanabileceği benzersiz bir kimlik sağlar. Tanımlayıcı adlandırma derlemeleri tehlikeli kodunu içeren bütünleştirilmiş kandırılan karşı korur. Tanımlayıcı adlandırma, bir bileşenin farklı sürümleri arasında sürüm tutarlılık sağlar. Genel Derleme Önbelleği (GAC) dağıtılacak tanımlayıcı ad derlemeleri gerekir. Daha fazla bilgi için [bkz](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>ADO.NET'te 2.0 kısmi güven  
 ADO.NET 2. 0'da, SQL Server, OLE DB, ODBC için .NET Framework veri sağlayıcısı ve Oracle için .NET Framework veri sağlayıcısı için .NET Framework veri sağlayıcısı için .NET Framework veri sağlayıcısı artık tüm çalışma kısmen güvenilen ortamlarda. Yalnızca .NET Framework'ün önceki sürümlerinde <xref:System.Data.SqlClient> küçüktür tam güven uygulamalarında destekleniyordu.  
  
 En azından, yürütme ve SQL Server sağlayıcıyı kısmen güvenilen bir uygulama olmalıdır ve <xref:System.Data.SqlClient.SqlClientPermission> izinleri.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Kısmi güven izni öznitelik özellikleri  
 Kısmi güven senaryoları için kullanabileceğiniz <xref:System.Data.SqlClient.SqlClientPermissionAttribute> üyeleri daha fazla SQL Server için .NET Framework veri sağlayıcısı için sunulan özellikler kısıtlama.  
  
 Aşağıdaki tabloda kullanılabilir listeler <xref:System.Data.SqlClient.SqlClientPermissionAttribute> özellikleri ve açıklamaları:  
  
|İzni öznitelik özelliği|Açıklama|  
|-----------------------------------|-----------------|  
|`Action`|Eylemi alır veya bir güvenlik ayarlar. Devralınan <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Etkinleştirir veya bir bağlantı dizesi boş parola kullanımı devre dışı bırakır. Geçerli değerler `true` (boş parola kullanımını etkinleştirmek için) ve `false` (boş parola kullanımı devre dışı bırakmak için). Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|İzin verilen bağlantı dizesini tanımlar. Birden çok bağlantı dizelerini tanımlanabilir. **Not:**  Bir kullanıcı kimliği veya parola bağlantı dizenizi içermez. Bu sürümde, .NET Framework yapılandırma aracı kullanarak bağlantı dizesi kısıtlamaları değiştiremezsiniz. <br /><br /> Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|İzin verilen veya izin verilmeyen bir bağlantı dizesi parametreleri tanımlar. Bağlantı dizesi parametreleri biçiminde tanımlanan  *\<parametre adı > =*. Noktalı virgül (;) kullanarak ayrılmış birden çok parametre belirtilebilir. **Not:**  Siz belirtmezseniz `KeyRestrictions`, ancak ayarladığınız `KeyRestrictionBehavior` özelliğini `AllowOnly` veya `PreventUsage`, hiçbir ek bağlantı dizesi parametreleri izin verilir. Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Yalnızca ek parametreleri izin verilen bağlantı dizesi parametreleri tanımlar (`AllowOnly`), veya izin verilmeyen ek parametreleri tanımlar (`PreventUsage`). `AllowOnly` varsayılandır. Devralınan <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. Devralınan <xref:System.Attribute>.|  
|`Unrestricted`|Kaynak Kısıtlanmamış izni bildirilmiş olup olmadığını gösterir. Devralınan <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Bağlantı dizesi söz dizimi  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `connectionStrings` kullanılacak yalnızca belirli bir bağlantı dizesi izin vermek için bir yapılandırma dosyası öğesi. Bkz: [bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings.md) depolamak ve bağlantı dizeleri yapılandırma dosyalarından alma hakkında daha fazla bilgi.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>KeyRestrictions söz dizimi  
 Aşağıdaki örnek aynı bağlantı dizesine sağlar, kullanımını etkinleştirir `Encrypt` ve `Packet Size` bağlantı dizesi seçenekleri, ancak başka bir bağlantı dizesi seçeneklerinin kullanımını kısıtlar.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior PreventUsage söz dizimi ile  
 Aşağıdaki örnek, aynı bağlantı dizesine sağlar ve dışında diğer tüm bağlantı parametrelerini sağlayan `User Id`, `Password` ve `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior AllowOnly söz dizimi ile  
 Aşağıdaki örnek de içeren iki bağlantı dizesi sağlar `Initial Catalog`, `Connection Timeout`, `Encrypt`, ve `Packet Size` parametreleri. Diğer tüm bağlantı dizesi parametreleri büyük/küçük harf kısıtlanır.  
  
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
 Kullanımını etkinleştirmek için <xref:System.Data.SqlClient> izinleri belirli bir bölge için bir Sistem Yöneticisi ayarlayın ve belirli bir bölge için bir izin olarak ayarlanmış özel izin oluşturmalısınız. İzin kümeleri gibi varsayılan `LocalIntranet`, değiştirilemez. Örneğin dahil etmek için <xref:System.Data.SqlClient> izinlere sahip kod için bir <xref:System.Security.Policy.Zone> , `LocalIntranet`, bir sistem yöneticisi izninin'e ayarlanmış olarak kopyalanamadı `LocalIntranet`, "CustomLocalIntranet için" yeniden adlandırmak, ekleme <xref:System.Data.SqlClient> izinleri, içeri aktarma kullanılarak ayarlanan CustomLocalIntranet izni [Caspol.exe (kod erişimi güvenliği ilke aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)ve izinleri kümesi `LocalIntranet_Zone` CustomLocalIntranet için.  
  
### <a name="sample-permission-set"></a>Örnek izin kümesi  
 .NET Framework veri sağlayıcısı için SQL Server için kısmen güvenilen bir senaryoda ayarlayın. bir örnek izin verilmiştir. Özel izin kümeleri oluşturma hakkında daha fazla bilgi için bkz. [yapılandırma izni ayarlar kullanarak Caspol.exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>ADO.NET kod erişim güvenlik izinlerini kullanarak doğrulanıyor  
 Kısmi güven senaryoları için CA ayrıcalıkları belirli yöntemler için kodunuzdaki belirterek gerektirebilir bir <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Bu ayrıcalık yürürlükte kısıtlı güvenlik ilkesi tarafından izin verilmiyorsa, kodunuzu çalıştırılmadan önce bir özel durum oluşturulur. Güvenlik İlkesi hakkında daha fazla bilgi için bkz. [Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) ve [güvenlik ilkesi en iyi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir bağlantı dizesi gerektirir kodunun nasıl yazılacağını gösterir. Sınırsız izinleri reddetme benzetim <xref:System.Data.SqlClient>, gerçek hayatta CAS ilkesini kullanarak bir Sistem Yöneticisi uygulayan.  
  
> [!IMPORTANT]
>  ADO.NET CAS izinlerini tasarlarken, doğru en kısıtlayıcı çalışması (izinleri hiç) ile başlayın ve ardından kodu gerçekleştirmesi gereken belirli görev için gereken belirli izinleri ekleyin modelidir. Aynı bağlantı dizesine ifade birçok yolu olduğundan tüm izinleri ile başlayan ve ardından belirli bir izni reddetme ters deseni, güvenli değildir. Örneğin, tüm izinleri ile başlayın ve bağlantı dizesini kullanımını engelle girişimi "sunucu someserver =", "server=someserver.mycompany.com" dizesi yine de izin verilir. Her zaman izin vererek başlatarak, izin kümesine boşluklarını olduğunu büyük olasılıkla azaltın.  
  
 Aşağıdaki kodda nasıl `SqlClient` oluşturur güvenlik talebi gerçekleştiren bir <xref:System.Security.SecurityException> uygun CA izinleri yerinde değilse. <xref:System.Security.SecurityException> Çıktıyı konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Konsol penceresinde bu bir çıktı görmeniz gerekir:  
  
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
 CLR dışında çalışan kod, yönetilmeyen kod adı verilir. Bu nedenle, güvenlik mekanizmaları CA'lar gibi yönetilmeyen koda uygulanamaz. COM bileşenleri ve ActiveX arabirimleri Windows API işlevlerinde yönetilmeyen kod örnekleridir. Genel uygulama güvenliği reddetmeniz değil, yönetilmeyen kod yürütülürken özel güvenlik konuları uygulayın. Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md).  
  
 .NET Framework, COM birlikte çalışma aracılığıyla erişim sağlayarak geriye dönük uyumluluk için mevcut COM bileşenlerini de destekler. COM birlikte çalışma araçları kullanarak ilgili COM türleri içeri aktarmak üzere bir .NET Framework uygulamasına COM bileşenlerini birleştirebilirsiniz. İçeri aktarılan sonra COM türlerini kullanmak hazır olursunuz. COM birlikte çalışma, yönetilen kod, derleme meta verileri için bir tür kitaplığı dışarı aktarıp bir COM bileşeni yönetilen bileşen kaydı erişmek COM istemcileri de sağlar. Daha fazla bilgi için [Gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Yerelde ve .NET Framework Kodunda Güvenlik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Rol Tabanlı Güvenlik](../../../../docs/standard/security/role-based-security.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
