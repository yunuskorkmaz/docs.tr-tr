---
title: 'Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642587"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="fc560-102">Nasıl yapılır: Genel Ara Sunucu Seçimini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="fc560-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="fc560-103">Bu örnekte gönderen bir **WebRequest** için `www.contoso.com` adında bir proxy sunucusu ile genel Ara sunucu seçimini geçersiz `alternateproxy` bağlantı noktası 80 üzerinde.</span><span class="sxs-lookup"><span data-stu-id="fc560-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc560-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc560-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc560-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fc560-105">Compiling the Code</span></span>  
 <span data-ttu-id="fc560-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fc560-106">This example requires:</span></span>  
  
- <span data-ttu-id="fc560-107">A [ `using` yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) için **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fc560-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc560-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc560-108">See also</span></span>

- [<span data-ttu-id="fc560-109">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc560-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="fc560-110">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="fc560-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
