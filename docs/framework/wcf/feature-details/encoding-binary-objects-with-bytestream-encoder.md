---
description: 'Hakkında daha fazla bilgi edinin: ByteStream kodlayıcı ile Ikili nesneleri kodlama'
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 4ef3d3cd378abacd14dd502530a8090f3982e4ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704907"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="47565-103">ByteStream Kodlayıcı ile İkili Nesneler Kodlama</span><span class="sxs-lookup"><span data-stu-id="47565-103">Encoding Binary Objects with ByteStream Encoder</span></span>

<span data-ttu-id="47565-104">Windows Communication Foundation (WCF) ile ham ikili verileri gönderme ve alma kullanılarak yapılandırılır <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="47565-104">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="47565-105">Bayt akışı Ileti Kodlayıcısı mimarisi</span><span class="sxs-lookup"><span data-stu-id="47565-105">Byte Stream Message Encoder Architecture</span></span>  

 <span data-ttu-id="47565-106">WCF tarafından kullanılan ikili ileti Kodlayıcısı, iletideki temel alınan ikili verileri işlemeye, doğrulamaya veya tanımlamaya yönelik bir özellik içermez.</span><span class="sxs-lookup"><span data-stu-id="47565-106">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="47565-107">Veri paketi XML olarak kodlanır, gönderilir, alınır ve kodu çözülür.</span><span class="sxs-lookup"><span data-stu-id="47565-107">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="47565-108">Kodlayıcı, ulaşım 'e geçtikten sonra ve ileti ileti kuyruğuna gönderilmeden önce verileri işler.</span><span class="sxs-lookup"><span data-stu-id="47565-108">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="47565-109">İşlevsellik, ikili kodlayıcı, ileti `<binary>` alındıktan sonra öğeleri göndermek ve silmek için öğeler halinde ileti verilerini sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="47565-109">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="47565-110">Byte Stream Ileti Kodlayıcısı 'nı kullanma</span><span class="sxs-lookup"><span data-stu-id="47565-110">Using the Byte Stream Message Encoder</span></span>  

 <span data-ttu-id="47565-111">Aşağıdaki örnek, bayt akışı ileti Kodlayıcısı 'nı uygulayan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="47565-111">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="47565-112">Aşağıdaki örnek, çağrılan hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="47565-112">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="47565-113">İleti altyapısını uygulayan bir hizmet (örneğin, yönlendirici) kullanıldığında ileti, aşağıdaki örnekte gösterildiği gibi İnceleme, doğrulama veya başka bir şekilde etkileşimde bulunmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="47565-113">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="47565-114">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="47565-114">Scenarios</span></span>  

 <span data-ttu-id="47565-115">Byte Stream Encoder, aşağıdaki senaryolarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="47565-115">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="47565-116">WCF kullanarak bir JPEG görüntüsünü bilgisayarlar arasında aktarma.</span><span class="sxs-lookup"><span data-stu-id="47565-116">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="47565-117">Bu senaryoda, görüntü bir dış kaynaktan aktarımdan geçer ve gönderilen veriler görüntüyü oluşturan ham bayt olur.</span><span class="sxs-lookup"><span data-stu-id="47565-117">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="47565-118">Bir hizmet ikili verileri alır ve görüntüyü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="47565-118">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="47565-119">Bilgileri bir ileti kuyruğundan okuma ve işleme.</span><span class="sxs-lookup"><span data-stu-id="47565-119">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="47565-120">İleti bir ileti kuyruğu yöneticisinden okunacak ve işlenmek üzere ileti kuyruğu kanalının başarılı olacağı.</span><span class="sxs-lookup"><span data-stu-id="47565-120">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="47565-121">İleti kuyruğu kanalı, WCF kanal yığınında bir sıra Yöneticisi görevi görür.</span><span class="sxs-lookup"><span data-stu-id="47565-121">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="47565-122">İleti kuyruğu kanalı üzerinden bir ileti gönderdiğinizde, gönderenin kuyruk yöneticisinden alınan baytlar üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="47565-122">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="47565-123">Alıcı işlemin ham baytları okuma yeteneği yoksa, ileti hatalı olarak biçimlendirilir ve işlenmeyecek olur; alma işleminin alınan baytları kullanılabilir bir biçime geri çevirme yeteneğine sahip olacağı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47565-123">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
