---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: aad89924b371d9d5032f32f29aac83fae445f253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959774"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Örnek, HTTP taşıması kullanıldığında akış senaryolarını destekleyecek şekilde tasarlanan bir bağlamanın nasıl oluşturulacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Yeni bir standart bağlama oluşturma ve yapılandırma adımları aşağıdaki gibidir.  
  
1. Yeni bir standart bağlama oluştur  
  
     BasicHttpBinding ve netTcpBinding gibi Windows Communication Foundation (WCF) içindeki standart bağlamalar, belirli gereksinimler için temel taşımaları ve kanal yığınını yapılandırır. Bu örnekte, `WSStreamedHttpBinding` kanal yığınını akışı destekleyecek şekilde yapılandırır. Varsayılan olarak, WS-Security ve güvenilir mesajlaşma, her iki özellik de akış tarafından desteklenmediğinden kanal yığınına eklenmez. Yeni bağlama, öğesinden `WSStreamedHttpBinding` <xref:System.ServiceModel.Channels.Binding>türetilen sınıfta uygulanır. <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, Aşağıdaki bağlama öğelerini <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>içerir:,, ve. `WSStreamedHttpBinding` Sınıfı, aşağıdaki örnek `CreateBindingElements()` kodda gösterildiği gibi, elde edilen bağlama yığınını yapılandırmak için bir yöntem sağlar.  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2. Yapılandırma desteği ekle  
  
     Aktarımı yapılandırma yoluyla göstermek için örnek iki sınıf daha uygular —`WSStreamedHttpBindingConfigurationElement` ve. `WSStreamedHttpBindingSection` Sınıfı `WSStreamedHttpBindingSection` , WCF yapılandırma <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> sistemine `WSStreamedHttpBinding` yönelik bir ' dir. Uygulamanın toplu işlemi, ' den `WSStreamedHttpBindingConfigurationElement` <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen için Temsilcili. Sınıfı `WSStreamedHttpBindingConfigurationElement` ,`WSStreamedHttpBinding`özelliklerine karşılık gelen özelliklere ve her yapılandırma öğesini bir bağlamaya eşlemek için işlevlere sahiptir.  
  
     Hizmetin yapılandırma dosyasına aşağıdaki bölümü ekleyerek işleyiciyi yapılandırma sistemine kaydedin.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     İşleyiciye daha sonra serviceModel yapılandırma bölümünden başvurulabilir.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)listelenen adımları gerçekleştirdiğinizden emin olun.  
  
3. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.  
  
4. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
5. Örneği bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
6. İstemci penceresi görüntülendiğinde "Sample. txt" yazın. Dizininizde bir "örnek. txt kopyası" bulmanız gerekir.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding örnek hizmeti  
 Tarafından kullanılan `WSStreamedHttpBinding` örnek hizmet, hizmet alt dizininde bulunur. Uygulamasının uygulamasını `OperationContract` döndürmeden önce `MemoryStream` gelen akıştan tüm verileri almak için bir kullanır. `MemoryStream` Örnek hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding örnek Istemcisi  
 Kullanılarak `WSStreamedHttpBinding` hizmetle etkileşim kurmak için kullanılan istemci, istemci alt dizininde bulunur. Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızda https://localhost/servicemodelsamples/service.svc bir https adresine erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir. WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir. Üretim sertifikaları kullanılırken kod ve eşlik eden sınıf gerekli değildir.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
