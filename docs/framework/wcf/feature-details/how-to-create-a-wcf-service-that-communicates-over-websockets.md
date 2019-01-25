---
title: 'Nasıl yapılır: WebSockets üzerinden iletişim kuran bir WCF hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: d578b58f6613fb48f1bfceb8929ec51b8e025de1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689162"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="124e6-102">Nasıl yapılır: WebSockets üzerinden iletişim kuran bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="124e6-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="124e6-103">WCF hizmetleri ve istemcilerin <xref:System.ServiceModel.NetHttpBinding> WebSockets üzerinden iletişim kurmak için bağlama.</span><span class="sxs-lookup"><span data-stu-id="124e6-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="124e6-104">WebSockets olacaktır kullanılabilir <xref:System.ServiceModel.NetHttpBinding> hizmet sözleşmesini tanımlayan bir geri çağırma anlaşması belirler.</span><span class="sxs-lookup"><span data-stu-id="124e6-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="124e6-105">Bu konu açıklar nasıl uygulanacağı bir WCF hizmeti ve kullanan istemci <xref:System.ServiceModel.NetHttpBinding> WebSockets üzerinden iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="124e6-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="124e6-106">Hizmet tanımlama</span><span class="sxs-lookup"><span data-stu-id="124e6-106">Define the Service</span></span>  
  
1.  <span data-ttu-id="124e6-107">Bir geri çağırma anlaşması tanımlama</span><span class="sxs-lookup"><span data-stu-id="124e6-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="124e6-108">Bu sözleşme istemciye geri göndermek izin verecek şekilde istemci uygulaması tarafından uygulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="124e6-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2.  <span data-ttu-id="124e6-109">Hizmet sözleşmesini tanımlama ve belirtme `IStockQuoteCallback` arabirimi olarak geri çağırma anlaşması.</span><span class="sxs-lookup"><span data-stu-id="124e6-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3.  <span data-ttu-id="124e6-110">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="124e6-110">Implement the service contract.</span></span>  
  
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
  
     <span data-ttu-id="124e6-111">Hizmet işlemi `StartSendingQuotes` zaman uyumsuz bir çağrı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="124e6-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="124e6-112">Geri çağırma kanal kullanılarak alıyoruz `OperationContext` ve kanal açıksa, bir zaman uyumsuz geri çağırma kanalda çağrı vermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="124e6-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4.  <span data-ttu-id="124e6-113">Hizmet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="124e6-113">Configure the service</span></span>  
  
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
  
     <span data-ttu-id="124e6-114">Hizmetin yapılandırma dosyası WCF'ın varsayılan bitiş noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="124e6-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="124e6-115">`<protocolMapping>` Belirtmek için kullanılan bölüm `NetHttpBinding` oluşturulan varsayılan uç noktalar için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="124e6-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="124e6-116">İstemci tanımlayın</span><span class="sxs-lookup"><span data-stu-id="124e6-116">Define the Client</span></span>  
  
1.  <span data-ttu-id="124e6-117">Geri çağırma anlaşması uygulayın.</span><span class="sxs-lookup"><span data-stu-id="124e6-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="124e6-118">Geri çağırma anlaşması işlemi zaman uyumsuz bir yöntem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="124e6-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1.  <span data-ttu-id="124e6-119">İstemci kodu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="124e6-119">Implement the client code.</span></span>  
  
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
  
         <span data-ttu-id="124e6-120">CallbackHandler açıklık için buraya yinelenir.</span><span class="sxs-lookup"><span data-stu-id="124e6-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="124e6-121">İstemci uygulaması, yeni bir InstanceContext oluşturur ve uygulamasını geri çağırma arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="124e6-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="124e6-122">Ardından yeni oluşturulan InstanceContext başvuru gönderme proxy sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="124e6-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="124e6-123">İstemci hizmeti çağırıp, belirtilen geri çağırma anlaşması kullanarak istemci hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="124e6-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2.  <span data-ttu-id="124e6-124">İstemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="124e6-124">Configure the client</span></span>  
  
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
  
         <span data-ttu-id="124e6-125">Özel istemci yapılandırmasında yapmak için yalnızca istemci tarafında kullanan uç noktasını belirtin. gereken şey `NetHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="124e6-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="124e6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="124e6-126">Example</span></span>  
 <span data-ttu-id="124e6-127">Bu konuda kullanılan tüm kod verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="124e6-127">The following is the complete code used in this topic.</span></span>  
  
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
  https://go.microsoft.com/fwlink/?LinkId=169433  
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
<!--App.config -->  
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
  
## <a name="see-also"></a><span data-ttu-id="124e6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="124e6-128">See also</span></span>
- [<span data-ttu-id="124e6-129">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="124e6-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="124e6-130">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="124e6-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
