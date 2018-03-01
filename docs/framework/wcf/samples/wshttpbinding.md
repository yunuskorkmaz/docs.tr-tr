---
title: WSHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ff105c626f72d34cf6963586a84aba945b5af01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wshttpbinding"></a><span data-ttu-id="234af-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="234af-102">WSHttpBinding</span></span>
<span data-ttu-id="234af-103">Bu örnek, tipik bir hizmet ve kullanarak tipik bir istemci uygulama gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="234af-103">This sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="234af-104">Bu örnek, bir istemci konsol programı (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="234af-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="234af-105">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="234af-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="234af-106">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="234af-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="234af-107">İstemci eş zamanlı istekleri verilen matematik işlemi ve sonuç ile hizmet yanıtları yapar.</span><span class="sxs-lookup"><span data-stu-id="234af-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="234af-108">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="234af-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="234af-109">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="234af-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="234af-110">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="234af-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="234af-111">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="234af-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="234af-112">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="234af-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="234af-113">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="234af-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="234af-114">Bu örnek sunan `ICalculator` kullanarak sözleşme [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="234af-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="234af-115">Bu bağlama yapılandırmasını Web.config dosyasında genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="234af-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="234af-116">Tabanında `binding` öğesi, `maxReceivedMessageSize` değeri en büyük boyutunu (bayt cinsinden) gelen ileti yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="234af-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="234af-117">`hostNameComparisonMode` Değer hostname XML'deki çoğullama hizmete zaman iletileri kabul olup olmadığını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="234af-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="234af-118">`messageEncoding` Değeri iletileri için metin veya MTOM kodlama kullanılıp kullanılmayacağını yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="234af-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="234af-119">`textEncoding` Değeri iletileri için karakter kodlamasını yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="234af-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="234af-120">`bypassProxyOnLocal` Değeri yerel iletişim için bir HTTP proxy kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="234af-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="234af-121">`transactionFlow` Değeri, geçerli işlem (bir işlem için işlem akışı yapılandırılmışsa) akıtılan olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="234af-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="234af-122">Üzerinde [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) öğesi, etkin Boole değeri yapılandırır güvenilir oturumlar etkinleştirilip etkinleştirilmediğini.</span><span class="sxs-lookup"><span data-stu-id="234af-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="234af-123">`ordered` Değeri ileti sıralama korundu olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="234af-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="234af-124">`inactivityTimeout` Değer ne kadar bir oturumun hatalı önce boşta kalabileceği yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="234af-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="234af-125">Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="234af-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="234af-126">Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="234af-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="234af-127">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="234af-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="234af-128">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="234af-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="234af-129">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="234af-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="234af-130">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="234af-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="234af-131">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="234af-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="234af-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="234af-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="234af-133">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="234af-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234af-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="234af-134">See Also</span></span>
