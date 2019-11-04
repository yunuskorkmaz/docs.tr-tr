---
title: Geçici Kuyruğa Alınmış İletişim
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 4a3c67de2966bb9b7379a191039f6405b4007c78
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424684"
---
# <a name="volatile-queued-communication"></a>Geçici Kuyruğa Alınmış İletişim

Bu örnek, Message Queuing (MSMQ) taşıması üzerinden geçici sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir. Bu örnek <xref:System.ServiceModel.NetMsmqBinding>kullanır. Bu durumda hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendine barındırılan bir konsol uygulamasıdır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.

Herhangi bir bilgi sahibi olmadan bir ileti gönderdiğinizde, MSMQ yalnızca iletiyi teslim etmek için en iyi çaba, MSMQ 'nun iletinin teslim edilmesini sağlayan veya teslim edileyemediği durumlarda iletinin teslim edilemez olduğunu bilmenizi sağlar.

Belirli senaryolarda, bir kuyruk üzerinden hiçbir zaman daha önemli olan bir geçici ileti göndermek isteyebilirsiniz. Geçici iletiler, kuyruk yöneticisi kilitlenmelerinden devam etmez. Bu nedenle, kuyruk yöneticisi kilitlenirse, geçici iletileri daha fazla saklamak için kullanılan işlem dışı sıra, iletiler diskte depolanmadığı için ileti kendileri değildir.

> [!NOTE]
> MSMQ kullanarak bir işlemin kapsamı içinde hiçbir ölçü olmadan geçici iletiler gönderemezsiniz. Ayrıca geçici iletiler göndermek için işlemsel olmayan bir sıra oluşturmanız gerekir.

Bu örnekteki hizmet sözleşmesi, kuyruğa alma için en uygun olan tek yönlü hizmetleri tanımlayan `IStockTicker`.

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

Hizmet işlemi, aşağıdaki örnek kodda gösterildiği gibi hisse senedi bandı sembolünü ve fiyatını görüntüler:

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte hizmet, sıranın varlığını denetlemek ve gerekirse oluşturmak için kod içerir. Sıra adı yapılandırma dosyasından okundu. Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete yönelik proxy oluşturmak için kullanılır.

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

MSMQ kuyruğu adı, yapılandırma dosyasının appSettings bölümünde belirtilir. Hizmetin uç noktası, yapılandırma dosyasının System. serviceModel bölümünde tanımlanır ve `netMsmqBinding` bağlamayı belirtir.

> [!NOTE]
> Sıra adı, <xref:System.Messaging>kullanarak bir sıra oluştururken, yerel makine ve ters eğik çizgi ayırıcılar için bir nokta (.) kullanır. Windows Communication Foundation (WCF) uç noktası adresi bir net. MSMQ: Scheme belirtir, yerel makine için "localhost" kullanır ve yolunda eğik çizgiler kullanır.

Yapılandırmada Ayrıca, bir veya daha fazla ileti de belirtilir.

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

Örnek, işlem olmayan bir sıra kullanarak sıraya alınmış iletiler gönderdiğinden, işlem temelli iletiler kuyruğa gönderilemez.

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın. Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun. İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

<xref:System.ServiceModel.NetMsmqBinding>varsayılan olarak, taşıma güvenliği etkinleştirilmiştir. MSMQ aktarım güvenliği, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>için iki uygun özellik vardır `.` varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır. Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ için, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir. Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örneği bir çalışma grubuna katılmış veya Active Directory Tümleştirmesi olmadan bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse veya Active Directory Tümleştirmesi yüklü değilse, aşağıdaki örnek yapılandırma kodunda gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın:

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.

    > [!NOTE]
    > `security mode` `None` ayarlanması, `Message` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>ve `None`güvenliğini ayarlamaya eşdeğerdir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
