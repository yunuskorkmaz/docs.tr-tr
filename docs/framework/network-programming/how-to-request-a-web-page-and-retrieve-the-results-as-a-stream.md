---
title: 'Nasıl yapılır: Web sayfası isteme ve sonuçları bir Stream alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2ceaa7cbaf2035276a0ba0105f3969f0249c6132
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084936"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="51bd6-102">Nasıl yapılır: Web sayfası isteme ve sonuçları bir Stream alma</span><span class="sxs-lookup"><span data-stu-id="51bd6-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="51bd6-103">Bu örnek, bir Web sayfası isteme ve sonuçları bir akış alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51bd6-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51bd6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="51bd6-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="51bd6-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="51bd6-105">Compiling the Code</span></span>  
 <span data-ttu-id="51bd6-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="51bd6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="51bd6-107">Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="51bd6-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51bd6-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51bd6-108">See Also</span></span>  
 [<span data-ttu-id="51bd6-109">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="51bd6-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
