---
title: TCP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 0a65e5ca20a11f50133efc90e6da923280a30f46
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846558"
---
# <a name="tcp-activation"></a>TCP Etkinleştirme
Bu örnek net.tcp protokolü üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanan bir hizmet barındırma gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 Örnek bir istemci konsol program (.exe) ve WAS tarafından etkinleştirilen bir çalışan işleminin barındırılan hizmet kitaplığı (.dll) oluşur. İstemci etkinliği konsol penceresinde görünür.  
  
 Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme), aşağıdaki örnek kodda gösterildiği gibi:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür:  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 Örnek bir TCP bağlantı noktası paylaşımı etkin ve devre dışı güvenlikle bağlama net.tcp çeşidini kullanır. Güvenli bir TCP bağlaması kullanmak istiyorsanız, sunucunun güvenlik modu istediğiniz ayara değiştirin ve Svcutil.exe bir güncelleştirme istemci yapılandırma dosyası oluşturmak için istemcide yeniden çalıştırın.  
  
 Aşağıdaki örnek, hizmet yapılandırmasını gösterir:  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Aşağıdaki örnek kodda gösterildiği gibi istemcinin uç nokta yapılandırılır:  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
</system.serviceModel>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gereklidir.  
  
2.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:  
  
    1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
    2.  Seçin **programlar ve Özellikler**.  
  
    3.  Tıklayın **Aç veya kapat Windows bileşenleri**.  
  
    4.  Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.  
  
3.  WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırın.  
  
     Bir kolaylık olarak örnek dizinde yer AddNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.  
  
    1.  NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır. Bu yapılabilir, Internet Information Services 7.0 (IIS) Yönetimi araç takımıyla yüklenmeyen Appcmd.exe kullanarak. Bir düzey yönetici komut isteminden aşağıdaki komutu çalıştırın:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  Tek metin satırı komutudur. Bu komut, varsayılan Web sitesine 808 tüm ana bilgisayar adına sahip numaralı TCP bağlantı noktasını dinleyen bir net.tcp site bağlaması ekler.  
  
    2.  Bir sitedeki tüm uygulamaları genel net.tcp bağlama paylaşsa da her uygulama net.tcp destek ayrı ayrı etkinleştirebilirsiniz. NET.TCP /servicemodelsamples uygulamanın etkinleştirmek için bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırın:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        > Tek metin satırı komutudur. Bu komut, her ikisi de kullanılarak erişilecektir /servicemodelsamples uygulama etkinleştirir `http://localhost/servicemodelsamples` ve `net.tcp://localhost/servicemodelsamples`.  
  
4.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Eklediğiniz net.tcp site bağlaması için bu örnek kaldırın.  
  
     Bir kolaylık olarak örnek dizinde yer RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.  
  
    1.  NET.TCP, bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Bu komut, tek satırlık bir metin girilmelidir.  
  
    2.  Net.tcp site bağlaması, bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırarak kaldırın:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Bu komut, tek satırlık bir metin yazılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
