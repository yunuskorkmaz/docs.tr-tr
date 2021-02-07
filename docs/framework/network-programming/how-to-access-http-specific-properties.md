---
description: 'Daha fazla bilgi edinin: nasıl yapılır: erişim HTTP-Specific özellikleri'
title: 'Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: a54ef247b479cf6cdec8dc28732304cf03b0b202
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729308"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="c16a9-103">Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="c16a9-103">How to: Access HTTP-Specific Properties</span></span>

<span data-ttu-id="c16a9-104">Bu örnekte, HTTP **canlı tutma** davranışının nasıl kapatılacağı ve Web sunucusundan protokol sürüm numarası alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c16a9-104">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c16a9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c16a9-105">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c16a9-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c16a9-106">Compiling the Code</span></span>  

 <span data-ttu-id="c16a9-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c16a9-107">This example requires:</span></span>  
  
- <span data-ttu-id="c16a9-108">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="c16a9-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16a9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c16a9-109">See also</span></span>

- [<span data-ttu-id="c16a9-110">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="c16a9-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c16a9-111">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c16a9-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="c16a9-112">HTTP</span><span class="sxs-lookup"><span data-stu-id="c16a9-112">HTTP</span></span>](http.md)
