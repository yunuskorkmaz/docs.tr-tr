---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d8453d85afb92c69bdf3066ccb8b31e26a34c6d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768091"
---
# <a name="wshttpbinding"></a><span data-ttu-id="72aba-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="72aba-102">WSHttpBinding</span></span>
<span data-ttu-id="72aba-103">Bu örnek, tipik bir hizmet ve Windows Communication Foundation (WCF) kullanan tipik bir istemciye uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="72aba-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="72aba-104">Bu örnek, bir istemci konsol programı'nı (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="72aba-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="72aba-105">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="72aba-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="72aba-106">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="72aba-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="72aba-107">İstemci verilen matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="72aba-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="72aba-108">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="72aba-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72aba-109">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="72aba-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72aba-110">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="72aba-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="72aba-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="72aba-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72aba-112">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="72aba-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="72aba-113">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="72aba-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="72aba-114">Bu örnek gösterir `ICalculator` kullanarak sözleşme [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72aba-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="72aba-115">Bu bağlama yapılandırmasını Web.config dosyasında genişletildi.</span><span class="sxs-lookup"><span data-stu-id="72aba-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="72aba-116">Taban `binding` öğesi `maxReceivedMessageSize` değeri en büyük boyutunu (bayt cinsinden) gelen ileti yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aba-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="72aba-117">`hostNameComparisonMode` Değeri ana bilgisayar hizmete XML'deki çoğullama, iletileri kabul olmadığını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aba-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="72aba-118">`messageEncoding` Değeri iletiler için metin veya MTOM kodlama kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aba-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="72aba-119">`textEncoding` Değeri karakter kodlaması için iletileri yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aba-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="72aba-120">`bypassProxyOnLocal` Değer yerel iletişim için bir HTTP proxy kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aba-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="72aba-121">`transactionFlow` Değeri, geçerli işlem (bir işlem için işlem akışı yapılandırılmışsa) akıtılan olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="72aba-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="72aba-122">Üzerinde [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) öğesi, etkin bir Boole değeri yapılandırır güvenilir oturumlar etkinleştirilip etkinleştirilmediğini.</span><span class="sxs-lookup"><span data-stu-id="72aba-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="72aba-123">`ordered` Değer ileti sıralama korundu olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="72aba-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="72aba-124">`inactivityTimeout` Değer ne kadar bir oturumun hatalı önce boşta kalabileceği yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="72aba-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="72aba-125">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72aba-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="72aba-126">Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72aba-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="72aba-127">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="72aba-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="72aba-128">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="72aba-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72aba-129">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="72aba-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="72aba-130">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="72aba-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="72aba-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72aba-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="72aba-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72aba-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="72aba-133">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72aba-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
