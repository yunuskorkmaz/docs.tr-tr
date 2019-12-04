---
title: Özel Güvenli Meta Veri Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 92fa468caf331fadcd6cab0ab57b34858053c1b5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715444"
---
# <a name="custom-secure-metadata-endpoint"></a>Özel Güvenli Meta Veri Uç Noktaları
Bu örnek, meta veri olmayan Exchange bağlamalarından birini kullanan güvenli meta veri uç noktası olan bir hizmetin nasıl uygulanacağını ve bu meta veri uç noktasından meta verileri getirmek için [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya istemcilerinin nasıl yapılandırılacağını gösterir. Meta veri uç noktalarını açığa çıkarmak için kullanılabilir iki sistem tarafından sağlanan bağlama vardır: mexHttpBinding ve mexHttpsBinding. mexHttpBinding, bir meta veri uç noktasının HTTP üzerinden güvenli olmayan bir şekilde kullanıma sunulması için kullanılır. mexHttpsBinding, HTTPS üzerinden bir meta veri uç noktası oluşturmak için güvenli bir şekilde kullanılır. Bu örnek, <xref:System.ServiceModel.WSHttpBinding>kullanarak güvenli bir meta veri uç noktasının nasıl açığa alınacağını gösterir. Bağlamasındaki güvenlik ayarlarını değiştirmek istediğinizde, ancak HTTPS kullanmak istemiyorsanız bunu yapmak isteyebilirsiniz. MexHttpsBinding kullanırsanız, meta veri uç noktanız güvende olur, ancak bağlama ayarlarını değiştirmek mümkün değildir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmette iki uç nokta bulunur. Uygulama uç noktası, `ReliableSession` etkin bir `WSHttpBinding` ve sertifikaları kullanarak `Message` güvenliği `ICalculator` sözleşmeye hizmet verir. Meta veri uç noktası aynı güvenlik ayarlarıyla ancak `ReliableSession`olmadan `WSHttpBinding`de kullanır. İlgili yapılandırma aşağıda verilmiştir:  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 Diğer örneklerin çoğunda, meta veri uç noktası, güvenli olmayan varsayılan `mexHttpBinding`kullanır. Burada, `Message` güvenliği ile `WSHttpBinding` kullanılarak meta veriler güvende hale getirilir. Meta veri istemcilerinin bu meta verileri alabilmesi için, eşleşen bir bağlama ile yapılandırılması gerekir. Bu örnek, bu iki istemciyi gösterir.  
  
 İlk istemci, meta verileri getirmek ve tasarım zamanında istemci kodu ve yapılandırması oluşturmak için Svcutil. exe ' yi kullanır. Hizmet meta veriler için varsayılan olmayan bir bağlama kullandığından, bu bağlamayı kullanarak hizmetten meta verileri alabilmek için Svcutil. exe aracının özel olarak yapılandırılması gerekir.  
  
 İkinci istemci, bilinen bir sözleşmenin meta verilerini dinamik olarak getirmek için `MetadataResolver` kullanır ve sonra dinamik olarak oluşturulan istemcideki işlemleri çağırır.  
  
## <a name="svcutil-client"></a>Svcutil istemcisi  
 `IMetadataExchange` uç noktanızı barındırmak için varsayılan bağlamayı kullanırken, Svcutil. exe ' yi bu uç noktanın adresiyle çalıştırabilirsiniz:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ve işe yarar. Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir uç nokta kullanır. Bu nedenle, doğru bağlamayı kullanması için Svcutil. exe ' ye bir talimat verilmelidir. Bu, bir Svcutil. exe. config dosyası kullanılarak yapılabilir.  
  
 Svcutil. exe. config dosyası normal bir istemci yapılandırma dosyası gibi görünür. İstemci uç noktası adı ve sözleşmesinin tek olağandışı yönleri şunlardır:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Uç nokta adı, meta verilerin barındırıldığı adresin düzeninin adı ve uç nokta sözleşmesinin `IMetadataExchange`olması gerekir. Bu nedenle, Svcutil. exe, aşağıdaki gibi bir komut satırı ile çalıştırıldığında:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 iletişim değişiminin bağlama ve davranışını meta veri uç noktası ile yapılandırmak için, "http" adlı bitiş noktasını ve sözleşme `IMetadataExchange` arar. Örnekteki Svcutil. exe. config dosyasının geri kalanı, bağlama yapılandırma ve davranış kimlik bilgilerini sunucunun meta veri uç noktası yapılandırmasıyla eşleşecek şekilde belirtir.  
  
 Svcutil. exe, Svcutil. exe. config dosyasındaki yapılandırmayı çekmek için Svcutil. exe ' nin yapılandırma dosyası ile aynı dizinde olması gerekir. Sonuç olarak, Svcutil. exe ' yi kendi install konumundan, Svcutil. exe. config dosyasını içeren dizine kopyalamanız gerekir. Ardından, bu dizinden aşağıdaki komutu çalıştırın:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Önde gelen ".\\", bu dizindeki Svcutil. exe kopyasının (karşılık gelen bir Svcutil. exe. config dosyasına sahip olan) çalıştırılmasını sağlar.  
  
## <a name="metadataresolver-client"></a>MetadataResolver istemcisi  
 İstemci sözleşmeyi bilir ve tasarım zamanında meta verilerle nasıl iletişim kuracağınızı, istemci, `MetadataResolver`kullanarak uygulama uç noktalarının bağlamasını ve adresini dinamik olarak bulabilir. Bu örnek istemci, bir `MetadataExchangeClient`oluşturarak ve yapılandırarak `MetadataResolver` tarafından kullanılan bağlama ve kimlik bilgilerinin nasıl yapılandırılacağını gösteren bunu gösterir.  
  
 Svcutil. exe. config dosyasında görüntülenen aynı bağlama ve sertifika bilgileri `MetadataExchangeClient`imperatively belirtilebilir:  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 `mexClient`, ilgilendiğiniz sözleşmeleri numaralandırabiliriz ve bu sözleşmeleri içeren uç noktaların bir listesini getirmek için `MetadataResolver` kullanabilirsiniz:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Son olarak, uygulama uç noktalarıyla iletişim kurmak üzere kanal oluşturmak için kullanılan bir `ChannelFactory` bağlama ve adresini başlatmak için bu uç noktalardan gelen bilgileri kullanabiliriz.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Bu örnek istemcinin anahtar noktası, `MetadataResolver`kullanıyorsanız ve meta veri değişimi iletişimi için özel bağlamalar veya davranışlar belirtmeniz gerekiyorsa, bu özel ayarları belirtmek için bir `MetadataExchangeClient` kullanabilirsiniz.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar. Setup. bat dosyasının, [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)setupCertTool. bat dosyasını çalıştırarak yüklenen FindPrivateKey. exe aracını kullandığını unutmayın.  
  
2. İstemci uygulamasını \MetadataResolverClient\bin veya \SvcutilClient\bin. adresinden çalıştırın İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
3. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
#### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Sunucusunda `setup.bat service`çalıştırın. `setup.bat` `service` bağımsız değişkeniyle çalıştırmak, makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
2. Sunucusunda, Web. config dosyasını yeni sertifika adını yansıtacak şekilde düzenleyin. Diğer bir deyişle, [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki `findValue` özniteliğini makinenin tam etki alanı adına değiştirin.  
  
3. Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.  
  
4. İstemcisinde `setup.bat client`' yi çalıştırın. `setup.bat` `client` bağımsız değişkeniyle çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
5. İstemci makinesindeki `MetadataResolverClient` App. config dosyasında, MEX uç noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz. Ayrıca, metadataResolverClient.cs dosyasındaki "localhost" öğesinin oluşumunu yeni hizmet sertifikası adına (sunucunun tam etki alanı adı) değiştirin. SvcutilClient projesinin App. config ' i için aynı şeyi yapın.  
  
6. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
7. İstemcisinde `ImportServiceCert.bat`' yi çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
8. Sunucusunda `ImportClientCert.bat`çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
9. Hizmet makinesinde, Visual Studio 'da hizmet projesini derleyin ve çalıştığını doğrulamak için bir Web tarayıcısında yardım sayfasını seçin.  
  
10. İstemci makinesinde, ve adresinden MetadataResolverClient veya SvcutilClient ' ı çalıştırın.  
  
    1. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Makinelerde sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
