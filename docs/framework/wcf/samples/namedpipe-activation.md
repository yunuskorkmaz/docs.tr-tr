---
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 46b59dab0f67c66ca364d9e880ef519386d0df94
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806389"
---
# <a name="namedpipe-activation"></a>NamedPipe Etkinleştirme
Bu örnek adları Kanallar üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanan bir hizmet barındırma gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve gerektirir [!INCLUDE[wv](../../../../includes/wv-md.md)] çalıştırmak için.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek, bir istemci konsol program (.exe) ve Windows İşlem Etkinleştirme Hizmetleri (WAS) tarafından etkinleştirilen bir çalışan işlemde barındırılan hizmet kitaplığı (.dll) oluşur. İstemci etkinliği konsol penceresinde görünür olur.  
  
 Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme) aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 İstemci eş zamanlı istekleri için verilen matematik işlemi yapar ve hizmet uygulaması hesaplar ve uygun sonucunu döndürür.  
  
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
  
 Örnek bir değiştirilmiş kullanır `netNamedPipeBinding` hiçbir güvenlik ile bağlama. Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü hizmeti için uç nokta öğesinin belirtilen `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
 Güvenli adlandırılmış kanal bağlama kullanmak istiyorsanız, istenen güvenlik ayarına sunucunun güvenlik modunu değiştirme ve svcutil.exe güncelleştirilmiş bir istemci yapılandırma dosyasını edinmek için istemcide yeniden çalıştırın.  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
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
  
 İstemcinin uç nokta bilgileri, aşağıdaki örnek kodda gösterildiği şekilde yapılandırılır.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gereklidir.  
  
2.  Gerçekleştirilen olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Ayrıca, WCF HTTP olmayan etkinleştirme bileşenleri yüklemeniz gerekir:  
  
    1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
    2.  Seçin **programlar ve Özellikler**.  
  
    3.  Tıklatın **açma veya kapatma Windows bileşenleri**.  
  
    4.  Genişletme **Microsoft .NET Framework 3.0** düğümü ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.  
  
3.  Adlandırılmış kanal etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.  
  
     Kolaylık, aşağıdaki iki adımdan örnek dizininde bulunan AddNetPipeSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.  
  
    1.  NET.pipe etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.pipe protokole bağlı olmalıdır. Bu yapılabilir ile IIS 7.0 Yönetim araç takımı yüklü appcmd.exe kullanma. (Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
         Bu komut net.pipe site bağlaması varsayılan Web sitesine ekler.  
  
    2.  Bir sitedeki tüm uygulamaları ortak net.pipe bağlama paylaşmak rağmen her uygulama net.pipe desteğini ayrı ayrı etkinleştirebilirsiniz. NET.pipe /servicemodelsamples uygulama için etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
         Bu komut her ikisini de kullanarak erişilecek /servicemodelsamples uygulamayı etkinleştirir http://localhost/servicemodelsamples ve net.tcp://localhost/servicemodelsamples.  
  
4.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Eklediğiniz net.pipe site bağlaması Bu örnek için kaldırın.  
  
     Kolaylık, örnek dizininde bulunan RemoveNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımdan uygulanır:  
  
    1.  NET.TCP yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Bu komut, tek satırlık metin girilmelidir.  
  
    2.  Net.tcp site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Bu komutu, içinde tek satırlık metin yazılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
