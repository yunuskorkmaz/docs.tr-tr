---
title: Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma
description: Bir kapsam oluşturarak ve bu kapsamdaki REST stili hizmeti çağırarak bir WCF hizmetinin bir REST stili hizmet ile doğru bağlamı nasıl kullandığını öğrenin.
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 15f468923cf55feb85e7aeca1a2cc5e38050d665
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245303"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="4a6ad-103">Bir WCF hizmetinden REST tarzı bir hizmete çağrı yapma</span><span class="sxs-lookup"><span data-stu-id="4a6ad-103">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="4a6ad-104">Normal (SOAP tabanlı) bir WCF hizmetinden REST tarzı bir hizmet çağrılırken, hizmet yöntemindeki (gelen istek hakkında bilgi içeren) işlem bağlamı, giden istek tarafından kullanılması gereken bağlamı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-104">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="4a6ad-105">Bu, HTTP GET isteklerinin HTTP POST isteklerinde değişmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-105">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="4a6ad-106">WCF hizmetini REST stili hizmeti çağırmak için doğru bağlamı kullanacak şekilde zorlamak için, yeni bir oluşturun <xref:System.ServiceModel.OperationContextScope> ve işlem bağlamı kapsamının IÇINDEN Rest stili hizmeti çağırın.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-106">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="4a6ad-107">Bu konu, bu tekniği gösteren basit bir örnek oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-107">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="4a6ad-108">REST stili hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a6ad-108">Define the REST-style service contract</span></span>

<span data-ttu-id="4a6ad-109">Basit bir REST stili hizmet sözleşmesi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-109">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="4a6ad-110">REST stili hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="4a6ad-110">Implement the REST-style service contract</span></span>

<span data-ttu-id="4a6ad-111">REST stili hizmet sözleşmesini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-111">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="4a6ad-112">WCF hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a6ad-112">Define the WCF service contract</span></span>

<span data-ttu-id="4a6ad-113">REST stili hizmeti çağırmak için kullanılacak bir WCF hizmeti sözleşmesi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-113">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="4a6ad-114">WCF hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="4a6ad-114">Implement the WCF service contract</span></span>

<span data-ttu-id="4a6ad-115">WCF hizmet sözleşmesini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-115">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="4a6ad-116">REST stili hizmet için istemci ara sunucusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a6ad-116">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="4a6ad-117"><xref:System.ServiceModel.ClientBase%601>İstemci proxy 'sini uygulamak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-117">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="4a6ad-118">Çağrılan her yöntem için, yeni bir <xref:System.ServiceModel.OperationContextScope> oluşturulur ve işlemi çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-118">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="4a6ad-119">Hizmetleri barındırın ve çağırın</span><span class="sxs-lookup"><span data-stu-id="4a6ad-119">Host and call the services</span></span>

<span data-ttu-id="4a6ad-120">Gerekli uç noktaları ve davranışları ekleyerek, her iki hizmeti de bir konsol uygulamasında barındırın.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-120">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="4a6ad-121">Ardından normal WCF hizmetini çağırın:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-121">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="4a6ad-122">Tam kod listesi</span><span class="sxs-lookup"><span data-stu-id="4a6ad-122">Complete code listing</span></span>

<span data-ttu-id="4a6ad-123">Aşağıda, bu konuda uygulanan örneğin bir bütün olarak listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a6ad-123">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4a6ad-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a6ad-124">See also</span></span>

- [<span data-ttu-id="4a6ad-125">Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a6ad-125">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="4a6ad-126">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="4a6ad-126">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
