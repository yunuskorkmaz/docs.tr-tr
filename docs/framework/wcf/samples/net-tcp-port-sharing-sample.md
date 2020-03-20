---
title: Net.TCP Bağlantı Noktası Paylaşımı Örneği
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: ac90a50c6fe06a643881da2889fdea308404508e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144298"
---
# <a name="nettcp-port-sharing-sample"></a>Net.TCP Bağlantı Noktası Paylaşımı Örneği
TCP/IP protokolü, aynı makinede çalışan birden çok ağ uygulamasına olan bağlantıları ayırt etmek için bağlantı noktası adı verilen 16 bitlik bir sayı kullanır. Bir uygulama bir bağlantı noktasında dinliyorsa, o bağlantı noktası için tüm TCP trafiği bu uygulamaya gider. Diğer uygulamalar aynı anda bu bağlantı noktasını dinleyemez.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Birçok protokolün kullandıkları standart veya varsayılan bağlantı noktası numarası vardır. Örneğin, HTTP protokolü genellikle TCP bağlantı noktası 80 kullanır. Internet Information Services (IIS) birden çok HTTP uygulamaları arasında bir bağlantı noktası paylaşmak için bir dinleyici vardır. IIS doğrudan bağlantı noktasında dinler ve ileti akışı içindeki bilgilere dayanarak iletileri uygun uygulamaya iletir. Bu, birden çok HTTP uygulamasının ileti almak için bağlantı noktasını ayırmak için rekabet etmek zorunda kalmadan aynı bağlantı noktası numarasını kullanmasına olanak tanır.  
  
 NetTcp Bağlantı Noktası Paylaşımı, benzer şekilde birden çok ağ uygulamasının tek bir bağlantı noktasını paylaşmasına olanak tanıyan bir Windows Communication Foundation (WCF) özelliğidir. NetTcp Bağlantı Noktası Paylaşım Hizmeti, net.tcp protokolünü kullanarak bağlantıları kabul eder ve hedef adreslerine göre iletiler ileder.  
  
 NetTcp Bağlantı Noktası Paylaşım Hizmeti varsayılan olarak etkinleştirilemez. Bu örneği çalıştırmadan önce hizmeti el ile etkinleştirmeniz gerekir. Daha fazla bilgi için [bkz: Net.TCP Bağlantı Noktası Paylaşım Hizmetini etkinleştirin.](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md) Hizmet devre dışı bırakılırsa, sunucu uygulaması başlatıldığında bir özel durum atılır.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Bağlantı noktası paylaşımı, bağlama veya <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> <xref:System.ServiceModel.Channels.TcpTransportBindingElement> bağlama öğesinin özelliğini ayarlayarak sunucuda etkinleştirilir. <xref:System.ServiceModel.NetTcpBinding> İstemci, bağlantı noktası paylaşımının sunucuda kullanmak üzere nasıl yapılandırıldığını bilmesi gerekmez.  
  
## <a name="enabling-port-sharing"></a>Bağlantı Noktası Paylaşımını Etkinleştirme  
 Aşağıdaki kod, sunucuda bağlantı noktası paylaşımını etkinleştirmeyi gösterir. Rasgele uri yolu `ICalculator` olan sabit bir bağlantı noktasında hizmetin bir örneğini başlatır. İki hizmet aynı bağlantı noktasını paylaşabilse de, NetTcp Bağlantı Noktası Paylaşım Hizmeti'nin iletileri doğru uygulamaya yönlendirebilmeleri için genel uç nokta adreslerinin yine de benzersiz olması gerekir.  

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

 Bağlantı noktası paylaşımı etkinken, bağlantı noktası numarası üzerinde çakışma olmadan hizmeti birden çok kez çalıştırabilirsiniz. Kodu bağlantı noktası paylaşımını devre dışı kılabilir şekilde değiştirirseniz, hizmetin iki <xref:System.ServiceModel.AddressAlreadyInUseException>kopyasını başlatmak, ikinci başarısız lıkla sonuçlanır.  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Örneği Çalıştırma  
 İletilerin bağlantı noktasını paylaşan hizmetlere doğru şekilde yönlendirildiğini denetlemek için test istemcisini kullanabilirsiniz.  

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

 Hizmetin her örneği benzersiz numarasını ve adresini yazdırır. Örneğin, service.exe'yi çalıştırdığınızda aşağıdaki metni görebilirsiniz.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Client.exe'yi çalıştırdığınızda burada gördüğünüz servis numarasını girin.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu örnek, istemcinin kullandığı oluşturulan adresi değiştirerek makineler arası bir yapılandırmada çalıştırılabilir. Client.cs, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktası adres biçimi dizesini değiştirin. "Localhost" için yapılan başvuruları sunucu makinesinin IP adresiyle değiştirin. Bu değişikliği yaptıktan sonra örneği yeniden derlemeniz gerekir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Giriş bölümünde daha önce açıklandığı gibi NetTcp Bağlantı Noktası Paylaşım Hizmeti'ni etkinleştirin.  
  
4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
5. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin. Bu örneği çalıştırmak için belirli ayrıntılar daha önce Örneği Çalıştırma bölümüne dahil edilmiştir.  
