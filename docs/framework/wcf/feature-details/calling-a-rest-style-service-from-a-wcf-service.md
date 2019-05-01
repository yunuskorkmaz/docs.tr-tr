---
title: Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: c2a3467fb5fe28194dcb8ee7715353f4cb6a1bff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048224"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="3a44b-102">Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma</span><span class="sxs-lookup"><span data-stu-id="3a44b-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="3a44b-103">Bir normal (SOAP tabanlı) WCF hizmetinden REST stilinde service çağrılırken (gelen isteği bilgilerini içeren) hizmeti yöntemi işlemi içeriğine giden istek tarafından kullanılması gereken bağlam geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3a44b-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="3a44b-104">Bu, HTTP GET isteklerini HTTP POST istekleri değiştirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a44b-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="3a44b-105">WCF hizmetinden REST stilinde service çağırmak için doğru bağlamda kullanmaya zorlamak için yeni bir oluşturma <xref:System.ServiceModel.OperationContextScope> ve REST stili hizmetinden işlemi bağlam kapsam içinde çağırın.</span><span class="sxs-lookup"><span data-stu-id="3a44b-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="3a44b-106">Bu konuda, bu teknik gösteren basit bir örnek oluşturmak nasıl anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a44b-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="3a44b-107">REST stilinde hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a44b-107">Define the REST-style service contract</span></span>

<span data-ttu-id="3a44b-108">Basit bir REST stilinde service sözleşmesi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="3a44b-108">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="3a44b-109">REST stilinde hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="3a44b-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="3a44b-110">REST stilinde hizmet sözleşmesini uygulama:</span><span class="sxs-lookup"><span data-stu-id="3a44b-110">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="3a44b-111">WCF hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a44b-111">Define the WCF service contract</span></span>

<span data-ttu-id="3a44b-112">REST stilinde service çağırmak için kullanılan bir WCF sözleşmesi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="3a44b-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="3a44b-113">WCF hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="3a44b-113">Implement the WCF service contract</span></span>

<span data-ttu-id="3a44b-114">WCF hizmet sözleşmesini uygulama:</span><span class="sxs-lookup"><span data-stu-id="3a44b-114">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="3a44b-115">REST stilinde service için istemci proxy oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a44b-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="3a44b-116">Kullanarak <xref:System.ServiceModel.ClientBase%601> istemci proxy uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="3a44b-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="3a44b-117">Her bir yöntemin adı verilen yeni bir <xref:System.ServiceModel.OperationContextScope> oluşturulur ve bu işlemi çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a44b-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="3a44b-118">Ana bilgisayar ve hizmetlere çağrı yapın</span><span class="sxs-lookup"><span data-stu-id="3a44b-118">Host and call the services</span></span>

<span data-ttu-id="3a44b-119">Her iki Hizmetleri gerekli uç noktalar ve davranışlar eklemeyi, bir konsol uygulamasında barındırır.</span><span class="sxs-lookup"><span data-stu-id="3a44b-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="3a44b-120">' İ tıklatın ve sonra normal bir WCF Hizmeti çağırın:</span><span class="sxs-lookup"><span data-stu-id="3a44b-120">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="3a44b-121">Tam kod listesi</span><span class="sxs-lookup"><span data-stu-id="3a44b-121">Complete code listing</span></span>

<span data-ttu-id="3a44b-122">Bu konudaki uygulanan örnek tam listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a44b-122">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3a44b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a44b-123">See also</span></span>

- [<span data-ttu-id="3a44b-124">Nasıl yapılır: Temel bir WCF Web HTTP hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a44b-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="3a44b-125">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="3a44b-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
