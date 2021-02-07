---
description: 'Daha fazla bilgi edinin: WSHttpBinding'
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 91537fa4237e0966864b53c37cd42da545fbe26d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668311"
---
# <a name="wshttpbinding"></a><span data-ttu-id="1f434-103">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1f434-103">WSHttpBinding</span></span>

<span data-ttu-id="1f434-104">Bu örnek, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f434-104">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1f434-105">Bu örnek, bir istemci konsol programından (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f434-105">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1f434-106">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="1f434-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="1f434-107">Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1f434-107">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="1f434-108">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="1f434-108">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="1f434-109">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="1f434-109">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1f434-110">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f434-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f434-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1f434-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1f434-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1f434-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f434-113">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1f434-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="1f434-114">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1f434-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1f434-115">Bu örnek `ICalculator` , kullanarak sözleşmeyi kullanıma sunar [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1f434-115">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="1f434-116">Web.config dosyasında bu bağlamanın yapılandırması genişletildi.</span><span class="sxs-lookup"><span data-stu-id="1f434-116">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="1f434-117">Taban `binding` öğesinde `maxReceivedMessageSize` değeri, gelen bir iletinin en büyük boyutunu (bayt cinsinden) yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1f434-117">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="1f434-118">`hostNameComparisonMode`Değer, ana bilgisayar adının hizmete ileti serbest bırakıldığında kabul edilip edilmeyeceğini yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f434-118">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="1f434-119">`messageEncoding`Değer, iletiler Için metin veya MTOM kodlamasının kullanılıp kullanılmayacağını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f434-119">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="1f434-120">`textEncoding`Değer, iletiler için karakter kodlamasını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f434-120">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="1f434-121">`bypassProxyOnLocal`Değer, yerel iletişim için BIR http proxy 'si kullanıp kullanmayacağınızı yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1f434-121">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="1f434-122">`transactionFlow`Değer, geçerli işlemin akan olup olmadığını yapılandırır (işlem akışı için bir işlem yapılandırılmışsa).</span><span class="sxs-lookup"><span data-stu-id="1f434-122">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="1f434-123">[\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md)Öğesinde, etkin Boole değeri, güvenilir oturumların etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1f434-123">On the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="1f434-124">`ordered`Değer, ileti sıralamasını korunup korunmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1f434-124">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="1f434-125">`inactivityTimeout`Değer, bir oturumun hata vermeden önce ne kadar süreyle boşta kalabileceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1f434-125">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="1f434-126">Üzerinde, [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1f434-126">On the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="1f434-127">Bu örnekte, ileti güvenliği kullanılmaktadır, bu neden [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilir [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1f434-127">In this sample, messages security is being used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="1f434-128">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f434-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1f434-129">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1f434-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f434-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1f434-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1f434-131">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="1f434-131">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="1f434-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1f434-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="1f434-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1f434-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1f434-134">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1f434-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
