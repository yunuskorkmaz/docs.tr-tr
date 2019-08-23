---
title: Kod Erişimi Güvenliği ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: b288ffe6346ac8260756115b50c253c42b596f96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948259"
---
# <a name="code-access-security-and-adonet"></a>Kod Erişimi Güvenliği ve ADO.NET
.NET Framework, her ikisi de ortak dil çalışma zamanı (CLR) tarafından sağlanan ortak bir altyapı kullanılarak uygulanan, rol tabanlı güvenlik ve kod erişim güvenliği (CAS) sağlar. Yönetilmeyen kod dünyasında, çoğu uygulama kullanıcı veya sorumlu izinleriyle yürütülür. Sonuç olarak, kötü amaçlı veya hata doldurulmuş yazılımlar yükseltilmiş ayrıcalıklara sahip bir kullanıcı tarafından çalıştırıldığında bilgisayar sistemleri zarar görmüş ve özel veri güvenliği tehlikeye girebilir.  
  
 Buna karşılık, .NET Framework çalıştırılan yönetilen kod, tek başına kod için geçerli olan kod erişim güvenliğini içerir. Kodun çalışmasına izin verilip verilmediğine bakılmaksızın kodun kaynağına veya kodun kimliğine ait diğer yönlere göre değil yalnızca sorumlu kimliğini değil. Bu, yönetilen kodun kötüye kullanılması olasılığını azaltır.  
  
## <a name="code-access-permissions"></a>Kod Erişim İzinleri  
 Kod yürütüldüğünde, CLR güvenlik sistemi tarafından değerlendirilen kanıt gösterir. Genellikle, bu kanıt URL, site, bölge ve derlemenin kimliğini sağlayan dijital imzalar dahil olmak üzere kodun kaynağını içerir.  
  
 CLR, kodun yalnızca kodun gerçekleştirme iznine sahip olduğu işlemleri gerçekleştirmesini sağlar. Kod izin isteyebilir ve bu istekler, bir yönetici tarafından ayarlanan güvenlik ilkesi temel alınarak kabul edilir.  
  
> [!NOTE]
> CLR 'de yürütülen kod kendi kendine izin veremez. Örneğin, kod bir güvenlik ilkesinin izin verdiğinden daha az izin verebilir, ancak hiçbir şekilde daha fazla izin verilmeyecektir. İzin verirken, hiçbir izin olmadan başlayın ve ardından gerçekleştirilen belirli bir görev için en dar izinleri ekleyin. Tüm izinlerle başlayıp, her birinin reddedilmesi, istenmeden güvenlik boşluklarını gerekenden daha fazla izin vermekten bağımsız olarak, güvenli olmayan uygulamalara yönlendirir. Daha fazla bilgi için bkz. [güvenlik Ilkesini yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) ve [güvenlik ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Üç tür kod erişim izni vardır:  
  
- `Code access permissions`<xref:System.Security.CodeAccessPermission> sınıfından türet. Dosyalar ve ortam değişkenleri gibi korumalı kaynaklara erişmek ve yönetilmeyen koda erişim gibi korumalı işlemleri gerçekleştirmek için izinler gereklidir.  
  
- `Identity permissions`bir derlemeyi tanımlayan özellikleri temsil eder. Bir derlemeye, dijital imza veya kodun kaynaklandığı gibi öğeleri içerebilen kanıt temelinde izin verilir. Kimlik izinleri Ayrıca <xref:System.Security.CodeAccessPermission> temel sınıftan türetilir.  
  
- `Role-based security permissions`bir sorumlunun belirtilen bir kimliğe sahip olup olmadığını veya belirtilen bir rolün üyesi olduğunu temel alır. <xref:System.Security.Permissions.PrincipalPermission> Sınıfı, etkin sorumlu için hem bildirime dayalı hem de zorunlu izin denetimlerine izin verir.  
  
 Kodun bir kaynağa erişmek veya bir işlemi gerçekleştirmek için yetkilendirilip yetkilendirilmediğini anlamak için, çalışma zamanının güvenlik sistemi, çağrı yığınında gezilir ve her çağıranın verilen izinlerini talep edilen izinlerle karşılaştırır. Çağrı yığınındaki herhangi bir çağıran, istenen izne sahip değilse, bir <xref:System.Security.SecurityException> oluşturulur ve erişim reddedilir.  
  
### <a name="requesting-permissions"></a>Izin isteme  
 İzin isteme amacı, uygulamanızın çalışması için hangi izinleri gerektirdiğini ve yalnızca gerçekten ihtiyaç duyduğu izinleri aldığından emin olmak içindir. Örneğin, uygulamanızın yerel diske veri yazması gerekiyorsa, bunu gerektirir <xref:System.Security.Permissions.FileIOPermission>. Bu izin verilmemişse, uygulama diske yazmaya çalıştığında başarısız olur. Ancak, uygulama istediğinde `FileIOPermission` ve bu izin verilmemişse, uygulama özel durumu bilinemeyebilir üzerinde oluşturur ve yüklemez.  
  
 Uygulamanın yalnızca diskten verileri okuması gereken bir senaryoda, hiçbir bir yazma izni verilmeyeceğinden emin olabilirsiniz. Bir hata veya kötü amaçlı saldırı durumunda kodunuz, üzerinde çalıştığı verilere zarar veremeyeceğinden. Daha fazla bilgi için bkz. [Izinleri isteme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Rol tabanlı güvenlik ve CA 'LAR  
 Rol tabanlı güvenlik ve kod erişim güvenliği (CAS) uygulamak, uygulamanız için genel güvenliği geliştirir. Rol tabanlı güvenlik, geçerli iş parçacığı için kullanılabilir güvenlik sorumlusu hakkında bilgi sunarak bir Windows hesabını veya özel bir kimliği temel alabilir. Ayrıca, uygulamalar genellikle kullanıcı tarafından sağlanan kimlik bilgilerine göre veri veya kaynaklara erişim sağlamak için gereklidir. Genellikle, bu gibi uygulamalar bir kullanıcının rolünü denetler ve bu rollere göre kaynaklara erişim sağlar.  
  
 Rol tabanlı güvenlik, bir bileşenin çalışma zamanında geçerli kullanıcıları ve bunlarla ilişkili rolleri belirlemesine olanak sağlar. Bu bilgiler daha sonra çalışma zamanında verilen izin kümesini belirleyebilmek için bir CAS ilkesi kullanılarak eşleştirilir. Konak, belirtilen bir uygulama etki alanı için varsayılan rol tabanlı güvenlik ilkesini değiştirebilir ve bir kullanıcıyı ve bu kullanıcıyla ilişkili rolleri temsil eden bir varsayılan güvenlik sorumlusu ayarlayabilir.  
  
 CLR, yönetilen kod üzerinde kısıtlamaları zorlama mekanizmasını uygulamak için izinleri kullanır. Rol tabanlı güvenlik izinleri, bir kullanıcının (veya Kullanıcı adına işlem yapan aracının) belirli bir kimliğe sahip olup olmadığını bulmak için bir mekanizma sağlar veya belirtilen rolün bir üyesidir. Daha fazla bilgi için bkz. [güvenlik izinleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 Oluşturmakta olduğunuz uygulamanın türüne bağlı olarak, veritabanında rol tabanlı izinleri uygulamayı da göz önünde bulundurmanız gerekir. SQL Server rol tabanlı güvenlik hakkında daha fazla bilgi için bkz. [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Bütünleştirilmiş kodlar  
 Derlemeler bir .NET Framework uygulaması için temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinlerini oluşturur. Derleme, birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak bir tür ve kaynak koleksiyonu sağlar. CLR 'ye bir tür, bir derleme bağlamı dışında yok. Derlemeleri oluşturma ve dağıtma hakkında daha fazla bilgi için bkz. [Derlemelerle programlama](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Tanımlayıcı adlandırma bütünleştirilmiş kodları  
 Güçlü bir ad veya dijital imza, derleme kimliğinden basit metin adı, sürüm numarası ve kültür bilgileri (sağlanmışsa) ve bir ortak anahtar ve dijital imza dahil oluşur. Dijital imza, karşılık gelen özel anahtar kullanılarak bir derleme dosyasından oluşturulur. Derleme dosyası, derlemeyi oluşturan tüm dosyaların adlarını ve karmalarını içeren derleme bildirimini içerir.  
  
 Bir derlemeyi tanımlayıcı adlandırma bir uygulamaya veya bileşene, başka yazılımın açıkça kendisine başvurabileceği benzersiz bir kimlik verir. Sağlam adlandırma koruyucuları derlemeleri, barındırma kodu içeren bir derleme tarafından sızdırılmakta. Güçlü adlandırma, bir bileşenin farklı sürümleri arasında sürüm tutarlılığını de sağlar. Genel derleme önbelleği 'ne (GAC) dağıtılacak tanımlayıcı ad derlemelerini yapmanız gerekir. Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>ADO.NET 2,0 ' de kısmi güven  
 ADO.NET 2,0 ' de .NET Framework Veri Sağlayıcısı SQL Server, Veri Sağlayıcısı için .NET Framework OLE DB, ODBC için .NET Framework veri sağlayıcısı ve Oracle için .NET Framework veri sağlayıcısı kısmen güvenilen ortamlarda çalıştırılabilir. .NET Framework önceki sürümlerinde, yalnızca <xref:System.Data.SqlClient> tam güvenle güvenilen uygulamalardan daha az desteklenmelidir.  
  
 En azından, SQL Server sağlayıcısı kullanan kısmen güvenilen bir uygulamanın yürütme ve <xref:System.Data.SqlClient.SqlClientPermission> izinleri olmalıdır.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Kısmi güven için izin özniteliği özellikleri  
 Kısmi güven senaryolarında, SQL Server için .NET Framework veri sağlayıcısı <xref:System.Data.SqlClient.SqlClientPermissionAttribute> kullanılabilir özellikleri daha fazla kısıtlamak üzere üyelerini kullanabilirsiniz.  
  
 Aşağıdaki tabloda kullanılabilen <xref:System.Data.SqlClient.SqlClientPermissionAttribute> Özellikler ve bunların açıklamaları listelenmektedir:  
  
|İzin özniteliği özelliği|Açıklama|  
|-----------------------------------|-----------------|  
|`Action`|Bir güvenlik eylemini alır veya ayarlar. Devralındığı <xref:System.Security.Permissions.SecurityAttribute>yer.|  
|`AllowBlankPassword`|Bir bağlantı dizesinde boş parola kullanımını etkinleştirilir veya devre dışı bırakır. Geçerli değerler `true` (Boş parolaların kullanımını etkinleştirmek için) ve `false` (Boş parolaların kullanımını devre dışı bırakmak için). Devralındığı <xref:System.Data.Common.DBDataPermissionAttribute>yer.|  
|`ConnectionString`|İzin verilen bir bağlantı dizesini tanımlar. Birden çok bağlantı dizesi tanımlanabilir. **Not:**  Bağlantı dizeniz için bir kullanıcı KIMLIĞI veya parola eklemeyin. Bu sürümde, .NET Framework yapılandırma aracını kullanarak bağlantı dizesi kısıtlamalarını değiştiremezsiniz. <br /><br /> Devralındığı <xref:System.Data.Common.DBDataPermissionAttribute>yer.|  
|`KeyRestrictions`|İzin verilen veya izin verilmeyen bağlantı dizesi parametrelerini tanımlar. Bağlantı dizesi parametreleri  *\<parametre adı > =* biçiminde tanımlanır. Birden çok parametre belirtilebilir, noktalı virgül (;)) ile ayrılır. **Not:**  Belirtmezseniz `KeyRestrictions`, ancak özelliğini veya `KeyRestrictionBehavior` `AllowOnly`olarakayarlarsanız, ekbağlantıdizesiparametrelerineizinverilmez`PreventUsage`. Devralındığı <xref:System.Data.Common.DBDataPermissionAttribute>yer.|  
|`KeyRestrictionBehavior`|Bağlantı dizesi parametrelerini yalnızca izin verilen (`AllowOnly`) ek parametreler olarak tanımlar veya izin verilmeyen ek parametreleri tanımlar (`PreventUsage`). `AllowOnly`varsayılandır. Devralındığı <xref:System.Data.Common.DBDataPermissionAttribute>yer.|  
|`TypeID`|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. Devralındığı <xref:System.Attribute>yer.|  
|`Unrestricted`|Kaynak üzerinde Kısıtlanmamış iznin bildirilip bildirilmemiş olduğunu gösterir. Devralındığı <xref:System.Security.Permissions.SecurityAttribute>yer.|  
  
#### <a name="connectionstring-syntax"></a>ConnectionString sözdizimi  
 Aşağıdaki örnek, yalnızca belirli bir bağlantı dizesinin `connectionStrings` kullanılmasına izin vermek için bir yapılandırma dosyası öğesinin nasıl kullanılacağını gösterir. Yapılandırma dosyalarından bağlantı dizelerini depolama ve alma hakkında daha fazla bilgi için bkz. [bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings.md) .  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>KeyRestrictions sözdizimi  
 Aşağıdaki örnek aynı bağlantı dizesini sağlar, `Encrypt` ve `Packet Size` bağlantı dizesi seçeneklerinin kullanımını sağlar, ancak diğer bağlantı dizesi seçeneklerinin kullanımını kısıtlar.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>PreventUsage sözdizimi ile KeyRestrictionBehavior  
 Aşağıdaki örnek `User Id`, `Password` ve `Persist Security Info`hariç tüm diğer bağlantı parametrelerini sağlar ve aynı bağlantı dizesini sağlar.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>AllowOnly söz dizimi ile KeyRestrictionBehavior  
 `Initial Catalog`Aşağıdaki örnek `Connection Timeout` ,`Encrypt`,, ve`Packet Size` parametreleri de içeren iki bağlantı dizesini mümkün bir şekilde sunar. Diğer tüm bağlantı dizesi parametreleri kısıtlıdır.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Özel bir Izin kümesiyle kısmi güven etkinleştiriliyor  
 Belirli bir bölge için <xref:System.Data.SqlClient> izin kullanımını etkinleştirmek üzere bir sistem yöneticisinin özel bir izin kümesi oluşturması ve belirli bir bölge için izin kümesi olarak ayarlaması gerekir. Gibi varsayılan izin kümeleri `LocalIntranet`değiştirilemez. <xref:System.Data.SqlClient> Örneğin, ' `LocalIntranet`a <xref:System.Security.Policy.Zone> sahip olan koda ilişkin izinleri eklemek için, bir sistem yöneticisi için izin kümesini kopyalayabilir, "CustomLocalIntranet" olarak <xref:System.Data.SqlClient> yeniden adlandırabilir, izinleri ekleyebilir, içeri aktarabilirsiniz `LocalIntranet` [Caspol. exe (kod erişimi güvenlik ilkesi aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)kullanarak CustomLocalIntranet izin kümesi ve izin kümesini `LocalIntranet_Zone` CustomLocalIntranet olarak ayarlayın.  
  
### <a name="sample-permission-set"></a>Örnek Izin kümesi  
 Aşağıda kısmen güvenilen bir senaryoda SQL Server için .NET Framework Veri Sağlayıcısı bir örnek izin kümesi verilmiştir. Özel izin kümeleri oluşturma hakkında bilgi için bkz. [Caspol. exe kullanarak Izin kümelerini yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Güvenlik Izinleri kullanarak ADO.NET kodu erişiminin doğrulanması  
 Kısmi güven senaryolarında, bir <xref:System.Data.SqlClient.SqlClientPermissionAttribute>belirterek kodunuzda belırlı yöntemler için CAS ayrıcalıklarına ihtiyacınız olabilir. Bu ayrıcalığa, kısıtlı güvenlik ilkesi etkin bir şekilde izin verilmiyorsa, kodunuz çalıştırılmadan önce bir özel durum oluşturulur. Güvenlik ilkesi hakkında daha fazla bilgi için bkz. [Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) ve [Güvenlik Ilkesi en iyi uygulamaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir bağlantı dizesi gerektiren kodun nasıl yazılacağını gösterir. Bir sistem yöneticisinin gerçek dünyada CAS <xref:System.Data.SqlClient>ilkesi kullanarak uygulayabileceği sınırsız izinleri reddetme benzetimi yapar.  
  
> [!IMPORTANT]
> ADO.NET için CAS izinleri tasarlarken, doğru model en kısıtlayıcı büyük/küçük harf (hiçbir izin olmadan) ile başlamalı ve ardından kodun gerçekleştirmesi gereken belirli bir görev için gereken belirli izinleri eklemektir. Aynı bağlantı dizesini ifade etmenin pek çok yolu olduğundan, tüm izinlerle başlayan ve ardından belirli bir izni reddeden ters bir model, güvenli değildir. Örneğin, tüm izinlerle başlayıp "Server = someserver" bağlantı dizesinin kullanımını reddetmeye çalışırsanız, "Server = someserver. mycompany. com" dizesinin yine de izin verilmesi gerekir. Her zaman, hiç izin vermeyerek başlayarak, izin kümesinde delik olma olasılığını azaltmış olursunuz.  
  
 Aşağıdaki kod, uygun CA `SqlClient` izinlerinin yerinde olmadığı durumlarda bir <xref:System.Security.SecurityException> oluşturan güvenlik talebini nasıl gerçekleştireceğini gösterir. <xref:System.Security.SecurityException> Çıktı, konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Bu çıktıyı konsol penceresinde görmeniz gerekir:  
  
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
  
## <a name="interoperability-with-unmanaged-code"></a>Yönetilmeyen kodla birlikte çalışabilirlik  
 CLR dışında çalışan koda yönetilmeyen kod denir. Bu nedenle, CA 'LAR gibi güvenlik mekanizmaları yönetilmeyen koda uygulanamaz. COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri, yönetilmeyen koda örnektir. Yönetilmeyen kod yürütürken, genel uygulama güvenliğini tehlikeye atmanız için özel güvenlik konuları geçerlidir. Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../../../docs/framework/interop/index.md).  
  
 .NET Framework, COM birlikte çalışabilirliğine erişim sağlayarak mevcut COM bileşenlerine geriye dönük uyumluluğu da destekler. Com bileşenlerini, ilgili COM türlerini içe aktarmak için COM birlikte çalışma araçlarını kullanarak bir .NET Framework uygulamasına ekleyebilirsiniz. İçeri aktarıldıktan sonra COM türleri kullanıma hazırlardır. COM birlikte çalışması Ayrıca COM istemcilerinin, derleme meta verilerini bir tür kitaplığına vererek ve yönetilen bileşeni bir COM bileşeni olarak kaydederek yönetilen koda erişmesini sağlar. Daha fazla bilgi için bkz. [GELIŞMIŞ com birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Yerel ve .NET Framework kodundaki güvenlik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Rol Tabanlı Güvenlik](../../../standard/security/role-based-security.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
