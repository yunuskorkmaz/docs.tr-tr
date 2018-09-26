---
title: 'Nasıl yapılır: Genel Ara sunucu seçimini geçersiz kılma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2be271123e34f155a79269d3b810c50fe24a40c6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112302"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="0e5df-102">Nasıl yapılır: Genel Ara sunucu seçimini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="0e5df-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="0e5df-103">Bu örnekte gönderen bir **WebRequest** için `www.contoso.com` adında bir proxy sunucusu ile genel Ara sunucu seçimini geçersiz `alternateproxy` bağlantı noktası 80 üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0e5df-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e5df-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e5df-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e5df-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e5df-105">Compiling the Code</span></span>  
 <span data-ttu-id="0e5df-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0e5df-106">This example requires:</span></span>  
  
-   <span data-ttu-id="0e5df-107">A [ `using` yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) için **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0e5df-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5df-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e5df-108">See Also</span></span>  
 [<span data-ttu-id="0e5df-109">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e5df-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="0e5df-110">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="0e5df-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
