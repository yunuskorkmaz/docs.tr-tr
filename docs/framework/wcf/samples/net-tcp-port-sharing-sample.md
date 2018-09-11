---
title: Net.TCP Bağlantı Noktası Paylaşımı Örneği
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44263881"
---
# <a name="nettcp-port-sharing-sample"></a>Net.TCP Bağlantı Noktası Paylaşımı Örneği
TCP/IP protokolünün bir bağlantı noktası olarak adlandırılan 16 bit bir sayı, aynı makinede çalışan birden çok ağ uygulamalarına bağlantıları ayırt etmek için kullanır. Uygulamaya bir bağlantı noktasında dinliyorsa, bu bağlantı için tüm TCP trafiği bu uygulamaya gider. Diğer uygulamalar bu bağlantı noktasına aynı anda dinleyemiyor.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Birçok iletişim kuralı kullandıkları bir standart veya varsayılan bağlantı noktası numarası yok. Örneğin, HTTP protokolü, genellikle 80 numaralı TCP bağlantı noktasını kullanır. Internet Information Services (IIS) bağlantı noktası HTTP birden çok uygulama arasında paylaşmak için bir dinleyici sahiptir. IIS doğrudan bağlantı noktasını dinleyen ve iletileri ileti akışı içindeki bilgileri temel alarak uygun uygulamasına iletir. Bu bağlantı noktası iletileri almak için ayrılacak rekabet zorunda kalmadan aynı bağlantı noktası numarasını kullanmak birden çok HTTP uygulamaları sağlar.  
  
 NetTcp bağlantı noktası paylaşımı benzer şekilde birden çok ağ uygulamaları tek bir bağlantı noktasını paylaşmasına izin veren bir Windows Communication Foundation (WCF) özelliğidir. NetTcp bağlantı noktası paylaşma hizmeti net.tcp protokolünü kullanarak bağlantıları kabul eder ve kendi hedef adresini temel alarak iletileri iletir.  
  
 NetTcp bağlantı noktası Paylaşımı hizmeti varsayılan olarak etkin değildir. Bu örneği çalıştırmadan önce hizmetini el ile etkinleştirmeniz gerekir. Daha fazla bilgi için [nasıl yapılır: Net.TCP bağlantı noktası paylaşım hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Hizmet devre dışı bırakılırsa, sunucu uygulaması başlatılırken bir özel durum oluşturulur.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Bağlantı noktası paylaşımı etkin sunucuda ayarlayarak <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği <xref:System.ServiceModel.NetTcpBinding> bağlama veya <xref:System.ServiceModel.Channels.TcpTransportBindingElement> bağlama öğesi. İstemci nasıl bağlantı noktası paylaşımı sunucuda kullanmak üzere yapılandırılmış bilmeniz gerekmez.  
  
## <a name="enabling-port-sharing"></a>Bağlantı noktası paylaşımı etkinleştirme  
 Aşağıdaki kod, sunucuda etkinleştirme bağlantı noktası paylaşımı gösterir. Bir örneğini başlatır `ICalculator` hizmet sabit bir bağlantı noktası ile rastgele bir URI yolu. İki hizmet de aynı bağlantı noktasını paylaşabilirsiniz olsa da, böylece NetTcp bağlantı noktası paylaşma hizmeti için doğru uygulama iletileri yönlendirebilirsiniz genel uç nokta adresleri hala benzersiz olması gerekir.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Bağlantı noktası ile paylaşımı, bağlantı noktası numarası üzerinde bir çakışma olmadan birden çok kez hizmetini çalıştırabilirsiniz. Hizmet sonuçları ile ikinci başarısız olan iki kopyasını yukarı bağlantı noktası paylaşımı devre dışı bırakmak için kodu değiştirirseniz, başlangıç bir <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 İletiler için bağlantı noktası paylaşımı hizmetleri doğru yönlendirilir denetlemek için test İstemcisi'ni kullanabilirsiniz.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
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

 Hizmetin her örneği, kendi benzersiz numarasını ve adresi yazdırır. Örneğin, service.exe çalıştırdığınızda, aşağıdaki metni görebilirsiniz.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Client.exe çalıştırdığınızda Burada gördüğünüz hizmet numarasını girin.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu örnek, istemcinin kullandığı oluşturulan adresini değiştirerek bir çapraz makine yapılandırmasında çalıştırılabilir. Client.cs uç nokta adresi biçim dizesi hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" olan başvuruları sunucu makinesinin IP adresiyle değiştirin. Bu değişikliği yaptıktan sonra örnek derlemeniz gerekir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  NetTcp bağlantı noktası paylaşımı daha önce giriş bölümünde açıklandığı gibi hizmet etkinleştirin.  
  
4.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Bu örneği çalıştırmak için belirli ayrıntıları daha önce çalışıyor dahil örnek bölümü.  
  
## <a name="see-also"></a>Ayrıca Bkz.
