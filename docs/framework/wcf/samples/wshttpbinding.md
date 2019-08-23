---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5d76cb2e4d9f3173c1eb3fda45e1f1c65efeadde
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959816"
---
# <a name="wshttpbinding"></a><span data-ttu-id="da9bb-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="da9bb-102">WSHttpBinding</span></span>
<span data-ttu-id="da9bb-103">Bu örnek, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="da9bb-104">Bu örnek, bir istemci konsol programından (Client. exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="da9bb-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="da9bb-105">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="da9bb-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="da9bb-106">Sözleşme, matematik işlemlerini (ekleme `ICalculator` , çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="da9bb-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="da9bb-107">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="da9bb-108">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="da9bb-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da9bb-109">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da9bb-110">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="da9bb-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da9bb-111">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="da9bb-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da9bb-112">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="da9bb-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="da9bb-113">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="da9bb-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="da9bb-114">Bu örnek, `ICalculator` bir sözleşmeyi [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="da9bb-115">Bu bağlamanın yapılandırması Web. config dosyasında genişletildi.</span><span class="sxs-lookup"><span data-stu-id="da9bb-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="da9bb-116">Taban `binding` öğesinde `maxReceivedMessageSize` değeri, gelen bir iletinin en büyük boyutunu (bayt cinsinden) yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="da9bb-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="da9bb-117">`hostNameComparisonMode` Değer, ana bilgisayar adının hizmete ileti serbest bırakıldığında kabul edilip edilmeyeceğini yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da9bb-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="da9bb-118">Değer `messageEncoding` , iletiler için metin veya MTOM kodlamasının kullanılıp kullanılmayacağını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da9bb-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="da9bb-119">Değer `textEncoding` , iletiler için karakter kodlamasını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da9bb-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="da9bb-120">Değer `bypassProxyOnLocal` , yerel iletişim için bir http proxy 'si kullanıp kullanmayacağınızı yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="da9bb-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="da9bb-121">`transactionFlow` Değer, geçerli işlemin akan olup olmadığını yapılandırır (işlem akışı için bir işlem yapılandırılmışsa).</span><span class="sxs-lookup"><span data-stu-id="da9bb-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="da9bb-122">ReliableSession > öğesinde, etkin Boole değeri, güvenilir oturumların etkinleştirilip etkinleştirilmeyeceğini yapılandırır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)</span><span class="sxs-lookup"><span data-stu-id="da9bb-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="da9bb-123">Değer `ordered` , ileti sıralamasını korunup korunmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="da9bb-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="da9bb-124">Değer `inactivityTimeout` , bir oturumun hata vermeden önce ne kadar süreyle boşta kalabileceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="da9bb-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="da9bb-125">Güvenlik >, değerhangigüvenlikmodununkullanılmasıgerektiğiniyapılandırır.`mode` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="da9bb-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="da9bb-126">Bu örnekte [ \<ileti](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) güvenliği kullanılmaktadır, bu neden > ileti [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="da9bb-127">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="da9bb-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="da9bb-128">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="da9bb-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da9bb-129">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="da9bb-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="da9bb-130">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="da9bb-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="da9bb-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="da9bb-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="da9bb-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="da9bb-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="da9bb-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="da9bb-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
