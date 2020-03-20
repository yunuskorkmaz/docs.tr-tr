---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183526"
---
# <a name="message-security-sample"></a>İleti Güvenliği Örneği
Bu örnek, ileti güvenliğini kullanan bir `basicHttpBinding` uygulamanın nasıl uygulanacağını gösterir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Güvenlik `basicHttpBinding` modu aşağıdaki değerlere ayarlanabilir: `Message`, `Transport` `TransportWithMessageCredential`, `TransportCredentialOnly` `None`ve . Aşağıdaki örnek hizmet App.config dosyasında, uç nokta `basicHttpBinding` tanımı aşağıdaki örnek `Binding1`yapılandırmada gösterildiği gibi, aşağıdaki örnek yapılandırmada gösterildiği gibi, bağlayıcı bir yapılandırmayı belirtir ve başvurur:  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 Bağlama yapılandırması, `mode` [ \<>güvenlik](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) özniteliğini ayarlar `Message` ve aşağıdaki örnek `Certificate` yapılandırmada gösterildiği gibi [ \<>iletin](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) özniteliğini ayarlar: `clientCredentialType`  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Hizmetin kendisini istemciye doğrulamak için kullandığı sertifika, `serviceCredentials` öğenin altındaki yapılandırma dosyasının davranışlar bölümünde ayarlanır. İstemcinin kendisini hizmete doğrulamak için kullandığı sertifikaya uygulanan doğrulama modu, öğenin `clientCertificate` altındaki davranışlar bölümünde de ayarlanır.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilir.  
  
 Arayanın kimliği aşağıdaki kod kullanılarak servis konsolu penceresinde görüntülenir:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Numuneyi aynı makinede çalıştırmak için  
  
1. Setup.bat'ı örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.  
  
    > [!NOTE]
    > Setup.bat toplu dosyası, Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir. Bu ortam değişkeni otomatik olarak bir Windows SDK Komut İstemi içinde ayarlanır.  
  
2. \service\bin'den hizmet uygulamasını çalıştırın.  
  
3. İstemci uygulamasını \client\bin'den çalıştırın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
5. Örneği bitirdikten sonra Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-machines"></a>Numuneyi makineler arasında çalıştırmak için  
  
1. Servis ikilileri için servis makinesinde bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını sunucudaki servis dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını sunucuya kopyalayın.  
  
3. İstemci ikilileri için istemci makinesinde bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
5. Sunucuda, çalıştırın. `setup.bat service` Bağımsız değişkenle birlikte çalışmak, `setup.bat` makinenin tam nitelikli alan adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`  
  
6. Makinenin tam nitelikli alan adı ile aynı olan yeni `findValue` sertifika adını [ \<(serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesindeki öznitelikte) yansıtacak şekilde Service.exe.config'i edin. Ayrıca, localhost yerine tam nitelikli bir makine adı belirtmek için temel adresin değerini değiştirin`.`  
  
7. Service.cer dosyasını servis dizininden istemci makinesindeki istemci dizinine kopyalayın.  
  
8. İstemci üzerinde, çalıştırın. `setup.bat client` Bağımsız değişkenle birlikte çalışmak, `setup.bat` client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`  
  
9. İstemci makinesindeki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin. Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yaparsınız. Ayrıca `findValue` [ \<varsayılan Sertifika>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) özniteliğini sunucunun tam nitelikli alan adı olan yeni hizmet sertifikası adı ile değiştirin.  
  
10. Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.  
  
11. İstemci üzerinde ImportServiceCert.bat'ı çalıştırın. Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
12. Sunucuda, ImportClientCert.bat çalıştırın, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.  
  
13. Servis makinesinde Service.exe'yi komut isteminden çalıştırın.  
  
14. İstemci makinesinde, istemci.exe komut istemi penceresinden başlatın.  
  
    1. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu komut dosyası, bu örneği makineler arasında çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Makineler arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
