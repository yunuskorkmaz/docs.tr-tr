---
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 61e8be6f7f621340a684bff69ec5c9d64ab36c61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565196"
---
# <a name="custom-binding-security"></a>Özel Bağlama Güvenliği
Bu örnek, özel bir bağlama kullanarak güvenlik yapılandırma işlemi gösterilmektedir. Bu, özel bağlama güvenli aktarım birlikte ileti düzeyi güvenliği etkinleştirmek için nasıl kullanılacağını gösterir. Bu hizmet ve istemci arasında ileti aktarmaya güvenli aktarım gereklidir ve iletileri ileti düzeyi üzerinde aynı anda güvenli olmalıdır yararlı olur. Bu yapılandırma, sistem tarafından sağlanan bağlamalar tarafından desteklenmiyor.  
  
 Bu örnek, bir istemci konsol programı'nı (EXE) ve hizmeti bir konsol programı (EXE) oluşur. Hizmet, çift yönlü sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculatorDuplex` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme). `ICalculatorDuplex` Oturumu üzerinden çalışan bir sonuç hesaplama matematik işlemlerini gerçekleştirmek üzere istemci arabirimi sağlar. Hizmet üzerinde bağımsız olarak, sonuçlar döndürebilir `ICalculatorDuplexCallback` arabirimi. Hizmet ve istemci arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlamı yeniden kurulması için çift yönlü sözleşme bir oturumu gerektirir. Özel bağlama güvenli ve çift yönlü iletişimi destekleyen tanımlanır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet yapılandırması aşağıdaki destekleyen özel bir bağlama tanımlar:  
  
-   TLS/SSL protokolü kullanılarak korunan TCP iletişimi.  
  
-   İleti güvenliği Windows.  
  
 Özel bağlama yapılandırması güvenli aktarım ileti düzeyi güvenliği aynı anda etkinleştirerek sağlar. Bağlama öğelerinin sıralama her bir katman kanal yığınında temsil ettiği için bir özel bağlamayı tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Özel bağlama hizmeti ve istemci yapılandırma dosyalarını, aşağıdaki örnek yapılandırmada gösterildiği gibi tanımlanır.  
  
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
  
 Özel bağlama taşıma düzeyinde hizmet kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında mesajlarını korumak için bir hizmet sertifikası kullanır. Bu tarafından gerçekleştirilir `sslStreamSecurity` bağlama öğesi. Hizmet sertifikası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışını kullanarak yapılandırılır.  
  
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
  
 Ayrıca, özel bağlamanın Windows kimlik bilgisi türü ile ileti güvenliği kullanır - bu varsayılan kimlik bilgisi türüdür. Bu tarafından gerçekleştirilir `security` bağlama öğesi. Hizmet ve istemci, Kerberos kimlik doğrulama mekanizması varsa, ileti düzeyi güvenliği kullanılarak doğrulanır. Bu örnek Active Directory ortamında çalışırsa gerçekleşir. Kerberos kimlik doğrulama mekanizması kullanılabilir durumda değilse, NTLM kimlik doğrulaması kullanılır. NTLM bir hizmete istemcinin kimliğini doğrular, ancak istemci hizmete kimlik doğrulaması yapmaz. `security` Bağlama öğesi kullanacak şekilde yapılandırıldığını `SecureConversation``authenticationType`, hem istemci hem de hizmet üzerinde bir güvenlik oturumu oluşturulmasıyla sonuçlanır. Bu, hizmetin çalışması çift yönlü sözleşme etkinleştirmek için gereklidir.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Örneği çalıştırdığında üzerinde istemciye döndürülen iletileri bkz hizmetinden gönderilen geri çağırma arabirimi. Tüm işlemler tamamlandıktan sonra tüm denklemi ardından her ara sonuçlar görüntülenir. İstemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
 Dahil edilen Setup.bat dosyasının, istemci ve sunucu sertifikası tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili hizmet sertifikası ile yapılandırmak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Bu örnek için geçerlidir ve böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Setup.bat dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu dosya sunucusu adı için localhost varsayar.  
  
     Depolanmış bir sertifikayla Web barındırılan hizmetleri CurrentUser deposunda.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.  
  
     İstemci güvenilir kişiler uygulamasına Setup.bat dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor. Bu ortam değişkeni, bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi penceresi açın ve örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2.  Service.exe \service\bin başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda:  
  
    1.  Hizmeti bilgisayarında servicemodelsamples adlı sanal bir dizin oluşturun.  
  
    2.  Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. Dosyaları \bin alt dizinde kopyalama emin olun.  
  
    3.  Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
    4.  Yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde aşağıdaki komutu çalıştırın: `Setup.bat service`. Bu, toplu iş dosyasını çalıştırmak bilgisayarın adı ile eşleşen bir konu adına sahip hizmet sertifikası oluşturur.  
  
        > [!NOTE]
        >  Setup.bat toplu iş dosyası, bir Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır. Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir. Bu ortam değişkeni, bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.  
  
    5.  Değişiklik [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) önceki adımda oluşturulan sertifikanın konu adı yansıtacak şekilde Service.exe.config dosyasının içinde.  
  
    6.  Service.exe, bir komut isteminden çalıştırın.  
  
2.  İstemci bilgisayarda:  
  
    1.  İstemci program dosyaları \client\bin\ klasöründen istemci bilgisayara kopyalayın. Ayrıca Cleanup.bat dosyasını kopyalayın.  
  
    2.  Önceki örneklerinden herhangi bir eski sertifika kaldırmak için Cleanup.bat çalıştırın.  
  
    3.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açıp hizmet bilgisayarda aşağıdaki komutu çalıştırarak hizmetin sertifikayı dışarı aktarma (yerine `%SERVER_NAME%` hizmeti, bilgisayarın tam olarak nitelenmiş ada sahip çalışan):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  %SERVER_NAME%.cer (yerine % sunucu_adı % tam olarak nitelenmiş adda hizmetinin çalıştığı bilgisayarın) istemci bilgisayara kopyalayın.  
  
    5.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açıp aşağıdaki komutu (yedek sunucu_adı % tam olarak nitelenmiş adda hizmeti, bilgisayarın istemci bilgisayarda çalışan hizmetin sertifika alma çalışan):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Adımları c, d ve e güvenilen veren tarafından sertifika verilirse gerekli değildir.  
  
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
  
    7.  Hizmet bir dışında NetworkService hesabı veya etki alanı ortamında LocalSystem hesabı altında çalışıyorsa, istemcinin App.config dosyasında uygun UPN veya SPN tabanlı ayarlamak için hizmet uç noktası için uç nokta kimliğini değiştirmeniz gerekebilir hesapta, hizmeti çalıştırmak için kullanılır. Uç nokta kimlik hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) konu.  
  
    8.  Client.exe bir komut isteminden çalıştırın.  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
