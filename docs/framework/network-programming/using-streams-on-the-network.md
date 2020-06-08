---
title: Ağda Akışları Kullanma
description: .NET Framework, ağ kaynaklarını akışlar olarak temsil eder. NetworkStream sınıfı, ağ kaynaklarıyla kullanılmak üzere Stream sınıfını uygular.
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
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501982"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="990cf-104">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="990cf-104">Using Streams on the Network</span></span>
<span data-ttu-id="990cf-105">Ağ kaynakları .NET Framework akışlar olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="990cf-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="990cf-106">Akışları genel olarak düşünerek, .NET Framework aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="990cf-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="990cf-107">Web verilerini göndermenin ve almanın yaygın bir yolu.</span><span class="sxs-lookup"><span data-stu-id="990cf-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="990cf-108">Dosyanın gerçek içerikleri ne olursa olsun — HTML, XML veya başka bir şey — uygulamanız, <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> veri göndermek ve almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="990cf-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="990cf-109">.NET Framework içindeki akışlarla uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="990cf-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="990cf-110">Akışlar, işlemek için zengin bir altyapıyı içeren .NET Framework boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="990cf-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="990cf-111">Örneğin, <xref:System.IO.FileStream> <xref:System.Net.Sockets.NetworkStream> yalnızca akışı başlatacak olan kodun yalnızca birkaç satırını değiştirerek, bir ' dan veri okumak için bir uygulamayı bir ' dan okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="990cf-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="990cf-112">**NetworkStream** sınıfı ve diğer akışlar arasındaki önemli farklılıklar, **NetworkStream** 'in aranabilir olmadığı, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> özelliğin her zaman **false**döndüğü ve <xref:System.Net.Sockets.NetworkStream.Seek%2A> ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemlerinin bir oluşturması <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="990cf-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="990cf-113">Verilerin ulaştığı gibi işlenmesi.</span><span class="sxs-lookup"><span data-stu-id="990cf-113">Processing of data as it arrives.</span></span> <span data-ttu-id="990cf-114">Akışlar, uygulamanızın bir veri kümesinin tamamını indirilmesini beklemek yerine, ağ üzerinden gelen verilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="990cf-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="990cf-115"><xref:System.Net.Sockets>Ad alanı, **NetworkStream** <xref:System.IO.Stream> sınıfı özel olarak ağ kaynaklarıyla kullanılmak üzere uygulayan bir NetworkStream sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="990cf-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="990cf-116"><xref:System.Net.Sockets>Ad alanındaki sınıflar, akışları temsil etmek Için **NetworkStream** sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="990cf-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="990cf-117">Döndürülen akışı kullanarak ağa veri göndermek için, üzerinde öğesini çağırın <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="990cf-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="990cf-118">**WebRequest** , istek üst bilgilerini sunucuya gönderir; ardından <xref:System.IO.Stream.BeginWrite%2A> , <xref:System.IO.Stream.EndWrite%2A> döndürülen akışta, veya yöntemini çağırarak ağ kaynağına veri gönderebilirsiniz <xref:System.IO.Stream.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="990cf-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="990cf-119">HTTP gibi bazı protokoller, verileri göndermeden önce protokole özgü özellikler ayarlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="990cf-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="990cf-120">Aşağıdaki kod örneğinde, veri göndermek için HTTP 'ye özgü özelliklerin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="990cf-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="990cf-121">Değişkenin `sendData` gönderileceği verileri içerdiğini ve değişkenin `sendLength` gönderileceği verilerin bayt sayısını olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="990cf-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="990cf-122">Ağdan veri almak için ' i arayın <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="990cf-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="990cf-123">Ardından <xref:System.IO.Stream.BeginRead%2A> , <xref:System.IO.Stream.EndRead%2A> döndürülen akışta, veya yöntemini çağırarak ağ kaynağından verileri okuyabilirsiniz <xref:System.IO.Stream.Read%2A> .</span><span class="sxs-lookup"><span data-stu-id="990cf-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="990cf-124">Ağ kaynaklarından akışlar kullanırken, aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="990cf-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="990cf-125">**NetworkStream** sınıfı akıştaki konumu Değiştirelemediğinden **CanSeek** özelliği her zaman **false** değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="990cf-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="990cf-126">**Seek** ve **Position** yöntemleri **NotSupportedException**oluşturur.</span><span class="sxs-lookup"><span data-stu-id="990cf-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="990cf-127">**WebRequest** ve **WebResponse**kullandığınızda, **GetResponseStream** çağrılırken oluşturulan akış örnekleri salt okunurdur ve **GetRequestStream** çağrılırken oluşturulan akış örnekleri salt yazılır.</span><span class="sxs-lookup"><span data-stu-id="990cf-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="990cf-128"><xref:System.IO.StreamReader>Kodlamayı daha kolay hale getirmek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="990cf-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="990cf-129">Aşağıdaki kod örneği bir **Web YANıTıNDAN** ASCII kodlamalı bir akış okumak Için bir **StreamReader** kullanır (örnek, istek oluşturmayı göstermez).</span><span class="sxs-lookup"><span data-stu-id="990cf-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="990cf-130">Ağ kaynaklarının kullanılabilir olup olmadığını **GetResponse** çağrısı engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="990cf-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="990cf-131">Ve yöntemleriyle zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız gerekir <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> .</span><span class="sxs-lookup"><span data-stu-id="990cf-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="990cf-132">Sunucu bağlantısı oluşturulurken **GetRequestStream** çağrısı engelleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="990cf-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="990cf-133">Ve yöntemleriyle akış için zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız <xref:System.Net.WebRequest.BeginGetRequestStream%2A> gerekir <xref:System.Net.WebRequest.EndGetRequestStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="990cf-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="990cf-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="990cf-134">See also</span></span>

- [<span data-ttu-id="990cf-135">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="990cf-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="990cf-136">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="990cf-136">Requesting Data</span></span>](requesting-data.md)
