---
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144441"
---
# <a name="message-security-over-message-queuing"></a>İleti Kuyruğa Alma ile İleti Güvenliği
Bu örnek, istemci için X.509v3 sertifika kimlik doğrulaması ile WS-Security kullanan bir uygulamanın nasıl uygulanacağını ve sunucunun MSMQ üzerinden X.509v3 sertifikasını kullanarak sunucu kimlik doğrulamasını nasıl gerektirdiğini gösterir. İleti güvenliği, MSMQ deposundaki iletilerin şifrelenmiş kalmasını ve uygulamanın iletinin kendi kimlik doğrulamasını gerçekleştirebilmesini sağlamak için bazen daha fazla tercih edilir.

 Bu [örnek, Transacted MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır. İletiler şifrelenir ve imzalanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler. Sıra yoksa, hizmet bir tane oluşturur. Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz. Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012'de Sunucu Yöneticisi'ni açın.

    2. **Özellikler** sekmesini genişletin.

    3. Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yolun Makecert.exe ve FindPrivateKey.exe içeren klasörü içerdiğinden emin olun.

2. Setup.bat'ı örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.

    > [!NOTE]
    > Örneği tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3. \service\bin'den Service.exe'yi başlatın.  
  
4. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için  
  
1. Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını servis bilgisayarına kopyalayın.  
  
2. İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.  
  
3. İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
4. Sunucuda, çalıştırın. `setup.bat service` Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`  
  
5. Bilgisayarın tam nitelikli alan adı ile aynı olan yeni sertifika adını `findValue` [ \<(hizmetSertifikası>'ndeki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde hizmetin service.exe.config'ini edin.  
  
6. Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
7. İstemci üzerinde, çalıştırın. `setup.bat client` Bağımsız değişkenle birlikte çalışmak, `setup.bat` client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`  
  
8. İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin. Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yapın.  Ayrıca, hizmet bilgisayarının tam nitelikli alan adı ile aynı olacak şekilde hizmetin sertifika `findValue` adını değiştirmeniz `serviceCertificate` gerekir `clientCredentials`(alt `defaultCertificate` öğedeki öznitelikte).  
  
9. Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.  
  
10. İstemci üzerinde, çalıştırın. `ImportServiceCert.bat` Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
11. Sunucuda, çalıştır `ImportClientCert.bat`, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.  
  
12. Servis bilgisayarında Service.exe komut isteminden başlatın.  
  
13. İstemci bilgisayarında, komut isteminden Client.exe'yi başlatın. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Gereksinimler
 Bu örnek, MSMQ'nun yüklü ve çalışıyor olması gerekir.

## <a name="demonstrates"></a>Gösteriler
 İstemci, hizmetin ortak anahtarını kullanarak iletiyi şifreler ve iletiyi kendi sertifikasını kullanarak imzalar. Kuyruktaki iletiyi okuyan hizmet, istemci sertifikasını güvenilir kişiler deposunda sertifikayla doğrular. Daha sonra iletinin şifresini çözer ve iletiyi hizmet işlemine gönderir.

 Windows Communication Foundation (WCF) iletisi MSMQ iletisinin gövdesinde bir yük olarak taşındığından, gövde MSMQ deposunda şifrelenmiş olarak kalır. Bu, iletinin istenmeyen şekilde açıklanmasını sağlar. MSMQ'nun taşıdığı iletinin şifrelenip şifrelenmediğinin farkında olmadığını unutmayın.

 Örnek, ileti düzeyinde karşılıklı kimlik doğrulamanın MSMQ ile nasıl kullanılabileceğini gösterir. Sertifikalar bant dışı değiştirilir. Hizmet ve istemci aynı anda çalışır durumda olması gerekmez, çünkü bu her zaman sıralı uygulama ile durumdur.

## <a name="description"></a>Açıklama
 Örnek istemci ve hizmet kodu, tek bir farkla [İşlenmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğiyle aynıdır. İşlem sözleşmesi koruma düzeyiyle ekolarak eklenmiştir ve bu da iletinin imzalanması ve şifrelemesi gerektiğini önerir.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 İletinin hizmeti ve istemciyi tanımlamak için gerekli belirteç kullanılarak güvenli olduğundan emin olmak için App.config kimlik bilgileri içerir.

 İstemci yapılandırması, hizmetin kimliğini doğrulamak için hizmet sertifikasını belirtir. Hizmetin geçerliliğine güvenmek için LocalMachine mağazasını güvenilir mağaza olarak kullanır. Ayrıca, istemcinin hizmet kimlik doğrulaması için iletiile birlikte eklenen istemci sertifikasını da belirtir.

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

 Güvenlik modunun İleti olarak ayarladığını ve ClientCredentialType'ın Sertifika olarak ayarladığını unutmayın.

 Hizmet yapılandırması, istemci hizmeti doğrularken kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışı içerir. Sunucu sertifikası özne adı `findValue` [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)öznitelik belirtilir.

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

 Örnek, yapılandırmayı kullanarak kimlik doğrulamayı denetlemeyi ve aşağıdaki örnek kodda gösterildiği gibi, arayanın kimliğinin güvenlik bağlamından nasıl alınabildiğini gösterir:

```csharp
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

 Çalıştırıldığında, servis kodu istemci kimliğini görüntüler. Hizmet kodundan örnek çıktı aşağıda veda edilir:

```console
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

## <a name="comments"></a>Yorumlar

- İstemci sertifikasıoluşturma.

     Toplu iş dosyasındaki aşağıdaki satır istemci sertifikasını oluşturur. Belirtilen istemci adı oluşturulan sertifikanın özne adında kullanılır. Sertifika mağaza da `My` `CurrentUser` depolanır.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- İstemci sertifikasını sunucunun güvenilir sertifika deposuna yükleme.

     Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını sunucunun Güvenilir Kişiler deposuna kopyalar, böylece sunucu ilgili güven veya güven siz kararları verebilir. Trusted People deposunda yüklü bir sertifikanın Bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilen `PeerOrChainTrust` bir `PeerTrust` sertifika için istemci sertifikası doğrulama modunun ayarlanması veya değeri nin ayarlanması gerekir. Bunun bir yapılandırma dosyası kullanarak nasıl yapılabileceğini öğrenmek için önceki hizmet yapılandırma örneğine bakın.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Sunucu sertifikası oluşturma.

     Setup.bat toplu iş dosyasındaki aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     %SERVER_NAME değişkeni sunucu adını belirtir. Sertifika LocalMachine mağazasında depolanır. Kurulum toplu dosyası bir hizmet bağımsız değişkeni (örneğin) `setup.bat service`ile çalıştırılırsa %SERVER_NAME%bilgisayarın tam nitelikli etki alanı adını içerir. Aksi takdirde varsayılan olarak localhost

- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.

     Aşağıdaki satır, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Microsoft Windows'un ABD İngilizce olmayan bir sürümünü kullanıyorsanız, Setup.bat dosyasını düzenlemelisiniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerinizle değiştirmelisiniz.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
