---
title: Özel Güvenli Meta Veri Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183843"
---
# <a name="custom-secure-metadata-endpoint"></a>Özel Güvenli Meta Veri Uç Noktaları
Bu örnek, meta olmayan veri değişimi bağlayıcılarından birini kullanan güvenli bir meta veri bitiş noktasına sahip bir hizmetin nasıl uygulanacağını ve [serviceModel Meta data utility aracını (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya istemcilerin meta verileri böyle bir meta veri bitiş noktasından nasıl getireceğini gösterir. Meta veri uç noktalarını ortaya çıkarmak için sistem tarafından sağlanan iki bağlama vardır: mexHttpBinding ve mexHttpsBinding. mexHttpBinding güvenli olmayan bir şekilde HTTP üzerinde bir meta veri bitiş noktası ortaya çıkarmak için kullanılır. mexHttpsBinding güvenli bir şekilde HTTPS üzerinde bir meta veri bitiş noktası ortaya çıkarmak için kullanılır. Bu örnek, güvenli bir meta veri bitiş <xref:System.ServiceModel.WSHttpBinding>noktasının nasıl ortaya çıkarılabildiğini göstermektedir. Bağlamadaki güvenlik ayarlarını değiştirmek istediğinizde bunu yapmak istersiniz, ancak HTTPS'yi kullanmak istemezsiniz. mexHttpsBinding kullanırsanız meta veri bitiş noktanız güvenli olacaktır, ancak bağlama ayarlarını değiştirmenin bir yolu yoktur.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmetin iki uç noktası vardır. Uygulama bitiş noktası, `ICalculator` sertifikaları `WSHttpBinding` kullanarak `ReliableSession` etkin `Message` leştirilmiş ve güvenlikli bir sözleşmeye hizmet eder. Meta veri bitiş noktası `WSHttpBinding`da kullanır , aynı `ReliableSession`güvenlik ayarları ile ama hiçbir . İşte ilgili yapılandırma:  
  
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
  
 Diğer örneklerin çoğunda, meta veri bitiş noktası `mexHttpBinding`varsayılan kullanır , güvenli değildir. Burada meta veriler güvenlik `WSHttpBinding` kullanılarak `Message` güvenlidir. Meta veri istemcilerinin bu meta verileri alabilmesi için eşleşen bir bağlamayla yapılandırılmak gerekir. Bu örnek, bu tür iki istemciyi göstermektedir.  
  
 İlk istemci, meta verileri almak ve tasarım zamanında istemci kodu ve yapılandırma oluşturmak için Svcutil.exe kullanır. Hizmet meta veriler için varsayılan olmayan bir bağlama kullandığından, Svcutil.exe aracının bu bağlamayı kullanarak hizmetten meta verileri alabilmesi için özel olarak yapılandırılması gerekir.  
  
 İkinci istemci, `MetadataResolver` bilinen bir sözleşme için meta verileri dinamik olarak getirmek ve ardından dinamik olarak oluşturulan istemci deki işlemleri çağırmak için kullanır.  
  
## <a name="svcutil-client"></a>Svcutil istemcisi  
 Bitiş noktanızı `IMetadataExchange` barındırmak için varsayılan bağlamayı kullanırken, Svcutil.exe'yi bu bitiş noktasının adresiyle çalıştırabilirsiniz:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ve işe yarıyor. Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir bitiş noktası kullanır. Yani Svcutil.exe doğru bağlama kullanmak için talimat olmalıdır. Bu bir Svcutil.exe.config dosyası kullanılarak yapılabilir.  
  
 Svcutil.exe.config dosyası normal bir istemci yapılandırma dosyası gibi görünüyor. Sadece olağandışı yönleri istemci bitiş noktası adı ve sözleşme vardır:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Bitiş noktası adı, meta verilerin barındırıldığı adres düzeninin adı olmalı ve bitiş `IMetadataExchange`noktası sözleşmesi olmalıdır. Böylece, Svcutil.exe aşağıdaki gibi bir komut satırı ile çalıştırıldığında:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 meta veri bitiş noktası ile iletişim `IMetadataExchange` alışverişinin bağlayıcıve davranışını yapılandırmak için "http" adlı bitiş noktasını ve sözleşmeyi arar. Örnekteki Svcutil.exe.config dosyasının geri kalanı, sunucunun meta veri bitiş noktası yapılandırmasına uyacak bağlama yapılandırmasını ve davranış kimlik bilgilerini belirtir.  
  
 Svcutil.exe'nin yapılandırmayı alabilmesi için Svcutil.exe,Svcutil.exe'nin yapılandırma dosyasıyla aynı dizinde olması gerekir. Sonuç olarak, Svcutil.exe'yi yükleme konumundan Svcutil.exe.config dosyasını içeren dizine kopyalamanız gerekir. Daha sonra bu dizinden aşağıdaki komutu çalıştırın:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Önde gelen ". \\" bu dizindeki Svcutil.exe'nin (karşılık gelen Svcutil.exe.config' e sahip olan) kopyasının çalıştırılmasını sağlar.  
  
## <a name="metadataresolver-client"></a>MetadataResolver istemcisi  
 İstemci sözleşmeyi biliyorsa ve tasarım zamanında meta verilerle nasıl konuşulabileceğini biliyorsa, istemci uygulama bitiş noktalarının bağlamasını ve adresini dinamik olarak '' `MetadataResolver`kullanarak . Bu örnek istemci, `MetadataResolver` bir `MetadataExchangeClient`.  
  
 Svcutil.exe.config'de yer alan aynı bağlama ve sertifika bilgileri `MetadataExchangeClient`zorunlu olarak şu şekilde belirtilebilir:  
  
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
  
 `mexClient` Yapılandırıldığında, ilgilendiğimiz sözleşmeleri sayısalolarak listeleyebilir ve bu `MetadataResolver` sözleşmelerle ilgili uç noktaların listesini almak için kullanabiliriz:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Son olarak, uygulama bitiş noktalarıyla iletişim kurmak için kanallar `ChannelFactory` oluşturmak için kullanılan bir kanalın bağlama ve adresini başlatmayı sağlamak için bu uç noktalardaki bilgileri kullanabiliriz.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Bu örnek istemcinin temel noktası, kullanıyorsanız `MetadataResolver`ve meta veri değişimi iletişimi için özel bağlamalar veya davranışlar belirtmeniz gerekiyorsa, bu özel ayarları belirtmek için bir `MetadataExchangeClient` kullanabilirsiniz göstermektir.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Numuneyi aynı makinede çalıştırmak için  
  
1. Setup.bat'ı örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler. Setup.bat [Windows İletişim Temel Örnekleri için Bir Kerelik Kurulum Yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)setupCertTool.bat çalıştırarak yüklenir FindPrivateKey.exe aracı, kullanır unutmayın.  
  
2. İstemci uygulamasını \MetadataResolverClient\bin veya \SvcutilClient\bin'den çalıştırın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
3. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
4. Örneği bitirdikten sonra Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
#### <a name="to-run-the-sample-across-machines"></a>Numuneyi makineler arasında çalıştırmak için  
  
1. Sunucuda, çalıştırın. `setup.bat service` Bağımsız değişkenle birlikte çalışmak, `setup.bat` makinenin tam nitelikli alan adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`  
  
2. Sunucuda, yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemeyi edin. Diğer bir deyişle, `findValue` [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki özniteliği makinenin tam nitelikli etki alanı adı ile değiştirin.  
  
3. Service.cer dosyasını servis dizininden istemci makinesindeki istemci dizinine kopyalayın.  
  
4. İstemci üzerinde, çalıştırın. `setup.bat client` Bağımsız değişkenle birlikte çalışmak, `setup.bat` Client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`  
  
5. İstemci makinesinin `MetadataResolverClient` App.config dosyasında, mex bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yaparsınız. Ayrıca, metadataResolverClient.cs dosyasındaki "localhost" oluşumunu yeni hizmet sertifikası adı (sunucunun tam nitelikli etki alanı adı) olarak değiştirin. Aynı şeyi SvcutilClient projesinin App.config'i için de yapın.  
  
6. Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.  
  
7. İstemci üzerinde, çalıştırın. `ImportServiceCert.bat` Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
8. Sunucuda, çalıştır `ImportClientCert.bat`, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.  
  
9. Servis makinesinde, Visual Studio'da servis projesini oluşturun ve çalıştığını doğrulamak için bir web tarayıcısındayardım sayfasını seçin.  
  
10. İstemci makinesinde, VS'den MetadataResolverClient'ı veya SvcutilClient'ı çalıştırın.  
  
    1. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu komut dosyası, bu örneği makineler arasında çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Makineler arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
