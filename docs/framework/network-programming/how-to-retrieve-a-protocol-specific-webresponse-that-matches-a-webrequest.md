---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 0cb2d11306f52df767d8c053e8ab745696bb8e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048134"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="2466f-102">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="2466f-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="2466f-103">Bu örnek, bir Webİsteği ile eşleşen protokole özgü bir WebYanıtı'nın nasıl alınılsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2466f-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2466f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2466f-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2466f-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2466f-105">Compiling the Code</span></span>  
 <span data-ttu-id="2466f-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2466f-106">This example requires:</span></span>  
  
- <span data-ttu-id="2466f-107">**System.Net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="2466f-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2466f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2466f-108">See also</span></span>

- [<span data-ttu-id="2466f-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="2466f-109">Requesting Data</span></span>](requesting-data.md)
