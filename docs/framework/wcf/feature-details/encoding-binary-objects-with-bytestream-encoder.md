---
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626935"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="d661a-102">ByteStream Kodlayıcı ile İkili Nesneler Kodlama</span><span class="sxs-lookup"><span data-stu-id="d661a-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="d661a-103">Gönderme ve alma ham ikili verileri Windows Communication Foundation (WCF) ile yapılandırılmış kullanarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d661a-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="d661a-104">Bayt Stream ileti Kodlayıcı mimarisi</span><span class="sxs-lookup"><span data-stu-id="d661a-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="d661a-105">WCF tarafından kullanılan ikili ileti Kodlayıcısı, işleme, doğrulama veya iletinin temel alınan ikili veriyi tanımlamak için hiçbir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="d661a-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="d661a-106">Veri paketi XML olarak kodlanmış, gönderilen, alınan ve çözülmüş.</span><span class="sxs-lookup"><span data-stu-id="d661a-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="d661a-107">Kodlayıcı, taşıma ve ileti kuyruğa ileti gönderilmeden önce geçirilen sonra verileri işler.</span><span class="sxs-lookup"><span data-stu-id="d661a-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="d661a-108">İkili Kodlayıcı ileti verileri işlevsellik, sarmalar `<binary>` öğeleri göndermek ve ileti alındıktan sonra öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d661a-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="d661a-109">Bayt Stream ileti Kodlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="d661a-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="d661a-110">Aşağıdaki örnek, bayt akışı ileti Kodlayıcı uygulayan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d661a-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="d661a-111">Aşağıdaki örnek, çağrılan hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="d661a-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="d661a-112">Bir ileti altyapısı (örneğin, bir yönlendirici) uygulayan bir hizmet kullanarak söz konusu olduğunda, ileti inceleyerek, doğrulama ya da aksi takdirde, iletinin etkileşim olmadan aşağıdaki örnekte gösterildiği gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="d661a-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="d661a-113">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="d661a-113">Scenarios</span></span>  
 <span data-ttu-id="d661a-114">Bayt Stream Kodlayıcı, aşağıdaki senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d661a-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="d661a-115">Bir JPEG görüntüsünü WCF kullanan bilgisayarlar arasında veri aktarımı.</span><span class="sxs-lookup"><span data-stu-id="d661a-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="d661a-116">Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d661a-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="d661a-117">Hizmet ikili verileri almak ve resmi görüntüle.</span><span class="sxs-lookup"><span data-stu-id="d661a-117">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="d661a-118">Bir ileti kuyruğu dışında bilgileri okunuyor ve işleniyor.</span><span class="sxs-lookup"><span data-stu-id="d661a-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="d661a-119">İleti bir ileti kuyruğu Yöneticisi'nden okuyun ve işlenecek ileti kuyruğu kanalı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="d661a-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="d661a-120">İleti kuyruğu kanal WCF kanalı yığındaki bir Kuyruk yöneticisi olarak hareket edecek.</span><span class="sxs-lookup"><span data-stu-id="d661a-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="d661a-121">Bir ileti kuyruğu kanal üzerinden ileti gönderme söz konusu olduğunda, gönderen Kuyruk Yöneticisi'nden alınan bayt miktarı üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d661a-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="d661a-122">Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi kullanılabilir bir biçime alınan bayt çevirme özelliğine sahip olacağını varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d661a-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
