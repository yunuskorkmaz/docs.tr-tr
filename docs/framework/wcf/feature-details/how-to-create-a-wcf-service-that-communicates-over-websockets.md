---
title: "Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49a0eeaedd9b41a7c4149aacc0193454f4691b1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="a6e19-102">Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6e19-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="a6e19-103">WCF hizmetleri ve istemcileri kullanabilir <xref:System.ServiceModel.NetHttpBinding> WebSockets üzerinden iletişim kurmak için bağlama.</span><span class="sxs-lookup"><span data-stu-id="a6e19-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="a6e19-104">WebSockets olacaktır kullanılır <xref:System.ServiceModel.NetHttpBinding> hizmet sözleşmesini tanımlayan bir geri çağırma sözleşme belirler.</span><span class="sxs-lookup"><span data-stu-id="a6e19-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="a6e19-105">Bu konu, bir WCF hizmeti ve kullanan istemci uygulamak açıklar <xref:System.ServiceModel.NetHttpBinding> WebSockets üzerinden iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="a6e19-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="a6e19-106">Hizmeti tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a6e19-106">Define the Service</span></span>  
  
1.  <span data-ttu-id="a6e19-107">Bir geri çağırma sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="a6e19-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="a6e19-108">Bu sözleşme, istemciye iletileri göndermeye izin verecek şekilde istemci uygulaması tarafından uygulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2.  <span data-ttu-id="a6e19-109">Hizmet sözleşmesini tanımlama ve belirtme `IStockQuoteCallback` geri çağırma sözleşme arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a6e19-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3.  <span data-ttu-id="a6e19-110">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="a6e19-110">Implement the service contract.</span></span>  
  
    ```  
    public class StockQuoteService : IStockQuoteService  
        {  
            public async Task StartSendingQuotes()  
            {  
                var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
                var random = new Random();  
                double price = 29.00;  
  
                while (((IChannel)callback).State == CommunicationState.Opened)  
                {  
                    await callback.SendQuote("MSFT", price);  
                    price += random.NextDouble();  
                    await Task.Delay(1000);  
                }  
            }  
        }  
    ```  
  
     <span data-ttu-id="a6e19-111">Hizmet işlemini `StartSendingQuotes` bir zaman uyumsuz çağrı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="a6e19-112">Geri çağırma kanalı kullanılarak alıyoruz `OperationContext` ve kanal açıksa, zaman uyumsuz geri çağırma kanalda çağrı vermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="a6e19-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4.  <span data-ttu-id="a6e19-113">Hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6e19-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />        
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="a6e19-114">WCF'ın varsayılan uç noktalarda hizmetin yapılandırma dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="a6e19-115">`<protocolMapping>` Belirtmek için kullanılan bölüm `NetHttpBinding` oluşturulan varsayılan uç noktalar için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="a6e19-116">İstemci tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a6e19-116">Define the Client</span></span>  
  
1.  <span data-ttu-id="a6e19-117">Geri arama sözleşmesi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a6e19-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="a6e19-118">Geri çağırma sözleşme işlem zaman uyumsuz bir yöntem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1.  <span data-ttu-id="a6e19-119">İstemci kodu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a6e19-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();              
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="a6e19-120">CallbackHandler burada daha anlaşılır olması için tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="a6e19-121">İstemci uygulamasının yeni InstanceContext oluşturur ve uygulama geri çağırma arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6e19-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="a6e19-122">Sonraki yeni oluşturulan InstanceContext başvuru gönderme proxy sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6e19-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="a6e19-123">İstemci hizmet çağırdığında hizmet belirtilen geri çağırma sözleşme kullanarak istemciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a6e19-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2.  <span data-ttu-id="a6e19-124">İstemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6e19-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>   
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="a6e19-125">Gereken istemci yapılandırmasında yapmak için yalnızca istemci tarafında kullanan uç noktasını belirtmek özel bir şey yok `NetHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="a6e19-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6e19-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6e19-126">Example</span></span>  
 <span data-ttu-id="a6e19-127">Bu konuda kullanılan tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6e19-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```  
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  http://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />        
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```  
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();              
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!—App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>   
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6e19-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6e19-128">See Also</span></span>  
 [<span data-ttu-id="a6e19-129">Zaman uyumlu ve zaman uyumsuz işlemler</span><span class="sxs-lookup"><span data-stu-id="a6e19-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [<span data-ttu-id="a6e19-130">NetHttpBinding kullanma</span><span class="sxs-lookup"><span data-stu-id="a6e19-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
