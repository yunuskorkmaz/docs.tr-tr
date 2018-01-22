---
title: "İleti Güvenliği Anonim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
caps.latest.revision: "52"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d6f3ac3ba51939f319d1d0e98265d7867233f2b6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-anonymous"></a>İleti Güvenliği Anonim
İleti güvenliği anonim örnek nasıl uygulandığını gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti düzeyi güvenlik herhangi bir istemci kimlik doğrulaması kullanan ancak sunucunun X.509 sertifikası kullanılarak kimlik doğrulaması gerektiren uygulama. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek. Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek yeni bir işlem döndürür hesaplayıcı arabirimi ekler `True` istemci doğrulanmadı durumunda.  
  
```  
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
  
 Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile yapılandırılmış bir `wsHttpBinding` bağlama. Varsayılan güvenlik modunu `wsHttpBinding` bağlama `Message`. `clientCredentialType` Özniteliği `None`.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
     <!--   
     <!--This configuration defines the security mode as Message and-->  
     <!--the clientCredentialType as None. This mode provides -- >  
     <!--server authentication only using the service certificate.-->  
  
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
  
 Hizmet kimlik doğrulaması için kullanılacak kimlik bilgileri belirtilen [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Sunucu sertifikası için aynı değeri içermelidir `SubjectName` için belirtilen değer olarak `findValue` özniteliği aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur. İstemci güvenlik modunu `wsHttpBinding` bağlama `Message`. `clientCredentialType` Özniteliği `None`.  
  
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
  
 Örnek kümeleri <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> için <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> hizmetin sertifika kimlik doğrulaması için. Bu istemcinin App.config dosyasında yapılır `behaviors` bölümü. Bu sertifika kullanıcının güvenilir kişiler deposunda ise, daha sonra sertifikanın veren zinciri doğrulamasının yapmadan güvenilir olduğunu anlamına gelir. Örnek bir sertifika yetkilisi (CA) tarafından verilen sertifikalara gerek kalmadan çalışabilmesi bu ayarı buraya kolaylık sağlamak için kullanılır. Bu ayar ChainTrust varsayılan daha az güvenlidir. Bu ayar güvenlik etkilerini kullanmadan önce dikkatle düşünülmelidir `PeerOrChainTrust` üretim kodunda.  
  
 İstemci uygulaması için bir çağrı ekler `IsCallerAnonymous` yöntemi ve aksi durumda farklı değil [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.  
  
```  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
IsCallerAnonymous returned: True  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 İleti güvenliği anonim örnekle dahil Setup.bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için uygun bir sertifika sunucusunu yapılandırmak sağlar. Toplu iş dosyası iki modda çalıştırabilirsiniz. Tek bilgisayar modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırında. Bu hizmet modunda çalıştırmak için yazın `setup.bat service`. Bu mod, örnek bilgisayarlar arasında çalıştırırken kullanın. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.  
  
 Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Sunucu_adı % değişkeni sunucusunun adını belirtir. Sertifika saklanır LocalMachine deposundaki. Kurulum toplu iş dosyası hizmetinin bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir. Aksi takdirde localhost için varsayılan olarak.  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Sertifikanın özel anahtarı izin verme.  
  
     Erişilebilir LocalMachine deposundaki depolanan sunucu sertifikası Setup.bat toplu iş dosyası aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
> [!NOTE]
>  ABD dışındaki kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` bölgesel eşdeğer. hesap adı.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründeki Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Kurulum toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]komut istemi. Path ortam değişkeni SDK yüklendiği dizinine işaret etmesini gerektirir. Bu ortam değişkenini içinde otomatik olarak ayarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]komut istemi.  
  
3.  Adres http://localhost/servicemodelsamples/service.svc girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.  
  
4.  Launch Client.exe from \client\bin. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2.  Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. \Bin alt dizinindeki dosyaları kopyalayın emin olun. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
3.  İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
6.  Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adı ile aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
9. İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
10. İstemci bilgisayarda bir komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.  
  
> [!NOTE]
>  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`  
  
## <a name="see-also"></a>Ayrıca Bkz.
