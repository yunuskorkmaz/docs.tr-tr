---
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 99fa1e7dea09601de5efff9ef8d8c6a66eae1bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953770"
---
# <a name="custom-binding-security"></a>Özel Bağlama Güvenliği
Bu örnek, bir özel bağlama kullanılarak güvenliğin nasıl yapılandırılacağını gösterir. Güvenli bir aktarımla ileti düzeyi güvenliği etkinleştirmek için özel bağlamayı nasıl kullanacağınızı gösterir. Bu, iletileri istemci ve hizmet arasında iletmek için güvenli bir aktarım gerektiğinde ve iletilerin ileti düzeyinde güvenli olması gerektiği durumlarda yararlıdır. Bu yapılandırma sistem tarafından belirtilen bağlamalar tarafından desteklenmiyor.

 Bu örnek, bir istemci konsol programından (EXE) ve bir hizmet konsolu programından (EXE) oluşur. Hizmet bir çift yönlü sözleşme uygular. Sözleşme, matematik işlemlerini (ekleme `ICalculatorDuplex` , çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır. `ICalculatorDuplex` Arabirim, istemcinin bir oturum üzerinde çalışan bir sonucu hesaplamak için matematik işlemleri gerçekleştirmesini sağlar. Bağımsız olarak, hizmet sonuçları `ICalculatorDuplexCallback` arabirime döndürebilir. Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir. Çift yönlü iletişimi destekleyen ve güvenli hale gelen özel bir bağlama tanımlanmıştır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Hizmet yapılandırması aşağıdakileri destekleyen özel bir bağlama tanımlar:

- TLS/SSL protokolü kullanılarak korunan TCP iletişimi.

- Windows ileti güvenliği.

 Özel bağlama yapılandırması, ileti düzeyi güvenliği aynı anda etkinleştirerek güvenli aktarımı etkinleştirir. Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir. Özel bağlama, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmette ve istemci yapılandırma dosyalarında tanımlanmıştır.

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

 Özel bağlama, Aktarım düzeyinde hizmetin kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır. Bu, `sslStreamSecurity` Binding öğesi tarafından gerçekleştirilir. Hizmetin sertifikası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışı kullanılarak yapılandırılır.

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

 Ayrıca, özel bağlama Windows kimlik bilgisi türü ile ileti güvenliği kullanır-bu, varsayılan kimlik bilgisi türüdür. Bu, `security` Binding öğesi tarafından gerçekleştirilir. Kerberos kimlik doğrulama mekanizması kullanılabiliyorsa, istemci ve hizmetin her ikisi de ileti düzeyi güvenlik kullanılarak doğrulanır. Bu, örnek Active Directory ortamda çalıştırıldığında oluşur. Kerberos kimlik doğrulama mekanizması kullanılamıyorsa, NTLM kimlik doğrulaması kullanılır. NTLM, istemcinin hizmet kimliğini doğrular, ancak hizmette hizmetin kimliğini doğrulamaz. Bağlama öğesi `SecureConversation` kullanmak`authenticationType`üzere yapılandırılmıştır, bu da hem istemcide hem de hizmette bir güvenlik oturumu oluşturulmasına neden olur. `security` Bu, hizmetin çift yönlü sözleşmesinin çalışmasını sağlamak için gereklidir.

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye döndürülen iletileri görürsünüz. Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir. İstemcisini kapatmak için ENTER tuşuna basın.

 Dahil edilen Setup. bat dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için istemciyi ve sunucuyu ilgili hizmet sertifikasıyla yapılandırmanıza olanak sağlar. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, bu örneğe uygulanan toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış verilmiştir:

- Sunucu sertifikası oluşturuluyor.

     Setup. bat dosyasındaki aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%` Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası, sunucu adını localhost olarak varsayılan olarak belirler.

     Sertifika, Web 'de barındırılan hizmetler için CurrentUser deposunda depolanır.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.

     Setup. bat dosyasındaki aşağıdaki satırlar sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Setup. bat toplu iş dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yönetici ayrıcalıklarıyla Visual Studio için bir Geliştirici Komut İstemi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    >  Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2. \Service\bin. adresinden Service. exe ' yi Başlat  
  
3. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında:  
  
    1. Hizmet bilgisayarında servicemodelsamples adlı bir sanal dizin oluşturun.  
  
    2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.  
  
    3. Setup. bat ve Cleanup. bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
    4. Yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi için aşağıdaki komutu çalıştırın: `Setup.bat service`. Bu işlem, toplu iş dosyasının çalıştırıldığı bilgisayarın adıyla eşleşen konu adına sahip hizmet sertifikasını oluşturur.  
  
        > [!NOTE]
        >  Setup. bat toplu iş dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır. PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.

    5. Service. exe. config dosyasının içindeki [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) , önceki adımda oluşturulan sertifikanın konu adını yansıtacak şekilde değiştirin.

    6. Service. exe ' yi bir komut isteminden çalıştırın.

2. İstemci bilgisayarda:

    1. İstemci program dosyalarını \client\bin\ klasöründen istemci bilgisayara kopyalayın. Ayrıca, Cleanup. bat dosyasını kopyalayın.

    2. Önceki örneklerden gelen eski sertifikaları kaldırmak için Cleanup. bat dosyasını çalıştırın.

    3. Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici komut istemi açarak hizmetin sertifikasını dışarı aktarın ve hizmet bilgisayarında aşağıdaki komutu çalıştırın (yerine `%SERVER_NAME%` , bilgisayarın tam adı hizmet çalışıyor):

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. % SERVER_NAME%. cer öğesini istemci bilgisayara kopyalayın (% SERVER_NAME% öğesini hizmetin çalıştığı bilgisayarın tam adı ile değiştirin).

    5. Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açarak hizmetin sertifikasını içeri aktarın ve istemci bilgisayarda aşağıdaki komutu çalıştırın (% SERVER_NAME% yerine, bilgisayarın tam adı hizmet çalışıyor):

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         Sertifika güvenilen bir veren tarafından verildiyse, c, d ve e adımları gerekli değildir.

    6. İstemcinin App. config dosyasını aşağıdaki gibi değiştirin:

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

    7. Hizmet, bir etki alanı ortamında NetworkService veya LocalSystem hesabı dışında bir hesap altında çalışıyorsa, uygun UPN veya SPN 'YI ayarlamak için istemcinin App. config dosyasındaki hizmet uç noktası kimliğini değiştirmeniz gerekebilir hizmetini çalıştırmak için kullanılan hesapta. Uç nokta kimliği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) konusu.

    8. Bir komut isteminden Client. exe ' yi çalıştırın.

### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için

- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.
