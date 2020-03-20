---
title: Ağda Akışları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180619"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="8396c-102">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8396c-102">Using Streams on the Network</span></span>
<span data-ttu-id="8396c-103">Ağ kaynakları .NET Framework'de akış olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8396c-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="8396c-104">Akışları genel olarak işleyerek,.NET Framework aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="8396c-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="8396c-105">Web verilerini göndermenin ve almanın yaygın bir yolu.</span><span class="sxs-lookup"><span data-stu-id="8396c-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="8396c-106">Dosyanın gerçek içeriği ne olursa olsun - HTML, XML <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> veya <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> başka bir şey - uygulamanızı kullanır ve veri göndermek ve almak için.</span><span class="sxs-lookup"><span data-stu-id="8396c-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="8396c-107">.NET Framework'deki akışlarla uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="8396c-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="8396c-108">Akışlar, bunları işlemek için zengin bir altyapıya sahip olan .NET Framework boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8396c-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="8396c-109">Örneğin, a'dan <xref:System.IO.FileStream> okunacak verilerden <xref:System.Net.Sockets.NetworkStream> XML verilerini okuyan bir uygulamayı, akışı başlatmayı yalnızca birkaç kod satırını değiştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8396c-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="8396c-110">**NetworkStream** sınıfı ve diğer akışlar arasındaki en büyük farklar **NetworkStream** <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> aranmaz, özellik <xref:System.Net.Sockets.NetworkStream.Seek%2A> her zaman <xref:System.NotSupportedException> **yanlış**döndürür ve ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemleri atmak bir .</span><span class="sxs-lookup"><span data-stu-id="8396c-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="8396c-111">Verilerin geldiği gibi işlenmesi.</span><span class="sxs-lookup"><span data-stu-id="8396c-111">Processing of data as it arrives.</span></span> <span data-ttu-id="8396c-112">Akışlar, uygulamanızı tüm veri kümesinin indirilmesi için beklemeye zorlamak yerine, ağdan gelen verilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8396c-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="8396c-113">Ad <xref:System.Net.Sockets> alanı, <xref:System.IO.Stream> sınıfı ağ kaynaklarıyla kullanılmak üzere özel olarak uygulayan bir **NetworkStream** sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="8396c-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="8396c-114">Ad alanındaki sınıflar akışları temsil etmek için Ağ Akışı sınıfını kullanır. **NetworkStream** <xref:System.Net.Sockets></span><span class="sxs-lookup"><span data-stu-id="8396c-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="8396c-115">Döndürülen akışı kullanarak ağa veri göndermek <xref:System.Net.WebRequest.GetRequestStream%2A> için. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="8396c-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="8396c-116">**WebRequest** sunucuya istek üstbilgilerini gönderir; ardından, döndürülen akıştaki <xref:System.IO.Stream.BeginWrite%2A>" veya <xref:System.IO.Stream.EndWrite%2A> <xref:System.IO.Stream.Write%2A> yöntemi" çağırarak ağ kaynağına veri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8396c-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="8396c-117">HTTP gibi bazı protokoller, veri göndermeden önce protokole özgü özellikler ayarlamanızı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="8396c-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="8396c-118">Aşağıdaki kod örneği, veri göndermek için HTTP'ye özgü özelliklerin nasıl ayarlanır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8396c-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="8396c-119">Değişkenin `sendData` gönderilecek verileri içerdiğini ve değişkenin `sendLength` gönderilecek bayt veri sayısı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8396c-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="8396c-120">Ağdan veri almak için, <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="8396c-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="8396c-121">Daha sonra, döndürülen akıştaki <xref:System.IO.Stream.BeginRead%2A>" <xref:System.IO.Stream.EndRead%2A>veya <xref:System.IO.Stream.Read%2A> yöntemi" çağırarak ağ kaynağındaki verileri okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8396c-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="8396c-122">Ağ kaynaklarından gelen akışları kullanırken aşağıdaki noktaları aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8396c-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="8396c-123">**Ağ Akışı** sınıfı akıştaki konumu değiştiremediğinden **CanSeek** özelliği her zaman **yanlış** döndürür.</span><span class="sxs-lookup"><span data-stu-id="8396c-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="8396c-124">**Arama** ve **Konum** yöntemleri **NotSupportedException**atar.</span><span class="sxs-lookup"><span data-stu-id="8396c-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="8396c-125">**WebRequest** ve **WebResponse'u**kullandığınızda, **GetResponseStream'i** arayarak oluşturulan akış örnekleri salt okunur ve **GetRequestStream'i** arayarak oluşturulan akış örnekleri yalnızca yazmadır.</span><span class="sxs-lookup"><span data-stu-id="8396c-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="8396c-126">Kodlamayı <xref:System.IO.StreamReader> kolaylaştırmak için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="8396c-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="8396c-127">Aşağıdaki kod örneği, **Bir WebResponse'dan** ASCII kodlanmış bir akışı okumak için bir **StreamReader** kullanır (örnek, isteği oluşturmayı göstermez).</span><span class="sxs-lookup"><span data-stu-id="8396c-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="8396c-128">Ağ kaynakları yoksa **GetResponse** çağrısı engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="8396c-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="8396c-129"><xref:System.Net.WebRequest.BeginGetResponse%2A> Senvel ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemlerle bir asynchronous istek kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8396c-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="8396c-130">Sunucuya bağlantı oluşturulurken **GetRequestStream'e** çağrı engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="8396c-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="8396c-131">Akış ve <xref:System.Net.WebRequest.BeginGetRequestStream%2A> <xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemlerle asenkron bir istek kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8396c-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8396c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8396c-132">See also</span></span>

- [<span data-ttu-id="8396c-133">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="8396c-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="8396c-134">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="8396c-134">Requesting Data</span></span>](requesting-data.md)
