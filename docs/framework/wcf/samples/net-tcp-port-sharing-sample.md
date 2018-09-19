---
title: Net.TCP Bağlantı Noktası Paylaşımı Örneği
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006268"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="61ab4-102">Net.TCP Bağlantı Noktası Paylaşımı Örneği</span><span class="sxs-lookup"><span data-stu-id="61ab4-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="61ab4-103">TCP/IP protokolünün bir bağlantı noktası olarak adlandırılan 16 bit bir sayı, aynı makinede çalışan birden çok ağ uygulamalarına bağlantıları ayırt etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="61ab4-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="61ab4-104">Uygulamaya bir bağlantı noktasında dinliyorsa, bu bağlantı için tüm TCP trafiği bu uygulamaya gider.</span><span class="sxs-lookup"><span data-stu-id="61ab4-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="61ab4-105">Diğer uygulamalar bu bağlantı noktasına aynı anda dinleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="61ab4-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61ab4-106">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="61ab4-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61ab4-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="61ab4-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="61ab4-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="61ab4-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61ab4-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="61ab4-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="61ab4-110">Birçok iletişim kuralı kullandıkları bir standart veya varsayılan bağlantı noktası numarası yok.</span><span class="sxs-lookup"><span data-stu-id="61ab4-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="61ab4-111">Örneğin, HTTP protokolü, genellikle 80 numaralı TCP bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="61ab4-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="61ab4-112">Internet Information Services (IIS) bağlantı noktası HTTP birden çok uygulama arasında paylaşmak için bir dinleyici sahiptir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="61ab4-113">IIS doğrudan bağlantı noktasını dinleyen ve iletileri ileti akışı içindeki bilgileri temel alarak uygun uygulamasına iletir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="61ab4-114">Bu bağlantı noktası iletileri almak için ayrılacak rekabet zorunda kalmadan aynı bağlantı noktası numarasını kullanmak birden çok HTTP uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="61ab4-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="61ab4-115">NetTcp bağlantı noktası paylaşımı benzer şekilde birden çok ağ uygulamaları tek bir bağlantı noktasını paylaşmasına izin veren bir Windows Communication Foundation (WCF) özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="61ab4-116">NetTcp bağlantı noktası paylaşma hizmeti net.tcp protokolünü kullanarak bağlantıları kabul eder ve kendi hedef adresini temel alarak iletileri iletir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="61ab4-117">NetTcp bağlantı noktası Paylaşımı hizmeti varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="61ab4-118">Bu örneği çalıştırmadan önce hizmetini el ile etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="61ab4-119">Daha fazla bilgi için [nasıl yapılır: Net.TCP bağlantı noktası paylaşım hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="61ab4-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="61ab4-120">Hizmet devre dışı bırakılırsa, sunucu uygulaması başlatılırken bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="61ab4-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="61ab4-121">Bağlantı noktası paylaşımı etkin sunucuda ayarlayarak <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği <xref:System.ServiceModel.NetTcpBinding> bağlama veya <xref:System.ServiceModel.Channels.TcpTransportBindingElement> bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="61ab4-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="61ab4-122">İstemci nasıl bağlantı noktası paylaşımı sunucuda kullanmak üzere yapılandırılmış bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="61ab4-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="61ab4-123">Bağlantı noktası paylaşımı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="61ab4-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="61ab4-124">Aşağıdaki kod, sunucuda etkinleştirme bağlantı noktası paylaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="61ab4-125">Bir örneğini başlatır `ICalculator` hizmet sabit bir bağlantı noktası ile rastgele bir URI yolu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="61ab4-126">İki hizmet de aynı bağlantı noktasını paylaşabilirsiniz olsa da, böylece NetTcp bağlantı noktası paylaşma hizmeti için doğru uygulama iletileri yönlendirebilirsiniz genel uç nokta adresleri hala benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

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

 <span data-ttu-id="61ab4-127">Bağlantı noktası ile paylaşımı, bağlantı noktası numarası üzerinde bir çakışma olmadan birden çok kez hizmetini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61ab4-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="61ab4-128">Hizmet sonuçları ile ikinci başarısız olan iki kopyasını yukarı bağlantı noktası paylaşımı devre dışı bırakmak için kodu değiştirirseniz, başlangıç bir <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="61ab4-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="61ab4-129">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="61ab4-129">Running the Sample</span></span>  
 <span data-ttu-id="61ab4-130">İletiler için bağlantı noktası paylaşımı hizmetleri doğru yönlendirilir denetlemek için test İstemcisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61ab4-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

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

 <span data-ttu-id="61ab4-131">Hizmetin her örneği, kendi benzersiz numarasını ve adresi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="61ab4-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="61ab4-132">Örneğin, service.exe çalıştırdığınızda, aşağıdaki metni görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61ab4-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="61ab4-133">Client.exe çalıştırdığınızda Burada gördüğünüz hizmet numarasını girin.</span><span class="sxs-lookup"><span data-stu-id="61ab4-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="61ab4-134">Bu örnek, istemcinin kullandığı oluşturulan adresini değiştirerek bir çapraz makine yapılandırmasında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="61ab4-135">Client.cs uç nokta adresi biçim dizesi hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="61ab4-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="61ab4-136">"Localhost" olan başvuruları sunucu makinesinin IP adresiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="61ab4-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="61ab4-137">Bu değişikliği yaptıktan sonra örnek derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61ab4-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="61ab4-138">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="61ab4-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="61ab4-139">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="61ab4-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="61ab4-140">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61ab4-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="61ab4-141">NetTcp bağlantı noktası paylaşımı daha önce giriş bölümünde açıklandığı gibi hizmet etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="61ab4-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="61ab4-142">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61ab4-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="61ab4-143">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61ab4-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="61ab4-144">Bu örneği çalıştırmak için belirli ayrıntıları daha önce çalışıyor dahil örnek bölümü.</span><span class="sxs-lookup"><span data-stu-id="61ab4-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ab4-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61ab4-145">See Also</span></span>
