---
title: 'Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma'
description: Bir URL 'ye Web Isteği göndererek genel proxy seçimini geçersiz kılmak için bu örneği izleyin. Bu, seçimi bir ara sunucu ile geçersiz kılar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502515"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="262a8-103">Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="262a8-103">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="262a8-104">Bu örnek **WebRequest** `www.contoso.com` , genel proxy seçimini, `alternateproxy` bağlantı noktası 80 ' de adlı bir ara sunucu Ile geçersiz kılacak bir Web isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="262a8-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="262a8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="262a8-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="262a8-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="262a8-106">Compiling the Code</span></span>  
 <span data-ttu-id="262a8-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="262a8-107">This example requires:</span></span>  
  
- <span data-ttu-id="262a8-108">**System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="262a8-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262a8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="262a8-109">See also</span></span>

- [<span data-ttu-id="262a8-110">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="262a8-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="262a8-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="262a8-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
