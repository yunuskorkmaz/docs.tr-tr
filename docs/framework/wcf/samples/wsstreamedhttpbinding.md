---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6259640bae2b4be4fac73883df8945bf1db7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Örnek, HTTP taşıma kullanıldığında akış senaryoları desteklemek üzere tasarlanmış bir bağlama oluşturun gösterilmiştir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Oluşturun ve yeni bir standart bağlama yapılandırmak için adımlar aşağıdaki gibidir.  
  
1.  Yeni bir standart bağlama oluşturma  
  
     Standart bağlamaları [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gibi basicHttpBinding ve netTcpBinding arka plandaki aktarım ve kanal yığını belirli gereksinimleri için yapılandırın. Bu örnekte `WSStreamedHttpBinding` akış desteklemek için kanal yığın yapılandırır. Varsayılan olarak, her iki özellik akış tarafından desteklenmediğinden WS güvenliği ve güvenilir Mesajlaşma kanalı yığına eklenmez. Yeni bağlamanın sınıfında uygulanır `WSStreamedHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Aşağıdaki bağlama öğeleri içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Bu sınıf sağladığı bir `CreateBindingElements()` yöntemi aşağıdaki örnek kodda gösterildiği gibi sonuçta elde edilen bağlama yığını yapılandırmak için.  
  
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
  
2.  Yapılandırma desteği ekleme  
  
     Taşıma yapılandırma yoluyla kullanıma sunmak için iki daha fazla sınıf örneği uygulayan —`WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection`. Sınıf `WSStreamedHttpBindingSection` olan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `WSStreamedHttpBinding` için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma sistemi. Uygulama toplu temsilci için `WSStreamedHttpBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>. Sınıf `WSStreamedHttpBindingConfigurationElement` özelliklerine karşılık gelen özelliklere sahip `WSStreamedHttpBinding`ve her yapılandırma öğesi için bir bağlama eşlemek için işlevleri.  
  
     İşleyici, aşağıdaki bölümde hizmetin yapılandırma dosyasına ekleyerek yapılandırma sistemi ile kaydedin.  
  
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
  
     İşleyici serviceModel yapılandırması bölümünden sonra başvurulabilir.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Listelenen adımları gerçekleştirildiğinden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Makineler arası yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  İstemci penceresi görüntülendiğinde, "Örnek.txt" yazın. Dizininizde "Örnek.txt Kopyala" bulmanız gerekir.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding örnek hizmeti  
 Kullanan örnek hizmet `WSStreamedHttpBinding` hizmet alt dizinindeki bulunur. Uygulaması `OperationContract` kullanan bir `MemoryStream` döndürmeden önce gelen akıştan ilk tüm verileri almak için `MemoryStream`. Örnek hizmeti Internet Information Services (IIS) tarafından barındırılır.  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding örnek istemcisi  
 Hizmetini kullanarak ile kullanılan etkileşim kurmak için istemci `WSStreamedHttpBinding` istemci alt dizininde bulunur. Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir HTTPS adresi https://localhost/servicemodelsamples/service.svc gibi tarayıcınızda erişmeyi denediğinde bir güvenlik uyarısı görüntüler. İzin vermek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, yerinde bir test sertifikası ile çalışmak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklendi. Kod ve eşlik eden sınıfı üretim sertifikaları kullanırken gerekli değildir.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.
