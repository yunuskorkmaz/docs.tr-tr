---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: e1f5ccb8849d5f8f6bd9156cd428d395a86b1301
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046013"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Tanılama için Windows Yönetim İzlemesini Kullanma
Windows Communication Foundation (WCF) bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında bir hizmetin İnceleme verilerini gösterir.  
  
## <a name="enabling-wmi"></a>WMI etkinleştiriliyor  
 WMI, Microsoft 'un web tabanlı kuruluş yönetimi (WBEM) standardı uygulamasıdır. WMI SDK hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları](/windows/desktop/WmiSdk/wmi-start-page). WBEM, uygulamaların yönetim araçları 'nı dış yönetim araçlarına nasıl sergilekullandığını gösteren bir sektör standardıdır.  
  
 WMI sağlayıcısı, çalışma zamanında WBEM ile uyumlu bir arabirim aracılığıyla izleme sunan bir bileşendir. Öznitelik/değer çiftlerine sahip bir WMI nesneleri kümesinden oluşur. Çiftler bir dizi basit türden olabilir. Yönetim Araçları, çalışma zamanında arabirim aracılığıyla hizmetlere bağlanabilir. WCF, adresler, bağlamalar, davranışlar ve dinleyicileri gibi hizmetlerin özniteliklerini gösterir.  
  
 Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilebilir. Bu, aşağıdaki örnek yapılandırmada `wmiProviderEnabled` gösterildiği gibi [ \<System. ServiceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümündeki [ \<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) özniteliği aracılığıyla yapılır.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Bu yapılandırma girişi bir WMI arabirimi sunar. Yönetim uygulamaları artık bu arabirimden bağlanabilir ve uygulamanın yönetim araçlarına erişebilir.  
  
## <a name="accessing-wmi-data"></a>WMI verilerine erişme  
 WMI verilerine birçok farklı yolla erişilebilir. Microsoft, betikler, Visual Basic uygulamalar, C++ uygulamalar ve .NET Framework Için WMI API 'leri sağlar. Daha fazla bilgi için bkz. [WMI kullanma](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
> WMI verilerine programlı olarak erişmek için .NET Framework sağlanan yöntemleri kullanırsanız, bu tür yöntemlerin bağlantı kurulurken özel durumlar oluşturduğunu bilmelisiniz. Bu bağlantı, <xref:System.Management.ManagementObject> örneğin oluşturulması sırasında, ancak gerçek veri değişimini içeren ilk istekte kurulmaz. Bu nedenle, olası özel durumları `try..catch` yakalamak için bir blok kullanmanız gerekir.  
  
 İzleme ve mesaj günlüğü düzeyini, WMI 'daki `System.ServiceModel` izleme kaynağı için de ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz. Bu, bu Boole özelliklerini sunan [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) örneğine erişerek yapılabilir `LogMessagesAtServiceLevel`:, `LogMessagesAtTransportLevel`, `LogMalformedMessages`ve `TraceLevel`. Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırma bölümünde ayarlarsanız, daha sonra uygulamanın çalıştığı zaman olarak `true` değiştirebilirsiniz. Bu işlem, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde etkinleştirir. Benzer şekilde, yapılandırma dosyanızda ileti günlüğünü etkinleştirirseniz, WMI kullanarak çalışma zamanında devre dışı bırakabilirsiniz.  
  
 İleti günlüğe kaydetme için hiçbir ileti günlüğe kaydetme veya `System.ServiceModel` yapılandırma dosyasında izleme dinleyicilerinin belirtilmediği durumlarda, değişiklikler WMI tarafından kabul edilse de, değişikliklerinizin etkin olmadığı farkında olmalısınız. İlgili dinleyicileri doğru şekilde ayarlama hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) ve [izlemeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Yapılandırma tarafından belirtilen diğer tüm izleme kaynaklarının izleme düzeyi uygulama başlatıldığında etkilidir ve değiştirilemez.  
  
 WCF, komut `GetOperationCounterInstanceName` dosyası oluşturmak için bir yöntem sunar. Bu yöntem, bir işlem adı ile sağlarsanız bir performans sayacı örnek adı döndürür. Ancak, girişinizi doğrulamaz. Bu nedenle, yanlış bir işlem adı sağlarsanız, yanlış bir sayaç adı döndürülür.  
  
 Örneğin özelliği, hedef hizmete yönelik WCF istemcisi `Service` yönteminde oluşturulmadıysa başka bir hizmete bağlanmak için bir hizmet tarafından açılan kanalları saymaz. `OutgoingChannel` `Service`  
  
 **Dikkat** edin WMI yalnızca 3 ondalık <xref:System.TimeSpan> noktaya kadar bir değeri destekler. Örneğin, hizmetiniz özelliklerinden birini olarak <xref:System.TimeSpan.MaxValue>ayarlarsa, WMI üzerinden görüntülendiğinde 3 ondalık noktadan sonra değeri kesilir.  
  
## <a name="security"></a>Güvenlik  
 WCF WMI sağlayıcısı bir ortamdaki hizmetlerin bulunmasına izin verdiğinden, buna erişim vermek için çok dikkatli olmanız gerekir. Varsayılan yalnızca yönetici erişimini rahatladıysanız, ortamınızda hassas verilere daha az güvenilir taraflar erişebilmeye izin verebilirsiniz. Özellikle, uzak WMI erişimiyle ilgili izinleri gevbir şekilde bırakırsanız, taşması saldırıları meydana gelebilir. Bir işlem aşırı sayıda WMI isteği ile taştığında, performansı düşebilir.  
  
 Ayrıca, MOF dosyası için erişim izinlerine güveniyorsanız, daha az güvenilir taraflar WMI davranışını değiştirebilir ve WMI şemasında yüklenen nesneleri değiştirebilir. Örneğin, kritik verilerin yöneticiden kaldırılması veya bir özel durum doldurulmayan veya neden olmayan alanlar dosyaya eklenebileceği için alanlar kaldırılabilir.  
  
 Varsayılan olarak, WCF WMI sağlayıcısı yönetici için "yürütme yöntemi", "sağlayıcı yazma" ve "hesabı etkinleştir" iznini ve ASP.NET, yerel hizmet ve ağ hizmeti için "hesabı etkinleştir" iznini verir. Özellikle,[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformlarda olmayan ASP.NET hesabı, WMI ServiceModel ad alanına okuma erişimine sahiptir. Bu ayrıcalıkları belirli bir kullanıcı grubuna vermek istemiyorsanız, WMI sağlayıcısını devre dışı bırakmanız gerekir (varsayılan olarak devre dışıdır) ya da belirli kullanıcı grubu için erişimi devre dışı bırakmanız gerekir.  
  
 Ayrıca, WMI 'yi yapılandırma yoluyla etkinleştirmeye çalıştığınızda, yetersiz kullanıcı ayrıcalıkları nedeniyle WMI etkinleştirilmemiş olabilir. Ancak, bu hatayı kaydetmek için olay günlüğüne hiçbir olay yazılmaz.  
  
 Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.  
  
1. Başlat ' a ve ardından Çalıştır ' a tıklayıp **compmgmt. msc**yazın.  
  
2. **Özellikler**' i seçmek için **Hizmetler ve uygulama/WMI denetimleri** öğesine sağ tıklayın.  
  
3. **Güvenlik** sekmesini seçin ve **kök/ServiceModel** ad alanına gidin. **Güvenlik** düğmesine tıklayın.  
  
4. Erişimi denetlemek istediğiniz belirli bir grup veya kullanıcıyı seçin ve izinleri yapılandırmak için **Izin ver** veya **Reddet** onay kutusunu kullanın.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Ek kullanıcılara WCF WMI kayıt Izinleri verme  
 WCF, yönetim verilerini WMI 'ya gösterir. Bu işlemi, bazen "ayrılmış sağlayıcı" olarak adlandırılan işlem içi bir WMI sağlayıcısını barındırarak yapar. Yönetim verilerinin açığa çıkarılması için, bu sağlayıcıyı kaydeden hesabın uygun izinlere sahip olması gerekir. Windows 'da, yalnızca küçük bir ayrıcalıklı hesap kümesi varsayılan olarak ayrılmış sağlayıcıları kaydedebilir. Bu bir sorun olduğundan, kullanıcılar genellikle varsayılan kümesinde olmayan bir hesap altında çalışan bir WCF hizmetinden WMI verilerini açığa çıkarmak istiyor.  
  
 Bu erişimi sağlamak için, yöneticinin ek hesaba aşağıdaki sırayla aşağıdaki izinleri vermesi gerekir:  
  
1. WCF WMI ad alanına erişme izni.  
  
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
  
     Bu PowerShell betiği, yerleşik kullanıcılar grubuna "root/ServiceModel" WMI ad alanına erişim izni vermek için güvenlik tanımlayıcısı tanım dili 'ni (SDDL) kullanır. Aşağıdaki ACL 'Leri belirtir:  
  
    - Yerleşik yönetici (BA)-zaten erişime sahipti.  
  
    - Ağ hizmeti (NS)-zaten erişime sahipti.  
  
    - Yerel sistem (LS)-zaten erişime sahipti.  
  
    - Yerleşik kullanıcılar-erişim verilecek grup.  
  
#### <a name="to-grant-provider-registration-access"></a>Sağlayıcı kayıt erişimi sağlamak için  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Rastgele kullanıcılara veya gruplara erişim verme  
 Bu bölümdeki örnek, tüm yerel kullanıcılara WMI sağlayıcı kayıt ayrıcalıkları verir. İçinde yerleşik olmayan bir kullanıcıya veya gruba erişim vermek istiyorsanız, bu kullanıcı veya grubun güvenlik tanımlayıcısını (SID) edinmeniz gerekir. Rastgele bir kullanıcı için SID almanın basit bir yolu yoktur. Bir yöntem, istenen kullanıcı olarak oturum açıp aşağıdaki kabuk komutunu yayınvermektir.  
  
```  
Whoami /user  
```  
  
 Bu, geçerli kullanıcının SID 'sini sağlar, ancak bu yöntem herhangi bir rastgele kullanıcının SID 'sini almak için kullanılamaz. SID 'yi almaya yönelik başka bir yöntem, [yönetim görevleri Için Windows 2000 Kaynak Seti araçlarından](https://go.microsoft.com/fwlink/?LinkId=178660) [GETSID. exe](https://go.microsoft.com/fwlink/?LinkId=186467) aracını kullanmaktır. Bu araç iki kullanıcının (yerel veya etki alanı) SID 'Lerini karşılaştırır ve yan etkisi olarak iki SID 'yi komut satırına yazdırır. Daha fazla bilgi için bkz. [tanınmış SID 'ler](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzak WMI nesne örneklerine erişme  
 Uzak bir makinedeki WCF WMI örneklerine erişmeniz gerekiyorsa, erişim için kullandığınız araçlarda paket gizliliğini etkinleştirmeniz gerekir. Aşağıdaki bölümde, bu, WMI CıM Studio, Windows Yönetim Araçları Sınayıcısı ve .NET SDK 2,0 ile nasıl elde edileceğini açıklamaktadır.  
  
### <a name="wmi-cim-studio"></a>WMI CıM Studio  
 [WMI yönetim araçları](https://go.microsoft.com/fwlink/?LinkId=95185)'nı yüklediyseniz WMI örneklerine erışmek IÇIN WMI CIM Studio 'yu kullanabilirsiniz. Araçlar şu klasörlerdir  
  
 **%windir%\Program Files\WMI araçları\\**  
  
1. **Ad alanına bağlan:** penceresinde, **Root\servicemodel** yazın ve Tamam ' a tıklayın **.**  
  
2. **WMI CIM Studio oturumu açma** penceresinde, **seçenekleri > >** düğmesine tıklayarak pencereyi genişletin. **Kimlik doğrulama düzeyi**için **paket gizliliği** ' ni seçin ve **Tamam**' ı tıklatın.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Yönetim Araçları Sınayıcısı  
 Bu araç Windows tarafından yüklenir. Çalıştırmak için **Başlat/Çalıştır** iletişim kutusuna **cmd. exe** yazarak bir komut konsolu başlatın ve **Tamam**' a tıklayın. Ardından, komut penceresine **WBEMTest. exe** yazın. Windows Yönetim Araçları sınayıcı aracı başlatılır.  
  
1. Pencerenin sağ üst köşesindeki **Bağlan** düğmesine tıklayın.  
  
2. Yeni pencerede, **ad alanı** alanı için **Root\servicemodel** yazın ve **kimlik doğrulama düzeyi**için **paket gizliliği** ' ni seçin. **Bağlan**'a tıklayın.  
  
### <a name="using-managed-code"></a>Yönetilen kodu kullanma  
 Ayrıca, <xref:System.Management> ad alanı tarafından sunulan sınıfları kullanarak uzak WMI örneklerine programlı bir şekilde erişebilirsiniz. Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
