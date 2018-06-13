---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 1f30c3a1c7a9a4874f4b831ee27192468e63c192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501422"
---
# <a name="mtom-encoding"></a><span data-ttu-id="9a7fd-102">MTOM Kodlama</span><span class="sxs-lookup"><span data-stu-id="9a7fd-102">MTOM Encoding</span></span>
<span data-ttu-id="9a7fd-103">Bu örnek bir WSHttpBinding kodlama ileti iletim en iyi duruma getirme mekanizmasını (MTOM) iletisi kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="9a7fd-104">MTOM SOAP iletilerle büyük ikili dosya eklerini ham bayt olarak iletmek için bir küçük iletiler için izin verme mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a7fd-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9a7fd-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9a7fd-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a7fd-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="9a7fd-109">Varsayılan, WSHttpBinding gönderir ve normal metin XML olarak alınan iletiler.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="9a7fd-110">MTOM ileti gönderme ve alma etkinleştirmek için ayarlanmış `messageEncoding` özniteliği bağlamanın yapılandırma (örneğin, aşağıdaki örnek kod) veya doğrudan bağlamayı kullanarak `MessageEncoding` özelliği.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="9a7fd-111">Hizmet veya istemci şimdi gönderip MTOM iletileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="9a7fd-112">MTOM Kodlayıcısı bayt ve akışlar dizileri en iyi duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="9a7fd-113">Bu örnekte, işlem kullanan bir `Stream` parametresi ve bu nedenle iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="9a7fd-114">Bu örnek için seçilen sözleşme hizmetine ikili veri aktaran ve dönüş değeri olarak karşıya bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="9a7fd-115">Hizmetin yüklü olduğundan ve istemci çalıştırın, tüm 1000 bayt aldığını gösteren sayı 1000 yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="9a7fd-116">Çıktı kalanı çeşitli yükü için en iyileştirilmiş veya iyileştirilmemiş ileti boyutlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="9a7fd-117">MTOM kullanma büyük ikili yüklerini iletimini en iyi duruma getirme amaçtır.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="9a7fd-118">MTOM kullanarak bir SOAP iletisi gönderme küçük ikili yükleri için belirgin yüke sahiptir, ancak birkaç bin bayt büyümeden harika tasarruf haline gelir.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="9a7fd-119">Bunun nedeni, normal metin XML için üç her bayt dört karakter gerektirir ve verilerin boyutunu üçte tarafından artıran Base64 kullanarak ikili veri kodlar ' dir.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="9a7fd-120">MTOM kodlama/kod çözme süresi kaydetme ham bayt ikili veri iletmek için ve elde edilen küçük ileti.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="9a7fd-121">Günümüzün iş belgeleri ve dijital fotoğraflar karşılaştırıldığında birkaç bin bayt eşiğinin küçüktür.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a7fd-122">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9a7fd-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9a7fd-123">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="9a7fd-124">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a7fd-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="9a7fd-125">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a7fd-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="9a7fd-126">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a7fd-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7fd-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a7fd-127">See Also</span></span>
