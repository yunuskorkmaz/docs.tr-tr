---
title: "Nasıl yapılır: Internet ile iletişim kurmak için bir ara sunucu kullanan bir Webrequest'i etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 1b10d895478a88556cf1d716480de568c8e9c9ad
ms.sourcegitcommit: 2151690e10d91545e2c20d6b5ad222c162b6b83d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2018
ms.locfileid: "50190449"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="ab938-102">Nasıl yapılır: Internet ile iletişim kurmak için bir ara sunucu kullanan bir Webrequest'i etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ab938-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="ab938-103">Bu örnek, tüm olanak sağlayacak bir genel proxy örneği oluşturur <xref:System.Net.WebRequest> Internet ile iletişim kurmak için bir ara sunucu kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="ab938-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="ab938-104">Bu örnek, proxy sunucusu adlandırıldığını varsayar `webproxy` ve üzerinde iletişim bağlantı noktası 80, standart HTTP bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="ab938-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab938-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab938-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab938-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ab938-106">Compiling the Code</span></span>  
 <span data-ttu-id="ab938-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ab938-107">This example requires:</span></span>  
  
-   <span data-ttu-id="ab938-108">A [ `using` yönergesi](../../csharp/language-reference/keywords/using-directive.md) için **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ab938-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab938-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab938-109">See Also</span></span>  
 [<span data-ttu-id="ab938-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="ab938-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="ab938-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="ab938-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
