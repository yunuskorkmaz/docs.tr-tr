---
title: "Nasıl yapılır: Internet ile iletişim kurmak için bir ara sunucu kullanan bir Webrequest'i etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86bf21580db9bc6d9890f0935e283b653ba2e0b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397796"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="fc2b5-102">Nasıl yapılır: Internet ile iletişim kurmak için bir ara sunucu kullanan bir Webrequest'i etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fc2b5-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="fc2b5-103">Bu örnek, tüm olanak sağlayacak bir genel proxy örneği oluşturur <xref:System.Net.WebRequest> Internet ile iletişim kurmak için bir ara sunucu kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="fc2b5-104">Bu örnek, proxy sunucusu adlandırıldığını varsayar `webproxy` ve üzerinde iletişim bağlantı noktası 80, standart HTTP bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc2b5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc2b5-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc2b5-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fc2b5-106">Compiling the Code</span></span>  
 <span data-ttu-id="fc2b5-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fc2b5-107">This example requires:</span></span>  
  
-   <span data-ttu-id="fc2b5-108">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2b5-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-109">See Also</span></span>  
 [<span data-ttu-id="fc2b5-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc2b5-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="fc2b5-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="fc2b5-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
