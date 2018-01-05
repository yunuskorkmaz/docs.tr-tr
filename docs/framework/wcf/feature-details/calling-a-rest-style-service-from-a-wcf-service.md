---
title: "Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b056e2c4dad46429462b377994919b46109cb9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="42fab-102">Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma</span><span class="sxs-lookup"><span data-stu-id="42fab-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="42fab-103">Normal bir (SOAP tabanlı) WCF hizmetinden REST tarzı bir hizmete çağırma etkinleştirildiğinde (gelen isteği bilgilerini içeren) hizmeti yöntemi işlemi içeriğine giden istek tarafından kullanılması gereken bağlamı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="42fab-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="42fab-104">Bu değişiklik HTTP POST istekleri için HTTP GET isteklerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="42fab-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="42fab-105">REST stilinde service çağırmak için doğru içeriği kullanmak için WCF Hizmeti zorlamak için yeni bir oluşturma <xref:System.ServiceModel.OperationContextScope> ve REST stili hizmetinden işlemi bağlam kapsam içinde çağırın.</span><span class="sxs-lookup"><span data-stu-id="42fab-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="42fab-106">Bu konu, bu tekniği gösterir basit bir örnek oluşturmak nasıl anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42fab-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="42fab-107">REST stilinde hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="42fab-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="42fab-108">Basit bir REST stilinde service sözleşme tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="42fab-108">Define a simple  REST-style service contract:</span></span>  
  
```csharp
[ServiceContract]
public interface IRestInterface  
{  
    [OperationContract, WebGet]
    int Add(int x, int y);
    
    [OperationContract, WebGet]
    string Echo(string input);
}
```
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="42fab-109">REST stilinde hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="42fab-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="42fab-110">REST stilinde hizmet sözleşmesini uygulama:</span><span class="sxs-lookup"><span data-stu-id="42fab-110">Implement the REST-style service contract:</span></span>  
  
```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }
    
    public string Echo(string input)
    {
        return input;
    }
}
```
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="42fab-111">WCF hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="42fab-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="42fab-112">REST stilinde hizmetini çağırmak için kullanılan bir WCF sözleşmesi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="42fab-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);
    
    [OperationContract]
    string CallEcho(string input);
}
```  
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="42fab-113">WCF hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="42fab-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="42fab-114">WCF hizmet sözleşmesini uygulama:</span><span class="sxs-lookup"><span data-stu-id="42fab-114">Implement the WCF service contract:</span></span>  
  
```csharp
public class NormalService : INormalInterface  
{  
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
    public int CallAdd(int x, int y)  
    {  
        return client.Add(x, y);  
    }  
    
    public string CallEcho(string input)  
    {  
        return client.Echo(input);  
    }  
}  
```  
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="42fab-115">REST stilinde service için istemci proxy oluşturma</span><span class="sxs-lookup"><span data-stu-id="42fab-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="42fab-116">Kullanarak <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` istemci proxy uygulayın.</span><span class="sxs-lookup"><span data-stu-id="42fab-116">Using <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implement the client proxy.</span></span> <span data-ttu-id="42fab-117">Her bir yöntemin adı verilen yeni bir <xref:System.ServiceModel.OperationContextScope> oluşturulur ve çağrı işlemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42fab-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```  
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="42fab-118">Ana bilgisayar ve Hizmetleri çağırın</span><span class="sxs-lookup"><span data-stu-id="42fab-118">Host and call the services</span></span>  
 <span data-ttu-id="42fab-119">Her iki hizmet davranışları ve gerekli uç noktaları ekleme, bir konsol uygulamasında barındırır.</span><span class="sxs-lookup"><span data-stu-id="42fab-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="42fab-120">Ve normal WCF Hizmeti çağırın:</span><span class="sxs-lookup"><span data-stu-id="42fab-120">And then call the regular WCF service:</span></span>  
  
```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```  
  
## <a name="complete-code-listing"></a><span data-ttu-id="42fab-121">Tam kod listeleri</span><span class="sxs-lookup"><span data-stu-id="42fab-121">Complete code listing</span></span>  
 <span data-ttu-id="42fab-122">Bu konudaki uygulanan örnek tam bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="42fab-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
```csharp
public class CallingRESTSample  
{  
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";  
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";  

    [ServiceContract]  
    public interface IRestInterface  
    {  
        [OperationContract, WebGet]  
        int Add(int x, int y);  
        [OperationContract, WebGet]  
        string Echo(string input);  
    }  

    [ServiceContract]  
    public interface INormalInterface  
    {  
        [OperationContract]  
        int CallAdd(int x, int y);  
        [OperationContract]  
        string CallEcho(string input);  
    }  

    public class RestService : IRestInterface  
    {  
        public int Add(int x, int y)  
        {  
            return x + y;  
        }  

        public string Echo(string input)  
        {  
            return input;  
        }  
    }  

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface  
    {  
        public MyRestClient(string address)  
            : base(new WebHttpBinding(), new EndpointAddress(address))  
        {  
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());  
        }  

        public int Add(int x, int y)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Add(x, y);  
            }  
        }  

        public string Echo(string input)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Echo(input);  
            }  
        }  
    }  

    public class NormalService : INormalInterface  
    {  
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
        public int CallAdd(int x, int y)  
        {  
            return client.Add(x, y);  
        }  

        public string CallEcho(string input)  
        {  
            return client.Echo(input);  
        }  
    }
    
    public static void Main()  
    {  
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));  
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
        restHost.Open();  

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));  
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");  
        normalHost.Open();  

        Console.WriteLine("Hosts opened");  

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));  
        INormalInterface proxy = factory.CreateChannel();  

        Console.WriteLine(proxy.CallAdd(123, 456));  
        Console.WriteLine(proxy.CallEcho("Hello world"));  
    }  
}
```
  
## <a name="see-also"></a><span data-ttu-id="42fab-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42fab-123">See Also</span></span>  
 [<span data-ttu-id="42fab-124">Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42fab-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="42fab-125">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="42fab-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
