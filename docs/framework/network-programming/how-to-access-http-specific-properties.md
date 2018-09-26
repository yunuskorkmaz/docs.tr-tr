---
title: "Nasıl yapılır: HTTP'ye özgü özelliklere erişim"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f008cf82b80e29f8fe741034a0e820b5eae5b0ba
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193770"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="8db35-102">Nasıl yapılır: HTTP'ye özgü özelliklere erişim</span><span class="sxs-lookup"><span data-stu-id="8db35-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="8db35-103">Bu örnek HTTP devre dışı bırakma gösterir **tutma** davranışı ve get protokol sürümü, Web sunucusu vm'sinden sayı.</span><span class="sxs-lookup"><span data-stu-id="8db35-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8db35-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8db35-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8db35-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8db35-105">Compiling the Code</span></span>  
 <span data-ttu-id="8db35-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8db35-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8db35-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8db35-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db35-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8db35-108">See Also</span></span>  
 [<span data-ttu-id="8db35-109">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="8db35-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="8db35-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="8db35-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="8db35-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="8db35-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
