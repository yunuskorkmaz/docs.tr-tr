---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
description: .NET Framework bir WebRequest ile eşleşen protokole özgü bir WebResponse almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fd163c115dcd19c05f93f4c202b043440834ba9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266746"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="e229c-103">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="e229c-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="e229c-104">Bu örnek, WebRequest ile eşleşen protokole özgü bir WebResponse 'un nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e229c-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e229c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e229c-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e229c-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e229c-106">Compiling the Code</span></span>  

 <span data-ttu-id="e229c-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e229c-107">This example requires:</span></span>  
  
- <span data-ttu-id="e229c-108">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="e229c-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e229c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e229c-109">See also</span></span>

- [<span data-ttu-id="e229c-110">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="e229c-110">Requesting Data</span></span>](requesting-data.md)
