---
title: İleti Güvenliği Örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: 33
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 0ead08c454ed8b9e484d23d426e918c9f11fe3ed
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="message-security-sample"></a>İleti Güvenliği Örneği
Bu örnek nasıl kullanan bir uygulamayı uygulanacağını gösterilen `basicHttpBinding` ve güvenlik iletisi. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Güvenlik modunu `basicHttpBinding` aşağıdaki değerleri ayarlayın: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` ve `None`. Aşağıdaki örnek hizmet App.config dosyasında, uç nokta tanımı belirtir `basicHttpBinding` ve adlı bir bağlama yapılandırması başvurur `Binding1`, aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  </services>   …  
</system.serviceModel>  
```  
  
 Bağlama yapılandırma kümeleri `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message` ve ayarlar `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)için `Certificate` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  
 Hizmetin kendisi için istemci kimlik doğrulaması için kullandığı sertifikayı altında yapılandırma dosyasının davranışları bölümünde ayarlanır `serviceCredentials` öğesi. İstemci hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da altındaki davranışları bölümünde ayarlandığından `clientCertificate` öğesi.  
  
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
  
 Arayanın Kimliği hizmet konsol penceresinde aşağıdaki kodu kullanarak görüntülenir:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor. Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.  
  
2.  Hizmet uygulaması \service\bin çalıştırın.  
  
3.  İstemci uygulaması \client\bin çalıştırın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Sertifikaları örnekle tamamladığınızda Cleanup.bat çalıştırarak kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-machines"></a>Makine genelinde örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları hizmeti makinede bir dizin oluşturun.  
  
2.  Hizmet program dosyaları sunucuda hizmet dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyaları sunucuya kopyalayın.  
  
3.  İstemci ikili dosyalarının için istemci makinede bir dizin oluşturun.  
  
4.  İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
6.  Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesi) makinenin tam etki alanı adı ile aynı olduğu. Ayrıca localhost yerine bir makine tam adı belirtmek için taban adresi değerini değiştirin`.`  
  
7.  Service.cer dosya hizmeti dizininden istemci makinesinde istemci dizinine kopyalayın.  
  
8.  İstemci üzerinde çalışan `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
9. İstemci makinesinde Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Bunun için localhost sunucunun tam etki alanı adı ile değiştirerek. Aynı zamanda değiştirmeniz `findValue` özniteliği [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adı.  
  
10. Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
12. ImportClientCert.bat, çalıştıran sunucuda, bu istemci sertifikasını Client.cer dosyadan LocalMachine - TrustedPeople deposunu alır.  
  
13. Hizmeti makinede Service.exe bir komut isteminden çalıştırın.  
  
14. İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
    > [!NOTE]
    >  Bu komut dosyası, bu örnek makine genelinde çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makine genelinde sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a>Ayrıca Bkz.
