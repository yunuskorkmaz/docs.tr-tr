---
title: 'Nasıl yapılır: WebRequest ile eşleşen protokole özgü WebResponse alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2a72e57156903c9d436a49aaf6da596868af4003
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454875"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="8c922-102">Nasıl yapılır: WebRequest ile eşleşen protokole özgü WebResponse alma</span><span class="sxs-lookup"><span data-stu-id="8c922-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="8c922-103">Bu örnekte, WebRequest ile eşleşen protokole özgü WebResponse alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c922-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c922-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c922-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c922-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8c922-105">Compiling the Code</span></span>  
 <span data-ttu-id="8c922-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8c922-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8c922-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8c922-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c922-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c922-108">See Also</span></span>  
 [<span data-ttu-id="8c922-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="8c922-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
