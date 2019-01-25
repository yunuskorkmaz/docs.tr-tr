---
title: "Nasıl yapılır: HTTP'ye özgü özelliklere erişim"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: da696e40248a077e6b8e32e077509bc8a0b589b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619733"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="70471-102">Nasıl yapılır: HTTP'ye özgü özelliklere erişim</span><span class="sxs-lookup"><span data-stu-id="70471-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="70471-103">Bu örnek HTTP devre dışı bırakma gösterir **tutma** davranışı ve get protokol sürümü, Web sunucusu vm'sinden sayı.</span><span class="sxs-lookup"><span data-stu-id="70471-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70471-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="70471-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="70471-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="70471-105">Compiling the Code</span></span>  
 <span data-ttu-id="70471-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="70471-106">This example requires:</span></span>  
  
-   <span data-ttu-id="70471-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="70471-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70471-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70471-108">See also</span></span>
- [<span data-ttu-id="70471-109">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="70471-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="70471-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="70471-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="70471-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="70471-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
