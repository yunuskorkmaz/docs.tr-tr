---
title: "Net.TCP Bağlantı Noktası Paylaşımı Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dea3a0f0d69662021c78b0f1d57ad0ba8c11fcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="44ea6-102">Net.TCP Bağlantı Noktası Paylaşımı Örneği</span><span class="sxs-lookup"><span data-stu-id="44ea6-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="44ea6-103">TCP/IP protokolü, aynı makinede çalışan birden çok ağ uygulamalarına bağlantıları ayırt etmek için bir bağlantı noktası adı verilen bir 16 bit numara kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ea6-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="44ea6-104">Uygulamaya bir bağlantı noktasında dinleme, tüm TCP trafiği, bağlantı noktası için bu uygulamaya gider.</span><span class="sxs-lookup"><span data-stu-id="44ea6-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="44ea6-105">Diğer uygulamalar aynı zamanda bu bağlantı noktasında dinleme yapamaz.</span><span class="sxs-lookup"><span data-stu-id="44ea6-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44ea6-106">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44ea6-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="44ea6-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="44ea6-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="44ea6-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44ea6-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="44ea6-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="44ea6-110">Birçok iletişim kuralı kullandıkları bir standart ya da varsayılan bağlantı noktası numarası yok.</span><span class="sxs-lookup"><span data-stu-id="44ea6-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="44ea6-111">Örneğin, HTTP protokolünü genellikle 80 numaralı TCP bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ea6-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="44ea6-112">Internet Information Services (IIS) birden çok HTTP uygulamalar arasında bir bağlantı noktası paylaşmak için bir dinleyici sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="44ea6-113">IIS doğrudan bağlantı noktasını dinler ve ileti akışı içindeki bilgileri temel alarak uygun uygulama iletileri iletir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="44ea6-114">Bu ileti almak için bağlantı noktası ayırmak için rekabet gerek kalmadan aynı bağlantı noktası numarasını kullanmak üzere birden çok HTTP uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ea6-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="44ea6-115">NetTcp bağlantı noktası paylaşımı bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]benzer şekilde tek bir bağlantı noktası paylaşmak birden çok ağ uygulamaları sağlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="44ea6-115">NetTcp Port Sharing is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="44ea6-116">NetTcp bağlantı noktası Paylaşımı hizmeti net.tcp protokolünü kullanarak bağlantıları kabul eder ve bunların hedef adresine göre iletileri iletir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="44ea6-117">NetTcp bağlantı noktası Paylaşımı hizmeti varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="44ea6-118">Bu örneği çalıştırmadan önce hizmetini el ile etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="44ea6-119">Daha fazla bilgi için bkz: [nasıl yapılır: Net.TCP bağlantı noktası Paylaşımı hizmeti etkinleştirmek](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="44ea6-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="44ea6-120">Hizmet devre dışıysa sunucu uygulaması başlatıldığında bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44ea6-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="44ea6-121">Bağlantı noktası paylaşımı etkin sunucuda ayarlayarak <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği <xref:System.ServiceModel.NetTcpBinding> bağlama veya <xref:System.ServiceModel.Channels.TcpTransportBindingElement> bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="44ea6-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="44ea6-122">İstemcinin nasıl bağlantı noktası paylaşımı sunucuda kullanmak için yapılandırıldı bilmeniz yok.</span><span class="sxs-lookup"><span data-stu-id="44ea6-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="44ea6-123">Bağlantı noktası paylaşımı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="44ea6-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="44ea6-124">Aşağıdaki kod, etkinleştirme bağlantı noktası sunucuda paylaşma gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="44ea6-125">Bir örneğini başlatır `ICalculator` rastgele bir URI yolu ile sabit bir bağlantı noktasına hizmet.</span><span class="sxs-lookup"><span data-stu-id="44ea6-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="44ea6-126">İki Hizmetleri aynı bağlantı noktasını paylaşabilirsiniz olsa bile, böylece NetTcp bağlantı noktası Paylaşımı hizmeti için doğru uygulama iletileri yönlendirmek genel bitiş noktası adreslerini hala benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  
  
```  
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
  
 <span data-ttu-id="44ea6-127">Etkin bağlantı noktası paylaşımı ile bağlantı noktası numarası üzerinden bir çakışma olmadan birden çok kez hizmet çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ea6-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="44ea6-128">Bağlantı noktası paylaşımı devre dışı bırakmak için kodu değiştirirseniz, ikinci başarısız olan hizmet sonuçlarında iki kopyasını başlatmadan bir <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="44ea6-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="44ea6-129">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="44ea6-129">Running the Sample</span></span>  
 <span data-ttu-id="44ea6-130">İletiler için bağlantı noktası paylaşımı hizmetleri doğru yönlendirilir denetlemek için test İstemcisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ea6-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  
  
```  
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
  
 <span data-ttu-id="44ea6-131">Her hizmet örneği, kendi benzersiz numarasını ve adresi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="44ea6-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="44ea6-132">Örneğin, service.exe çalıştırdığınızda, aşağıdaki metni görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ea6-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="44ea6-133">Client.exe çalıştırdığınızda, burada gördüğünüz hizmet numarasını girin.</span><span class="sxs-lookup"><span data-stu-id="44ea6-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="44ea6-134">Bu örnek, istemcinin kullandığı oluşturulan adresi değiştirerek makineler arası yapılandırmada çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="44ea6-135">Client.cs içinde yeni adresi hizmetinizin eşleştirmek için uç nokta adresi biçimi dizesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44ea6-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="44ea6-136">"Localhost" yönelik tüm başvuruları Sunucu makinesi IP adresiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44ea6-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="44ea6-137">Bu değişikliği yaptıktan sonra örnek derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44ea6-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="44ea6-138">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="44ea6-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="44ea6-139">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="44ea6-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="44ea6-140">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44ea6-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="44ea6-141">NetTcp bağlantı noktası paylaşımı daha önce giriş bölümünde açıklandığı gibi hizmetini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="44ea6-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="44ea6-142">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44ea6-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="44ea6-143">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44ea6-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="44ea6-144">Bu örneği çalıştırmak için belirli ayrıntılar daha önce çalışır dahil örnek bölüm.</span><span class="sxs-lookup"><span data-stu-id="44ea6-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ea6-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44ea6-145">See Also</span></span>
