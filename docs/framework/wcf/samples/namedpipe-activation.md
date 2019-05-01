---
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 3e6084e8334eddc16b115cc1199819c6ab637666
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051851"
---
# <a name="namedpipe-activation"></a>NamedPipe Etkinleştirme

Bu örnek adları Kanallar üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanan bir hizmet barındırma gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve gerektiren [!INCLUDE[wv](../../../../includes/wv-md.md)] çalıştırılacak.

> [!NOTE]
> Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.

> [!IMPORTANT]
> Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Örnek Ayrıntıları

Örnek bir istemci konsol program (.exe) ve Windows İşlem Etkinleştirme Hizmetleri (WAS) tarafından etkin bir çalışan işleminin barındırılan hizmet kitaplığı (.dll) oluşur. İstemci etkinliği konsol penceresinde görünür.

Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme), aşağıdaki örnek kodda gösterildiği gibi.

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

İstemci bir verilen matematik işlemi için zaman uyumlu istekleri yapar ve hizmet uygulaması hesaplar ve uygun sonucu döndürür.

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

Örnek bir değiştirilen kullanır `netNamedPipeBinding` ile güvenlik bağlama. İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi. Bağlama türü için hizmet uç noktası öğenin belirtilen `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.

Güvenli bir adlandırılmış kanal bağlama kullanmak istiyorsanız, istenen güvenlik sunucunun güvenlik modunu değiştirin ve svcutil.exe güncelleştirilmiş bir istemci yapılandırma dosyası almak için istemcide yeniden çalıştırın.

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

Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gereklidir.

2. Gerçekleştirdiğiniz olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:

    1. Gelen **Başlat** menüsünde seçin **Denetim Masası**.

    2. Seçin **programlar ve Özellikler**.

    3. Tıklayın **Aç veya kapat Windows bileşenleri**.

    4. Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.

3. Adlandırılmış kanal etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.

    Bir kolaylık olarak örnek dizinde yer AddNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.

    1. NET.pipe etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.pipe protokole bağlı olmalıdır. Bu yapılabilir, IIS 7.0 Yönetim araç takımıyla yüklenmeyen appcmd.exe kullanarak. (Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Tek metin satırı komutudur.

        Bu komut, varsayılan Web sitesine net.pipe site bağlaması ekler.

    2. Bir sitedeki tüm uygulamaları genel net.pipe bağlama paylaşsa da her uygulama net.pipe destek ayrı ayrı etkinleştirebilirsiniz. /Servicemodelsamples uygulamanın NET.pipe etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > Tek metin satırı komutudur.

        Bu komut, her ikisi de kullanılarak erişilecektir /servicemodelsamples uygulama etkinleştirir `http://localhost/servicemodelsamples` ve `net.tcp://localhost/servicemodelsamples`.

4. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Eklediğiniz net.pipe site bağlaması için bu örnek kaldırın.

    Bir kolaylık olarak örnek dizinde yer RemoveNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır:

    1. NET.TCP, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin girilmelidir.

    2. Net.tcp site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin yazılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve Kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
