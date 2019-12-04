---
title: Net.TCP Bağlantı Noktası Paylaşımı Örneği
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: e7a814dcdc027980f70ec90e384f3ec2f74b364d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714712"
---
# <a name="nettcp-port-sharing-sample"></a>Net.TCP Bağlantı Noktası Paylaşımı Örneği
TCP/IP protokolü, aynı makinede çalışan birden çok ağ uygulamasına olan bağlantıları ayırt etmek için bağlantı noktası olarak adlandırılan 16 bitlik bir sayı kullanır. Bir uygulama bir bağlantı noktasında dinliyorsa, bu bağlantı noktası için tüm TCP trafiği bu uygulamaya gider. Diğer uygulamalar bu bağlantı noktasını aynı anda dinleyemiyor.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Birçok protokolün, kullandıkları standart veya varsayılan bağlantı noktası numarası vardır. Örneğin, HTTP protokolü genellikle 80 numaralı TCP bağlantı noktasını kullanır. Internet Information Services (IIS), birden çok HTTP uygulaması arasında bir bağlantı noktası paylaşmak için bir dinleyicisine sahiptir. IIS, bağlantı noktasını doğrudan dinler ve iletileri ileti akışı içindeki bilgilere göre uygun uygulamaya iletir. Bu, birden çok HTTP uygulamasının, ileti almak için bağlantı noktasını ayırmak üzere rekabet etmenize gerek kalmadan aynı bağlantı noktası numarasını kullanmasına izin verir.  
  
 NetTcp bağlantı noktası Paylaşımı, benzer şekilde birden çok ağ uygulamasının tek bir bağlantı noktasını paylaşmasına izin veren bir Windows Communication Foundation (WCF) özelliğidir. NetTcp bağlantı noktası paylaşım hizmeti, net. tcp protokolünü kullanarak bağlantıları kabul eder ve iletileri hedef adreslerine göre iletir.  
  
 NetTcp bağlantı noktası Paylaşımı hizmeti varsayılan olarak etkinleştirilmemiştir. Bu örneği çalıştırmadan önce, hizmeti el ile etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: net. TCP bağlantı noktası paylaşım hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Hizmet devre dışıysa, sunucu uygulaması başlatıldığında bir özel durum oluşturulur.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Bağlantı noktası Paylaşımı, <xref:System.ServiceModel.NetTcpBinding> bağlamasının veya <xref:System.ServiceModel.Channels.TcpTransportBindingElement> bağlama öğesinin <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğini ayarlayarak sunucuda etkindir. İstemci, bağlantı noktası paylaşımının sunucuda kullanmak üzere nasıl yapılandırıldığını öğrenmek zorunda değildir.  
  
## <a name="enabling-port-sharing"></a>Bağlantı noktası paylaşımını etkinleştirme  
 Aşağıdaki kod, sunucuda bağlantı noktası paylaşımını etkinleştirmeyi gösterir. Rastgele bir URI yolu olan sabit bir bağlantı noktasında `ICalculator` hizmetinin bir örneğini başlatır. İki hizmet aynı bağlantı noktasını paylaşsa da, NetTcp bağlantı noktası paylaşım hizmeti 'nin iletileri doğru uygulamaya yönlendirebilmesi için genel uç nokta adresleri yine de benzersiz olmalıdır.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Bağlantı noktası Paylaşımı etkinken, bağlantı noktası numarası üzerinden çakışmadan hizmeti birden çok kez çalıştırabilirsiniz. Bağlantı noktası paylaşımını devre dışı bırakmak için kodu değiştirirseniz, hizmetin iki kopyasının başlatılması ikinci bir <xref:System.ServiceModel.AddressAlreadyInUseException>ile başarısız olur.  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Örnek çalıştırma  
 Sınama istemcisini, iletilerin bağlantı noktasını paylaşan hizmetlere doğru yönlendirildiğini denetlemek için kullanabilirsiniz.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 Hizmetin her örneği, benzersiz sayısını ve adresini yazdırır. Örneğin, Service. exe ' yi çalıştırdığınızda aşağıdaki metni görebilirsiniz.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Client. exe ' yi çalıştırdığınızda burada gördüğünüz hizmet numarasını girin.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu örnek, istemcinin kullandığı oluşturulan adresi değiştirerek, bir çapraz makine yapılandırmasında çalıştırılabilir. Client.cs içinde, uç nokta adresi biçim dizesini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" ile ilgili tüm başvuruları sunucu makinesinin IP adresiyle değiştirin. Bu değişikliği yaptıktan sonra örneği yeniden derlemeniz gerekir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Daha önce giriş bölümünde açıklanan NetTcp bağlantı noktası paylaşım hizmetini etkinleştirin.  
  
4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
5. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin. Bu örneği çalıştırmaya yönelik belirli ayrıntılar, daha önce örnek bölümünde çalışan bölümüne eklenmiştir.  
