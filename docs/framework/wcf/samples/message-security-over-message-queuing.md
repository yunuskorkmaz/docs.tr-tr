---
title: "İleti Kuyruğa Alma ile İleti Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6e3d87ab31b7a0910b270e81c28985ffe9279d4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-over-message-queuing"></a>İleti Kuyruğa Alma ile İleti Güvenliği
Bu örnek, WS-güvenlik X.509v3 sertifika kimlik doğrulaması için istemci ile kullanan ve üzerinde MSMQ sunucunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulama uygulamak gösterilmiştir. Güvenlik bazen MSMQ depodaki ileti şifreli kalmasını sağlamak için daha fazla tercih ve uygulama ileti iletinin kendi kimlik doğrulaması gerçekleştirebilir.  
  
 Bu örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek. İletileri şifrelenir ve imzalanmış.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Yolun Makecert.exe ve FindPrivateKey.exe içeren klasörü içerdiğinden emin olun.  
  
2.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Örnekle tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3.  Service.exe \service\bin başlatın.  
  
4.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.  
  
2.  İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.  
  
3.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
4.  Sunucu üzerinde çalışan `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
5.  Yeni sertifika yansıtacak şekilde hizmetin service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu.  
  
6.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
7.  İstemci üzerinde çalışan `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.  Hizmeti bilgisayarın tam etki alanı adı ile aynı olması için hizmet sertifikası adını değiştirmeniz gerekir (içinde `findValue` özniteliğini `defaultCertificate` öğesinin `serviceCertificate` altında `clientCredentials`).  
  
9. Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
10. İstemci üzerinde çalışan `ImportServiceCert.bat`. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
11. Sunucu üzerinde çalışan `ImportClientCert.bat`, bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposunu alır.  
  
12. Hizmet bilgisayarda komut isteminden Service.exe başlatın.  
  
13. İstemci bilgisayarda komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
    > [!NOTE]
    >  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örnek, MSMQ yüklü ve çalışıyor olmasını gerektirir.  
  
## <a name="demonstrates"></a>Gösteriler  
 İstemci hizmeti ortak anahtarını kullanarak ileti şifreler ve kendi sertifikasını kullanarak iletiyi imzalar. Sıradan iletiyi okuma hizmet kendi güvenilir kişiler deposundaki sertifikayı istemci sertifikasıyla kimliğini doğrular. İletinin şifresini çözer ve hizmet işlemi iletiyi gönderir.  
  
 Çünkü [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti yükü MSMQ İleti gövdesi olarak yazımının, gövde MSMQ deposunda şifreli olarak kalır. Bu iletinin istenmeyen açığa iletiden güvenliğini sağlar. MSMQ kendisini onu taşıyan iletisi olup olmadığını şifrelenir farkında olmadığını unutmayın.  
  
 Örnek nasıl karşılıklı kimlik doğrulaması gösterir ileti düzeyi MSMQ ile kullanılabilir. Alışverişi-bant sertifikalardır. Hizmet ve istemci aynı anda açık ve çalışıyor olması gerekmez çünkü bu her zaman sıraya alınan uygulamayla durumdur.  
  
## <a name="description"></a>Açıklama  
 Örnek istemci ve hizmet kodu aynı olan [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) bir farkla örnek. İşlem sözleşmesi ileti İmzalanabilir ve şifrelenebilir gerekir, öneren koruma düzeyiyle işaretiyle gösterilir.  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 İstemci ve hizmet tanımlamak için gerekli belirteci kullanarak ileti güvenli olduğundan emin olmak için App.config kimlik bilgilerini içerir.  
  
 İstemci yapılandırmasında hizmetin kimliğini doğrulamak için hizmet sertifikası belirtir. LocalMachine depolama, hizmet geçerliliğini yararlanmayı güvenilir deposu olarak kullanır. Ayrıca istemci hizmeti kimlik doğrulama ileti ile bağlı istemci sertifikası belirtir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"   
                binding="netMsmqBinding"   
                bindingConfiguration="messageSecurityBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"  
                behaviorConfiguration="ClientCertificateBehavior" />  
    </client>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate"/>  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 İletiye güvenlik modunu ayarlama ve ClientCredentialType sertifikaya ayarlanır unutmayın.  
  
 Hizmet Yapılandırma hizmeti istemci kimlik doğrulaması gerçekleştirdiğinde kullanılan hizmetin kimlik bilgilerini belirtir hizmet davranışı içerir. Sunucu sertifikası konu adı belirtilen `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
          behaviorConfiguration="PurchaseOrderServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="messageSecurityBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="PurchaseOrderServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!--   
               The serviceCredentials behavior allows one to define a service certificate.  
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
               This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Örnek Yapılandırması ve güvenlik bağlamından çağıranının kimliğini edinme aşağıdaki örnek kodda gösterildiği gibi kullanarak denetleme kimlik doğrulaması gösterir:  
  
```  
    // Service class which implements the service contract.  
    // Added code to write output to the console window.  
    public class OrderProcessorService : IOrderProcessor  
    {  
        private string GetCallerIdentity()  
        {  
            // The client certificate is not mapped to a Windows identity by default.  
            // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
            // in the certificate that the client used to authenticate itself to the service.  
            return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void SubmitPurchaseOrder(PurchaseOrder po)  
        {  
            Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
  //…  
}  
```  
  
 Çalıştırdığınızda, servis kodunu istemci kimliğini görüntüler. Hizmet kodundan örnek çıktı verilmiştir:  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C  
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
## <a name="comments"></a>Açıklamalar  
  
-   İstemci sertifikası oluşturma.  
  
     Toplu iş dosyasında aşağıdaki satırı istemci sertifikası oluşturur. Belirtilen istemci adı oluşturulan sertifika konu adı kullanılır. Sertifika depolandığı `My` adresindeki depolamak `CurrentUser` depolama konumu.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme.  
  
     Toplu dosya kopyalarını aşağıdaki satırda sunucunun TrustedPeople içine istemci sertifikası sunucu ilgili güven veya no güven kararları yapabilmek depolar. Tarafından güvenilmesi için TrustedPeople deposundaki yüklü bir sertifika için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti, istemci sertifikası doğrulama modunu ayarlanmalıdır `PeerOrChainTrust` veya `PeerTrust` değeri. Önceki hizmet yapılandırma örneği bu nasıl yapılabilir bilgi edinmek için bkz: bir yapılandırma dosyası kullanarak.  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun:  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Sunucu_adı % değişkeni sunucusunun adını belirtir. Sertifika saklanır LocalMachine deposundaki. Kurulum toplu iş dosyası hizmetinin bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir. Aksi takdirde localhost için varsayılan olarak  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  ABD dışındaki kullanıyorsanız Setup.bat düzenlemelisiniz Windows dosya ve "NT AUTHORITY\NETWORK SERVICE" hesap adı, bölgesel eşdeğerleriyle değiştirme Microsoft İngilizce sürümü.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a>Ayrıca Bkz.
