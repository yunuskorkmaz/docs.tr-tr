---
title: 'Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048267"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="47ae2-102">Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="47ae2-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="47ae2-103">Bu örnek, genel proxy seçimini, `www.contoso.com` bağlantı noktası 80 ' de adlı `alternateproxy` bir ara sunucu ile geçersiz kılacak bir **Web isteği** gönderir.</span><span class="sxs-lookup"><span data-stu-id="47ae2-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ae2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="47ae2-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47ae2-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="47ae2-105">Compiling the Code</span></span>  
 <span data-ttu-id="47ae2-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="47ae2-106">This example requires:</span></span>  
  
- <span data-ttu-id="47ae2-107">**System.net** ad alanı için bir [ `using` yönerge](../../csharp/language-reference/keywords/using-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="47ae2-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ae2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47ae2-108">See also</span></span>

- [<span data-ttu-id="47ae2-109">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="47ae2-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="47ae2-110">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="47ae2-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
