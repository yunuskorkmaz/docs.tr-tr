---
title: 'Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: f902fb3ee97e94c85192836be047dfe632249735
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048487"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="f4b44-102">Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="f4b44-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="f4b44-103">Bu örnekte, HTTP **canlı tutma** davranışının nasıl kapatılacağı ve Web sunucusundan protokol sürüm numarası alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4b44-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4b44-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4b44-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4b44-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f4b44-105">Compiling the Code</span></span>  
 <span data-ttu-id="f4b44-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f4b44-106">This example requires:</span></span>  
  
- <span data-ttu-id="f4b44-107">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="f4b44-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b44-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4b44-108">See also</span></span>

- [<span data-ttu-id="f4b44-109">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="f4b44-109">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="f4b44-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4b44-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="f4b44-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="f4b44-111">HTTP</span></span>](http.md)
