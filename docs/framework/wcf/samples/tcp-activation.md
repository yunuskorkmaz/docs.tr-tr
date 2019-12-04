---
title: TCP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c1a2c0de5fbb666ec3b68ec3da31cc27f8234cbd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716603"
---
# <a name="tcp-activation"></a>TCP Etkinleştirme

Bu örnekte, net. TCP protokolü üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows Işlem etkinleştirme Hizmetleri 'ni (WAS) kullanan bir hizmetin barındırılması gösterilmektedir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

Örnek, bir istemci konsol programından (. exe) ve tarafından etkinleştirilen bir çalışan işlemde barındırılan bir hizmet kitaplığından (. dll) oluşur. İstemci etkinliği konsol penceresinde görünür.

Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, aşağıdaki örnek kodda gösterildiği gibi matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır:

```csharp
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

Hizmet uygulama, uygun sonucu hesaplar ve döndürür:

```csharp
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

Örnek, TCP bağlantı noktası Paylaşımı etkin ve güvenlik kapatılmış olan net. TCP bağlamasının bir türevini kullanır. Güvenli bir TCP bağlaması kullanmak istiyorsanız, sunucunun güvenlik modunu istenen ayarla değiştirin ve istemci üzerinde bir güncelleştirme istemci yapılandırma dosyası oluşturmak için Svcutil. exe dosyasını yeniden çalıştırın.

Aşağıdaki örnekte hizmetin yapılandırması gösterilmektedir:

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
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

İstemcinin uç noktası aşağıdaki örnek kodda gösterildiği gibi yapılandırılır:

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

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. IIS 7,0 'nin yüklü olduğundan emin olun. WAS etkinleştirmesi için IIS 7,0 gereklidir.

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

    Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:

    1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

    2. **Programlar ve Özellikler '** i seçin.

    3. **Windows bileşenlerini aç veya kapat**' a tıklayın.

    4. **Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.

3. TCP etkinleştirmesini destekleyecek şekilde yapılandırın.

    Kolaylık olması halinde, örnek dizinde bulunan AddNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.

    1. Net. TCP etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin bir net. TCP bağlantı noktasına bağlanması gerekir. Bu işlem, Internet Information Services 7,0 (IIS) yönetim araç takımı ile yüklenen appcmd. exe kullanılarak yapılabilir. Yönetici düzeyindeki bir komut isteminden aşağıdaki komutu çalıştırın:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > Bu komut, tek satırlık bir metin. Bu komut, TCP bağlantı noktası 808 üzerinde dinleme yapan varsayılan Web sitesine bir net. TCP site bağlamayı herhangi bir ana bilgisayar adı ile ekler.

    2. Bir sitedeki tüm uygulamalar ortak bir net. TCP bağlamasını paylaşır, ancak her uygulama net. TCP desteğini tek tek etkinleştirebilir. /Servicemodelsamples uygulaması için net. TCP 'yi etkinleştirmek üzere yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırın:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin. Bu komut,/servicemodelsamples uygulamasına hem `http://localhost/servicemodelsamples` hem de `net.tcp://localhost/servicemodelsamples`kullanılarak erişilmesini sağlar.

4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

5. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

    Bu örnek için eklemiş olduğunuz net. TCP site bağlamasını kaldırın.

    Kolaylık olması halinde, örnek dizinde bulunan RemoveNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.

    1. Yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Bu komut tek satırlık bir metin olarak girilmelidir.

    2. Yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Bu komutun tek satırlık bir metin olarak yazılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
