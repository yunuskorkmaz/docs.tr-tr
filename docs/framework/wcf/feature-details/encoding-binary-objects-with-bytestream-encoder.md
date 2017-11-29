---
title: "ByteStream Kodlayıcı ile İkili Nesneler Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acf9d2ace66702c5f0bc522d97ae92869891a38b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="b40cc-102">ByteStream Kodlayıcı ile İkili Nesneler Kodlama</span><span class="sxs-lookup"><span data-stu-id="b40cc-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="b40cc-103">Ham ikili verileri gönderip [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanılarak yapılandırılmış <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b40cc-103">Sending and receiving raw binary data with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="b40cc-104">Bayt akışı ileti Kodlayıcı mimarisi</span><span class="sxs-lookup"><span data-stu-id="b40cc-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="b40cc-105">Tarafından kullanılan ikili ileti Kodlayıcı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işleme, doğrulama veya iletisi temel ikili verileri tanımlamak için hiçbir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="b40cc-105">The binary message encoder used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="b40cc-106">Veri paketi XML kodlanmış, gönderilen, alınan ve kodunu çözdü.</span><span class="sxs-lookup"><span data-stu-id="b40cc-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="b40cc-107">Kodlayıcı, taşıma ve ileti kuyruğuna ileti gönderilmeden önce geçirilen sonra verileri işler.</span><span class="sxs-lookup"><span data-stu-id="b40cc-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="b40cc-108">İkili kodlama ileti verilerde işlevsellik, sarmalar `<binary>` öğeleri gönderme ve iletiyi aldıktan sonra öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b40cc-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="b40cc-109">Bayt akışı ileti Kodlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="b40cc-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="b40cc-110">Aşağıdaki örnek bayt akışı ileti Kodlayıcı uygulayan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b40cc-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="b40cc-111">Aşağıdaki örnek, çağrılan hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="b40cc-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="b40cc-112">Bir ileti altyapısı (örneğin, bir yönlendirici) uygulayan bir hizmet kullanarak söz konusu olduğunda, ileti inceleyerek, doğrulama veya aksi halde iletisiyle etkileşim olmadan aşağıdaki örnekte gösterildiği gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="b40cc-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="b40cc-113">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="b40cc-113">Scenarios</span></span>  
 <span data-ttu-id="b40cc-114">Bayt akışı Kodlayıcı aşağıdaki senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b40cc-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="b40cc-115">JPEG Resim kullanarak bilgisayarlar arasında veri aktarımı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b40cc-115">Transferring a JPEG image between computers using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="b40cc-116">Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b40cc-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="b40cc-117">Hizmet ikili verileri alır ve resmi görüntüle.</span><span class="sxs-lookup"><span data-stu-id="b40cc-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="b40cc-118">Bir ileti sırası bilgilerini okuma ve işleniyor.</span><span class="sxs-lookup"><span data-stu-id="b40cc-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="b40cc-119">İleti bir ileti sırası Yöneticisi'nden okuma ve ileti sırası kanalı işlenecek geçirildi.</span><span class="sxs-lookup"><span data-stu-id="b40cc-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="b40cc-120">Bir kuyruk Yöneticisi'nde ileti sırası kanal görecek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal yığını.</span><span class="sxs-lookup"><span data-stu-id="b40cc-120">The message queue channel will act as a queue manager in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack.</span></span>  
  
 <span data-ttu-id="b40cc-121">İleti sırası kanal üzerinden ileti gönderme söz konusu olduğunda, gönderenin Kuyruk Yöneticisi'nden alınan bayt üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b40cc-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="b40cc-122">Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi alınan bayt kullanılabilir biçime çevirme özelliği olduğunu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b40cc-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
