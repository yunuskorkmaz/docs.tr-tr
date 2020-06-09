---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 935695a46e907bf1deeb2e5cb24917ba92b81fe0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584876"
---
# <a name="message-security-sample"></a>İleti Güvenliği Örneği
Bu örnek, ve ileti güvenliğini kullanan bir uygulamanın nasıl uygulanacağını gösterir `basicHttpBinding` . Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Güvenlik modu `basicHttpBinding` aşağıdaki değerlere ayarlanabilir: `Message` , `Transport` , `TransportWithMessageCredential` , `TransportCredentialOnly` ve `None` . Aşağıdaki örnek Service App. config dosyasında, uç nokta tanımı ' `basicHttpBinding` ı belirtir ve `Binding1` Aşağıdaki örnek yapılandırmada gösterildiği gibi, adlı bir bağlama yapılandırmasına başvurur:  
  
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
  
 Bağlama yapılandırması `mode` , öğesinin özniteliğini [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) olarak ayarlar `Message` ve `clientCredentialType` öğesinin özniteliğini [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `Certificate` Aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlar:  
  
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
  
 Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, öğesinin altındaki yapılandırma dosyasının davranışlar bölümünde ayarlanır `serviceCredentials` . İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, öğesinin altındaki davranışlar bölümünde de ayarlanır `clientCertificate` .  
  
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
  
 Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.  
  
 Arayanın kimliği, aşağıdaki kod kullanılarak hizmet konsolu penceresinde görüntülenir:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
    > [!NOTE]
    > Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.  
  
2. Hizmet uygulamasını \service\bin. adresinden çalıştırma  
  
3. \Client\bin. adresinden istemci uygulamasını çalıştırma İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet makinesinde bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını sunucusundaki hizmet dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını sunucuya kopyalayın.  
  
3. İstemci ikili dosyaları için istemci makinesinde bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda öğesini çalıştırın `setup.bat service` . `setup.bat` `service` Bağımsız değişkeniyle birlikte çalıştırmak makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Service. exe. config dosyasını, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) makinenin tam etki alanı adıyla aynı olan yeni sertifika adını (öğesindeki özniteliğinde) yansıtacak şekilde düzenleyin. Ayrıca, temel adresin değerini localhost yerine tam bir makine adı belirtecek şekilde değiştirin`.`  
  
7. Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.  
  
8. İstemcisinde öğesini çalıştırın `setup.bat client` . `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` Client.com adlı bir istemci sertifikası oluşturur ve Istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
9. İstemci makinesindeki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz. Ayrıca `findValue` , öğesinin özniteliğini [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adıyla değiştirin.  
  
10. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
12. Sunucusunda ImportClientCert. bat dosyasını çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
13. Hizmet makinesinde, bir komut isteminden Service. exe ' yi çalıştırın.  
  
14. İstemci makinesinde, bir komut istemi penceresinden Client. exe ' yi başlatın.  
  
    1. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Makinelerde sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
