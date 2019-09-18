---
title: 'Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048291"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="46a39-102">Nasıl yapılır: İnternet ile İletişim Kurmak Üzere Ara Sunucu Kullanan bir WebRequest’i Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="46a39-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="46a39-103">Bu örnek, Internet ile iletişim kurmak için bir proxy kullanmasını <xref:System.Net.WebRequest> sağlayacak küresel bir ara sunucu örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46a39-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="46a39-104">Örnek, proxy sunucusunun adlandırıldığını `webproxy` ve standart http bağlantı noktası 80 bağlantı noktası üzerinden iletişim kurduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46a39-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46a39-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a39-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46a39-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="46a39-106">Compiling the Code</span></span>  
 <span data-ttu-id="46a39-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="46a39-107">This example requires:</span></span>  
  
- <span data-ttu-id="46a39-108">**System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="46a39-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a39-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46a39-109">See also</span></span>

- [<span data-ttu-id="46a39-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="46a39-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="46a39-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="46a39-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
