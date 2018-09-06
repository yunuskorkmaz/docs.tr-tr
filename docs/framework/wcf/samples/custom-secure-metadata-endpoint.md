---
title: Özel Güvenli Meta Veri Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3ff8c5b08bb50b894511d1f9bdd28ddb2683d13b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777200"
---
# <a name="custom-secure-metadata-endpoint"></a>Özel Güvenli Meta Veri Uç Noktaları
Bu örnek, bir hizmeti meta veri olmayan exchange bağlamaları birini kullanan bir güvenli meta veri uç noktası ile uygulama ve nasıl yapılandırılacağını gösterir. [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya getirilecek istemcileri Böyle bir meta veri uç noktası meta verileri. Meta veri uç noktalarını açığa çıkarmak için kullanılabilen iki sistem tarafından sağlanan bağlamaları vardır: mexHttpBinding ve mexHttpsBinding. mexHttpBinding meta veri uç noktası güvenli olmayan bir yöntemle HTTP üzerinden kullanıma sunmak için kullanılır. mexHttpsBinding meta veri uç noktasına HTTPS üzerinden güvenli bir şekilde kullanıma sunmak için kullanılır. Bu örnek gösterir kullanarak bir güvenli meta veri uç noktası nasıl sunacağınızı öğrenin <xref:System.ServiceModel.WSHttpBinding>. Bu bağlama üzerinde güvenlik ayarlarını değiştirmek istediğiniz, ancak HTTPS kullanmak istemiyorsanız ne yapılacağını istersiniz. MexHttpsBinding kullanırsanız, meta veri uç noktası güvenli olacaktır, ancak bağlama ayarlarını değiştirmek için bir yolu yoktur.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu hizmet, iki uç nokta vardır. Uygulama uç noktasını hizmet `ICalculator` üzerinde sözleşme bir `WSHttpBinding` ile `ReliableSession` etkin ve `Message` sertifikaları kullanan güvenliği. Meta veri uç noktası da kullanan `WSHttpBinding`, aynı güvenlik ayarlarına sahip, ancak olmadan `ReliableSession`. İlgili yapılandırma şu şekildedir:  
  
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
  
 Birçok diğer örnekleri varsayılan meta veri uç noktası kullanan `mexHttpBinding`, güvenli değil. Meta veriler kullanılarak burada güvenli `WSHttpBinding` ile `Message` güvenlik. Bu meta verilerini almak meta verileri istemciler için sırada, bunlar ile eşleşen bir bağlama yapılandırılmalıdır. Bu örnek, iki istemci gösterir.  
  
 İlk istemci, meta verileri getirmek ve istemci kodu ve tasarım zamanında yapılandırma üretmek için Svcutil.exe kullanır. Hizmet meta verileri için varsayılan olmayan bağlama kullandığından, bu bağlama kullanarak hizmetinden meta verilerini alabilmesi Svcutil.exe aracını özellikle yapılandırılması gerekir.  
  
 İkinci istemcinin kullandığı `MetadataResolver` dinamik olarak bilinen bir sözleşme için meta verileri getirmek ve ardından dinamik olarak oluşturulan istemci işlemleri çağırmak için.  
  
## <a name="svcutil-client"></a>Svcutil istemci  
 Ana bilgisayar için varsayılan bağlama kullanırken, `IMetadataExchange` uç nokta, bu uç nokta adresi ile Svcutil.exe çalıştırabilirsiniz:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ve çalışır. Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir uç nokta kullanır. Bu nedenle Svcutil.exe doğru bağlama kullanması talimat gerekir. Bu yapılabilir Svcutil.exe.config dosyasını kullanarak.  
  
 Svcutil.exe.config dosya normal istemci yapılandırma dosyası gibi görünüyor. Sözleşme ve istemci uç nokta adı yalnızca olağan dışı yönleri şunlardır:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Uç nokta adı düzeni adresinin nerede meta verileri barındırır ve uç nokta sözleşme olmalıdır olmalıdır `IMetadataExchange`. Bu nedenle, Svcutil.exe aşağıdaki gibi bir komut satırı ile çalıştırıldığında:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 "http" ve sözleşme adlı uç nokta için görünüyor `IMetadataExchange` bağlama ve iletişim exchange davranışını meta veri uç noktası ile yapılandırılır. Örnek Svcutil.exe.config dosyasında geri kalanını bağlama yapılandırma ve meta veri uç sunucu yapılandırmasıyla eşleşecek şekilde davranış kimlik bilgilerini belirtir.  
  
 Sırayla Svcutil.exe Svcutil.exe.config yapılandırmayı alması için Svcutil.exe yapılandırma dosyası ile aynı dizinde olmalıdır. Sonuç olarak, yükleme konumundan Svcutil.exe Svcutil.exe.config dosyasını içeren dizine kopyalamalısınız. Ardından söz konusu dizinde, aşağıdaki komutu çalıştırın:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Başında ". \\"Svcutil.exe kopyasını bu dizinde (bir karşılık gelen Svcutil.exe.config olan) çalıştırılmasını sağlar.  
  
## <a name="metadataresolver-client"></a>MetadataResolver istemci  
 Sözleşme ve tasarım zamanında meta verilere nasıl istemci bildiği istemci dinamik olarak bağlama ve adresini kullanarak bir uygulama uç noktalarını bulabilirsiniz `MetadataResolver`. Bu örnek istemci bu, bağlama ve tarafından kullanılan kimlik bilgileri nasıl yapılandırılacağını gösteren gösterir. `MetadataResolver` oluşturarak ve yapılandırarak bir `MetadataExchangeClient`.  
  
 Svcutil.exe.config içinde görünen bağlama ve sertifika bilgileri kesin üzerinde belirtilebilir `MetadataExchangeClient`:  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 İle `mexClient` yapılandırılmış, biz ilgilendiğiniz ve kullanırız anlaşmalar numaralandırabilirsiniz `MetadataResolver` uç noktaları ile bu sözleşme listesini almak için:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Son olarak bu Uç noktalara bilgilerinden bağlamasını ve adresini başlatmak için kullanabilir miyiz bir `ChannelFactory` uygulama uç noktaları ile iletişim kurmak için Kanallar oluşturmak için kullanılır.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Kullanıyorsanız, göstermek için bu örnek istemci anahtar noktasıdır `MetadataResolver`ve özel bağlamalar veya meta veri değişimi iletişim için davranışlar belirtmelisiniz, kullanabileceğiniz bir `MetadataExchangeClient` bu özel ayarları belirtmek için.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler. Setup.bat setupCertTool.bat gelen çalıştırarak yüklü FindPrivateKey.exe aracı kullanmaktadır [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  İstemci uygulaması \MetadataResolverClient\bin veya \SvcutilClient\bin çalıştırın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Örnek ile tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
#### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1.  Sunucu üzerinde çalışan `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
2.  Sunucu üzerinde Web.config dosyasını yeni sertifika adını yansıtacak şekilde düzenleyin. Diğer bir deyişle, değişiklik `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesi makinenin tam etki alanı adı.  
  
3.  Service.cer dosya hizmeti dizininden istemci makine üzerinde istemci dizinine kopyalayın.  
  
4.  Bir istemcide çalışmasına `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.  
  
5.  App.config dosyasında `MetadataResolverClient` istemci makinede hizmetinizin yeni adresiyle eşleşecek şekilde mex uç nokta adresi değerini değiştirin. Localhost sunucunun tam etki alanı adıyla değiştirerek bunu yapabilirsiniz. Ayrıca metadataResolverClient.cs dosyasındaki "localhost" oluşumunu yeni hizmet sertifika adı (sunucusunun tam etki alanı adı) değiştirin. Aynı şeyi SvcutilClient projenizin App.config için yapın.  
  
6.  Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.  
  
7.  Bir istemcide çalışmasına `ImportServiceCert.bat`. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
8.  Sunucu üzerinde çalışan `ImportClientCert.bat`, bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.  
  
9. Hizmeti makinede Visual Studio'da hizmet projeyi oluşturun ve çalıştığını doğrulamak için bir web tarayıcısında Yardım sayfasını seçin.  
  
10. İstemci makinesinde MetadataResolverClient veya SvcutilClient VS'den çalıştırın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
    > [!NOTE]
    >  Bu betik, bu örnek makinelerde çalışan hizmet sertifikaları bir istemci üzerinde kaldırmaz. Makinelerde sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Ayrıca Bkz.
