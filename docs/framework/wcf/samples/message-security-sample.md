---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
author: BrucePerlerMS
ms.openlocfilehash: 46e17cb2d4fecc8a71988ff61287e6cc682654c9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079759"
---
# <a name="message-security-sample"></a>İleti Güvenliği Örneği
Bu örnek kullanan bir uygulamanın nasıl uygulanacağını gösterir `basicHttpBinding` güvenlik iletisi. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Güvenlik modu `basicHttpBinding` aşağıdaki değerleri ayarlayın: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` ve `None`. Aşağıdaki örnek hizmet App.config dosyasında, uç nokta tanımı belirtir `basicHttpBinding` ve adlı bir bağlama yapılandırmasını başvurur `Binding1`aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  
 Hizmetin kendisini istemcinin kimliğini doğrulamak için kullandığı sertifikayı davranışları bölümü altında yapılandırma dosyasının kümesindeki `serviceCredentials` öğesi. İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da davranışları bölümünde ayarlanır `clientCertificate` öğesi.  
  
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
  
 Aynı bağlama ve güvenlik ayrıntıları, istemci yapılandırma dosyasında belirtilir.  
  
 Çağıranın kimliğini, hizmet konsol penceresinde aşağıdaki kodu kullanarak görüntülenir:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor. Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.  
  
2.  Hizmet uygulaması \service\bin çalıştırın.  
  
3.  \Client\bin istemci uygulamasını çalıştırın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Örnek ile tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1.  Hizmet makinede hizmet ikili dosyaları için bir dizin oluşturun.  
  
2.  Hizmet program dosyaları sunucuda hizmet dizinine kopyalayın. Ayrıca Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları sunucuya kopyalayın.  
  
3.  İstemci ikili dosyaları için istemci makinede bir dizin oluşturun.  
  
4.  İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
6.  Yeni sertifika adını yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesi) makinesinin tam etki alanı adıyla aynı olduğu. Ayrıca temel adresini localhost yerine tam makine adını değiştirin`.`  
  
7.  Service.cer dosya hizmeti dizininden istemci makine üzerinde istemci dizinine kopyalayın.  
  
8.  Bir istemcide çalışmasına `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.  
  
9. İstemci makinesinde Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin. Localhost sunucunun tam etki alanı adıyla değiştirerek bunu yapabilirsiniz. Ayrıca `findValue` özniteliği [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adı.  
  
10. Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
12. ImportClientCert.bat, çalıştıran sunucuda bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.  
  
13. Hizmeti makinede Service.exe bir komut isteminden çalıştırın.  
  
14. İstemci makinesinde bir komut istemi penceresinden Client.exe başlatın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
    > [!NOTE]
    >  Bu betik, bu örnek makinelerde çalışan hizmet sertifikaları bir istemci üzerinde kaldırmaz. Makinelerde sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a>Ayrıca Bkz.
