---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0862f747cb969a6aa2e63d86e842097260e95b56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Tanılama için Windows Yönetim İzlemesini Kullanma
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Çalışma zamanında bir hizmetin denetleme kullanıma sunan bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Yönetim Araçları (WMI) sağlayıcısı.  
  
## <a name="enabling-wmi"></a>WMI etkinleştirme  
 WMI, Web tabanlı Kuruluş Yönetimi'nin (WBEM) standart Microsoft uygulamasıdır. [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]bkz: WMI SDK [Windows Yönetim Araçları](https://msdn.microsoft.com/library/aa394582.aspx). WBEM nasıl uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı kullanıma sunmak için bir endüstri standardıdır.  
  
 Bir WMI sağlayıcısı WBEM uyumlu arabirimi aracılığıyla çalışma zamanında izleme kullanıma sunan bir bileşenidir. Öznitelik/değer çiftine sahip WMI nesneler kümesinden oluşur. Çiftleri basit türler sayısı olabilir. Yönetim Araçları, çalışma zamanında arabirimi üzerinden hizmetlere bağlanabilir. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]adresler, bağlamalar, davranışları ve dinleyicileri gibi hizmetleri özniteliklerini kullanır.  
  
 Uygulama yapılandırma dosyasında yerleşik WMI Sağlayıcısı'nın etkin hale getirilebilir. Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Bu yapılandırma girdisi WMI arabirimini kullanıma sunar. Yönetim uygulamaları artık bu arabirimi üzerinden bağlanır ve Yönetim Araçları'nı uygulamanın erişir.  
  
## <a name="accessing-wmi-data"></a>WMI verilerine erişme  
 WMI veri birçok farklı yolla erişilebilir. Microsoft, komut dosyaları için WMI API'lerini sağlar [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] uygulamalar, C++ uygulamaları ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Daha fazla bilgi için bkz: [kullanılarak WMI](http://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  WMI verilerini programlı olarak erişmek için yöntemler sağlanan .NET Framework'te kullanıyorsanız bağlantı kurulduğunda tür yöntem özel durumlar oluşturma farkında olması gerekir. Bağlantı oluşturma işlemi sırasında kurulmaz <xref:System.Management.ManagementObject> örneği, ancak ilk istek gerçek veri değişimi içeren. Bu nedenle, kullanmanız gereken bir `try..catch` olası özel durumlarını yakalama bloğu.  
  
 İzleme ve ileti günlüğe kaydetme düzeyi, yanı sıra ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz `System.ServiceModel` WMI izleme kaynağı. Bu erişerek yapılabilir [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) Boolean bu özellikleri sunar örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, ve `TraceLevel`. Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırmanıza rağmen ayarlamak bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebileceğiniz `true` uygulama çalışırken. Bu ileti günlüğe kaydetme çalışma zamanında etkili bir şekilde etkinleştirir. İleti günlüğe kaydetme, yapılandırma dosyanızda etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz.  
  
 Bilmeniz gereken olması durumunda hiçbir ileti günlük kaydı izleme dinleyicileri ileti günlüğe kaydetme veya Hayır için `System.ServiceModel` izleme dinleyicileri izleme için yapılandırma dosyasında belirtilen, değişiklikleri WMI tarafından kabul edilen olsa bile, değişikliklerin hiçbiri yürürlüğe, alınır. Düzgün ilgili dinleyicileri ayarlama hakkında daha fazla bilgi için bkz: [yapılandırma ileti günlüğe kaydetme](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) ve [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Uygulama başladığında yapılandırması tarafından belirtilen diğer tüm izleme kaynakları izleme düzeyini etkilidir ve değiştirilemez.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]kullanıma sunan bir `GetOperationCounterInstanceName` komut dosyası için yöntem. Bir işlem adıyla sağlarsanız, bu yöntem bir performans sayacı örneği adını döndürür. Ancak, giriş doğrulamaz. Bu nedenle, yanlış işlem adı sağlarsanız, yanlış sayaç adı döndürülür.  
  
 `OutgoingChannel` Özelliği `Service` örneği başka bir hizmete bağlanmak için bir hizmet tarafından açılmış kanalları saymak değil [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hedef hizmeti istemciye oluşturulmadı içinde `Service` yöntemi.  
  
 **Uyarı** WMI yalnızca destekleyen bir <xref:System.TimeSpan> 3 adede kadar ondalık ayırıcıların değeri. Örneğin, hizmetiniz için özelliklerinden biri ayarlarsa <xref:System.TimeSpan.MaxValue>, değeri 3 ondalık WMI aracılığıyla görüntülendiğinde noktadan sonra kesilir.  
  
## <a name="security"></a>Güvenlik  
 Çünkü [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI sağlayıcısı, bir ortamda Hizmetleri bulma sayesinde, kendisine erişim verilmesi için çok dikkatli olmanız gerekir. Varsayılan yalnızca yönetici erişimi hafifletin, ortamınızda hassas bilgilere erişimi daha az güvenilir tarafların izin verebilir. Uzak WMI erişim izinlerini çözmek, özellikle saldırıları taşmasını ortaya çıkabilir. Bir işlem tarafından aşırı WMI istekleri yayılan, kendi performans düşebilir.  
  
 Ayrıca, MOF dosyası için erişim izinlerini hafifletin, daha az güvenilen taraf WMI davranışını denetlemek ve WMI şemasını yüklenen nesneler alter. Örneğin, alanlar kritik verileri Yöneticisi'nden gizli bilgiler veya dosyasına eklenen doldurmak veya özel durumlara neden alanları şekilde kaldırılabilir.  
  
 Varsayılan olarak, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI sağlayıcısı verir "yürütme yöntemi", "Sağlayıcı yazma" ya Administrator "hesabı etkinleştir" izinlerini ve ASP.NET, yerel hizmet ve ağ hizmeti için "hesabı etkinleştir" izni. Özellikle, üzerinde olmayan[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformları, ASP.NET hesabını okuyun WMI ServiceModel ad alanına erişimi. Belirli bir kullanıcı grubuna Bu ayrıcalıkları vermek istemiyorsanız (varsayılan olarak devre dışıdır) WMI sağlayıcısı devre dışı bırakmak veya erişimi belirli bir kullanıcı grubu için devre dışı bırakın.  
  
 WMI aracılığıyla yapılandırma etkinleştirmeye çalıştığınızda, ayrıca, WMI yetersiz kullanıcı ayrıcalıkların yetersizliği etkinleştirilmemiş olabilir. Ancak, hiçbir olay bu hatayı kaydetmek için olay günlüğüne yazılır.  
  
 Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.  
  
1.  Başlat'ı tıklatın ve ardından çalıştırın ve yazın **compmgmt.msc**.  
  
2.  Sağ **Hizmetleri ve uygulama/WMI denetimleri** seçmek için **özellikleri**.  
  
3.  Seçin **güvenlik** sekmesine gidin **kök/ServiceModel** ad alanı. Tıklatın **güvenlik** düğmesi.  
  
4.  Belirli bir grup veya erişimi denetlemek ve kullanmak istediğiniz kullanıcıyı seçin **izin** veya **reddetme** izinlerini yapılandırmak için onay kutusunu.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>WCF WMI kayıt ek kullanıcılara izin verme  
 WCF WMI yönetimi verilerini gösterir. Bunu bir "sağlayıcıyla" olarak da adlandırılan bir işlemdeki WMI sağlayıcısı barındırarak yapar. Yönetim verileri açığa çıkarılması bu sağlayıcısını kaydeder hesap uygun izinlere sahip gerekir. Windows, ayrıcalıklı hesaplar, yalnızca küçük bir kümesini ayrılmış sağlayıcıları varsayılan olarak kaydedebilirsiniz. Kullanıcıların yaygın olarak WMI veri varsayılan kümesinde olmayan bir hesap altında çalışan bir WCF hizmetinden kullanıma sunmak istediğiniz sorun olmasıdır.  
  
 Bu erişimi sağlamak için yönetici aşağıdaki sırayla ek hesap için aşağıdaki izinleri vermeniz gerekir:  
  
1.  WCF WMI Namespace için erişim izni.  
  
2.  WCF ayrılmış WMI sağlayıcısı kaydetme izni.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>WMI ad alanı erişim izni vermek için  
  
1.  Aşağıdaki PowerShell betiğini çalıştırın.  
  
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
  
     Bu PowerShell komut dosyasını, "kök/servicemodel" WMI ad alanına yerleşik Kullanıcılar grubu erişimi vermek için Güvenlik Tanımlayıcısı Tanım Dili (SDDL) kullanır. Aşağıdaki EDL'ler belirtir:  
  
    -   Yerleşik yönetici (BA) - erişim zaten var.  
  
    -   Ağ Hizmeti (NS) - zaten Erişebiliyordunuz.  
  
    -   Yerel Sistem (LS) - erişim zaten var.  
  
    -   Yerleşik kullanıcılar - erişim izni vermek için Grup.  
  
#### <a name="to-grant-provider-registration-access"></a>Sağlayıcı vermek için kayıt erişme  
  
1.  Aşağıdaki PowerShell betiğini çalıştırın.  
  
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
 Bu bölümdeki örnek tüm yerel kullanıcılar için WMI sağlayıcısı kayıt ayrıcalıklar verir. Daha sonra bir kullanıcı veya grup içinde yerleşik değildir erişim vermek istiyorsanız, o kullanıcının veya grubun güvenlik tanımlayıcısı (SID) edinmeniz gerekir. İsteğe bağlı bir kullanıcı için SID almak için basit bir yolu yoktur. İstenen kullanıcı olarak oturum açın ve aşağıdaki Kabuk komut vermek için bir yöntem var.  
  
```  
Whoami /user  
```  
  
 Bu geçerli kullanıcının SID sağlar, ancak bu yöntem, üzerinde herhangi bir kullanıcı SID almak için kullanılamaz. SID almak için başka bir yöntem kullanmaktır [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) öğesinden aracı [Windows 2000 Kaynak Seti Araçları yönetim görevleri için](http://go.microsoft.com/fwlink/?LinkId=178660). Bu aracı (yerel veya etki alanı) iki kullanıcı SID'si karşılaştırır ve bir yan etkisi komut satırına iki SID'ler yazdırır. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][İyi bilinen SID](http://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzak WMI nesne örneklerini erişme  
 Erişmeniz gerekiyorsa [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI örnekleri uzak makinede paket gizliliği erişmek için kullandığınız araçları etkinleştirmeniz gerekir. Aşağıdaki bölümde bu elde etmek WMI CIM Studio, Windows Yönetim Araçları Sınayıcısı, yanı sıra .NET SDK 2.0 kullanarak açıklar.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Yüklediyseniz [WMI Yönetimsel Araçlar](http://go.microsoft.com/fwlink/?LinkId=95185), WMI CIM Studio erişim WMI örnekleri için kullanabilirsiniz. Aşağıdaki klasörde araçlardır  
  
 **%windir%\Program Files\WMI araçları\\**  
  
1.  İçinde **ad Connect:** penceresinde, türü **root\ServiceModel** tıklatıp **Tamam.**  
  
2.  İçinde **WMI CIM Studio oturum açma** penceresinde tıklatın **Seçenekleri >>** penceresini genişletmek için düğmesi. Seçin **paket gizliliği** için **kimlik doğrulama düzeyi**, tıklatıp **Tamam**.  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Yönetim Araçları Sınayıcısı  
 Bu araç, Windows tarafından yüklenir. Çalıştırmak için bir komut konsolundan yazarak başlatma **cmd.exe** içinde **Başlat/Çalıştır** iletişim kutusu ve tıklatın **Tamam**. Ardından, yazın **wbemtest.exe** komut penceresinde. Windows Yönetim Araçları Sınayıcısı aracı sonra başlatılır.  
  
1.  Tıklatın **Bağlan** pencerenin sağ üst köşesinde bulunan düğmesi.  
  
2.  Yeni pencerede girin **root\ServiceModel** için **Namespace** alan ve select **paket gizliliği** için **kimlik doğrulama düzeyi**. **Bağlan**'a tıklayın.  
  
### <a name="using-managed-code"></a>Yönetilen kod kullanarak  
 Aynı zamanda uzak WMI örnekleri program aracılığıyla tarafından sağlanan sınıflarını kullanarak erişebilirsiniz <xref:System.Management> ad alanı. Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
