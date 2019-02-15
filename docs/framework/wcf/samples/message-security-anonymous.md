---
title: İleti Güvenliği Anonim
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 2cb1834414b402f8840a9dfa1ee9e2497cea7af5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304251"
---
# <a name="message-security-anonymous"></a>İleti Güvenliği Anonim
İleti güvenliği anonim örnek nasıl herhangi bir istemci kimlik doğrulaması ileti düzeyi güvenlik kullanan bir Windows Communication Foundation (WCF) uygulaması uygulamak için ancak sunucunun X.509 kullanarak kimlik doğrulaması gerektiren gösterir. Sertifika. Tüm uygulama iletileri istemci ve sunucu arasında imzalanmış ve şifrelenmiş. Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek. Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.

> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

 Bu örnek yeni bir işlem döndüren hesaplayıcı ekler `True` , istemcinin kimliği doğrulanmadı.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bağlama ile yapılandırılan bir `wsHttpBinding` bağlama. Varsayılan güvenlik modu `wsHttpBinding` bağlamanın `Message`. `clientCredentialType` Özniteliği `None`.

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Hizmet kimlik doğrulaması için kullanılacak kimlik bilgilerini belirtilen [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Sunucu sertifikası için aynı değeri içermelidir `SubjectName` için belirtilen değer olarak `findValue` öznitelik aşağıdaki örnek kodda gösterildiği gibi.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur. İstemci güvenlik modunu `wsHttpBinding` bağlamanın `Message`. `clientCredentialType` Özniteliği `None`.

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Örnek kümelerini <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> için <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> hizmetin sertifika kimlik doğrulaması. Bu istemcinin App.config dosyasında gerçekleştirilir `behaviors` bölümü. Bu, kullanıcının güvenilir kişiler deposunda sertifika ise, ardından sertifika veren zincirinin bir doğrulama gerçekleştirmeden güvenilir olduğunu anlamına gelir. Bu ayar, burada örnek bir sertifika yetkilisi (CA) tarafından verilen sertifikalara gerek kalmadan çalıştırılabilir. böylece kolaylık sağlamak için kullanılır. Bu ayar ChainTrust varsayılandan daha az güvenlidir. Bu ayar güvenlik etkilerini kullanmadan önce dikkatle düşünülmelidir `PeerOrChainTrust` üretim kodunda.

 İstemci uygulaması için bir çağrı ekler `IsCallerAnonymous` yöntemi ve aksi durumda farklı değil [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 İle ileti güvenliği anonim örnek dahil Setup.bat toplu iş dosyası sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili bir sertifika sunucusu yapılandırmanızı sağlar. Toplu iş dosyasını iki modda çalıştırabilirsiniz. Tek bilgisayarlı modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırına. Bu hizmet modunda çalıştırmak için yazın `setup.bat service`. Bu mod, örnek bilgisayarlar arasında çalıştırırken kullanın. Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.

 Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:

-   Sunucu sertifikası oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % Sunucu_adı % değişkeni, sunucu adını belirtir. Depolanmış bir sertifikayla LocalMachine depolama. Kurulum toplu iş dosyasını hizmet bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir. Aksi takdirde localhost için varsayılan olarak.

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.

     Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Sertifikanın özel anahtarı izin verme.

     Sunucu sertifikası için erişilebilir LocalMachine deposunda depolanır Setup.bat toplu iş dosyasında aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  ABD dışı kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` , bölgesel karşılığı hesap adıyla.

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1.  Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.

2.  Setup.bat Visual Studio'yu yönetici ayrıcalıklarıyla çalıştırmak için bir geliştirici Komut İstemi'nde örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    > Kurulum toplu iş dosyası, Visual Studio için geliştirici komut isteminden çalıştırılması için tasarlanmıştır. Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir. Bu ortam değişkeni, Visual Studio için geliştirici komut istemi içinde otomatik olarak ayarlanır.  
  
3.  Adresini girerek bir tarayıcı kullanarak hizmetine erişiminizi doğrulayın `http://localhost/servicemodelsamples/service.svc`.  
  
4.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2.  Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. Dosyaları \bin alt dizinde kopyalama emin olun. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
6.  Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adıyla aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut isteminden çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
10. İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
> [!NOTE]
>  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`

## <a name="see-also"></a>Ayrıca bkz.
