---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: aa24a8f8553ceb035e5fc9c0c6094b1279711674
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839840"
---
# <a name="mtom-encoding"></a><span data-ttu-id="7d7e7-102">MTOM Kodlama</span><span class="sxs-lookup"><span data-stu-id="7d7e7-102">MTOM Encoding</span></span>
<span data-ttu-id="7d7e7-103">Bu örnek, bir WSHttpBinding kodlamasını ileti aktarım en iyi duruma getirme mekanizması (MTOM) kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="7d7e7-104">MTOM ham bayt, büyük ikili eklerle SOAP iletilerini ileten bir izin vermek için daha küçük iletileri mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d7e7-105">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d7e7-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d7e7-107">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d7e7-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="7d7e7-109">Varsayılan, WSHttpBinding gönderir ve normal metin XML olarak alınan iletiler.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="7d7e7-110">MTOM ileti gönderme ve alma etkinleştirmek için ayarlayın `messageEncoding` özniteliği bağlama yapılandırma (örneğin, aşağıdaki kod örneği), veya doğrudan bağlama kullanarak `MessageEncoding` özelliği.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="7d7e7-111">Hizmet veya istemcinin artık gönderebilir ve MTOM iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="7d7e7-112">MTOM Kodlayıcısı dizileri bayt akışları ve en iyi duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="7d7e7-113">Bu örnekte, işlemi kullanan bir `Stream` parametre ve bu nedenle iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="7d7e7-114">Bu örnek için seçilen sözleşme ikili veri hizmetine ileten ve dönüş değeri olarak karşıya yüklenen bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="7d7e7-115">Yüklü hizmeti algılayamaz ve istemci çalıştırın, tüm 1000 bayt aldığını gösteren sayı 1000 yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="7d7e7-116">Çıkış geri kalanı için çeşitli yüklerini en iyi duruma getirilmiş ve getirilmemiş ileti boyutları listeler.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7d7e7-117">MTOM kullanma amacı, büyük ikili yükler iletimini en iyi duruma getirme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="7d7e7-118">MTOM kullanarak bir SOAP ileti gönderme küçük ikili yükler için fark edilebilir bir yüke sahiptir, ancak birkaç bin bayttan fazla büyürler harika tasarruf olur.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="7d7e7-119">Bunun nedeni, normal metin XML dört karakter için her üç bayt gerektirir ve üçte tarafından verilerin boyutunu artırır, Base64 kullanarak ikili verileri kodlar ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="7d7e7-120">MTOM kodlama/kod çözme zamandan tasarruf ikili veri ham bayt aktarmak mümkün ve elde edilen küçük ileti.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="7d7e7-121">Günümüzde iş belgeleri ve dijital fotoğraflar karşılaştırıldığında birkaç bin bayt sayısı eşiğini küçüktür.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d7e7-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7d7e7-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7d7e7-123">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="7d7e7-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="7d7e7-124">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d7e7-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="7d7e7-125">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d7e7-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7d7e7-126">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d7e7-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
