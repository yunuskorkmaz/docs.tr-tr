---
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489488"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="54dd0-102">ByteStream Kodlayıcı ile İkili Nesneler Kodlama</span><span class="sxs-lookup"><span data-stu-id="54dd0-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="54dd0-103">Ham ikili veri Windows Communication Foundation (WCF) ile gönderme ve alma yapılandırılmış kullanarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="54dd0-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="54dd0-104">Bayt akışı ileti Kodlayıcı mimarisi</span><span class="sxs-lookup"><span data-stu-id="54dd0-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="54dd0-105">WCF tarafından kullanılan ikili ileti Kodlayıcı işleme, doğrulama veya iletisi temel ikili verileri tanımlamak için hiçbir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="54dd0-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="54dd0-106">Veri paketi XML kodlanmış, gönderilen, alınan ve kodunu çözdü.</span><span class="sxs-lookup"><span data-stu-id="54dd0-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="54dd0-107">Kodlayıcı, taşıma ve ileti kuyruğuna ileti gönderilmeden önce geçirilen sonra verileri işler.</span><span class="sxs-lookup"><span data-stu-id="54dd0-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="54dd0-108">İkili kodlama ileti verilerde işlevsellik, sarmalar `<binary>` öğeleri gönderme ve iletiyi aldıktan sonra öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="54dd0-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="54dd0-109">Bayt akışı ileti Kodlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="54dd0-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="54dd0-110">Aşağıdaki örnek bayt akışı ileti Kodlayıcı uygulayan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54dd0-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="54dd0-111">Aşağıdaki örnek, çağrılan hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="54dd0-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="54dd0-112">Bir ileti altyapısı (örneğin, bir yönlendirici) uygulayan bir hizmet kullanarak söz konusu olduğunda, ileti inceleyerek, doğrulama veya aksi halde iletisiyle etkileşim olmadan aşağıdaki örnekte gösterildiği gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="54dd0-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="54dd0-113">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="54dd0-113">Scenarios</span></span>  
 <span data-ttu-id="54dd0-114">Bayt akışı Kodlayıcı aşağıdaki senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="54dd0-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="54dd0-115">JPEG Resim WCF kullanan bilgisayarlar arasında aktarılıyor.</span><span class="sxs-lookup"><span data-stu-id="54dd0-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="54dd0-116">Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır.</span><span class="sxs-lookup"><span data-stu-id="54dd0-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="54dd0-117">Hizmet ikili verileri alır ve resmi görüntüle.</span><span class="sxs-lookup"><span data-stu-id="54dd0-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="54dd0-118">Bir ileti sırası bilgilerini okuma ve işleniyor.</span><span class="sxs-lookup"><span data-stu-id="54dd0-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="54dd0-119">İleti bir ileti sırası Yöneticisi'nden okuma ve ileti sırası kanalı işlenecek geçirildi.</span><span class="sxs-lookup"><span data-stu-id="54dd0-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="54dd0-120">İleti sırası kanal WCF kanalı yığınında sıra yöneticisi olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="54dd0-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="54dd0-121">İleti sırası kanal üzerinden ileti gönderme söz konusu olduğunda, gönderenin Kuyruk Yöneticisi'nden alınan bayt üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="54dd0-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="54dd0-122">Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi alınan bayt kullanılabilir biçime çevirme özelliği olduğunu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="54dd0-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
