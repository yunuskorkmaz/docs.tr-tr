---
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 56775842a742d0c6b07c6870bfce524ed1d275fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556108"
---
# <a name="namedpipe-activation"></a>NamedPipe Etkinleştirme

Bu örnekte, ad kanalları üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows Işlem etkinleştirme hizmeti (WAS) kullanan bir hizmetin barındırılması gösterilmektedir. Bu örnek [Başlarken](getting-started-sample.md) ' e dayalıdır ve Windows Vista 'nın çalışmasını gerektirir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Örnek Ayrıntılar

Örnek, bir istemci konsol programından (. exe) ve Windows Işlem etkinleştirme Hizmetleri (WAS) tarafından etkinleştirilen bir çalışan işleminde barındırılan bir hizmet kitaplığından (. dll) oluşur. İstemci etkinliği konsol penceresinde görünür.

Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `ICalculator` Aşağıdaki örnek kodda gösterildiği gibi matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.

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

İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet uygulamasını hesaplar ve ilgili sonucu döndürür.

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

Örnek, bir `netNamedPipeBinding` güvenlik olmadan değiştirilmiş bağlamayı kullanır. Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir. Hizmetin bağlama türü, `binding` Aşağıdaki örnek yapılandırmada gösterildiği gibi Endpoint öğesinin özniteliğinde belirtilir.

Güvenli adlandırılmış kanal bağlamayı kullanmak istiyorsanız, sunucunun güvenlik modunu istediğiniz güvenlik ayarıyla değiştirin ve güncelleştirilmiş bir istemci yapılandırma dosyası almak için istemcide svcutil.exe yeniden çalıştırın.

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
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
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

İstemcinin uç nokta bilgileri aşağıdaki örnek kodda gösterildiği gibi yapılandırılır.

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
            Each property is configured with the default value. -->

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

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

    Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:

    1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

    2. **Programlar ve Özellikler '** i seçin.

    3. **Windows bileşenlerini aç veya kapat**' a tıklayın.

    4. **Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.

3. Windows Işlem etkinleştirme hizmeti 'ni (WAS) adlandırılmış kanal etkinleştirmesini destekleyecek şekilde yapılandırın.

    Kolaylık olması halinde, örnek dizinde bulunan AddNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.

    1. Net. pipe etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin net. pipe protokolüne bağlanması gerekir. Bu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd.exe kullanılarak yapılabilir. Yükseltilmiş (yönetici) komut isteminden aşağıdaki komutu çalıştırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

        Bu komut, varsayılan Web sitesine bir net. pipe site bağlaması ekler.

    2. Bir sitedeki tüm uygulamalar ortak bir net. pipe bağlamasını paylaşır, ancak her uygulama net. pipe desteğini tek tek etkinleştirebilir. /Servicemodelsamples uygulamasının net. pipe ' ı etkinleştirmek için, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

        Bu komut, hem hem de kullanılarak/servicemodelsamples uygulamasına erişilmesini sağlar `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` .

4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

5. Bu örnek için eklemiş olduğunuz net. pipe site bağlamasını kaldırın.

    Kolaylık olması için aşağıdaki iki adım örnek dizinde yer alan RemoveNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında uygulanır:

    1. Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Bu komut tek satırlık bir metin olarak girilmelidir.

    2. Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Bu komutun tek satırlık bir metin olarak yazılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))
