---
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a0d716c3689b506ad29d99f006f1a4bb7c53a3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-binding-security"></a>Özel Bağlama Güvenliği
Bu örnek güvenliğinin özel bağlama kullanılarak nasıl yapılandırılacağı gösterilmektedir. Özel bağlama güvenli bir taşıma birlikte ileti düzeyi güvenliği etkinleştirmek için nasıl kullanılacağını gösterir. Bu, güvenli bir taşıma hizmet ve istemci arasındaki iletileri iletmek için gerekli ve iletileri ileti düzeyi üzerinde aynı anda güvenli olmalıdır durumunda faydalı olur. Bu yapılandırma, sistem tarafından sağlanan bağlamalar tarafından desteklenmiyor.  
  
 Bu örnek, bir istemci konsol programı (EXE) ve hizmeti bir konsol programı (EXE) oluşur. Hizmet çift yönlü sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculatorDuplex` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme). `ICalculatorDuplex` Arabirimi oturumu üzerinden çalışan bir sonuç hesaplama matematik işlemleri gerçekleştirmek istemci izin verir. Hizmet üzerinde bağımsız olarak, sonuçlar döndürebilir `ICalculatorDuplexCallback` arabirimi. İstemci ile hizmet arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlam kurulmalıdır için çift yönlü sözleşme bir oturum gerektirir. Özel bağlama güvenli ve çift yönlü iletişimi desteklediğini tanımlanır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet yapılandırması aşağıdaki destekleyen özel bağlama tanımlar:  
  
-   TLS/SSL protokolü kullanılarak korunan TCP iletişimi.  
  
-   Windows ileti güvenliği.  
  
 Özel bağlama yapılandırma, aynı anda ileti düzeyi güvenlik etkinleştirerek güvenli aktarımı sağlar. Bağlama öğeleri sıralama her bir katman kanal yığınında olabilmesinden dolayı bir özel bağlama, tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Özel bağlama, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmet ve istemci yapılandırma dosyalarını tanımlanır.  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 Özel bağlama taşıma düzeyi hizmette kimlik doğrulaması ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır. Bu tarafından gerçekleştirilir `sslStreamSecurity` bağlama öğesi. Hizmetin sertifika, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışı kullanılarak yapılandırılır.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata />  
        <serviceDebug includeExceptionDetailInFaults="False" />  
        <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
        </serviceCredentials>  
    </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Ayrıca, Windows kimlik bilgisi türü ile ileti güvenliği özel bağlama kullanır - varsayılan kimlik bilgisi türü budur. Bu tarafından gerçekleştirilir `security` bağlama öğesi. Hem istemci hem de hizmet Kerberos kimlik doğrulama mekanizması varsa ileti düzeyi güvenlik kullanılarak doğrulanır. Örnek Active Directory ortamında çalıştırıyorsanız bu gerçekleşir. Kerberos kimlik doğrulama mekanizması kullanılabilir durumda değilse, NTLM kimlik doğrulaması kullanılır. NTLM istemci hizmeti için kimlik doğrulaması yapar ancak istemci hizmete kimlik doğrulamasını yapmaz. `security` Bağlama öğesi kullanacak şekilde yapılandırılmış `SecureConversation``authenticationType`, hem istemci hem de hizmet güvenlik oturumu oluşturulmasına sonuçlanır. Bu hizmetin çalışmak çift yönlü sözleşme etkinleştirmek için gereklidir.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Üzerinde istemciye döndürülen iletileri örneği çalıştırdığınızda, gördüğünüz hizmetinden gönderilen geri çağırma arabirimi. Her bir ara sonucu, tüm işlemleri tamamlandıktan sonra tüm denklemi arkasından görüntülenir. İstemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
 Eklenen Setup.bat dosya, istemci ve sunucu sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili hizmet sertifikası ile yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Bu örnek için geçerlidir ve böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat dosyasından kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu dosya sunucusu adı için localhost varsayılan olarak ayarlanır.  
  
     Sertifika depolanan Web barındırılan hizmetleri Currentuser'a deposunda.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     İstemci güvenilir kişiler içine Setup.bat dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor. Bu ortam değişkenine bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi penceresi açın ve Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Service.exe \service\bin başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda:  
  
    1.  Hizmeti bilgisayarında servicemodelsamples adlı bir sanal dizin oluşturun.  
  
    2.  Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. \Bin alt dizinindeki dosyaları kopyalayın emin olun.  
  
    3.  Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
    4.  Açılan yönetici ayrıcalıklarına sahip bir Visual Studio komut isteminde aşağıdaki komutu çalıştırın: `Setup.bat service`. Bu toplu iş dosyasını çalıştıracağınız bilgisayar adıyla eşleşen konu adına sahip hizmet sertifikası oluşturur.  
  
        > [!NOTE]
        >  Setup.bat toplu iş dosyası, Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır. Path ortam değişkeni SDK yüklendiği dizinine işaret etmesini gerektirir. Bu ortam değişkenine bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.  
  
    5.  Değişiklik [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) önceki adımda oluşturulan sertifikasının konu adını yansıtacak şekilde Service.exe.config dosya içinde.  
  
    6.  Service.exe bir komut isteminden çalıştırın.  
  
2.  İstemci bilgisayarda:  
  
    1.  İstemci program dosyaları \client\bin\ klasöründen istemci bilgisayara kopyalayın. Ayrıca Cleanup.bat dosyasını kopyalayın.  
  
    2.  Önceki örneklerinden herhangi bir eski sertifika kaldırmak için Cleanup.bat çalıştırın.  
  
    3.  Yönetici ayrıcalıkları olan bir Visual Studio komut istemi açıp hizmet bilgisayarda aşağıdaki komutu çalıştırarak hizmetin sertifika verme (yerine `%SERVER_NAME%` hizmet olduğu bilgisayar tam adı çalıştıran):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  %SERVER_NAME%.cer (alternatif % sunucu_adı % tam adda hizmetinin çalıştığı bilgisayar) istemci bilgisayara kopyalayın.  
  
    5.  Yönetici ayrıcalıkları olan bir Visual Studio komut istemi açıp (alternatif sunucu_adı % tam ada sahip hizmet olduğu bilgisayarın istemci bilgisayarda aşağıdaki komutu çalıştırarak hizmetin sertifikayı alın çalıştıran):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Adımları c, d ve e güvenilir bir veren tarafından sertifika verilirse gerekli değildir.  
  
    6.  İstemcinin App.config dosyasını aşağıdaki gibi değiştirin:  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  Hizmet bir NetworkService dışında hesabı veya etki alanı ortamında LocalSystem hesabı altında çalışıyorsa, uygun UPN veya temel SPN ayarlamak için istemcinin App.config dosyası içinde hizmet uç noktası için uç nokta kimlik değiştirmeniz gerekebilir hizmetini çalıştırmak için kullanılan hesap üzerinde. Uç noktası kimlik hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) konu.  
  
    8.  Client.exe bir komut isteminden çalıştırın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
