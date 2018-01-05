---
title: "Özel Güvenli Meta Veri Uç Noktaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cad98ab0df372b19efcf102cce3f80e3f7b0632f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-secure-metadata-endpoint"></a>Özel Güvenli Meta Veri Uç Noktaları
Bu örnek bir hizmeti meta veri olmayan exchange bağlamaları birini kullanan bir güvenli meta veri uç noktası ile uygulama ve nasıl yapılandırılacağı gösterilmektedir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya fetch istemcileri Bu tür bir meta veri uç noktasından meta veriler. İki sistem tarafından sağlanan bağlamalar meta veri uç noktalarını gösterme için kullanılabilir: mexHttpBinding ve mexHttpsBinding. mexHttpBinding meta veri uç noktasına HTTP üzerinden güvenli olmayan bir biçimde göstermek için kullanılır. mexHttpsBinding meta veri uç noktasına HTTPS üzerinden güvenli bir şekilde kullanıma sunmak için kullanılır. Bu örnek, güvenli meta veri kullanan uç noktasını kullanıma sunmak verilmektedir <xref:System.ServiceModel.WSHttpBinding>. Bağlama üzerinde güvenlik ayarlarını değiştirmek istediğiniz ancak HTTPS kullanmak istemediğiniz durumlarda yapmak istiyor. MexHttpsBinding kullanırsanız, meta veri uç noktası güvenli olacaktır, ancak bağlama ayarlarını değiştirmek için bir yolu yoktur.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu örnek hizmetinde iki uç nokta vardır. Uygulama uç noktasını hizmet `ICalculator` üzerinde sözleşme bir `WSHttpBinding` ile `ReliableSession` etkin ve `Message` sertifikaları kullanan güvenliği. Meta veri uç noktasının de kullanır `WSHttpBinding`, aynı güvenlik ayarlarına sahip ancak hiçbir `ReliableSession`. İlgili yapılandırma şöyledir:  
  
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
  
 Birçok diğer örnekleri varsayılan meta veri uç noktasının kullanır `mexHttpBinding`, güvenli değil. Meta verileri kullanarak burada güvenliği `WSHttpBinding` ile `Message` güvenlik. Meta veri istemcilerin bu meta verilerini almak sırayla bunlar eşleşen bir bağlama ile yapılandırılmalıdır. Bu örnek iki tür istemcileri gösterir.  
  
 İlk istemci Svcutil.exe meta veri Getir ve istemci kodu ve tasarım zamanında yapılandırma oluşturmak üzere kullanır. Hizmet için meta veriler varsayılan olmayan bağlama kullandığından, böylece bu bağlama işlemini kullanma hizmetinden meta verileri alabilir Svcutil.exe aracı özellikle yapılandırılması gerekir.  
  
 İkinci istemcinin kullandığı `MetadataResolver` dinamik olarak bilinen bir sözleşme meta verilerini getirmek ve dinamik olarak üretilen istemci işlemlerini çağırma.  
  
## <a name="svcutil-client"></a>Svcutil istemci  
 Ana bilgisayar için varsayılan bağlama kullanırken, `IMetadataExchange` uç noktası, o uç noktası adresi ile Svcutil.exe çalıştırabilirsiniz:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ve bu çalışır. Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir uç kullanır. Bu nedenle Svcutil.exe doğru bağlama kullanmak için talimat gerekir. Bu yapılabilir bir Svcutil.exe.config dosyası kullanarak.  
  
 Svcutil.exe.config dosya normal istemci yapılandırma dosyası gibi görünüyor. Sözleşme ve istemci uç nokta adı yalnızca olağan dışı yönleri şunlardır:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Uç nokta adı burada meta verileri barındırılan ve uç nokta sözleşme olmalıdır adres düzeni adı olmalıdır `IMetadataExchange`. Bu nedenle, Svcutil.exe aşağıdaki gibi komut satırı ile çalıştırıldığında:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 "http" ve sözleşme adlı uç noktası için görünüyor `IMetadataExchange` meta veri uç noktası ile bağlama ve iletişim exchange davranışını yapılandırmak için. Örnek Svcutil.exe.config dosyasında kalan bağlama yapılandırması ve meta veri uç noktasının sunucunun yapılandırma ile eşleşmesi için davranış kimlik bilgilerini belirtir.  
  
 Sırayla Svcutil.exe Svcutil.exe.config yapılandırmasında alması için Svcutil.exe yapılandırma dosyası ile aynı dizinde olmalıdır. Sonuç olarak, yükleme konumundan Svcutil.exe Svcutil.exe.config dosyasını içeren dizine kopyalamalısınız. Ardından bu dizininden aşağıdaki komutu çalıştırın:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Başında ". \\"Svcutil.exe kopyasını bu dizindeki (bir karşılık gelen Svcutil.exe.config olan) çalıştığını sağlar.  
  
## <a name="metadataresolver-client"></a>MetadataResolver istemci  
 İstemci sözleşme ve tasarım zamanında meta verilere nasıl biliyorsa, istemci dinamik olarak bağlama ve uygulama uç noktalarını kullanarak adresini bulabilirsiniz `MetadataResolver`. Bu örnek istemcisi bu, bağlama ve tarafından kullanılan kimlik bilgilerini nasıl yapılandırılacağını gösteren gösterir `MetadataResolver` oluşturma ve yapılandırma tarafından bir `MetadataExchangeClient`.  
  
 Svcutil.exe.config içinde görünen aynı bağlama ve sertifika bilgileri imperatively üzerinde belirtilebilir `MetadataExchangeClient`:  
  
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
  
 İle `mexClient` yapılandırılmış, biz biz ilgilendiğiniz ve kullanmak sözleşmeleri numaralandırabilir `MetadataResolver` bu sözleşmelerle bitiş noktaları listesini getirmek için:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Biz bağlama ve adresini başlatmak için bu uç bilgilerinden son kullanabilirsiniz bir `ChannelFactory` uygulama uç noktaları ile iletişim kanalı oluşturmak için kullanılır.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Kullanıyorsanız anahtar Bu örnek istemcisi, göstermek için noktasıdır `MetadataResolver`ve özel bağlamaları veya meta veri exchange iletişimi için davranışlar belirtmelisiniz, kullanabileceğiniz bir `MetadataExchangeClient` bu özel ayarları belirtmek için.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler. Setup.bat gelen setupCertTool.bat çalıştırarak yüklü FindPrivateKey.exe aracı kullandığına dikkat edin [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  İstemci uygulaması \MetadataResolverClient\bin veya \SvcutilClient\bin çalıştırın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Sertifikaları örnekle tamamladığınızda Cleanup.bat çalıştırarak kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
#### <a name="to-run-the-sample-across-machines"></a>Makine genelinde örneği çalıştırmak için  
  
1.  Sunucu üzerinde çalışan `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
2.  Sunucu üzerinde Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin. Diğer bir deyişle, değişiklik `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) makinenin tam etki alanı adı öğesi.  
  
3.  Service.cer dosya hizmeti dizininden istemci makinesinde istemci dizinine kopyalayın.  
  
4.  İstemci üzerinde çalışan `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
5.  App.config dosyasında `MetadataResolverClient` istemci makinede hizmetinizin yeni adresi eşleşecek şekilde mex uç noktası adresi değerini değiştirin. Bunun için localhost sunucunun tam etki alanı adı ile değiştirerek. Ayrıca metadataResolverClient.cs dosyasındaki "localhost" oluşumunun yeni hizmet sertifikası adı (sunucunun tam etki alanı adı) değiştirin. Aynı şey SvcutilClient proje App.config için yapın.  
  
6.  Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
7.  İstemci üzerinde çalışan `ImportServiceCert.bat`. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
8.  Sunucu üzerinde çalışan `ImportClientCert.bat`, bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposunu alır.  
  
9. Hizmeti makinede Visual Studio'da hizmet projeyi oluşturun ve çalıştığını doğrulamak için bir web tarayıcısında Yardım sayfasını seçin.  
  
10. İstemci makinesinde MetadataResolverClient veya SvcutilClient VS'den çalıştırın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
    > [!NOTE]
    >  Bu komut dosyası, bu örnek makine genelinde çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makine genelinde sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Ayrıca Bkz.
