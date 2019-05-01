---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: de0c5683b081ecebf2168ffb5d6a2768fdd0a1fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007467"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Örnek HTTP aktarımı kullanıldığında akış senaryoları desteklemek için tasarlanan bir bağlama oluşturma işlemini gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Oluşturma ve yeni bir standart bağlama yapılandırma adımları aşağıdaki gibidir.  
  
1. Yeni standart bir bağlama oluşturma  
  
     Windows Communication Foundation (WCF) basicHttpBinding ve netTcpBinding gibi standart bağlamaları temel alınan aktarımları ve kanal yığınında belirli gereksinimleri için yapılandırın. Bu örnekte `WSStreamedHttpBinding` akış desteklemek için kanal yığın yapılandırır. Varsayılan olarak, her iki özellik, akış tarafından desteklenmediği için WS-güvenlik ve güvenilir Mesajlaşma kanalı yığına eklenmez. Yeni bağlamanın sınıfta uygulandığını `WSStreamedHttpBinding` türetilen <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Aşağıdaki bağlama öğeleri içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Sağlar sınıfını bir `CreateBindingElements()` aşağıdaki örnek kodda gösterildiği gibi ortaya çıkan bağlama yığını yapılandırmak için yöntem.  
  
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
  
2. Yapılandırma desteği eklendi  
  
     Taşıma yapılandırma aracılığıyla kullanıma sunmak için iki daha fazla sınıf örneği uygular —`WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection`. Sınıf `WSStreamedHttpBindingSection` olduğu bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `WSStreamedHttpBinding` WCF yapılandırma sistemi için. Toplu uygulama için temsilci `WSStreamedHttpBindingConfigurationElement`, öğesinden türetildiğini <xref:System.ServiceModel.Configuration.StandardBindingElement>. Sınıf `WSStreamedHttpBindingConfigurationElement` özelliklerine karşılık gelen özelliklerle sahip `WSStreamedHttpBinding`ve her yapılandırma öğesi için bir bağlama eşlemek için işlev.  
  
     İşleyici, aşağıdaki bölümde bu hizmetin yapılandırma dosyasına ekleyerek yapılandırma sistemi ile kaydedin.  
  
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
  
     İşleyici serviceModel Yapılandırma bölümünden sonra başvurulabilir.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Listelenen adımları gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Gerçekleştirdiğinizden emin olmak [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6. İstemci penceresi görüntülendiğinde, "Örnek.txt" yazın. Dizininizde "Örnek.txt Kopyala" bulmanız gerekir.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding örnek hizmeti  
 Kullanan örnek hizmet `WSStreamedHttpBinding` hizmet alt dizinindeki yer alır. Uygulamasını `OperationContract` kullanan bir `MemoryStream` döndürmeden önce gelen akıştan önce tüm verileri almak için `MemoryStream`. Örnek hizmeti Internet Information Services (IIS) tarafından barındırılır.  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding örnek istemci  
 Hizmeti kullanmaya kullanılan etkileşim kurmak için istemci `WSStreamedHttpBinding` istemci alt dizinde bulunur. Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulan bir test sertifikası olduğundan, tarayıcınızda bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görüntüler https://localhost/servicemodelsamples/service.svc. Yerinde bir test sertifikası ile çalışmak için WCF istemcisini izin vermek için güvenlik uyarıyı gizlemek için istemci için bazı ek kod eklendi. Kod ve eşlik eden sınıfı üretim sertifikaları kullanırken gerekli değildir.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
