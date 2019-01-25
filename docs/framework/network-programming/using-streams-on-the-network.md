---
title: Ağda akışları kullanma
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
ms.openlocfilehash: 9849c64b30ed1021c12f34a7920104537292197a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628467"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="fd54f-102">Ağda akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="fd54f-102">Using Streams on the Network</span></span>
<span data-ttu-id="fd54f-103">Ağ kaynaklarını .NET Framework akışları olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="fd54f-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="fd54f-104">.NET Framework akışları genel düşünerek, aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="fd54f-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
-   <span data-ttu-id="fd54f-105">Web veri göndermek ve almak için yaygın bir yolu.</span><span class="sxs-lookup"><span data-stu-id="fd54f-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="fd54f-106">Hangi gerçek dosyasının içeriğini — HTML, XML veya başka bir şey — uygulamanızın kullanacağı <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> veri göndermek ve almak için.</span><span class="sxs-lookup"><span data-stu-id="fd54f-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
-   <span data-ttu-id="fd54f-107">Arasında .NET Framework akışları ile uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="fd54f-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="fd54f-108">Akışları bunları işlemesi için zengin bir altyapı olan .NET Framework boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd54f-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="fd54f-109">XML verileri okuyan bir uygulama gibi değiştirebileceğiniz bir <xref:System.IO.FileStream> verileri okumak için bir <xref:System.Net.Sockets.NetworkStream> bunun yerine, akışı başlatmak yalnızca birkaç satır kod ile değiştirme.</span><span class="sxs-lookup"><span data-stu-id="fd54f-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="fd54f-110">Arasındaki temel farklar **NetworkStream** sınıfı ve diğer akışlar olduğundan, **NetworkStream** aranabilir, değil <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> özelliği her zaman döndürür **false**ve <xref:System.Net.Sockets.NetworkStream.Seek%2A> ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemleri throw bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="fd54f-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
-   <span data-ttu-id="fd54f-111">Verilerin işlenmesini ulaşır.</span><span class="sxs-lookup"><span data-stu-id="fd54f-111">Processing of data as it arrives.</span></span> <span data-ttu-id="fd54f-112">Uygulamanızı bir bütün indirilmesi için veri kümesi beklenecek zorlamak yerine ağ ulaştıkça akışları verilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd54f-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="fd54f-113"><xref:System.Net.Sockets> Ad alanı içeren bir **NetworkStream** uygulayan sınıf <xref:System.IO.Stream> ağ kaynakları ile kullanılmak üzere özel olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="fd54f-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="fd54f-114">Sınıflar <xref:System.Net.Sockets> ad **NetworkStream** akışları temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="fd54f-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="fd54f-115">Döndürülen akışa kullanarak ağa veri göndermek için arama <xref:System.Net.WebRequest.GetRequestStream%2A> üzerinde <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="fd54f-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="fd54f-116">**WebRequest** sunucuya; istek üst bilgilerini gönderir, ardından çağırarak ağ kaynağına veri gönderebilir <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, veya <xref:System.IO.Stream.Write%2A> döndürülen akışa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd54f-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="fd54f-117">HTTP gibi bazı protokoller, verileri göndermeden önce protokole özgü özelliklerini ayarlamak gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="fd54f-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="fd54f-118">Aşağıdaki kod örneği, veri göndermek için HTTP özel özelliklerin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd54f-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="fd54f-119">Olduğunu varsayar değişkeni `sendData` gönderilecek verileri içeren değişken `sendLength` gönderilecek verileri baytlık sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="fd54f-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="fd54f-120">Ağ üzerinden veri almak için çağrı <xref:System.Net.WebResponse.GetResponseStream%2A> üzerinde <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="fd54f-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="fd54f-121">Çağırarak verileri ağ kaynak ardından okuyabilir <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, veya <xref:System.IO.Stream.Read%2A> döndürülen akışa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd54f-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="fd54f-122">Ağ kaynaklarını akışlardan kullanırken aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fd54f-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
-   <span data-ttu-id="fd54f-123">**CanSeek** özelliği her zaman döndürür **false** beri **NetworkStream** sınıfı, akışta konumu değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fd54f-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="fd54f-124">**Arama** ve **konumu** yöntemleri throw bir **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="fd54f-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
-   <span data-ttu-id="fd54f-125">Kullanırken **WebRequest** ve **WebResponse**, akış çağrılarak oluşturulan örnekleri **GetResponseStream** salt okunurdur ve bunların akışını çağrılarakoluşturulanörnekleri **GetRequestStream** salt yazılır.</span><span class="sxs-lookup"><span data-stu-id="fd54f-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
-   <span data-ttu-id="fd54f-126">Kullanım <xref:System.IO.StreamReader> kodlama daha kolay hale getirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="fd54f-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="fd54f-127">Aşağıdaki kod örneğinde bir **StreamReader** ASCII kodlamalı bir akıştan okumak için bir **WebResponse** (örneğin isteği oluşturma göstermez).</span><span class="sxs-lookup"><span data-stu-id="fd54f-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
-   <span data-ttu-id="fd54f-128">Çağrı **GetResponse yanıtına** ağ kaynaklarını kullanılabilir durumda değilse, engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd54f-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="fd54f-129">Zaman uyumsuz bir istekle kullanmayı düşünmeniz gerekir <xref:System.Net.WebRequest.BeginGetResponse%2A> ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fd54f-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
-   <span data-ttu-id="fd54f-130">Çağrı **GetRequestStream** sunucusuyla bağlantı oluşturulurken engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd54f-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="fd54f-131">Sahip akış için bir zaman uyumsuz istek kullanmayı düşünmeniz gerekir <xref:System.Net.WebRequest.BeginGetRequestStream%2A> ve <xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fd54f-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd54f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd54f-132">See also</span></span>
- [<span data-ttu-id="fd54f-133">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="fd54f-133">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="fd54f-134">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="fd54f-134">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
