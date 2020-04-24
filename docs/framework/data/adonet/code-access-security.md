---
title: Kod Erişimi Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 7b0f269bd4dce8ddaaaa72c3760a4d7a0e3eb8b9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646022"
---
# <a name="code-access-security-and-adonet"></a>Kod Erişimi Güvenliği ve ADO.NET
.NET Framework, her ikisi de ortak dil çalışma süresi (CLR) tarafından sağlanan ortak bir altyapı kullanılarak uygulanan rol tabanlı güvenliğin yanı sıra kod erişim güvenliği (CAS) sunar. Yönetilmeyen kod dünyasında, çoğu uygulama kullanıcının veya asıl ın izinleriyle yürütülür. Sonuç olarak, kötü amaçlı veya hata dolu yazılımlar yüksek ayrıcalıklara sahip bir kullanıcı tarafından çalıştırıldığında bilgisayar sistemleri zarar görebilir ve özel veriler tehlikeye atılabilir.  
  
 Bunun aksine, .NET Framework'de yönetilen kod yürütme, yalnızca kod için geçerli olan kod erişim güvenliğini içerir. Kodun çalışmasına izin verilip verilmemesi, yalnızca asıl kimliğine değil, kodun kaynağına veya kodun kimliğinin diğer yönlerine bağlıdır. Bu, yönetilen kodun kötüye kullanılma olasılığını azaltır.  
  
## <a name="code-access-permissions"></a>Kod Erişim İzinleri  
 Kod yürütüldüğünde, CLR güvenlik sistemi tarafından değerlendirilen kanıtları sunar. Genellikle, bu kanıt URL, site ve bölge ve derleme kimliğini sağlamak dijital imzalar da dahil olmak üzere kodun kökenini içerir.  
  
 CLR, kodun yalnızca kodun gerçekleştirme izni olan işlemleri gerçekleştirmesine izin verir. Kod izin isteyebilir ve bu istekler yönetici tarafından belirlenen güvenlik ilkesine göre onurlandırıldı.  
  
> [!NOTE]
> CLR'de çalıştırılan kod kendisine izin veremez. Örneğin, kod bir güvenlik ilkesinin izin verdiğinden daha az izin isteyebilir ve verilebilir, ancak hiçbir zaman daha fazla izin verilecektir. İzin verirken, hiç izin almadan başlayın ve ardından gerçekleştirilen belirli görev için en dar izinleri ekleyin. Tüm izinlerle başlayıp tek tek olanları reddetmek, istenmeyen güvenlik açıkları içerebilecek güvenli olmayan uygulamalara, gerekenden daha fazla izin verilmesine neden olur. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) [Security Policy Management](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))  
  
 Üç tür kod erişim izni vardır:  
  
- `Code access permissions`sınıftan <xref:System.Security.CodeAccessPermission> türetilmiştir. Dosyalar ve ortam değişkenleri gibi korumalı kaynaklara erişmek ve yönetilmeyen koda erişmek gibi korumalı işlemleri gerçekleştirmek için izinler gereklidir.  
  
- `Identity permissions`bir derlemeyi tanımlayan özellikleri temsil eder. İzinler, dijital imza veya kodun kaynağı gibi öğeleri içerebilen kanıtlara dayalı bir derlemeye verilir. Kimlik izinleri de taban <xref:System.Security.CodeAccessPermission> sınıftan türetilmiştir.  
  
- `Role-based security permissions`bir müdürün belirli bir kimliğe sahip olup olmadığına veya belirli bir rolün üyesi olup olmadığına bağlıdır. Sınıf, <xref:System.Security.Permissions.PrincipalPermission> etkin anaparaya karşı hem bildirimsel hem de zorunlu izin denetimlerine izin verir.  
  
 Kodun kaynağa erişmeye veya bir işlem gerçekleştirmeye yetkili olup olmadığını belirlemek için, çalışma zamanının güvenlik sistemi çağrı yığınından geçerek her arayanın verilen izinlerini istenen izinle karşılaştırır. Arama yığınındaki herhangi bir arayan istenen izne <xref:System.Security.SecurityException> sahip değilse, bir a atılır ve erişim reddedilir.  
  
### <a name="requesting-permissions"></a>İzin İsteme  
 İzin istemenin amacı, uygulamanızın çalıştırılabilmesi için gereken izinleri çalışma zamanını bildirmek ve yalnızca gerçekten ihtiyaç duyduğu izinleri aldığından emin olmaktır. Örneğin, uygulamanızın yerel diske veri yazması gerekiyorsa, <xref:System.Security.Permissions.FileIOPermission>bunu gerektirir. Bu izin verilmediyse, diske yazmaya çalıştığında uygulama başarısız olur. Ancak, başvuru istekleri `FileIOPermission` ve bu izin verilmediyse, uygulama ilk başta özel durum oluşturur ve yüklenmez.  
  
 Uygulamanın yalnızca diskteki verileri okuması gereken bir senaryoda, hiçbir zaman yazma izni verilmemesini isteyebilirsiniz. Bir hata veya kötü amaçlı bir saldırı durumunda, kodunuz çalıştığı verilere zarar veremez. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))  
  
## <a name="role-based-security-and-cas"></a>Rol Tabanlı Güvenlik ve CAS  
 Hem rol tabanlı güvenlik hem de koda erişilen güvenlik (CAS) uygulamak, uygulamanızın genel güvenliğini artırır. Rol tabanlı güvenlik, bir Windows hesabına veya özel bir kimliğe dayalı olarak, güvenlik ilkesi yle ilgili bilgileri geçerli iş parçacığının kullanımına açık hale getirebilir. Buna ek olarak, uygulamalar genellikle kullanıcı tarafından sağlanan kimlik bilgilerine dayalı verilere veya kaynaklara erişim sağlamak için gereklidir. Genellikle, bu tür uygulamalar bir kullanıcının rolünü denetler ve bu rolleri temel alan kaynaklara erişim sağlar.  
  
 Rol tabanlı güvenlik, bir bileşenin geçerli kullanıcıları ve ilişkili rollerini çalışma zamanında tanımlamasına olanak tanır. Bu bilgiler daha sonra, çalışma zamanında verilen izinkümesini belirlemek için bir CAS ilkesi kullanılarak eşlenir. Belirli bir uygulama etki alanı için ana bilgisayar varsayılan rol tabanlı güvenlik ilkesini değiştirebilir ve bir kullanıcıyı ve bu kullanıcıyla ilişkili rolleri temsil eden varsayılan bir güvenlik ilkesi ayarlayabilir.  
  
 CLR, yönetilen kodüzerindeki kısıtlamaları uygulamak için mekanizmasını uygulamak için izinleri kullanır. Rol tabanlı güvenlik izinleri, bir kullanıcının (veya kullanıcı adına hareket eden aracının) belirli bir kimliğe sahip olup olmadığını veya belirli bir rolün üyesi olup olmadığını keşfetmek için bir mekanizma sağlar. Daha fazla bilgi için [Güvenlik İzinleri'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100))bakın.  
  
 Oluşturmakta olduğunuz uygulama türüne bağlı olarak, veritabanında rol tabanlı izinleri uygulamayı da düşünmelisiniz. SQL Server'da rol tabanlı güvenlik hakkında daha fazla bilgi için [SQL Server Security'ye](./sql/sql-server-security.md)bakın.  
  
## <a name="assemblies"></a>Bütünleştirilmiş kodlar  
 Derlemeler, bir .NET Framework uygulaması için dağıtım, sürüm denetimi, yeniden kullanma, etkinleştirme kapsamlandırma ve güvenlik izinlerinin temel birimini oluşturur. Derleme, birlikte çalışmak ve mantıksal bir işlevsellik birimi oluşturmak üzere oluşturulmuş türler ve kaynaklar topluluğu sağlar. CLR için, bir tür bir derleme bağlamı dışında yok. Derlemeler oluşturma ve dağıtma hakkında daha fazla bilgi için [Derlemelerle Programlama'ya](../../../standard/assembly/index.md)bakın.  
  
### <a name="strong-naming-assemblies"></a>Güçlü adlandırma Derlemeleri  
 Güçlü bir ad veya dijital imza, basit metin adını, sürüm numarasını ve kültür bilgilerini (sağlanmışsa) içeren derlemenin kimliğinden, ortak anahtar ve dijital imzadan oluşur. Dijital imza, ilgili özel anahtar kullanılarak bir derleme dosyasından oluşturulur. Derleme dosyası, derlemeyi oluşturan tüm dosyaların adlarını ve işlerini içeren derleme bildirimini içerir.  
  
 Güçlü adlandırma bir derleme, bir uygulamaya veya bileşene diğer yazılımların açıkça başvurmak için kullanabileceği benzersiz bir kimlik verir. Güçlü adlandırma korumaları, düşman kodu içeren bir derleme tarafından taklit edilmesine karşı toplanır. Güçlü adlandırma, bir bileşenin farklı sürümleri arasında sürüm tutarlılığı da sağlar. Genel Derleme Önbelleğine (GAC) dağıtılacak güçlü ad derlemeleri olmalıdır. Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md)  
  
## <a name="partial-trust-in-adonet-20"></a>2.0'ADO.NET Kısmi Güven  
 2.0ADO.NET da, SQL Server için .NET Framework Veri Sağlayıcısı, OLE DB için .NET Framework Veri Sağlayıcısı, ODBC için .NET Framework Veri Sağlayıcısı ve Oracle için .NET Framework Data Provider artık kısmen güvenilen ortamlarda çalıştırılabilir. .NET Framework'ün önceki sürümlerinde, yalnızca <xref:System.Data.SqlClient> tam güven uygulamalarından daha az bir şekilde desteklenmiştir.  
  
 En azından, SQL Server sağlayıcısını kullanan kısmen güvenilen bir uygulamayürütme ve <xref:System.Data.SqlClient.SqlClientPermission> izinlere sahip olmalıdır.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Kısmi Güven için İzin Özniteliği Özellikleri  
 Kısmi güven senaryoları için, <xref:System.Data.SqlClient.SqlClientPermissionAttribute> SQL Server için .NET Framework Data Provider için kullanılabilir yetenekleri daha da kısıtlamak için üyeleri kullanabilirsiniz.  
  
 Aşağıdaki tabloda kullanılabilir <xref:System.Data.SqlClient.SqlClientPermissionAttribute> özellikleri ve açıklamaları listelenmektedir:  
  
|İzin özniteliği özelliği|Açıklama|  
|-----------------------------------|-----------------|  
|`Action`|Bir güvenlik eylemi alır veya ayarlar. Miras. <xref:System.Security.Permissions.SecurityAttribute>|  
|`AllowBlankPassword`|Bağlantı dizesinde boş bir parolanın kullanımını etkinleştirir veya devre dışı kılabilir. Geçerli değerler `true` (boş parolaların kullanımını etkinleştirmek `false` için) ve (boş parolaların kullanımını devre dışı kılabilir). Miras. <xref:System.Data.Common.DBDataPermissionAttribute>|  
|`ConnectionString`|İzin verilen bir bağlantı dizesi tanımlar. Birden çok bağlantı dizeleri tanımlanabilir. **Not:**  Bağlantı dizenize bir kullanıcı kimliği veya parola eklemeyin. Bu sürümde, .NET Framework Configuration Tool'u kullanarak bağlantı dize kısıtlamalarını değiştiremezsiniz. <br /><br /> Miras. <xref:System.Data.Common.DBDataPermissionAttribute>|  
|`KeyRestrictions`|İzin verilen veya izin verilmeyen bağlantı dize parametrelerini tanımlar. Bağlantı dize parametreleri form * \<parametre adı>=* tanımlanır. Birden çok parametre belirtilebilir, bir yarı kolon (;) kullanılarak sınırlandırılabilir. **Not:**  `KeyRestrictions`Belirtmezseniz, ancak özelliği `AllowOnly` veya `PreventUsage`özelliği ni ayarlarsanız, `KeyRestrictionBehavior` ek bağlantı dize parametrelerine izin verilmez. Miras. <xref:System.Data.Common.DBDataPermissionAttribute>|  
|`KeyRestrictionBehavior`|Bağlantı dize parametrelerini izin verilen`AllowOnly`tek ek parametre olarak tanımlar`PreventUsage`( ), veya izin verilmeyen ek parametreleri tanımlar ( ). `AllowOnly` varsayılan değerdir. Miras. <xref:System.Data.Common.DBDataPermissionAttribute>|  
|`TypeID`|Türemiş bir sınıfta uygulandığında bu öznitelik için benzersiz bir tanımlayıcı alır. Miras. <xref:System.Attribute>|  
|`Unrestricted`|Kaynağa sınırsız izin verilip vermediğini gösterir. Miras. <xref:System.Security.Permissions.SecurityAttribute>|  
  
#### <a name="connectionstring-syntax"></a>ConnectionString Sözdizimi  
 Aşağıdaki örnek, yalnızca belirli `connectionStrings` bir bağlantı dizesinin kullanılmasına izin vermek için yapılandırma dosyasının öğesinin nasıl kullanılacağını gösterir. Bağlantı [dizelerini](connection-strings.md) yapılandırma dosyalarından depolama ve alma hakkında daha fazla bilgi için Bağlantı Dizeleri'ne bakın.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>KeyRestrictions Sözdizimi  
 Aşağıdaki örnek aynı bağlantı dizesini etkinleştiri, `Encrypt` ve `Packet Size` bağlantı dize seçeneklerinin kullanımını sağlar, ancak diğer bağlantı dize seçeneklerinin kullanımını kısıtlar.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>PreventUsage Sözdizimi ile KeyRestrictionBehavior  
 Aşağıdaki örnek aynı bağlantı dizesini etkinleştirive `User Id`' `Password` ve `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>AllowOnly Sözdizimi ile KeyRestrictionBehavior  
 Aşağıdaki örnek, `Initial Catalog`", , `Connection Timeout` `Encrypt`" ve `Packet Size` parametreleri de içeren iki bağlantı dizeleri sağlar. Diğer tüm bağlantı dize parametreleri kısıtlanmıştır.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Özel İzin Kümesiyle Kısmi Güveni Etkinleştirme  
 Belirli bir bölge <xref:System.Data.SqlClient> için izinlerin kullanımını etkinleştirmek için, sistem yöneticisinin özel bir izin kümesi oluşturması ve belirli bir bölge için izin kümesi olarak ayarlaması gerekir. Varsayılan izin kümeleri, gibi, `LocalIntranet`değiştirilemez. <xref:System.Data.SqlClient> Örneğin, <xref:System.Security.Policy.Zone> bir sistem yöneticisi için izin `LocalIntranet`kümesini kopyalayabilir, "CustomLocalIntranet" `LocalIntranet`olarak yeniden adlandırabilir, <xref:System.Data.SqlClient> izinleri ekleyebilir, [Caspol.exe (Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md)kullanarak CustomLocalIntranet izin `LocalIntranet_Zone` kümesini içe aktarabilir ve izin kümesini CustomLocalIntranet olarak ayarlayabilir.  
  
### <a name="sample-permission-set"></a>Örnek İzin Seti  
 Aşağıda, kısmen güvenilen bir senaryoda SQL Server için .NET Framework Data Provider için örnek bir izin kümesi verilmiştir. Özel izin kümeleri oluşturma hakkında bilgi için [Caspol.exe'yi Kullanarak İzin Kümelerini Yapılandırma'ya](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100))bakın.  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Güvenlik İzinlerini Kullanarak ADO.NET Kodu Erişimini Doğrulama  
 Kısmi güven senaryoları için, kodunuzdaki belirli yöntemler için cas <xref:System.Data.SqlClient.SqlClientPermissionAttribute>ayrıcalıkları gerektirebilir. Bu ayrıcalığa yürürlükteki kısıtlı güvenlik ilkesi tarafından izin verilmezse, kodunuz çalıştırılmadan önce bir özel durum atılır. Güvenlik ilkesi hakkında daha fazla bilgi için [Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) ve [Güvenlik İlkesi En İyi Uygulamaları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))bakın.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir bağlantı dizesi gerektiren kodun nasıl yazılabildiğini gösterir. Bir sistem yöneticisinin gerçek dünyada <xref:System.Data.SqlClient>bir CAS ilkesi kullanarak uygulayacağı sınırsız izinleri reddetmeyi simüle eder.  
  
> [!IMPORTANT]
> ADO.NET için CAS izinleri tasarlarken, doğru desen en kısıtlayıcı servis talebiyle (hiç izin yok) başlamak ve ardından kodun gerçekleştirmesi gereken belirli görev için gereken belirli izinleri eklemektir. Aynı bağlantı dizesini ifade etmenin birçok yolu olduğundan, tüm izinlerle başlayıp belirli bir izni reddetmenin tersi desen güvenli değildir. Örneğin, tüm izinlerle başlar ve "server=someserver" bağlantı dizesini kullanmayı reddetmeyi denerseniz, "server=someserver.mycompany.com" dizesi yine de izin verilir. Her zaman hiç izin vermeyerak başlayarak, izin kümesinde boşluklar olma olasılığını azaltırsınız.  
  
 Aşağıdaki kod, uygun `SqlClient` CAS izinlerinin yerinde olmaması <xref:System.Security.SecurityException> durumunda güvenlik talebinin nasıl gerçekleştirildiğini gösterir. Çıktı <xref:System.Security.SecurityException> konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Bu çıktıyı Konsol penceresinde görmeniz gerekir:  
  
```output  
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
  
## <a name="interoperability-with-unmanaged-code"></a>Yönetilmeyen Kodla Birlikte Çalışabilirlik  
 CLR dışında çalışan kodyönetilmeyen kod olarak adlandırılır. Bu nedenle, CAS gibi güvenlik mekanizmaları yönetilmeyen koda uygulanamaz. COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri yönetilmeyen kod örnekleridir. Genel uygulama güvenliğini tehlikeye atmamak için yönetilmeyen kodu yürüerken özel güvenlik konuları uygulanır. Daha fazla bilgi için [bkz.](../../interop/index.md)  
  
 .NET Framework ayrıca COM interop üzerinden erişim sağlayarak varolan COM bileşenlerine geriye dönük uyumluluğu destekler. Com bileşenlerini, ilgili COM türlerini almak için COM interop araçlarını kullanarak bir .NET Framework uygulamasına dahil edebilirsiniz. İçe aktarılan COM türleri kullanıma hazırdır. COM interop ayrıca, derleme meta verilerini bir tür kitaplığına dışlayarak ve yönetilen bileşeni com bileşeni olarak kaydederek COM istemcilerinin yönetilen koda erişmesini de sağlar. Daha fazla bilgi için [Gelişmiş COM Birlikte Çalışabilirliği'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [Yerel güvenlik ve .NET Çerçeve Kodu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Rol Tabanlı Güvenlik](../../../standard/security/role-based-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
