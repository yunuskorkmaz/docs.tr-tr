---
title: MTOM Kodlama
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144389"
---
# <a name="mtom-encoding"></a><span data-ttu-id="43539-102">MTOM Kodlama</span><span class="sxs-lookup"><span data-stu-id="43539-102">MTOM Encoding</span></span>
<span data-ttu-id="43539-103">Bu örnek, Bir WSHttpBinding ile kodlama İleti Aktarım Optimizasyonu Mekanizması (MTOM) iletisinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43539-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="43539-104">MTOM, büyük ikili ekleri SOAP iletileri ile ham bayt olarak iletmek için bir mekanizmadır ve daha küçük iletilere olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43539-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43539-105">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="43539-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43539-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="43539-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="43539-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="43539-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43539-108">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="43539-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="43539-109">Varsayılan olarak, WSHttpBinding gönderir ve normal metin XML olarak iletileri aldı.</span><span class="sxs-lookup"><span data-stu-id="43539-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="43539-110">MTOM iletilerinin gönderilmesini ve alınmasını `messageEncoding` etkinleştirmek için, özniteliği bağlama yapılandırmasına (aşağıdaki örnek kodda olduğu `MessageEncoding` gibi) veya özelliği kullanarak doğrudan bağlamaya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43539-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="43539-111">Hizmet veya istemci artık MTOM iletileri gönderip alabilir.</span><span class="sxs-lookup"><span data-stu-id="43539-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="43539-112">MTOM kodlayıcısı bayt ve akış dizilerini optimize edebilir.</span><span class="sxs-lookup"><span data-stu-id="43539-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="43539-113">Bu örnekte, işlem `Stream` bir parametre kullanır ve bu nedenle en iyi duruma getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="43539-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="43539-114">Bu örnek için seçilen sözleşme, ikili verileri hizmete iletir ve iade değeri olarak yüklenen bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="43539-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="43539-115">Hizmet yüklendiğinde ve istemci çalıştırıldığında, 1000 baytın tamamının alındığını gösteren 1000 sayısını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="43539-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="43539-116">Çıktının geri kalanı, çeşitli yükler için en iyi duruma getirilmiş ve optimize edilmeyen ileti boyutlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="43539-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="43539-117">MTOM'u kullanmanın amacı, büyük ikili yüklerin iletimini optimize etmektir.</span><span class="sxs-lookup"><span data-stu-id="43539-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="43539-118">MTOM kullanarak soap iletisi göndermek, küçük ikili yükler için gözle görülür bir yüke sahiptir, ancak birkaç bin baytın üzerinde büyüdüklerinde büyük bir tasarruf sağlar.</span><span class="sxs-lookup"><span data-stu-id="43539-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="43539-119">Bunun nedeni, normal metin XML'in her üç bayt için dört karakter gerektiren Base64 kullanarak ikili verileri kodlaması ve verilerin boyutunu üçte bir oranında artırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="43539-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="43539-120">MTOM, ikili verileri ham bayt olarak iletebilir, kodlama/çözme süresini kaydeder ve ortaya çıkan iletiler daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="43539-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="43539-121">Birkaç bin bayt eşiği bugünün iş belgeleri ve dijital fotoğraflar ile karşılaştırıldığında küçüktür.</span><span class="sxs-lookup"><span data-stu-id="43539-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43539-122">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="43539-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="43539-123">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="43539-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="43539-124">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="43539-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="43539-125">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="43539-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="43539-126">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="43539-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
