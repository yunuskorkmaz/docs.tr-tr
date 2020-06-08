---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
description: .NET Framework bir WebRequest ile eşleşen protokole özgü bir WebResponse almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502463"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="60f9e-103">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="60f9e-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="60f9e-104">Bu örnek, WebRequest ile eşleşen protokole özgü bir WebResponse 'un nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="60f9e-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f9e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="60f9e-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60f9e-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="60f9e-106">Compiling the Code</span></span>  
 <span data-ttu-id="60f9e-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="60f9e-107">This example requires:</span></span>  
  
- <span data-ttu-id="60f9e-108">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="60f9e-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f9e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60f9e-109">See also</span></span>

- [<span data-ttu-id="60f9e-110">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="60f9e-110">Requesting Data</span></span>](requesting-data.md)
