---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 4156ebed22dc775aa69cf473dc89a26d7e2070d7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714763"
---
# <a name="mtom-encoding"></a><span data-ttu-id="391eb-102">MTOM Kodlama</span><span class="sxs-lookup"><span data-stu-id="391eb-102">MTOM Encoding</span></span>
<span data-ttu-id="391eb-103">Bu örnek, bir WSHttpBinding ile Ileti Iletimi Iyileştirme mekanizması (MTOM) ileti kodlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="391eb-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="391eb-104">MTOM, SOAP iletileri olan büyük ikili ekleri ham bayt olarak iletme ve daha küçük iletilere izin veren bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="391eb-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="391eb-105">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="391eb-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="391eb-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="391eb-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="391eb-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="391eb-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="391eb-108">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="391eb-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="391eb-109">Varsayılan olarak, WSHttpBinding iletileri normal metin XML olarak gönderir ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="391eb-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="391eb-110">MTOM iletilerinin gönderilmesini ve alınmasını etkinleştirmek için, bağlamanın yapılandırmasındaki `messageEncoding` özniteliğini (Aşağıdaki örnek kodda olduğu gibi) veya doğrudan bağlama üzerinde `MessageEncoding` özelliğini kullanarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="391eb-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="391eb-111">Hizmet veya istemci artık MTOM iletileri gönderebilir ve alabilir.</span><span class="sxs-lookup"><span data-stu-id="391eb-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="391eb-112">MTOM Kodlayıcısı, bayt ve akış dizilerini iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="391eb-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="391eb-113">Bu örnekte, işlem bir `Stream` parametresi kullanır ve bu nedenle en iyi duruma getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="391eb-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="391eb-114">Bu örnek için seçilen sözleşme, ikili verileri hizmete aktarır ve dönüş değeri olarak karşıya yüklenen bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="391eb-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="391eb-115">Hizmet yüklendiğinde ve istemci çalıştırıldığında, tüm 1000 baytlarının alındığını belirten 1000 sayısını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="391eb-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="391eb-116">Çıktının geri kalanı, çeşitli yükleri için iyileştirilmiş ve en iyi duruma getirilmemiş ileti boyutlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="391eb-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
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
  
 <span data-ttu-id="391eb-117">MTOM kullanmanın amacı, büyük ikili yüklerin iletimini en iyi hale getirsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="391eb-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="391eb-118">MTOM kullanarak bir SOAP iletisi gönderdiğinizde küçük ikili yükleri için fark edilebilir bir ek yük vardır, ancak birkaç bin baytlık büyürken harika bir tasarruf olur.</span><span class="sxs-lookup"><span data-stu-id="391eb-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="391eb-119">Bunun nedeni, normal metin XML 'nin ikili verileri her üç bayt için dört karakter gerektiren Base64 kullanarak kodlayacağı ve verilerin boyutunu bir üçüncü artırır.</span><span class="sxs-lookup"><span data-stu-id="391eb-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="391eb-120">MTOM, ikili verileri ham bayt olarak aktarabilir, kodlama/kod çözme süresini ve sonuç olarak daha küçük mesajlar elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="391eb-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="391eb-121">Bugünün iş belgelerinin ve dijital fotoğraflarına kıyasla birkaç bin baytlık eşik değeri küçüktür.</span><span class="sxs-lookup"><span data-stu-id="391eb-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="391eb-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="391eb-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="391eb-123">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="391eb-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="391eb-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="391eb-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="391eb-125">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="391eb-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="391eb-126">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="391eb-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
