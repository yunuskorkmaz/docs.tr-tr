---
title: 'Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 21a5a81c6a5457897078db03fe35eaff330ed62d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647364"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="770b8-102">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="770b8-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="770b8-103">Bu örnekte, WebRequest ile eşleşen protokole özgü WebResponse alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="770b8-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="770b8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="770b8-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="770b8-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="770b8-105">Compiling the Code</span></span>  
 <span data-ttu-id="770b8-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="770b8-106">This example requires:</span></span>  
  
- <span data-ttu-id="770b8-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="770b8-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770b8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="770b8-108">See also</span></span>

- [<span data-ttu-id="770b8-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="770b8-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
