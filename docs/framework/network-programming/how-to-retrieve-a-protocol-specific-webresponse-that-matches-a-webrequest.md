---
title: 'Nasıl yapılır: WebRequest ile eşleşen protokole özgü WebResponse alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 3b3b523d6248b3c61a0994728b035bc6f02d5cf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745356"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="8d211-102">Nasıl yapılır: WebRequest ile eşleşen protokole özgü WebResponse alma</span><span class="sxs-lookup"><span data-stu-id="8d211-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="8d211-103">Bu örnekte, WebRequest ile eşleşen protokole özgü WebResponse alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d211-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d211-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d211-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d211-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8d211-105">Compiling the Code</span></span>  
 <span data-ttu-id="8d211-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8d211-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8d211-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8d211-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d211-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d211-108">See also</span></span>
- [<span data-ttu-id="8d211-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="8d211-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
