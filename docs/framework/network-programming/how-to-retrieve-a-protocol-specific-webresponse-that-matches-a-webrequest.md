---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
description: .NET Framework bir WebRequest ile eşleşen protokole özgü bir WebResponse almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 920704bedce478ed5a4f7906379a634a3b2a4e31
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584349"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="af7a0-103">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="af7a0-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="af7a0-104">Bu örnek, WebRequest ile eşleşen protokole özgü bir WebResponse 'un nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af7a0-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af7a0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="af7a0-105">Example</span></span>  
  
```csharp  
HttpWebRequest req = (HttpWebRequest)WebRequest.Create("http://www.contoso.com/");
HttpWebResponse resp = (HttpWebResponse)req.GetResponse();
```  
  
```vb  
Dim req As HttpWebRequest = CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)
Dim resp As HttpWebResponse = CType(req.GetResponse(), HttpWebResponse)
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af7a0-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="af7a0-106">Compiling the Code</span></span>  

 <span data-ttu-id="af7a0-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="af7a0-107">This example requires:</span></span>  
  
- <span data-ttu-id="af7a0-108">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="af7a0-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7a0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af7a0-109">See also</span></span>

- [<span data-ttu-id="af7a0-110">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="af7a0-110">Requesting Data</span></span>](requesting-data.md)
