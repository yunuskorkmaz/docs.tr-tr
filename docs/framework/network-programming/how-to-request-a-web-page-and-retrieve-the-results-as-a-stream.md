---
title: 'Nasıl yapılır: Web sayfası isteme ve sonuçları bir Stream alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 6481e923c8daabfcfa94adc45d7d4172e47a779a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041615"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="0831a-102">Nasıl yapılır: Web sayfası isteme ve sonuçları bir Stream alma</span><span class="sxs-lookup"><span data-stu-id="0831a-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="0831a-103">Bu örnek, bir Web sayfası isteme ve sonuçları bir akış alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0831a-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0831a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0831a-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0831a-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0831a-105">Compiling the Code</span></span>  
 <span data-ttu-id="0831a-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0831a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="0831a-107">Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="0831a-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0831a-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0831a-108">See Also</span></span>  
 [<span data-ttu-id="0831a-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="0831a-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
