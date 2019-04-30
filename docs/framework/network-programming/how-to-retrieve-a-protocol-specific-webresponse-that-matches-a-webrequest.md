---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fee2b725afbceef45b9651a7cd88a61b37952e32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642522"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="3dbe1-102">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="3dbe1-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="3dbe1-103">Bu örnekte, WebRequest ile eşleşen protokole özgü WebResponse alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3dbe1-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dbe1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3dbe1-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3dbe1-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3dbe1-105">Compiling the Code</span></span>  
 <span data-ttu-id="3dbe1-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3dbe1-106">This example requires:</span></span>  
  
- <span data-ttu-id="3dbe1-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3dbe1-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dbe1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dbe1-108">See also</span></span>

- [<span data-ttu-id="3dbe1-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="3dbe1-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
