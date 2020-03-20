---
title: 'Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: d420ac8fcb98ddec195093be8ae25be37443da4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184972"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="29eeb-102">Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29eeb-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="29eeb-103">WCF hizmetleri ve istemcileri WebSockets üzerinden iletişim kurmak için <xref:System.ServiceModel.NetHttpBinding> bağlama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29eeb-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="29eeb-104">WebSockets hizmet sözleşmesi <xref:System.ServiceModel.NetHttpBinding> bir geri arama sözleşmesi tanımlar belirler zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="29eeb-105">Bu konu, WebSockets üzerinden iletişim kurmak <xref:System.ServiceModel.NetHttpBinding> için kullanan bir WCF hizmeti nin ve istemcinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="29eeb-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="29eeb-106">Hizmeti Tanımla</span><span class="sxs-lookup"><span data-stu-id="29eeb-106">Define the Service</span></span>  
  
1. <span data-ttu-id="29eeb-107">Geri arama sözleşmesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="29eeb-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="29eeb-108">Bu sözleşme, hizmetin istemciye ileti göndermesine izin vermek için istemci uygulaması tarafından uygulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="29eeb-109">Hizmet sözleşmesini tanımlayın `IStockQuoteCallback` ve arabirimi geri arama sözleşmesi olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="29eeb-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="29eeb-110">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="29eeb-110">Implement the service contract.</span></span>  
  
    ```csharp
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
  
     <span data-ttu-id="29eeb-111">Hizmet işlemi `StartSendingQuotes` eşzamanlı çağrı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="29eeb-112">Geri arama kanalını `OperationContext` kullanarak geri alma kanalını alıyoruz ve kanal açıksa, geri arama kanalında bir async araması yapıyoruz.</span><span class="sxs-lookup"><span data-stu-id="29eeb-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="29eeb-113">Hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29eeb-113">Configure the service</span></span>  
  
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
  
     <span data-ttu-id="29eeb-114">Hizmetin yapılandırma dosyası WCF'nin varsayılan uç noktalarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="29eeb-115">Bölüm, `<protocolMapping>` oluşturulan varsayılan uç `NetHttpBinding` noktalar için kullanılması gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="29eeb-116">İstemciyi Tanımla</span><span class="sxs-lookup"><span data-stu-id="29eeb-116">Define the Client</span></span>  
  
1. <span data-ttu-id="29eeb-117">Geri arama sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="29eeb-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="29eeb-118">Geri arama sözleşmesi işlemi eşzamanlı bir yöntem olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="29eeb-119">İstemci kodunu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="29eeb-119">Implement the client code.</span></span>  
  
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
  
         <span data-ttu-id="29eeb-120">CallbackHandler burada netlik için tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="29eeb-121">İstemci uygulaması yeni bir Örnek Bağlam oluşturur ve geri arama arabiriminin uygulanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29eeb-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="29eeb-122">Daha sonra, yeni oluşturulan InstanceContext'a başvuru gönderen proxy sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29eeb-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="29eeb-123">İstemci hizmeti aradığında, hizmet belirtilen geri arama sözleşmesini kullanarak istemciyi arar.</span><span class="sxs-lookup"><span data-stu-id="29eeb-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="29eeb-124">İstemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29eeb-124">Configure the client</span></span>  
  
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
  
         <span data-ttu-id="29eeb-125">İstemci yapılandırmasında yapmanız gereken özel bir şey yoktur, sadece `NetHttpBinding`istemci yan uç noktasını kullanarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="29eeb-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29eeb-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="29eeb-126">Example</span></span>  
 <span data-ttu-id="29eeb-127">Bu konuda kullanılan kodun tamamı aşağıda veda edilebedilir.</span><span class="sxs-lookup"><span data-stu-id="29eeb-127">The following is the complete code used in this topic.</span></span>  
  
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
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="29eeb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29eeb-128">See also</span></span>

- [<span data-ttu-id="29eeb-129">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="29eeb-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="29eeb-130">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="29eeb-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
