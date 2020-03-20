---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0c803e3988f7a63980d991190db87c263c992b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185683"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Tanılama için Windows Yönetim İzlemesini Kullanma
Windows Communication Foundation (WCF), bir WCF Windows Management Instrumentation (WMI) sağlayıcısı aracılığıyla bir hizmetin denetim verilerini çalışma zamanında ortaya çıkarır.  
  
## <a name="enabling-wmi"></a>WMI'yi etkinleştirme  
 WMI, Microsoft'un Web Tabanlı Kurumsal Yönetim (WBEM) standardını uygulamasıdır. WMI SDK hakkında daha fazla bilgi için [Windows Management Instrumentation'a](/windows/desktop/WmiSdk/wmi-start-page)bakın. WBEM, uygulamaların yönetim araçlarını dış yönetim araçlarına nasıl maruz bıraktamaları için bir endüstri standardıdır.  
  
 WMI sağlayıcısı, WBEM uyumlu bir arabirim aracılığıyla çalışma zamanında enstrümantasyonu ortaya çıkaran bir bileşendir. Öznitelik/değer çiftleri olan bir WMI nesne kümesinden oluşur. Çiftleri basit türleri bir dizi olabilir. Yönetim araçları, çalışma zamanında arabirim üzerinden hizmetlere bağlanabilir. WCF, adresler, bağlamalar, davranışlar ve dinleyiciler gibi hizmetlerin özniteliklerini ortaya çıkarır.  
  
 Yerleşik WMI sağlayıcısı uygulamanın yapılandırma dosyasında etkinleştirilebilir. Bu, aşağıdaki `wmiProviderEnabled` örnek yapılandırmada gösterildiği [ \<gibi, system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde [ \<>tanılama](../../../configure-apps/file-schema/wcf/diagnostics.md) özniteliği ile yapılır.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi bir WMI arabirimini ortaya çıkarır. Yönetim uygulamaları artık bu arayüz üzerinden bağlanabilir ve uygulamanın yönetim enstrümantasyonuna erişebilir.  
  
## <a name="accessing-wmi-data"></a>WMI Verilerine Erişim  
 WMI verilerine birçok farklı şekilde erişilebilir. Microsoft komut dosyaları, Visual Basic uygulamaları, C++ uygulamaları ve .NET Framework için WMI API'leri sağlar. Daha fazla bilgi için [WMI kullanma'ya](/windows/win32/wmisdk/using-wmi)bakın.  
  
> [!CAUTION]
> .NET Framework sağlanan yöntemleri nizveolarak WMI verilerine erişmek için kullanıyorsanız, bağlantı kurulduğunda bu tür yöntemlerin özel durumlar oluşturabileceğini unutmayın. <xref:System.Management.ManagementObject> Bağlantı, örneğin yapımı sırasında değil, gerçek veri alışverişini içeren ilk istek üzerine kurulur. Bu nedenle, olası `try..catch` özel durumları yakalamak için bir blok kullanmanız gerekir.  
  
 İzleme ve ileti günlüğe kaydetme düzeyini ve WMI'deki `System.ServiceModel` izleme kaynağı için ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz. Bu [AppDomainInfo](appdomaininfo.md) örneğine erişerek yapılabilir, hangi bu Boolean `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`özellikleri `LogMalformedMessages`ortaya `TraceLevel`çıkarır: , , ve . Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırmada ayarlarsanız, bunları daha sonra uygulama çalışırken değiştirebilirsiniz. `true` Bu, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde etkinleştirecektir. Benzer şekilde, yapılandırma dosyanızda ileti günlüğe kaydetmeyi etkinleştiriseniz, WMI kullanarak çalışma zamanında devre dışı kalabilirsiniz.  
  
 İleti günlüğe kaydetme için hiçbir ileti günlüğe kaydetme `System.ServiceModel` dinleyicisi yoksa veya yapılandırma dosyasında izleme için izleme dinleyicisi belirtilmemişse, değişiklikler WMI tarafından kabul edilse bile değişikliklerinizin hiçbirinin geçerli olmadığını unutmayın. İlgili dinleyicilerin düzgün bir şekilde ayarlanması hakkında daha fazla bilgi için Bkz. [İleti Günlüğe Kaydetme](../configuring-message-logging.md) ve [İzlemeyi Yapılandırma.](../tracing/configuring-tracing.md) Yapılandırma tarafından belirtilen diğer tüm izleme kaynaklarının izleme düzeyi, uygulama başladığında etkilidir ve değiştirilemez.  
  
 WCF komut `GetOperationCounterInstanceName` dosyası için bir yöntem ortaya çıkarır. Bu yöntem, bir işlem adı ile sağlarsanız bir performans sayacı örnek adı döndürür. Ancak, giriş doğrulamıyor. Bu nedenle, yanlış bir işlem adı sağlarsanız, yanlış bir sayaç adı döndürülür.  
  
 WCF istemcisi hedef hizmete `OutgoingChannel` `Service` metodun içinde oluşturulmazsa, örneğin özelliği başka bir hizmete bağlanmak için bir hizmet tarafından açılan kanalları saymaz. `Service`  
  
 **Dikkat** WMI yalnızca <xref:System.TimeSpan> 3 ondalık noktaya kadar olan bir değeri destekler. Örneğin, hizmetiniz özelliklerinden birini <xref:System.TimeSpan.MaxValue>, WMI üzerinden görüntülendiğinde 3 ondalık noktadan sonra kesilir.  
  
## <a name="security"></a>Güvenlik  
 WCF WMI sağlayıcısı bir ortamda hizmetlerin bulunmasına izin verdiği için, bu hizmete erişim sağlamak için çok dikkatli olmalısınız. Yalnızca varsayılan yönetici erişimini rahatlatırsanız, daha az güvenilen tarafların ortamınızdaki hassas verilere erişmesine izin verebilirsiniz. Özellikle, uzaktan WMI erişimi izinleri gevşetin, sel saldırıları oluşabilir. Bir işlem aşırı WMI istekleri yle su basarsa, performansı düşürülebilir.  
  
 Buna ek olarak, MOF dosyası için erişim izinlerini gevşetirseniz, daha az güvenilen taraflar WMI'nin davranışını değiştirebilir ve WMI şemasına yüklenen nesneleri değiştirebilir. Örneğin, kritik verilerin yöneticiden gizlenmesi veya dosyaya doldurmayan veya özel durumlara neden olmayan alanlar eklenecek şekilde alanlar kaldırılabilir.  
  
 Varsayılan olarak, WCF WMI sağlayıcısı yönetici için "yürütme yöntemi", "sağlayıcı yazma" ve "hesap etkinleştirme" izni ve ASP.NET, Yerel Hizmet ve Ağ Hizmeti için "hesap etkinleştirme" izni verir. Özellikle, Windows Vista olmayan platformlarda, ASP.NET hesabı WMI ServiceModel ad alanına erişimi okumuştur. Bu ayrıcalıkları belirli bir kullanıcı grubuna vermek istemiyorsanız, WMI sağlayıcısını devre dışı bırakmanız (varsayılan olarak devre dışı bırakılır) veya belirli kullanıcı grubu için erişimi devre dışı bırakmanız gerekir.  
  
 Ayrıca, yapılandırma yoluyla WMI'yi etkinleştirmeye çalıştığınızda, kullanıcı ayrıcalığı yetersiz olduğu için WMI etkinleştirilemeyebilir. Ancak, bu hatayı kaydetmek için olay günlüğüne hiçbir olay yazılmamıştır.  
  
 Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.  
  
1. Başlat'ı tıklatın ve sonra çalıştır Ve **compmgmt.msc**yazın.  
  
2. **Özellikleri**seçmek için **Hizmetler ve Uygulama/WMI Denetimleri'ni** sağ tıklatın.  
  
3. **Güvenlik** Sekmesi'ni seçin ve **Root/ServiceModel** ad alanına gidin. **Güvenlik** düğmesini tıklatın.  
  
4. Erişimi denetlemek istediğiniz belirli grubu veya kullanıcıyı seçin ve izinleri yapılandırmak için **İzin Ver** veya **Reddet** onay kutusunu kullanın.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Ek Kullanıcılara WCF WMI Kayıt İzni Verilmesi  
 WCF, yönetim verilerini WMI'ye maruz bırakır. Bunu bazen "ayrılmış sağlayıcı" olarak adlandırılan bir süreç içinde WMI sağlayıcısı barındırarak yapar. Yönetim verilerinin açığa alınması için, bu sağlayıcıyı kaydeden hesabın uygun izinlere sahip olması gerekir. Windows'da, yalnızca küçük bir ayrıcalıklı hesap kümesi varsayılan olarak ayrılmış sağlayıcıları kaydedebilir. Kullanıcılar genellikle varsayılan kümede olmayan bir hesap altında çalışan bir WCF hizmetinden WMI verilerini ortaya çıkarmak istediğinizden, bu bir sorundur.  
  
 Bu erişimi sağlamak için, yöneticinin aşağıdaki sırada ek hesaba aşağıdaki izinleri vermesi gerekir:  
  
1. WCF WMI İsim Alanına erişim izni.  
  
2. WCF Decoupled WMI Sağlayıcısı'nı kaydetme izni.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>WMI ad alanı erişim izni vermek için  
  
1. Aşağıdaki PowerShell komut dosyasını çalıştırın.  
  
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
  
     Bu PowerShell komut dosyası, Yerleşik Kullanıcılar grubuna "root/servicemodel" WMI ad alanına erişim sağlamak için Güvenlik Tanımlayıcı Tanım Dili (SDDL) kullanır. Aşağıdaki ALA'ları belirtir:  
  
    - Yerleşik yönetici (BA) - zaten erişimi vardı.  
  
    - Ağ Hizmeti (NS) - Zaten erişimi vardı.  
  
    - Yerel sistem (LS) - zaten erişimi vardı.  
  
    - Yerleşik Kullanıcılar - Erişim izni verecek grup.  
  
#### <a name="to-grant-provider-registration-access"></a>Sağlayıcı kaydı erişimi sağlamak için  
  
1. Aşağıdaki PowerShell komut dosyasını çalıştırın.  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Rasgele Kullanıcılara veya Gruplara Erişim Verme  
 Bu bölümdeki örnek, wmi sağlayıcı kayıt ayrıcalıklarını tüm yerel kullanıcılara verir. Yerleşik olmayan bir kullanıcıya veya gruba erişim izni vermek istiyorsanız, o kullanıcının veya grubun Güvenlik Tanımlayıcısını (SID) edinmeniz gerekir. Rasgele bir kullanıcı için SID almak için basit bir yolu yoktur. Bir yöntem istenilen kullanıcı olarak oturum açmak ve sonra aşağıdaki kabuk komutunu vermektir.  
  
```console
Whoami /user  
```  
  
 Bu, geçerli kullanıcının SID'sini sağlar, ancak bu yöntem herhangi bir rasgele kullanıcıüzerinde SID almak için kullanılamaz. SID almak için başka bir yöntem yönetim görevleri için Windows 2000 Kaynak Kiti Araçları [getsid.exe](/windows/win32/wmisdk/using-wmi) aracını kullanmaktır. Bu araç, iki kullanıcının (yerel veya etki alanı) SID'sini karşılaştırır ve yan etki olarak iki SID'yi komut satırına yazdırır. Daha fazla bilgi için, [Bilinen SIT'lere](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems)bakın.  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzak WMI Nesne Örneklerine Erişim  
 Uzak bir makinede WCF WMI örneklerine erişmeniz gerekiyorsa, erişmek için kullandığınız araçlarda paket gizliliğini etkinleştirmeniz gerekir. Aşağıdaki bölümde WMI CIM Studio, Windows Management Instrumentation Tester ve .NET SDK 2.0'ı kullanarak bunların nasıl elde edilebildiğini açıklanmaktadır.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Stüdyo  
 [WMI Yönetim Araçları](https://go.microsoft.com/fwlink/?LinkId=95185)yüklediyseniz, WMI örneklerine erişmek için WMI CIM Studio'yu kullanabilirsiniz. Araçlar aşağıdaki klasörde  
  
 **%windir%\Program Dosyaları\WMI Araçları\\**  
  
1. Ad **alanına Bağlan:pencere,** **root\ServiceModel** yazın ve **Tamam'ı tıklatın.**  
  
2. **WMI CIM Studio Giriş** penceresinde, pencereyi genişletmek için **Seçenekler >>** düğmesini tıklatın. Kimlik Doğrulama **düzeyi**için Paket **gizliliği'ni** seçin ve **Tamam'ı**tıklatın.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Yönetimi Enstrümantasyon Test Cihazı  
 Bu araç Windows tarafından yüklenir. Çalıştırmak için **Başlat/Çalıştır** iletişim kutusuna **cmd.exe** yazarak bir komut konsolu başlatın ve **Tamam'ı**tıklatın. Ardından, komut penceresinde **wbemtest.exe** yazın. Windows Yönetimi Instrumentation Tester aracı daha sonra başlatılır.  
  
1. Pencerenin sağ üst köşesindeki **Bağlan** düğmesini tıklatın.  
  
2. Yeni pencerede, **Ad Alanı** alanı için **root\ServiceModel'i** girin ve **Kimlik Doğrulama düzeyi**için Paket **gizliliğini** seçin. **Bağlan**'a tıklayın.  
  
### <a name="using-managed-code"></a>Yönetilen Kodu Kullanma  
 Ayrıca, ad alanı tarafından sağlanan sınıfları kullanarak uzaktan <xref:System.Management> WMI örneklerine programlı olarak erişebilirsiniz. Aşağıdaki kod örneği bunun nasıl yapılacağını gösterir.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
