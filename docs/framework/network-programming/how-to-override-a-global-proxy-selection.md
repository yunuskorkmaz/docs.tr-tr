---
title: 'Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: e5f4dc22ad75dc4d4f7dc30f44e6ae304403ef16
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914525"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="89ece-102">Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="89ece-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="89ece-103">Bu örnek, genel proxy seçimini, `www.contoso.com` bağlantı noktası 80 ' de adlı `alternateproxy` bir ara sunucu ile geçersiz kılacak bir **Web isteği** gönderir.</span><span class="sxs-lookup"><span data-stu-id="89ece-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ece-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ece-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89ece-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="89ece-105">Compiling the Code</span></span>  
 <span data-ttu-id="89ece-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="89ece-106">This example requires:</span></span>  
  
- <span data-ttu-id="89ece-107">**System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="89ece-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ece-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ece-108">See also</span></span>

- [<span data-ttu-id="89ece-109">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="89ece-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="89ece-110">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="89ece-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
