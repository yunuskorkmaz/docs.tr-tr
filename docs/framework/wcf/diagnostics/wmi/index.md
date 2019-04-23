---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 9acb1b280248f8552680ea3fbba831b3de53b2c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308594"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Tanılama için Windows Yönetim İzlemesini Kullanma
Windows Communication Foundation (WCF) hizmetinin çalışma zamanında bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla denetleme verileri kullanıma sunar.  
  
## <a name="enabling-wmi"></a>WMI etkinleştirme  
 WMI Web tabanlı kuruluş yönetimi (WBEM) standart Microsoft uygulamasıdır. WMI SDK'sı hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları'nı](/windows/desktop/WmiSdk/wmi-start-page). WBEM, uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı nasıl kullanıma için standart bir endüstri standardıdır.  
  
 WMI sağlayıcısı izleme çalışma zamanında bir WBEM uyumlu arabirimi üzerinden kullanıma sunan bir bileşenidir. Bu öznitelik/değer çiftleri olan WMI nesneleri kümesinden oluşur. Birkaç basit türler çiftleri olabilir. Yönetim Araçları hizmetler zamanında arabirimi aracılığıyla bağlanabilirsiniz. WCF hizmetleri adresler, bağlamalar, davranışları ve dinleyicileri gibi öznitelikleri gösterir.  
  
 Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilebilir. Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi WMI arabirimini kullanıma sunar. Yönetim uygulamaları artık bu arabirimi üzerinden bağlanabilir ve Yönetim Araçları uygulamanın erişim.  
  
## <a name="accessing-wmi-data"></a>WMI verilerine erişme  
 WMI verilerini birçok farklı şekilde erişilebilir. Microsoft, betikleri, Visual Basic uygulamaları, C++ uygulamaları için WMI API'lerini sağlar ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Daha fazla bilgi için [WMI kullanarak](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  WMI veri programlı olarak erişmek için sağlanan yöntemleri .NET Framework kullanırsanız, tür yöntemler bağlantı kurulduğunda özel durumlar oluşturabilecek farkında olmalıdır. Oluşumu sırasında bağlantı kurulmaz <xref:System.Management.ManagementObject> örneği, ancak ilk istek gerçek veri değişimi ilgili. Bu nedenle, kullanması gereken bir `try..catch` olası özel durumları yakalama bloğu.  
  
 İzleme ve ileti günlüğe kaydetme düzeyi yanı için ileti günlüğe kaydetme seçenekleri değiştirebilirsiniz `System.ServiceModel` WMI izleme kaynağı. Bu erişerek yapılabilir [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) bu Boolean özellikleri sunan bir örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, ve `TraceLevel`. Bu nedenle, İzleme dinleyicisi için ileti günlüğe kaydetmeyi yapılandırın, ancak ayarlayın, bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebilirsiniz `true` uygulama çalışırken. Bu durum, ileti günlüğe kaydetme, çalışma zamanında etkili bir şekilde etkinleştirir. Yapılandırma dosyanızda günlük iletisi etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz.  
  
 Bilmeniz gereken olması durumunda ileti günlüğünü izleme dinleyicileri ileti günlüğe kaydetme veya no `System.ServiceModel` izleme dinleyicilerine izleme için yapılandırma dosyasında belirtilen, değişiklikleri WMI tarafından kabul edilir olsa da, değişikliklerin hiçbiri etkili olur, alınır. Düzgün bir şekilde ilgili dinleyicileri ayarlama hakkında daha fazla bilgi için bkz. [iletileri günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) ve [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Uygulama başladığında yapılandırması tarafından belirtilen diğer tüm izleme kaynakları izleme düzeyini etkilidir ve değiştirilemez.  
  
 WCF sunan bir `GetOperationCounterInstanceName` komut dosyası için yöntemi. Bir işlem adıyla sağlarsanız, bu yöntem bir performans sayacı örneği adını döndürür. Ancak, giriş doğrulamaz. Hatalı işlem adı sağlarsanız, bu nedenle, bir yanlış sayaç adı döndürülür.  
  
 `OutgoingChannel` Özelliği `Service` örneği başka bir hizmete bağlanmak için bir hizmet içinde hedef hizmeti WCF istemcisi oluşturulmamışsa açan kanalları sayısı değil `Service` yöntemi.  
  
 **Uyarı** WMI yalnızca destekleyen bir <xref:System.TimeSpan> en fazla 3 ondalık nokta değeri. Örneğin, hizmetiniz için özelliklerinden birini ayarlar <xref:System.TimeSpan.MaxValue>, değeri WMI aracılığıyla görüntülendiğinde 3 ondalık nokta sonrasında kesilir.  
  
## <a name="security"></a>Güvenlik  
 WCF WMI sağlayıcısı, bir ortamda Hizmetleri bulma izin verdiğinden, sizin ona erişim izni verme için dikkatli olmalıdır. Varsayılan yalnızca yönetici erişimi yöntemlerinde, ortamınızda en az güvenilen taraf hassas verilere erişimi sağlayabilir. WMI uzaktan erişim izinlerini çözmek, özellikle saldırıları taşmasını ortaya çıkabilir. Bir işlem tarafından aşırı WMI isteklerini kurtarılmakta, kendi performans düşebilir.  
  
 Ayrıca, MOF dosyasını erişim izinlerini hafifletin, en az güvenilen taraf WMI davranışını değiştirmek ve WMI Şeması nesneleri değiştirme. Örneğin, alanlar, kritik veri Yöneticisi'nden altına gizlenmiş veya dosyaya doldurmak veya özel durumlarına neden alanlar eklenmiş şekilde kaldırılabilir.  
  
 Varsayılan olarak, "yürütme yöntemi", WCF WMI sağlayıcısı verir. "Sağlayıcı yazma" ve "hesabı etkinleştir" izni için ASP.NET, yerel hizmet ve ağ hizmeti ve yönetici "hesabı etkinleştir" izin. Özellikle, şirket dışı[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformları, ASP.NET hesabı okuyun ServiceModel WMI ad alanına erişimi. Belirli bir kullanıcı grubuna Bu ayrıcalıkları vermek istemiyorsanız (varsayılan olarak devre dışıdır) WMI sağlayıcısı devre dışı bırakmak veya erişimi belirli bir kullanıcı grubu için devre dışı bırakın.  
  
 WMI aracılığıyla yapılandırması etkinleştirmeye çalıştığınızda, buna ek olarak, WMI yetersiz kullanıcı ayrıcalıkların yetersizliği etkinleştirilmemiş olabilir. Ancak, olay, bu hatayı kaydetmek için olay günlüğüne yazılır.  
  
 Kullanıcı ayrıcalık düzeyleri değiştirmek için aşağıdaki adımları kullanın.  
  
1. Başlat'a tıklayın ve ardından çalıştırın ve türü **compmgmt.msc**.  
  
2. Sağ **Hizmetleri ve uygulama/WMI denetimleri** seçilecek **özellikleri**.  
  
3. Seçin **güvenlik** sekmesine gidin **kök/ServiceModel** ad alanı. Tıklayın **güvenlik** düğmesi.  
  
4. Belirli bir grup veya erişimi denetlemek ve kullanmak istediğiniz kullanıcıyı seçin **izin** veya **Reddet** izinlerini yapılandırmak için onay kutusu.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Ek kullanıcılar için WCF WMI kayıt izinleri veriliyor  
 WCF WMI yönetimi verilerini kullanıma sunar. Bunu bir "ayrılmış sağlayıcı" olarak da adlandırılan bir işlem içi WMI sağlayıcısı barındırarak yapar. Yönetim verilerini sağlamak bu sağlayıcısını Kaydet hesabı uygun izinlere sahip olmalıdır. Windows ayrıcalıklı hesaplar yalnızca küçük bir kümesi, varsayılan olarak ayrılmış sağlayıcılar kaydedebilirsiniz. Kullanıcıların yaygın olarak WMI verilerinden varsayılan kümede olmayan bir hesap altında çalışan bir WCF Hizmeti kullanıma sunmak istediğiniz bir sorun olmasıdır.  
  
 Bu erişimi sağlamak için yönetici aşağıdaki sırayla ek hesap aşağıdaki izinleri vermeniz gerekir:  
  
1. WCF WMI Namespace'için erişim izni.  
  
2. WCF ayrılmış WMI sağlayıcısını kaydetme izni.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>WMI ad alanı erişim izni vermek için  
  
1. Aşağıdaki PowerShell betiğini çalıştırın.  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     Bu PowerShell Betiği, "kök/servicemodel" WMI ad alanına yerleşik kullanıcı grubu erişimi vermek için Güvenlik Tanımlayıcısı Tanım Dili (SDDL) kullanır. Aşağıdaki EDL'ler belirtir:  
  
    -   Yerleşik yönetici (BA) - erişim zaten var.  
  
    -   Ağ Hizmeti (NS) - zaten erişebiliyordu.  
  
    -   Yerel Sistem (LS) - erişim zaten var.  
  
    -   Yerleşik kullanıcılar - erişim izni vermek için bir grup.  
  
#### <a name="to-grant-provider-registration-access"></a>Sağlayıcı vermek için kayıt erişim  
  
1. Aşağıdaki PowerShell betiğini çalıştırın.  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Rastgele kullanıcılara veya gruplara erişim izni verme  
 Bu bölümdeki örnek, tüm yerel kullanıcılar için WMI sağlayıcısı kayıt ayrıcalıklar verir. Ardından kullanıcı veya yerleşik olmayan bir gruba erişim vermek istiyorsanız, bu kullanıcı veya grubun güvenlik tanımlayıcısı (SID) almanız gerekir. Herhangi bir kullanıcı için SID almak için basit bir yolu yoktur. İstenen kullanıcı olarak oturum açın ve ardından aşağıdaki Kabuk komutu vermek için bir yöntem var.  
  
```  
Whoami /user  
```  
  
 Bu, geçerli kullanıcının SID'si sağlar, ancak bu yöntem, üzerinde herhangi bir kullanıcı SID almak için kullanılamaz. SID almak için başka bir yöntem [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) gelen aracı [Windows 2000 Kaynak Seti Araçları yönetim görevleri için](https://go.microsoft.com/fwlink/?LinkId=178660). SID (yerel veya etki alanı) iki kullanıcı bu aracı karşılaştırır ve bir yan etkisi komut satırına iki SID yazdırır. Daha fazla bilgi için [iyi bilinen SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzak WMI nesne örneklerini erişme  
 Uzak makinede WCF WMI örnekleri erişmeniz gerekiyorsa, paket gizlilik erişmek için kullandığınız araçları etkinleştirmeniz gerekir. Aşağıdaki bölümde, WMI CIM Studio, Windows Yönetim Araçları Sınayıcısı, hem de .NET SDK 2. 0'ı kullanarak bu elde etmek nasıl açıklar.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Yüklediyseniz [WMI Yönetimsel Araçlar](https://go.microsoft.com/fwlink/?LinkId=95185), erişim WMI örnekleri için WMI CIM Studio kullanabilirsiniz. Araçlar, aşağıdaki klasörde yer  
  
 **%windir%\Program Files\WMI araçları\\**  
  
1. İçinde **ad Connect:** penceresinde, tür **root\ServiceModel** tıklatıp **Tamam.**  
  
2. İçinde **WMI CIM Studio oturum açma** penceresinde tıklayın **Seçenekleri >>** düğmesini penceresini genişletin. Seçin **paket gizlilik** için **kimlik doğrulama düzeyi**, tıklatıp **Tamam**.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Yönetim Araçları test aracı  
 Bu araç, Windows tarafından yüklenir. Çalıştırmak için yazarak bir komut konsolunu Başlat **cmd.exe** içinde **başlangıç/çalıştırma** iletişim kutusu ve tıklatın **Tamam**. Ardından yazın **wbemtest.exe** komut penceresinde. Windows Yönetim Araçları Sınayıcısı aracı sonra başlatılır.  
  
1. Tıklayın **Connect** pencerenin sağ üst köşesindeki düğmesi.  
  
2. Yeni pencerede girin **root\ServiceModel** için **Namespace** alan ve seçim **paket gizlilik** için **kimlik doğrulama düzeyi**. **Bağlan**'a tıklayın.  
  
### <a name="using-managed-code"></a>Yönetilen kod kullanarak  
 Ayrıca uzak WMI örnekleri program aracılığıyla tarafından sağlanan sınıfları kullanarak erişebileceğiniz <xref:System.Management> ad alanı. Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
